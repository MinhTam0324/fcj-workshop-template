---
title: "Worklog Tuần 9"
date: 2026-06-15
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu Tuần 9:
- Triển khai project LiveCap: ứng dụng phụ đề và dịch song ngữ Việt-Anh theo thời gian thực.
- Phụ trách vai trò Cloud Infrastructure và Network Security: nghiên cứu dịch vụ, thiết kế kiến trúc mạng và vẽ sơ đồ hạ tầng cho hệ thống.

### Các công việc thực hiện trong tuần:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | ---- | ---------- | --------------- | ------------------ |
| 2 | - Họp nhóm phân công công việc, thống nhất phạm vi MVP <br> - Nhận vai trò phụ trách hạ tầng cloud và bảo mật mạng | 15/06/2026 | 15/06/2026 | |
| 3 | - Nghiên cứu các dịch vụ AWS dùng trong project: <br>&emsp; + Amazon Transcribe Streaming, Amazon Translate <br>&emsp; + Amazon S3, CloudFront, CloudWatch <br>&emsp; + Yêu cầu định dạng âm thanh | 16/06/2026 | 16/06/2026 | <https://docs.aws.amazon.com/transcribe/> |
| 4 | - Đọc và phân tích các luồng xử lý chính của LiveCap: <br>&emsp; + Luồng thời gian thực: Microphone → WebSocket → Transcribe → Translate → Frontend <br>&emsp; + Luồng export: transcript → S3 → Presigned URL | 17/06/2026 | 17/06/2026 | |
| 5 | - Thiết kế kiến trúc mạng cho hệ thống: <br>&emsp; + VPC, public/private subnet <br>&emsp; + Security Group và routing cho backend EC2 <br>&emsp; + Vị trí S3/CloudFront cho frontend | 18/06/2026 | 18/06/2026 | |
| 6 | - Thiết kế mô hình phân quyền IAM cho Transcribe, Translate, S3, CloudWatch (least privilege) <br> - Vẽ sơ đồ kiến trúc tổng thể và sơ đồ mạng bằng draw.io | 19/06/2026 | 19/06/2026 | |

### Kết quả đạt được trong Tuần 9:
- Đóng vai trò phụ trách Cloud Infrastructure và Network Security cho project LiveCap.
- Hiểu vai trò của từng dịch vụ AWS trong hệ thống và đọc hiểu hai luồng xử lý chính: luồng phụ đề thời gian thực và luồng export transcript.
- Thiết kế được kiến trúc mạng cho hệ thống:
  - Phân chia public subnet (cho thành phần cần truy cập internet) và private subnet
  - Xác định Security Group và routing cần thiết cho backend EC2
  - Bố trí frontend trên S3 và phân phối qua CloudFront
- Thiết kế mô hình phân quyền IAM theo nguyên tắc least privilege: mỗi thành phần chỉ được cấp quyền tối thiểu cần thiết để gọi Transcribe, Translate, S3 và ghi log CloudWatch.
- Hoàn thành sơ đồ kiến trúc tổng thể và sơ đồ mạng bằng draw.io, làm cơ sở cho việc triển khai hạ tầng ở các tuần tiếp theo.