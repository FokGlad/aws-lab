# Runbooks Index

> Operational procedures for common scenarios.

## Available Runbooks

| Runbook | Description |
|---------|-------------|
| [Instance Recovery](instance-recovery.md) | EC2 instance unhealthy — diagnose and recover |
| [RDS Failover](rds-failover.md) | Handle RDS Multi-AZ failover event |
| [ALB 5xx Spike](alv-5xx-spike.md) | Debug sudden increase in ALB 5xx errors |
| [Terraform State Lock](terraform-state-lock.md) | Force-unlock stuck Terraform state |
| [Certificate Renewal](cert-renewal.md) | Renew Let's Encrypt certificates manually |
| [Scaling Event](scaling-event.md) | Respond to unexpected ASG scaling |

## How to Use

Each runbook follows the format:
1. **Symptoms** — What you observe
2. **Diagnosis** — How to confirm the root cause
3. **Resolution** — Step-by-step fix
4. **Prevention** — How to avoid recurrence
