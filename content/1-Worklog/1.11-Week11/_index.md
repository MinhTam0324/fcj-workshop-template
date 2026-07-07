---
title: "Worklog Tuần 11"
date: 2026-06-29
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu Tuần 11:
- Hoàn thiện hạ tầng frontend và bảo mật kết nối cho project LiveCap.
- Cấu hình domain, HTTPS/WSS, monitoring và viết blog kỹ thuật về AWS Shield Advanced.

### Các công việc thực hiện trong tuần:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | ---- | ---------- | --------------- | ------------------ |
| 2 | - Deploy frontend lên S3 <br> - Cấu hình CloudFront phân phối frontend | 29/06/2026 | 29/06/2026 | <https://docs.aws.amazon.com/AmazonS3/> |
| 3 | - Cấu hình domain và DNS (Route 53) <br> | 30/06/2026 | 30/06/2026 | <https://docs.aws.amazon.com/Route53/> |
| 4 | - Cấu hình HTTPS/TLS cho frontend và backend <br> - Cấu hình WebSocket Secure (WSS) qua Nginx | 01/07/2026 | 01/07/2026 | |
| 5 | - Thiết lập monitoring/log với CloudWatch <br> - Kiểm tra bảo mật: firewall, CORS, khả năng phục hồi kết nối | 02/07/2026 | 02/07/2026 | <https://docs.aws.amazon.com/cloudwatch/> |
| 6 | - Viết blog kỹ thuật về AWS Shield Advanced (chống DDoS) | 03/07/2026 | 03/07/2026 | <https://docs.aws.amazon.com/waf/latest/developerguide/shield-chapter.html> |

### Kết quả đạt được trong Tuần 11:
- Triển khai frontend lên S3 và phân phối qua CloudFront, đảm bảo tốc độ tải và khả năng mở rộng.
- Cấu hình domain và DNS qua Route 53
- Cấu hình HTTPS/TLS cho frontend và backend; thiết lập WebSocket Secure (WSS) qua Nginx cho luồng phụ đề thời gian thực.
- Thiết lập monitoring và log tập trung với CloudWatch; kiểm tra các khía cạnh bảo mật gồm firewall, CORS và khả năng phục hồi kết nối WebSocket.
- Hoàn thành blog kỹ thuật về AWS Shield Advanced, trình bày cơ chế chống DDoS và cách áp dụng cho hệ thống.