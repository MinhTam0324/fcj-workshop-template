---
title: "Week 2 Worklog"
date: 2026-04-27
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:
- Understand AWS networking fundamentals: Amazon VPC and its core components.
- Practice building a complete VPC through Module 2 hands-on labs.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| 2 | - Study Module 2 - Amazon VPC: <br>&emsp; + VPC and Subnet concepts (public/private) <br>&emsp; + Route Table and how to create a public subnet <br>&emsp; + ENI and Elastic IP Address | 04/27/2026 | 04/27/2026 | <https://www.youtube.com/@AWSStudyGroup/courses> |
| 3 | - Study Module 2 (continued): <br>&emsp; + Internet Gateway and NAT Gateway <br>&emsp; + Security Group and Network ACLs <br>&emsp; + VPC Flow Logs | 04/28/2026 | 04/28/2026 | <https://www.youtube.com/@AWSStudyGroup/courses> |
| 4 | - Practice Module 2 - Lab03: <br>&emsp; + Create VPC, Subnets, Route Table <br>&emsp; + Create Internet Gateway, NAT Gateway <br>&emsp; + Configure Security Group, Network ACLs <br>&emsp; + Create EC2 instances in Subnets and test connectivity | 04/29/2026 | 04/29/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5-6 | - Public holidays (April 30th - May 1st) | | | |

### Week 2 Achievements:
- Understood the basic network architecture on AWS:
  - A subnet resides in only one AZ; public and private subnets are essentially the same, differing only in route configuration (a public subnet requires a custom route table pointing to an Internet Gateway)
  - IP addresses are not attached directly to EC2 instances but to virtual network cards (ENIs); an ENI can be detached and attached to another instance while keeping its private IP, Elastic IP, and MAC address
  - Elastic IP is a static IPv4 address that persists through instance restarts and is charged even when not in use
- Distinguished the two firewall layers on AWS:
  - Security Group: stateful, allow rules only, applied at the ENI level
  - Network ACLs: stateless, requires configuring both inbound and outbound rules, applied at the subnet level so changes can affect multiple instances at once
- Understood the roles of the Internet Gateway (lets instances reach the internet, fully managed and scaled by AWS) and the NAT Gateway (lets private subnets make outbound-only connections to the internet).
- Completed the lab building a full VPC: VPC → Subnets → Route Table → IGW → NAT → Security Group → NACLs → created EC2 instances in subnets and tested connectivity.