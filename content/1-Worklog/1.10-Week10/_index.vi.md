---
title: "Worklog Tuần 10"
date: 2026-06-22
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu Tuần 10:
- Triển khai hạ tầng mạng và backend cho project LiveCap trên AWS.
- Cấu hình VPC, EC2, Nginx và phân quyền IAM cho các dịch vụ sử dụng.

### Các công việc thực hiện trong tuần:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | ---- | ---------- | --------------- | ------------------ |
| 2 | - Tạo VPC và cấu hình mạng: <br>&emsp; + Public/private subnet <br>&emsp; + Internet Gateway, Route Table | 22/06/2026 | 22/06/2026 | <https://docs.aws.amazon.com/vpc/> |
| 3 | - Cấu hình Security Group và routing cho backend: <br>&emsp; + Mở các cổng cần thiết (HTTP/HTTPS, WebSocket) <br>&emsp; + Giới hạn truy cập theo nguyên tắc least privilege | 23/06/2026 | 23/06/2026 | <https://docs.aws.amazon.com/vpc/latest/userguide/vpc-security-groups.html> |
| 4 | - Khởi tạo EC2 instance cho backend <br> - Cài đặt môi trường chạy FastAPI (Python, dependencies) | 24/06/2026 | 24/06/2026 | <https://docs.aws.amazon.com/ec2/> |
| 5 | - Cấu hình Nginx làm reverse proxy cho FastAPI <br> - Kiểm tra luồng request từ ngoài vào backend | 25/06/2026 | 25/06/2026 | |
| 6 | - Thiết lập IAM Role/Policy cho EC2 truy cập Transcribe, Translate, S3, CloudWatch (least privilege) <br> - Kiểm tra backend gọi được các dịch vụ AWS | 26/06/2026 | 26/06/2026 | <https://docs.aws.amazon.com/IAM/> |

### Kết quả đạt được trong Tuần 10:
- Triển khai được hạ tầng mạng cho LiveCap: VPC với public/private subnet, Internet Gateway và Route Table.
- Cấu hình Security Group và routing cho backend: chỉ mở các cổng cần thiết (HTTP/HTTPS, WebSocket), hạn chế truy cập không cần thiết.
- Khởi tạo và cấu hình EC2 instance chạy backend FastAPI với đầy đủ môi trường và dependencies.
- Cấu hình thành công Nginx làm reverse proxy đứng trước FastAPI, xử lý luồng request từ bên ngoài vào backend.
- Thiết lập IAM Role cho EC2 theo nguyên tắc least privilege: backend gọi được Amazon Transcribe, Translate, S3 và ghi log CloudWatch mà không dùng access key cứng.