# Terraform in Action

## State Management
- Terraform stores state in terraform.tfstate
- Tracks what resources exist
- Remote state for team collaboration

## Remote Backend (S3 example)
```hcl
terraform {
  backend "s3" {
    bucket = "my-terraform-state"
    key    = "prod/terraform.tfstate"
    region = "us-east-1"
  }
}
```

## Variables
```hcl
variable "instance_type" {
  description = "EC2 instance type"
  default     = "t2.micro"
}

resource "aws_instance" "web" {
  instance_type = var.instance_type
}
```

## Outputs
```hcl
output "instance_ip" {
  value = aws_instance.web.public_ip
}
```

## Practical Example - VPC + EC2
```hcl
resource "aws_vpc" "main" {
  cidr_block = "10.0.0.0/16"
}

resource "aws_subnet" "public" {
  vpc_id     = aws_vpc.main.id
  cidr_block = "10.0.1.0/24"
}

resource "aws_instance" "app" {
  ami           = "ami-12345678"
  instance_type = "t2.micro"
  subnet_id     = aws_subnet.public.id
}
```

## Best Practices
- Use modules for reusability
- Store state remotely
- Use variables for flexibility
- Lock state for team work
- Never commit secrets

## Useful Commands
```bash
terraform fmt      # format files
terraform validate # check syntax
terraform output   # show outputs
terraform state list # list resources
```
