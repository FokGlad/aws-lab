# Ansible Role Reference

> Configuration management roles and their responsibilities.

## Roles

### `common`
- System updates, timezone, NTP
- SSH hardening (key-only, non-default port)
- Fail2ban, UFW basics
- Create deploy user

### `nginx`
- Install and configure Nginx
- Reverse proxy to app
- TLS via Let's Encrypt (certbot)
- Security headers, rate limiting

### `app`
- Deploy application code
- Manage systemd service
- Environment variables from AWS Secrets Manager
- Health check endpoint

### `monitoring`
- Node Exporter
- Prometheus (optional, for non-CloudWatch setup)
- Grafana dashboards
- CloudWatch agent config

## Playbooks

| Playbook | Purpose |
|----------|---------|
| `site.yml` | Full stack: common → nginx → app → monitoring |
| `deploy.yml` | App-only rolling deploy |
| `monitoring.yml` | Monitoring stack only |
| `hardening.yml` | Security baseline only |

## Inventory Structure

```
inventories/
├── dev/
│   ├── hosts          # Static or dynamic
│   └── group_vars/
│       ├── all.yml
│       └── webservers.yml
├── staging/
└── prod/
```

## Running

```bash
ansible-playbook playbooks/site.yml -i inventories/dev/hosts
```
