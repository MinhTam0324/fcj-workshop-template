---
title: "Week 11 worklog"
date: 2026-06-29
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives:
- Finalize the frontend infrastructure and connection security for the LiveCap project.
- Configure custom domain, HTTPS/WSS, monitoring, and author a technical blog post regarding AWS Shield Advanced.

### Tasks Executed During the Week:
| Day | Task | Start Date | Completion Date | Reference Documents |
| --- | ---- | ---------- | --------------- | ------------------ |
| Mon | - Deploy frontend to S3 <br> - Configure CloudFront for frontend distribution | 2026-06-29 | 2026-06-29 | <https://docs.aws.amazon.com/AmazonS3/> |
| Tue | - Configure custom domain and DNS (Route 53) <br> | 2026-06-30 | 2026-06-30 | <https://docs.aws.amazon.com/Route53/> |
| Wed | - Configure HTTPS/TLS for both frontend and backend <br> - Configure WebSocket Secure (WSS) via Nginx | 2026-07-01 | 2026-07-01 | |
| Thu | - Set up monitoring/logging with CloudWatch <br> - Perform security assessments: firewall rules, CORS, and connection resilience | 2026-07-02 | 2026-07-02 | <https://docs.aws.amazon.com/cloudwatch/> |
| Fri | - Write a technical blog post on AWS Shield Advanced (DDoS mitigation) | 2026-07-03 | 2026-07-03 | <https://docs.aws.amazon.com/waf/latest/developerguide/shield-chapter.html> |

### Key Achievements in Week 11:
- Successfully deployed the frontend on S3 and distributed it via CloudFront, ensuring optimal loading speeds and high scalability.
- Successfully configured the custom domain and DNS resolution utilizing Route 53.
- Configured HTTPS/TLS encryption across the frontend and backend architectures; successfully established WebSocket Secure (WSS) via Nginx to support the real-time subtitling data stream.
- Set up centralized monitoring and logging capabilities with CloudWatch; validated critical security layers including firewall rules, CORS configurations, and WebSocket connection resilience.
- Completed the technical blog post detailing AWS Shield Advanced, presenting its underlying DDoS mitigation mechanisms and architectural implementation strategies for the system.