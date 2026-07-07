---
title: "Worklog Tuần 2"
date: 2026-04-27
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu Tuần 2:
- Nắm kiến thức nền tảng về mạng trên AWS: Amazon VPC và các thành phần cốt lõi.
- Thực hành xây dựng VPC hoàn chỉnh qua các bài lab của Module 2.

### Các công việc thực hiện trong tuần:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | ---- | ---------- | --------------- | ------------------ |
| 2 | - Học Module 2 - Amazon VPC: <br>&emsp; + Khái niệm VPC, Subnet (public/private) <br>&emsp; + Route Table và cách tạo public subnet <br>&emsp; + ENI và Elastic IP Address | 27/04/2026 | 27/04/2026 | <https://www.youtube.com/@AWSStudyGroup/courses> |
| 3 | - Học Module 2 (tiếp): <br>&emsp; + Internet Gateway và NAT Gateway <br>&emsp; + Security Group và Network ACLs <br>&emsp; + VPC Flow Logs | 28/04/2026 | 28/04/2026 | <https://www.youtube.com/@AWSStudyGroup/courses> |
| 4 | - Thực hành Lab03 của Module 2: <br>&emsp; + Tạo VPC, Subnets, Route Table <br>&emsp; + Tạo Internet Gateway, NAT Gateway <br>&emsp; + Cấu hình Security Group, Network ACLs <br>&emsp; + Tạo EC2 instance trong Subnet và kiểm tra kết nối | 29/04/2026 | 29/04/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5-6 | - Nghỉ lễ 30/04 - 01/05 | | | |

### Kết quả đạt được trong Tuần 2:
- Hiểu kiến trúc mạng cơ bản trên AWS:
  - Subnet chỉ nằm trong 1 AZ; public/private subnet bản chất giống nhau, khác nhau ở cách cấu hình route (public subnet cần custom route table trỏ ra Internet Gateway)
  - Địa chỉ IP không gán trực tiếp vào EC2 mà gán qua card mạng ảo ENI; ENI có thể tháo ra gắn sang máy chủ khác mà vẫn giữ private IP, Elastic IP và địa chỉ MAC
  - Elastic IP là IPv4 tĩnh, không đổi khi restart máy chủ, bị tính phí kể cả khi không sử dụng
- Phân biệt được hai lớp tường lửa trên AWS:
  - Security Group: stateful, chỉ có rule allow, áp dụng ở mức ENI
  - Network ACLs: stateless, cần cấu hình cả chiều vào và ra, áp dụng ở mức subnet nên thay đổi có thể ảnh hưởng nhiều máy chủ cùng lúc
- Hiểu được vai trò Internet Gateway (cho máy chủ ra internet, AWS tự quản lý và scale) và NAT Gateway (cho private subnet ra internet một chiều).
- Hoàn thành lab dựng VPC hoàn chỉnh: VPC → Subnet → Route Table → IGW → NAT → Security Group → NACLs → tạo EC2 trong subnet và test kết nối.