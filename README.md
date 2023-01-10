# TerraformingWithTerraform
Testing how to do Infrastructure as Code with Terraform

# Requirements
- Terraform
- Azure CLI

`Invoke-WebRequest -Uri https://aka.ms/installazurecliwindows -OutFile .\AzureCLI.msi; Start-Process msiexec.exe -Wait -ArgumentList '/I AzureCLI.msi /quiet'; rm .\AzureCLI.msi`

# Setup: based on https://developer.hashicorp.com/terraform/tutorials/azure-get-started/azure-build
1. Authenticate to Azure: `az login`
1. On successful authentication, your subscription info will be displayed in the terminal, take note of the subscription id.
1. Set the desired subscription id for use with Azure CLI: `az account set --subscription "35akss-subscription-id"`
1. Create a Service Principal, the application with the authentication tokens Terraform needs to perform actions:
`az ad sp create-for-rbac --role="Contributor" --scopes="/subscriptions/<SUBSCRIPTION_ID>"`
1. Set environment variables. Use values from the output of the Service Principal command.
`$ $Env:ARM_CLIENT_ID = "<APPID_VALUE>"`
`$ $Env:ARM_CLIENT_SECRET = "<PASSWORD_VALUE>"`
`$ $Env:ARM_SUBSCRIPTION_ID = "<SUBSCRIPTION_ID>"`
`$ $Env:ARM_TENANT_ID = "<TENANT_VALUE>"`