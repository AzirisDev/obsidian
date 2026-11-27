We are going to create secrets in Azure Key Vault. Then sync it with our kubernetes cluster.

#### Terraform code changes

We add in `azurerm_kubernetes_cluster:
```
  key_vault_secrets_provider {
    secret_rotation_enabled = false
  }
``` 
We need it to enable the Azure secrets vault CSI driver. 

#### Azure Key Vault
Creating a Key Vault itself
```
data "azurerm_client_config" "current" {}

resource "azurerm_key_vault" "mercury_vault" {
  name                = "kv-n8n-mercury"
  location            = azurerm_resource_group.aks.location
  resource_group_name = azurerm_resource_group.aks.name
  tenant_id           = data.azurerm_client_config.current.tenant_id
  sku_name            = "standard"

  # Make it easy to destroy and recreate
  soft_delete_retention_days = 7
  purge_protection_enabled   = false

  # Allow Terraform to manage secrets
  rbac_authorization_enabled = true
  depends_on                 = [azurerm_kubernetes_cluster.main]
}
```

Permissions
```
# Give yourself permission to manage secrets
resource "azurerm_role_assignment" "kv_admin" {
  scope                = azurerm_key_vault.mercury_vault.id
  role_definition_name = "Key Vault Administrator"
  principal_id         = data.azurerm_client_config.current.object_id
}
# Give kubernetes permission to access/decode secrets 
resource "azurerm_role_assignment" "aks_keyvault_secrets_provider" {
  scope                = azurerm_key_vault.mercury_vault.id
  role_definition_name = "Key Vault Secrets User"
  principal_id         = azurerm_kubernetes_cluster.main.key_vault_secrets_provider[0].secret_identity[0].object_id
}
```

Create the secrets
```
resource "azurerm_key_vault_secret" "db_host" {
  name         = "db-host"
  value        = azurerm_postgresql_flexible_server.n8n_db.fqdn
  key_vault_id = azurerm_key_vault.mercury_vault.id

  depends_on = [azurerm_role_assignment.kv_admin]
}

resource "azurerm_key_vault_secret" "db_name" {
  name         = "db-name"
  value        = azurerm_postgresql_flexible_server_database.n8n.name
  key_vault_id = azurerm_key_vault.mercury_vault.id

  depends_on = [azurerm_role_assignment.kv_admin]
}

resource "azurerm_key_vault_secret" "db_user" {
  name         = "db-user"
  value        = azurerm_postgresql_flexible_server.n8n_db.administrator_login
  key_vault_id = azurerm_key_vault.mercury_vault.id

  depends_on = [azurerm_role_assignment.kv_admin]
}

resource "azurerm_key_vault_secret" "db_password" {
  name         = "db-password"
  value        = "n8n-password-123"
  key_vault_id = azurerm_key_vault.mercury_vault.id

  depends_on = [azurerm_role_assignment.kv_admin]
}

output "key_vault_name" {
  value = azurerm_key_vault.mercury_vault.name
}

output "key_vault_uri" {
  value = azurerm_key_vault.mercury_vault.vault_uri
}

# We are going to add that to kubernetes secrets
output "aks_keyvault_secrets_provider_client_id" {
  value       = azurerm_kubernetes_cluster.main.key_vault_secrets_provider[0].secret_identity[0].client_id
  description = "AKS Key Vault Secrets Provider Client ID for use in SecretProviderClass"
} 
```

#### Manifests
In n8n yaml files

In `deployment.yaml`:
```
	...
	envFrom:
		...
		- secretRef:
			name: n8n-container-env
	volumeMounts:
		...
		- mountPath: /mnt/secrets-store
			name: secrets-store
			readOnly: true
	...
volumes:
	...
	- name: secrets-store
		csi:
			driver: secrets-store.csi.k8s.io
			readOnly: true
			volumeAttributes :
				secretProviderClass: n8n-secrets
```
We have to mount that secrets to the pod as a volume to access it. That is how Container Storage Interface (CSI) works.

We also have `secrets.yaml`, this connects to Azure Key Vault secrets and creates kubernetes secrets:
```
apiVersion: secrets-store.csi.x-k8s.io/v1
kind: SecretProviderClass
metadata:
  name: n8n-secrets
spec:
  provider: azure
  parameters:
    usePodIdentity: "false"
    useVMManagedIdentity: "true"
    # It is client ID that terraform outputed - secrets provider client ID
    userAssignedIdentityID: "8fffcdf6-d232-4faa-be30-6d62fdef31a9"
    # We have that in main.tf
    keyvaultName: "kv-n8n-mercury"
    # We can get that by az account list
    tenantId: "6c0d1498-a808-4d41-a865-fdebeb412738"
    objects: |
	  # secret names in Azure Key Vault
      array:
        - |
          objectName: db-user
          objectType: secret
        - |
          objectName: db-password
          objectType: secret 
  secretObjects:
	  # Name of kubernetes secrets object
    - secretName: n8n-container-env
      type: Opaque
      # It kubernetes secret data connected to object from Azure Key Vault
      data:
        - objectName: db-user
          # those we get from n8n docs for db
          key: DB_POSTGRESDB_USER
        - objectName: db-password
          key: DB_POSTGRESDB_PASSWORD
```


Links:

202611272152

