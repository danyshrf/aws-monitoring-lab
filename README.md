# AWS CloudWatch + Prometheus + Grafana Unified Monitoring Lab

A production-style monitoring lab built on AWS Free Tier demonstrating
dual-pipeline observability, incident simulation, and automated alerting.

---

## Architecture
```
EC2 Instance (t2.micro - Amazon Linux 2023)
├── Node Exporter  → exposes Linux metrics (CPU, RAM, Disk, Network)
├── Prometheus     → scrapes & stores Node Exporter metrics
├── Grafana        → unified dashboard (Prometheus + CloudWatch)
└── CloudWatch Agent → ships custom metrics to AWS CloudWatch

AWS Services
├── CloudWatch  → receives agent metrics + triggers alarms
├── SNS         → sends email alerts on threshold breach
└── IAM Role    → grants EC2 permission to write CloudWatch metrics
```

---

## What This Project Demonstrates

- Dual monitoring pipelines from a single EC2 instance
- Custom CloudWatch metrics (RAM, Disk) not available by default in AWS
- Prometheus scraping via Node Exporter with PromQL alert rules
- Grafana with two simultaneous data sources (Prometheus + CloudWatch)
- SNS email alerting triggered by real CPU stress tests
- IAM Role-based authentication (no hardcoded credentials)
- Full systemd service management on Linux

---

## Tech Stack

- | Cloud | AWS EC2, CloudWatch, SNS, IAM |
- | Monitoring | Prometheus, Node Exporter |
- | Visualization | Grafana (latest) |
- | OS | Amazon Linux 2023 |
- | Automation | systemd, bash |
- | Incident Sim | stress-ng |

---

## Key Results

- CPU stress test triggered **both alert pipelines** within 1 minute
- CloudWatch alarm fired: `OK → ALARM` at **90.17% CPU**
- Grafana alert fired: `High-CPU-Prometheus-Alert` at **100% CPU**
- Custom metrics namespace `MonitoringLab/EC2` visible in CloudWatch console
- Grafana dashboard showing real-time CPU, RAM, Disk, and Network panels

---

## Setup Guide

See [docs/setup-guide.md](docs/setup-guide.md) for full step-by-step instructions.

---

## Skills Demonstrated

`AWS` `EC2` `CloudWatch` `SNS` `IAM` `Prometheus` `Grafana` `Node Exporter`
`Linux Administration` `systemd` `PromQL` `Observability` `Alerting` `Incident Simulation`
