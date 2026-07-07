---
title: "Week 9 Worklog"
date: 2026-06-15
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Week 9 Objectives:
- Implement the LiveCap project: a real-time Vietnamese-English bilingual captioning and translation web app.
- Take on the Cloud Infrastructure and Network Security role: research services, design the network architecture, and draw the infrastructure diagrams.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| 2 | - Team meeting to assign tasks and agree on the MVP scope <br> - Took on the cloud infrastructure and network security role | 06/15/2026 | 06/15/2026 | |
| 3 | - Research the AWS services used in the project: <br>&emsp; + Amazon Transcribe Streaming, Amazon Translate <br>&emsp; + Amazon S3, CloudFront, CloudWatch <br>&emsp; + Audio format requirements | 06/16/2026 | 06/16/2026 | <https://docs.aws.amazon.com/transcribe/> |
| 4 | - Read and analyze LiveCap's main processing flows: <br>&emsp; + Real-time flow: Microphone → WebSocket → Transcribe → Translate → Frontend <br>&emsp; + Export flow: transcript → S3 → Presigned URL | 06/17/2026 | 06/17/2026 | |
| 5 | - Design the network architecture for the system: <br>&emsp; + VPC, public/private subnets <br>&emsp; + Security Groups and routing for the backend EC2 <br>&emsp; + Placement of S3/CloudFront for the frontend | 06/18/2026 | 06/18/2026 | |
| 6 | - Design the IAM permission model for Transcribe, Translate, S3, CloudWatch (least privilege) <br> - Draw the overall architecture and network diagrams with draw.io | 06/19/2026 | 06/19/2026 | |

### Week 9 Achievements:
- Took on the Cloud Infrastructure and Network Security role for the LiveCap project.
- Understood the role of each AWS service in the system and analyzed the two main processing flows: the real-time captioning flow and the transcript export flow.
- Designed the network architecture for the system:
  - Separated public subnets (for components needing internet access) and private subnets
  - Defined the Security Groups and routing needed for the backend EC2
  - Placed the frontend on S3 and distributed it via CloudFront
- Designed the IAM permission model following the least-privilege principle: each component is granted only the minimum permissions needed to call Transcribe, Translate, S3, and write CloudWatch logs.
- Completed the overall architecture and network diagrams with draw.io, serving as the basis for infrastructure deployment in the following weeks.