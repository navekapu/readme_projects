# 1-org

It sets up top level shared folders, monitoring and networking projects, and
organization-level logging, and sets baseline security settings through organizational policy described in [Google Cloud security foundations guide](../google-cloud-security-foundations-guide.pdf).

## Purpose

The purpose of this folder is to set up top-level shared folders, monitoring and networking projects, organization-level logging, and baseline security settings through organizational policies.

## Prerequisites

1. 0-bootstrap executed successfully.
2. terraform service account is added to Organization administrators group.
3. Security Command Center notifications require that you choose a Security Command Center tier and create and grant permissions for the Security Command Center service account as outlined in [Setting up Security Command Center](https://cloud.google.com/security-command-center/docs/quickstart-security-command-center)
4. Ensure that you have requested for sufficient projects quota, as the Terraform scripts will create multiple projects from this point onwards. For more information, please [see the FAQ](https://github.com/terraform-google-modules/terraform-example-foundation/blob/master/docs/FAQ.md).

**Note:** Make sure that you use the same version of Terraform throughout this series, otherwise you might experience Terraform state snapshot lock errors.

## Instructions:

Once 0-bootstrap is executed successfully. It will create a terraform service account under seeding project (shared-services), you need to generate key for this service acoount then download it to your workspace.
 
```
cd 1-org
rm -f providers.tfvars variables.tfvars terraform.tfvars
ln -s ../_shared/providers.tf providers.tfvars
ln -s ../_shared/variables.tf variables.tfvars
ln -s ../_shared/terraform-lzaas.tfvars terraform.tfvars
export GOOGLE_APPLICATION_CREDENTIALS=<location of terraform service account key json file>
terraform init
terraform apply 

```
