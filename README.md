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
