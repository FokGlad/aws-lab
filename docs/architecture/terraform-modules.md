# Terraform Module Guide

> How the Terraform code is organized and why.

## Module Structure

Each module lives under `terraform/modules/<name>/` and contains:

```
modules/vpc/
├── main.tf          # Resources
├── variables.tf     # Inputs
├── outputs.tf       # Outputs
└── README.md        # Module-specific docs
```

## Modules

### `vpc`
- VPC, subnets (public + private), IGW, NAT GW, route tables
- Variables: `vpc_cidr`, `az_count`, `enable_nat_gateway`

### `ec2`
- Launch template, ASG, ALB, target group, listeners
- Variables: `instance_type`, `min_size`, `max_size`, `ami_id`

### `rds`
- RDS instance, subnet group, parameter group, security group
- Variables: `engine_version`, `instance_class`, `multi_az`

### `s3`
- Buckets with versioning, encryption, lifecycle, public access block
- Variables: `bucket_names`, `lifecycle_days`

### `iam`
- Roles, policies, instance profiles
- Variables: `role_name`, `policy_arns`

## State Management

- Remote state in S3 with DynamoDB locking
- Per-environment state files: `env/<env>/terraform.tfstate`

## Usage

```bash
cd terraform/environments/dev
terraform init
terraform plan -out=plan.tfplan
terraform apply plan.tfplan
```
