---
title: "Week 4 Worklog"
date: 2026-05-11
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:
- Learn more about Amazon EC2: Instance Types, AMI, storage, and auto scaling.
- Explore other compute and storage services: Amazon Lightsail, EFS/FSx.
- Practice hands-on labs on core AWS services.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| 2 | - Learn more about Amazon EC2: <br>&emsp; + Instance Types (CPU, Memory, Network, Storage) <br>&emsp; + Hardware Node, Placement Options <br>&emsp; + Hypervisors (Nitro, HVM, PV) and AMI | 05/11/2026 | 05/11/2026 | <https://www.youtube.com/@AWSStudyGroup/courses> |
| 3 | - Study EC2 storage: <br>&emsp; + EBS, Instance Store <br>&emsp; + Key Pair, Snapshot/Backup <br> - Practice IAM lab | 05/12/2026 | 05/12/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Study EC2 User Data, Meta Data, and EC2 Auto Scaling <br> - Practice AWS CLI lab | 05/13/2026 | 05/13/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Explore Amazon Lightsail and Amazon EFS/FSx <br> - Practice Static Website Hosting lab with Amazon S3 | 05/14/2026 | 05/14/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Review EC2 knowledge from the week <br> - Practice monitoring lab with Amazon CloudWatch | 05/15/2026 | 05/15/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Week 4 Achievements:
- Understood how EC2 configuration is chosen through Instance Types (determining CPU, Memory, Network, Storage); hardware nodes are not chosen directly but through Instance Type, Placement Options, and AMI.
- Grasped the AMI concept: a template file containing the OS and hypervisor choice, used to provision one or many EC2 instances; learned the 3 hypervisor types.
- Distinguished the two storage types for EC2:
  - EBS: block storage connected through a dedicated network channel, replicated across 3 storage nodes within an AZ for high availability — suitable for important data
  - Instance Store: NVMe attached directly to the hardware node, very fast but data is lost when the instance stops — only suitable for cache/buffer
- Understood EC2 User Data (a script that runs only once at instance launch, used for automated application setup) and Meta Data (information about the instance itself, accessed via an internal URL, used for automation).
- EC2 Auto Scaling increases or decreases the number of instances based on scaling policies, automatically registers instances with ELB, and works across multiple AZs.
- Learned about Amazon Lightsail: suitable for small projects and test/dev environments.
- Completed 4 hands-on labs: IAM, AWS CLI, static website hosting on S3, and monitoring with CloudWatch.