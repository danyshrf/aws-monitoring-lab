## Prerequisites
- AWS Free Tier account
- EC2 t2.micro with Amazon Linux 2023
- IAM Role with CloudWatchAgentServerPolicy attached
- Security Group with ports 22, 3000, 9090, 9100 open

## Installation Order
1. Node Exporter (port 9100)
2. Prometheus (port 9090)
3. Grafana (port 3000)
4. CloudWatch Agent

## Verify All Services
```bash
sudo systemctl status node_exporter prometheus grafana-server amazon-cloudwatch-agent
```

## Grafana Data Sources
- Prometheus: http://localhost:9090
- CloudWatch: EC2 IAM Role auth, region eu-north-1

## Alert Pipelines
- Grafana → SMTP email via Gmail App Password
- CloudWatch → SNS Topic → Email subscription
