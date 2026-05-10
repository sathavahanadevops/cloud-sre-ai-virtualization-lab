# cloud-sre-ai-virtualization-lab

This repository contains Terraform code for a focused Azure lab environment used for SRE, DevOps, AI tooling, and virtualization practice. The current configuration is centered on a single Oracle resource group deployment with networking, VM, and Bastion host resources.

## What is included

- `main.tf` - root Terraform configuration for the Oracle RG deployment
- `variables.tf` - input variables for environment and resource names
- `outputs.tf` - outputs exposing key resource IDs and names
- `terraform.tf` - Azure backend configuration for remote state
- `modules/resource-group` - Azure Resource Group definition
- `modules/networking` - VNet, subnets, NSG, public IPs and networking resources
- `modules/bastion` - Azure Bastion host definition and import alignment

## Current setup

- Azure resource group: `oracle`
- Virtual network: `sqltesting-vnet`
- Bastion host: `SQL` (Basic SKU)
- VM: `sqltesting`
- Public IPs: `sqltesting-ip`, `sqltesting-vnet-IPv4`
- Network security group: `sqltesting-nsg`

## Notes

- The repository now contains only the Oracle RG-related Terraform code and backend config.
- The Terraform backend is configured in `terraform.tf` and has been kept untouched.
- The Bastion host has been imported from the existing Azure resource and aligned with the current Terraform state.

## How to use

```bash
cd /path/to/cloud-sre-ai-virtualization-lab
terraform init
terraform validate
terraform plan -var-file=your-vars.tfvars
```

> Use a variable file or `-var` options to pass required secrets such as `client_secret` and `vm_admin_password`.

## Important

- Do not remove `terraform.tf` if you want to keep the remote backend configuration.
- If you delete `.terraform`, rerun `terraform init` before other Terraform commands.

## Goal

This repo is designed as a learning and practice workspace for Azure-based SRE, DevOps, virtualization, and AI tooling scenarios with Terraform-managed infrastructure.