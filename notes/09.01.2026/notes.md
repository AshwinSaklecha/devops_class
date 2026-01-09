# Infrastructure as Code & Terraform

## What is IaC?
- Manage infrastructure using code
- Version control for infrastructure
- Reproducible and consistent environments

## Benefits of IaC
- Automation - no manual setup
- Version control - track changes
- Consistency - same config every time
- Documentation - code is documentation

## Terraform Overview
- Open source IaC tool by HashiCorp
- Cloud agnostic (AWS, GCP, Azure, etc.)
- Declarative language (HCL)

## How Terraform Works
1. Write configuration files (.tf)
2. `terraform init` - initialize
3. `terraform plan` - preview changes
4. `terraform apply` - apply changes
5. `terraform destroy` - remove resources

## Basic Terraform File
```hcl
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "example" {
  ami           = "ami-12345678"
  instance_type = "t2.micro"
  
  tags = {
    Name = "example-instance"
  }
}
```

## Key Concepts
- **Provider** - cloud/service to use
- **Resource** - infrastructure component
- **State** - tracks real infrastructure
- **Module** - reusable configuration

## Commands
```bash
terraform init    # initialize
terraform plan    # preview
terraform apply   # create/update
terraform destroy # delete
```
