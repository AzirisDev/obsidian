1) `mise install terraform`
2) install `Azur CLI`
	`curl -fsSL 'https://azurecliprod.blob.core.windows.net/$root/deb_install.sh' | sudo bash`
3) Login to Azure environment:
	`az login --use-device-code`
4) Check login:
	`az account list` - it will give us information about account 
5) In `phase-1` directory create `vm.tf` file and put inside this:
> [!info]- `vm.tf` — full config (phase-1, working: `Standard_B2ts_v2`)
> ```hcl
> terraform {
>   required_version = ">= 1.0"
>   required_providers {
>     azurerm = {
>       source  = "hashicorp/azurerm"
>       version = "~> 4.0"
>     }
>   }
> }
>
> provider "azurerm" {
>   features {}
>   subscription_id = "32c1e551-2ca1-4005-800a-708959d57556"
> }
>
> # Resource Group
> resource "azurerm_resource_group" "main" {
>   name     = "rg-terraform-demo"
>   location = "centralindia"
> }
>
> resource "azurerm_resource_group" "demo_state" {
>   name     = "rg-state-demo"
>   location = "centralindia"
> }
>
> # Virtual Network
> resource "azurerm_virtual_network" "main" {
>   name                = "vnet-demo"
>   address_space       = ["10.0.0.0/16"]
>   location            = azurerm_resource_group.main.location
>   resource_group_name = azurerm_resource_group.main.name
> }
>
> # Subnet
> resource "azurerm_subnet" "main" {
>   name                 = "subnet-demo"
>   resource_group_name  = azurerm_resource_group.main.name
>   virtual_network_name = azurerm_virtual_network.main.name
>   address_prefixes     = ["10.0.1.0/24"]
> }
>
> # Public IP
> resource "azurerm_public_ip" "main" {
>   name                = "pip-demo"
>   location            = azurerm_resource_group.main.location
>   resource_group_name = azurerm_resource_group.main.name
>   allocation_method   = "Static"
> }
>
> # Network Security Group (Firewall Rules)
> resource "azurerm_network_security_group" "main" {
>   name                = "nsg-demo"
>   location            = azurerm_resource_group.main.location
>   resource_group_name = azurerm_resource_group.main.name
>
>   security_rule {
>     name                       = "SSH"
>     priority                   = 1001
>     direction                  = "Inbound"
>     access                     = "Allow"
>     protocol                   = "Tcp"
>     source_port_range          = "*"
>     destination_port_range     = "22"
>     source_address_prefix      = "*"
>     destination_address_prefix = "*"
>   }
> }
>
> # Network Interface
> resource "azurerm_network_interface" "main" {
>   name                = "nic-demo"
>   location            = azurerm_resource_group.main.location
>   resource_group_name = azurerm_resource_group.main.name
>
>   ip_configuration {
>     name                          = "internal"
>     subnet_id                     = azurerm_subnet.main.id
>     private_ip_address_allocation = "Dynamic"
>     public_ip_address_id          = azurerm_public_ip.main.id
>   }
> }
>
> # Connect NSG to NIC
> resource "azurerm_network_interface_security_group_association" "main" {
>   network_interface_id      = azurerm_network_interface.main.id
>   network_security_group_id = azurerm_network_security_group.main.id
> }
>
> # Virtual Machine
> resource "azurerm_linux_virtual_machine" "main" {
>   name                = "vm-demo"
>   resource_group_name = azurerm_resource_group.main.name
>   location            = azurerm_resource_group.main.location
>   size                = "Standard_B2ts_v2"
>   admin_username      = "azureuser"
>
>   network_interface_ids = [
>     azurerm_network_interface.main.id,
>   ]
>
>   admin_ssh_key {
>     username   = "azureuser"
>     public_key = file("~/.ssh/mercury.pub")
>   }
>
>   os_disk {
>     caching              = "ReadWrite"
>     storage_account_type = "Standard_LRS"
>   }
>
>   source_image_reference {
>     publisher = "Canonical"
>     offer     = "ubuntu-24_04-lts"
>     sku       = "server"
>     version   = "latest"
>   }
> }
>
> # Output the public IP so we can SSH
> output "public_ip" {
>   value = azurerm_public_ip.main.ip_address
> }
>
> output "ssh_command" {
>   value = "ssh -i ~/.ssh/mercury azureuser@${azurerm_public_ip.main.ip_address}"
> }
> ```

6) Currently it will not work, cause we have to do `terraform init` and download the `azurerm` - Azure provider. It sets up where state is stored: a local `terraform.tfstate` file by default, or a remote backend like S3, GCS, or Terraform Cloud. Also creates `.terraform` directory and `.terreform.lock.hcl`
7) We have to create ssh key pair, cause we pass it to `admin_ssh_key` in VM:
```
# Generate SSH key with custom name
ssh-keygen -t rsa -b 4096 -f ~/.ssh/mercury -C "your.email@example.com"
# Press enter twice for no passphrase (or set one)

# Verify it exists
cat ~/.ssh/mercury.pub
```
8) `terrafrom plan` is like `git status`, it will talk to Azure API via `azure CLI` and identify what it is going to apply.
9) `terraform apply` - again will run `terraform plan`, show the plan, then apply those changes.
10) After apply, things are created and also we see `terraform.tfstate` is created.
> [!warning] > Don't edit and commit `terraform.tfstate` file

Usually those files live in storage accounts, not in local machines, so that multiple people use it.
11) `terraform destroy` deletes everything that we mention in `vm.tf` file



#### [[Troubles with login]]

Links:

202611181545

