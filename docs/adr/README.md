# Architecture Decision Records (ADR)

> Every major design decision documented with context, decision, and consequences.

## Index

| ADR | Title | Status |
|-----|-------|--------|
| [ADR-001](adr-001-terraform-over-cloudformation.md) | Terraform over CloudFormation | Accepted |
| [ADR-002](adr-002-ansible-over-user-data.md) | Ansible over EC2 User Data for config | Accepted |
| [ADR-003](adr-003-multi-env-strategy.md) | Multi-environment strategy (directories vs workspaces) | Accepted |
| [ADR-004](adr-004-rds-over-dynamodb.md) | RDS PostgreSQL over DynamooDB for primary datastore | Accepted |
| [ADR-005](adr-005-github-actions-over-jenkins.md) | GitHub Actions over Jenkins for CI | Accepted |

## ADR Template

Each ADR follows the format:

```
# ADR-XXX: Title

## Status
Proposed | Accepted | Deprecated | Superseded

## Context
What is the issue we're deciding on?

## Decision
What did we decide?

## Consequences
What are the trade-offs? What becomes easier/harder?
```
