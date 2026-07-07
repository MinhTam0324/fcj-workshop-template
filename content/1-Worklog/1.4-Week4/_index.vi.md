---
title: "Worklog Tuần 4"
date: 2026-05-11
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu Tuần 4:
- Hiểu thêm về Amazon EC2: Instance Type, AMI, lưu trữ và tự động mở rộng.
- Tìm hiểu các dịch vụ tính toán và lưu trữ khác: Amazon Lightsail, EFS/FSx.
- Thực hành các lab về những dịch vụ AWS cơ bản.

### Các công việc thực hiện trong tuần:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | ---- | ---------- | --------------- | ------------------ |
| 2 | - Học thêm về Amazon EC2 : <br>&emsp; + Instance Type (CPU, Memory, Network, Storage) <br>&emsp; + Hardware Node, Placement Option <br>&emsp; + Hypervisor (Nitro, HVM, PV) và AMI | 11/05/2026 | 11/05/2026 | <https://www.youtube.com/@AWSStudyGroup/courses> |
| 3 | - Học về lưu trữ cho EC2: <br>&emsp; + EBS, Instance Store <br>&emsp; + Key Pair, Snapshot/Backup <br> - Thực hành lab IAM | 12/05/2026 | 12/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Học EC2 User Data, Meta Data và EC2 Auto Scaling <br> - Thực hành lab AWS CLI | 13/05/2026 | 13/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Tìm hiểu Amazon Lightsail và Amazon EFS/FSx <br> - Thực hành lab Static Website Hosting với Amazon S3 | 14/05/2026 | 14/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Ôn tập kiến thức EC2 trong tuần <br> - Thực hành lab giám sát với Amazon CloudWatch | 15/05/2026 | 15/05/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được trong Tuần 4:
- Hiểu cách chọn cấu hình EC2 qua Instance Type (quyết định CPU, Memory, Network, Storage); không chọn trực tiếp hardware node mà thông qua Instance Type, Placement Option và AMI.
- Nắm được khái niệm AMI: file template chứa hệ điều hành và lựa chọn hypervisor, dùng để provision một hoặc nhiều EC2 instance; biết 3 loại hypervisor
- Phân biệt hai loại lưu trữ cho EC2:
  - EBS: lưu trữ dạng khối, kết nối qua kênh mạng riêng, replicate giữa 3 storage node trong 1 AZ để đạt độ sẵn sàng cao — phù hợp dữ liệu quan trọng
  - Instance Store: NVMe gắn trực tiếp trên hardware node, tốc độ cao nhưng mất dữ liệu khi stop máy — chỉ phù hợp cache/buffer
- Hiểu được EC2 User Data (script chạy một lần duy nhất khi khởi tạo, dùng cài đặt ứng dụng tự động) và Meta Data (thông tin về chính instance, truy cập qua URL nội bộ, phục vụ tự động hóa).
- EC2 Auto Scaling giúp tăng giảm số lượng instance theo scaling policy, tự đăng ký instance vào ELB và hoạt động trên nhiều AZ.
- Nắm được Amazon Lightsail:phù hợp dự án nhỏ và môi trường test/dev.
- Hoàn thành 4 bài lab: IAM, AWS CLI, hosting static website trên S3, giám sát với CloudWatch.