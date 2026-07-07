---
title: "Week 10 Worklog"
date: 2026-06-22
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Week 10 Objectives:
- Deploy the network infrastructure and backend for the LiveCap project on AWS.
- Configure VPC, EC2, Nginx, and IAM permissions for the services used.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| 2 | - Create the VPC and configure networking: <br>&emsp; + Public/private subnets <br>&emsp; + Internet Gateway, Route Table | 06/22/2026 | 06/22/2026 | <https://docs.aws.amazon.com/vpc/> |
| 3 | - Configure Security Groups and routing for the backend: <br>&emsp; + Open only the necessary ports (HTTP/HTTPS, WebSocket) <br>&emsp; + Restrict access following the least-privilege principle | 06/23/2026 | 06/23/2026 | <https://docs.aws.amazon.com/vpc/latest/userguide/vpc-security-groups.html> |
| 4 | - Launch an EC2 instance for the backend <br> - Set up the FastAPI runtime environment (Python, dependencies) | 06/24/2026 | 06/24/2026 | <https://docs.aws.amazon.com/ec2/> |
| 5 | - Configure Nginx as a reverse proxy for FastAPI <br> - Test the request flow from outside into the backend | 06/25/2026 | 06/25/2026 | |
| 6 | - Set up an IAM Role/Policy for EC2 to access Transcribe, Translate, S3, CloudWatch (least privilege) <br> - Verify the backend can call the AWS services | 06/26/2026 | 06/26/2026 | <https://docs.aws.amazon.com/IAM/> |

### Week 10 Achievements:
- Deployed the network infrastructure for LiveCap: a VPC with public/private subnets, Internet Gateway, and Route Table.
- Configured Security Groups and routing for the backend: opening only the necessary ports (HTTP/HTTPS, WebSocket) and restricting unnecessary access.
- Launched and configured an EC2 instance running the FastAPI backend with a complete environment and dependencies.
- Successfully configured Nginx as a reverse proxy in front of FastAPI, handling the request flow from the outside into the backend.
- Set up an IAM Role for EC2 following the least-privilege principle: the backend can call Amazon Transcribe, Translate, S3, and write CloudWatch logs without using hardcoded access keys.