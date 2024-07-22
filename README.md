# Deploying Azure Backup Resources with Terraform and GitHub Actions

This task demonstrates how to automate the deployment of a comprehensive backup solution for your Azure resources using Terraform and GitHub Actions.

## Overview

This task focuses on creating and managing Azure Backup resources for two scenarios:
1. VM Backup
2. File Share Backup

Each scenario includes its own set of resources and configurations.

## Prerequisites

- Completed setup from the previous task (Azure infrastructure deployment with Terraform and GitHub Actions)
- Basic understanding of Azure Backup concepts
- Azure subscription with necessary permissions

## Steps to Complete the Task

**1. Define Project Structure**

The project consists of several Terraform configuration files:

- `VM.tf`: Configures resources for VM backup.
- `FileShare.tf`: Configures resources for File Share backup.
- `provider.tf`: Specifies the required providers and their versions.
- `variables.tf`: Defines input variables.
- `terraform.tfvars`: Sets values for the defined variables.

**2. VM Backup Configuration (`VM.tf`)**

- `Resource Group`: A dedicated resource group for VM backup resources.
- `Recovery Services Vault`: A vault to store VM backup data.
- `Backup Policy`: Defines the schedule and retention period for VM backups.
- `Random ID`: Generates a unique identifier for the vault name.

**3. File Share Backup Configuration (`FileShare.tf`)**

- `Resource Group`: A separate resource group for File Share backup resources.
- `Recovery Services Vault`: A vault to store File Share backup data.
- `Storage Account`: Hosts the File Share to be backed up.
- `File Share`: The actual File Share that will be backed up.
- `Backup Container`: Registers the Storage Account with the Recovery Services Vault.
- `Backup Policy`: Defines the schedule and retention period for File Share backups.
- `Random IDs`: Generate unique identifiers for vault and storage account names.

**4. Provider Configuration (`provider.tf`)**

- Specifies the use of the `azurerm` provider for Azure resources.
- Includes the `random` provider for generating unique resource names.

**5. Variable Definitions (`variables.tf` and `terraform.tfvars`)**

- Defines and sets the `location` variable, determining where resources will be deployed.

**6. GitHub Actions Workflow**

- The workflow for this project is based on the one from the [previous task](https://github.com/mate-academy/terraform_extra_task_github_actions). 
- Copy the workflow file to `.github/workflows/` in this repository.
- Deploy the code.

**7. Additional Task: Configure .gitignore**

- Create a `.gitignore` file in the root of your repository with the following content:
    * Terraform state files.
    * Terraform directory.
    * Crash log files.
    * Exclude all .tfvars files, which are likely to contain sentitive data.

**8. Pull request's description should also contain a reference to a successful workflow run**