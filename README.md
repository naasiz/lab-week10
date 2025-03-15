# Week 10 Lab - Packer, Ansible, and Terraform

## Overview
This project demonstrates the deployment of an EC2 instance on AWS using **Packer**, **Ansible**, and **Terraform**. The process involves creating a custom Amazon Machine Image (AMI) with Packer, automating configuration with Ansible, and deploying the infrastructure with Terraform.

## Steps to Complete the Lab

### 1. Clone the Repository
```bash
git clone https://gitlab.com/cit_4640/4640-w10-lab-start-w25.git
cd 4640-w10-lab-start-w25
```

### 2. Add SSH Key to AWS
Run the provided script to add your SSH key to AWS:
```bash
bash scripts/import_lab_key ~/.ssh/aws.pub
```

### 3. Build the AMI with Packer
Navigate to the `packer/` directory and run:
```bash
cd packer
packer init .
packer validate ansible-web.pkr.hcl
packer build ansible-web.pkr.hcl
```
Note the **AMI ID** generated at the end.

### 4. Configure Terraform
In the `terraform/` directory:
```bash
cd ../terraform
```
- Created the `web-server` module under `modules/`.
- Defined required variables and outputs for the module.

### 5. Deploy the Infrastructure with Terraform
Initialize and apply Terraform:
```bash
terraform init
terraform apply -auto-approve
```
Note the **Public IP** and **DNS** provided in the outputs.

### 7. Clean Up the Environment
After testing, run the following to clean up resources:
```bash
terraform destroy -auto-approve
```
Also remove the AMI and snapshot using the AWS Console or CLI.


