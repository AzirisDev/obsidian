# Azure CLI / Terraform: AADSTS530035 "Blocked by security defaults"

## Symptom
- `az login --use-device-code` worked one day, failed the next with:
  `AADSTS530035: Access has been blocked by security defaults`
- Browser showed: "Your sign-in was successful but you don't have permission to access this resource" (error 530035)
- `terraform plan` failed with the same error via the azurerm provider (it gets tokens through the Azure CLI)

## Root cause
- The tenant had **Security defaults** enabled, so MFA is required for Azure management.
- My login (Gmail) is a **personal Microsoft account (MSA)**, not a native Entra user.
  The tenant's Security info page shows "No methods available", so MFA can't be registered there.
- With no way to challenge MFA, Entra **blocks** any sign-in it considers risky
  (device code flow plus an unregistered device both raise risk).
  That's why it worked yesterday and failed today: the risk score changed, not the config.

## Misleading things
- `az account list` works even when logged out, because it only reads the local cache (`~/.azure/azureProfile.json`).
  → Real check: `az account get-access-token --query expiresOn -o tsv`
- `az login` without `--tenant` can appear to succeed, but tokens for the actual tenant still get blocked.
- The subscription ID was **not** the problem. Auth failed before subscriptions were even listed.
- `aka.ms/mfasetup` without a tenant redirects to the "Microsoft Services" tenant → error.
  Tenant-scoped URL: `https://mysignins.microsoft.com/security-info?tenant=<TENANT_ID>`

## Fixes
1. **Disable security defaults** (OK for a personal lab tenant)
   Portal → Microsoft Entra ID → Overview → Properties → Manage security defaults → Disabled
   Propagation takes about 5–10 min.
2. **Protect the account itself**: enable two-step verification on the MSA
   account.microsoft.com/security → Advanced security options → Authenticator app + Two-step verification ON
   Save the recovery code in the password manager.
3. **Use a service principal for Terraform/CI** (no interactive login needed)
   Created in portal Cloud Shell (`>_` icon):
   ```bash
   az ad sp create-for-rbac --name mercury-workflows-sp --role Contributor \
     --scopes /subscriptions/<SUBSCRIPTION_ID>
   ```
   On the machine running Terraform:
   ```bash
   export ARM_CLIENT_ID="<appId>"
   export ARM_CLIENT_SECRET="<password>"
   export ARM_TENANT_ID="<TENANT_ID>"
   export ARM_SUBSCRIPTION_ID="<SUBSCRIPTION_ID>"
   ```
   The provider block stays clean: `provider "azurerm" { features {} }`
   Keep the secrets in a `.env` outside git (in `.gitignore`), loaded via mise `[env]` or direnv.

## Correct CLI login (from the Dell, approving in the Mac browser)
```bash
az logout
az login --tenant <TENANT_ID> --use-device-code
az account get-access-token --query expiresOn -o tsv
```

## Concepts
- **Tenant** (Entra ID directory): identities + policies (security defaults live here). "Who are you?"
- **Subscription**: billing + access boundary, trusts exactly one tenant. "What can you create, who pays?"
- Hierarchy: Tenant → Subscription → Resource groups → Resources
- Tenant ID isn't secret on its own, but there's no need to publish it.

## My values
- Tenant: Default Directory, `azim228228gmail.onmicrosoft.com`, ID `ca613f61-bf43-48eb-a614-3a2806d706f0`
- Subscription: "Azure subscription 1", ID `32c1e551-2ca1-4005-800a-708959d57556`, role Owner
- Setup: project on Dell (Ubuntu), browser on MacBook
- Free credit expires around 2026-12-18. Deallocate `test01` VM when not in use.

## Useful checks
```bash
az account show -o table                          # which tenant/subscription is selected
az account get-access-token --query expiresOn -o tsv   # is the session actually valid
az group list -o table                            # real API call
```

Links:

202611191528

