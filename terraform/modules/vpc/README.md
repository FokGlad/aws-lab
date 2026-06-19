# VPC Module

Creates a VPC with public and private subnets across multiple AZs.

## Usage

```hcl
module "vpc" {
  source = "../../modules/vpc"

  vpc_cidr    = "10.0.0.0/16"
  az_count    = 2
  environment = "dev"
}
```

## Inputs

| Name | Type | Default | Description |
|------|------|---------|-------------|
| vpc_cidr | string | `10.0.0.0/16` | VPC CIDR block |
| az_count | number | `2` | Number of AZs |
| environment | string | `dev` | Environment tag |

## Outputs

| Name | Description |
|------|-------------|
| vpc_id | VPC ID |
| public_subnet_ids | List of public subnet IDs |
| private_subnet_ids | List of private subnet IDs |
