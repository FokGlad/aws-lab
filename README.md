# AWS Lab — Infrastructure as Code

> Multi-environment AWS infrastructure provisioned with Terraform, configured with Ansible, documented like a pro.

## Structure

```
aws-lab/
├── terraform/          # All IaC — modules + per-env configs
│   ├── modules/        # Reusable: VPC, EC2, RDS, S3, IAM
│   └── environments/   # dev / staging / prod
├── ansible/            # Configuration management
│   ├── roles/          # common, nginx, app, monitoring
│   ├── inventories/    # Per-environment host files
│   └── playbooks/      # Site, app deploy, monitoring setup
├── docs/               # The why, not just the what
│   ├── architecture/   # System design docs
│   ├── runbooks/       # Incident response, ops procedures
│   └── adr/            # Architecture Decision Records
├── diagrams/           # Architecture visuals (drawio, excalidraw)
└── .github/workflows/  # CI/CD — terraform plan/apply, lint, test
```

## Goals

- [ ] Multi-VPC network with public/private subnets across 2 AZs
- [ ] EC2 Auto Scaling Group behind an ALB
- [ ] RDS PostgreSQL (Multi-AZ in prod)
- [ ] S3 buckets with versioning, encryption, lifecycle rules
- [ ] IAM roles & policies following least-privilege
- [ ] Ansible playbooks for app deployment and hardening
- [ ] Terraform CI with plan-on-merge and apply-on-approval
- [ ] Monitoring stack via Ansible (Prometheus + Grafana or CloudWatch)
- [ ] ADRs for every major design decision

## Environments

| Env | AWS Account | Region | Purpose |
|-----|-------------|--------|---------|
| dev | sandbox | eu-west-1 | Experimentation, destroy freely |
| staging | staging | eu-west-1 | Pre-prod validation |
| prod | production | eu-west-1 | Real workloads |

## Getting Started

1. Configure AWS credentials (`aws configure --profile aws-lab-dev`)
2. `cd terraform/environments/dev && terraform init && terraform plan`
3. `ansible-playbooks site.yml -i inventories/dev/hosts`

## Docs

- [Architecture Overview](docs/architecture/overview.md)
- [Terraform Module Guide](docs/architecture/terraform-modules.md)
- [Ansible Role Reference](docs/architecture/ansible-roles.md)
- [Runbooks Index](docs/runbooks/README.md)
- [ADR Index](docs/adr/README.md)
