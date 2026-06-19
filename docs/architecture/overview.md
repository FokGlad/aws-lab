# Architecture Overview

> High-level system design for the AWS Lab environment.

## Network

- VPC with public and private subnets across 2 AZs
- Internet Gateway for public subnets
- NAT Gateway for private subnet outbound traffic
- VPC Flow Logs enabled

## Compute

- EC2 Auto Scaling Group (t3.micro in dev, t3.small+ in prod)
- Application Load Balancer (ALB) in public subnets
- Target Group with health checks
- Launch Template with latest Amazon Linux 2023 AMI

## Data

- RDS PostgreSQL (Multi-AZ in prod, single-AZ in dev)
- S3 buckets: app assets, backups, Terraform state
- Encryption at rest (KMS) and in transit (TLS)

## Security

- IAM roles for EC2 instances (no hardcoded credentials)
- Security Groups: least-privilege, explicit deny by default
- S3 bucket policies block public access
- Secrets in AWS Secrets Manager

## Monitoring

- CloudWatch alarms for CPU, memory, disk, ALB 5xx
- Ansible-deployed Prometheus + Grafana (optional)
- SNS notifications for critical alerts

## CI/CD

- GitHub Actions: `terraform fmt` → `terraform validate` → `terraform plan`
- Manual approval gate before `terraform apply`
- Ansible playbook runs post-provisioning
