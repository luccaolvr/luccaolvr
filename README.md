# Lucca Oliveira

**IT infrastructure · automation · observability · applied AI** — Greater São Paulo, Brazil

I work in IT at a food-industry company, where I handle L1/L2 support and the infrastructure
of an industrial site with about 210 workstations. Most of what I build solves a problem I
ran into on the job: monitoring that showed green while a fiber link was down, preventive
maintenance done by hand on each machine, a production server that needed backups proven by
real restores.

I'm studying Systems Analysis and Development and Cloud Computing, heading toward DevOps
and SRE.

## What I work on

- **Observability** — Prometheus, Grafana and Blackbox Exporter watching 70 network and
  infrastructure assets, 28 alerts with runbooks, alerts routed to Microsoft Teams via n8n.
- **Linux in production** — an Ubuntu Server VM (Hyper-V) running Docker, nginx as the single
  entry point, key-only SSH, daily encrypted backups with an automated monthly restore test.
- **Automation** — PowerShell maintenance and inventory for the whole Windows fleet; OCS
  Inventory rolled out through that same routine.
- **Applied AI** — a delivery pipeline of AI agents (Claude Code) that takes internal systems
  from a GitHub issue to deployment, with a human approval gate at scope, pull request and
  deploy.

## Selected work

The systems below run inside my employer's network, so the code is private. I describe them
by problem, approach and stack, without internal details.

| Project | Problem → approach | Stack |
|---|---|---|
| Monitoring and production Linux server | Monitoring ran on my own PC and collected data 32.6% of the time. Moved it to a dedicated server with a before/after reachability baseline and a rollback path: coverage went to 100%, flapping alerts from 58 to 4. | Prometheus, Grafana, Blackbox, n8n, Docker Compose, Ubuntu Server, nginx |
| Backup with proof of restore | A backup only counts once it has been restored. Daily encrypted backup plus a monthly job that restores into an isolated container and checks the data against production. | BorgBackup, borgmatic, systemd timers, Prometheus |
| Endpoint maintenance hub | Inventory and cleanup were manual, one machine at a time. A PowerShell routine with 8 modes, offline queue and automatic resend, consolidated into a spreadsheet and an HTML dashboard. | PowerShell, Task Scheduler, Excel COM, OCS Inventory |
| AI-agent delivery pipeline | A small IT team needs to take internal systems (such as an HR approval workflow) from request to production safely. 9 agents (product, UX, risk, dev, QA, security, DevOps, monitoring, docs), 3 human gates, CI with secret scanning; no agent can merge, deploy or touch production. | Claude Code, GitHub Issues, GitHub Actions, Docker |

**Public code:** [windows-endpoint-maintenance](https://github.com/luccaolvr/windows-endpoint-maintenance)
— the first public version (v1.0) of the maintenance script.

## Stack

**Used at work:** Linux (Ubuntu Server) · Docker · Docker Compose · Hyper-V · nginx · Prometheus ·
PromQL · Grafana · n8n · PowerShell · Bash · Git · GitHub Actions · BorgBackup · Active Directory ·
Microsoft 365 · TCP/IP · VLANs · Ubiquiti/UniFi · MariaDB · SQL · Claude Code

**Learning:** AWS (Cloud Architecting, Cloud Developing) · Terraform · Python · TypeScript

## Contact

[Portfolio](https://lucca-oliveira.vercel.app) · [LinkedIn](https://www.linkedin.com/in/luccaolvr) · luccaso1227@gmail.com
