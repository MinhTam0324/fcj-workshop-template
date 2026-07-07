---
title: "Worklog Tuần 3"
date: 2026-05-04
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu Tuần 3:
- Nắm các phương thức kết nối nâng cao trong VPC: VPC Endpoint, VPC Peering, Transit Gateway, VPN và Direct Connect.
- Hiểu về cân bằng tải với Elastic Load Balancing.
- Thực hành lab VPC Peering và Route 53.

### Các công việc thực hiện trong tuần:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | ---- | ---------- | --------------- | ------------------ |
| 2 | - Học Module 2 (tiếp): <br>&emsp; + VPC Endpoint (Interface Endpoint và Gateway Endpoint) <br>&emsp; + VPC Peering | 04/05/2026 | 04/05/2026 | <https://www.youtube.com/@AWSStudyGroup/courses> |
| 3 | - Học các phương thức kết nối hybrid: <br>&emsp; + Transit Gateway <br>&emsp; + VPN Site-to-Site và Client-to-Site <br>&emsp; + AWS Direct Connect | 05/05/2026 | 05/05/2026 | <https://www.youtube.com/@AWSStudyGroup/courses> |
| 4 | - Học Elastic Load Balancing: <br>&emsp; + 4 loại: ALB, NLB, CLB, Gateway LB <br>&emsp; + Health Check, Sticky Session, Access Logs | 06/05/2026 | 06/05/2026 | <https://www.youtube.com/@AWSStudyGroup/courses> |
| 5 | - Thực hành Lab19 - VPC Peering: <br>&emsp; + Khởi tạo CloudFormation Templates <br>&emsp; + Tạo Security Group <br>&emsp; + Tạo EC2 instance và thiết lập VPC Peering | 07/05/2026 | 07/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Thực hành Lab10 - Route 53: <br>&emsp; + Route 53 Resolver Rules <br>&emsp; + Tạo Route 53 Inbound Endpoints <br>&emsp; + Kiểm tra kết quả và dọn dẹp tài nguyên | 08/05/2026 | 08/05/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được trong Tuần 3:
- Hiểu VPC Endpoint cho phép tài nguyên trong VPC kết nối đến dịch vụ AWS bên ngoài qua mạng nội bộ, không cần đi qua internet:
  - Interface Endpoint: dùng ENI với private IP để kết nối dịch vụ hỗ trợ
  - Gateway Endpoint: dùng route table để định tuyến, chỉ hỗ trợ S3 và DynamoDB
- Hiểu VPC Peering kết nối các VPC không qua internet: là kết nối 1:1, không hỗ trợ transitive routing và không dùng được khi 2 VPC bị trùng dải IP.
- Nắm các phương án kết nối hybrid:
  - Transit Gateway: kết nối nhiều VPC và mạng on-premises qua một hub trung tâm, đơn giản hóa định tuyến
  - VPN Site-to-Site: gồm Virtual Private Gateway và Customer Gateway (phía khách hàng)
  - Direct Connect: kết nối riêng từ data center đến AWS, độ trễ thấp, không mã hóa nên vẫn cần kết hợp VPN
- Hiểu Elastic Load Balancing phân phối request đến nhiều máy chủ:
  - Phân biệt 4 loại: ALB (layer 7, DNS), NLB (layer 4, hỗ trợ IP tĩnh), CLB (cũ, dần không dùng), Gateway LB
  - Health Check đảm bảo chỉ gửi request đến target còn hoạt động; Sticky Session giữ phiên người dùng trên cùng một target
- Hoàn thành lab VPC Peering với CloudFormation và lab Route 53.