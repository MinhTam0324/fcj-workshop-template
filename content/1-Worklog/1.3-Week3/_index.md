---
title: "Week 3 Worklog"
date: 2026-05-04
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:
- Understand advanced VPC connectivity: VPC Endpoint, VPC Peering, Transit Gateway, VPN, and Direct Connect.
- Learn about load balancing with Elastic Load Balancing.
- Practice VPC Peering and Route 53 labs.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| 2 | - Study Module 2 (continued): <br>&emsp; + VPC Endpoint (Interface Endpoint and Gateway Endpoint) <br>&emsp; + VPC Peering | 05/04/2026 | 05/04/2026 | <https://www.youtube.com/@AWSStudyGroup/courses> |
| 3 | - Study hybrid connectivity options: <br>&emsp; + Transit Gateway <br>&emsp; + VPN Site-to-Site and Client-to-Site <br>&emsp; + AWS Direct Connect | 05/05/2026 | 05/05/2026 | <https://www.youtube.com/@AWSStudyGroup/courses> |
| 4 | - Study Elastic Load Balancing: <br>&emsp; + 4 types: ALB, NLB, CLB, Gateway LB <br>&emsp; + Health Check, Sticky Session, Access Logs | 05/06/2026 | 05/06/2026 | <https://www.youtube.com/@AWSStudyGroup/courses> |
| 5 | - Practice Lab19 - VPC Peering: <br>&emsp; + Initialize CloudFormation Templates <br>&emsp; + Create Security Group <br>&emsp; + Create EC2 instances and set up VPC Peering | 05/07/2026 | 05/07/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Practice Lab10 - Route 53: <br>&emsp; + Route 53 Resolver Rules <br>&emsp; + Create Route 53 Inbound Endpoints <br>&emsp; + Test results and clean up resources | 05/08/2026 | 05/08/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Week 3 Achievements:
- Understood that VPC Endpoints let resources inside a VPC connect to AWS services outside the VPC over a private internal network, without going through the internet:
  - Interface Endpoint: uses an ENI with a private IP to connect to supported services
  - Gateway Endpoint: uses route tables for routing, supports only S3 and DynamoDB
- Understood VPC Peering for connecting VPCs without the internet: a 1:1 connection that does not support transitive routing and cannot be used when the two VPCs have overlapping IP address ranges.
- Grasped hybrid connectivity options:
  - Transit Gateway: connects multiple VPCs and on-premises networks through a central hub, simplifying routing
  - VPN Site-to-Site: consists of a Virtual Private Gateway and a Customer Gateway (customer side)
  - Direct Connect: a dedicated connection from a data center to AWS with low latency; traffic is not encrypted, so a VPN is still needed on top
- Understood how Elastic Load Balancing distributes requests across multiple servers:
  - Distinguished the 4 types: ALB (layer 7, DNS), NLB (layer 4, supports static IP), CLB (legacy, being phased out), Gateway LB
  - Health Check ensures requests are only sent to healthy targets; Sticky Session keeps a user's session on the same target
- Completed the VPC Peering lab with CloudFormation and the Route 53 lab.