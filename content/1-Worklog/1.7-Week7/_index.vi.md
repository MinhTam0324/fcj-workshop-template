---
title: "Worklog Tuần 7"
date: 2026-06-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu Tuần 7:
- Tìm hiểu, đọc và nghiên cứu các dịch vụ bảo mật trên AWS.
- Thực hành cơ bản một số bài lab về bảo mật.

### Các công việc thực hiện trong tuần:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | ---- | ---------- | --------------- | ------------------ |
| 2 | - Tìm hiểu AWS SSO: quản lý đăng nhập tập trung cho Organization <br> - Thực hành cơ bản lab thiết lập SSO | 01/06/2026 | 01/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - Nghiên cứu về kiểm soát quyền trong IAM: <br>&emsp; + IAM Permission Boundary <br>&emsp; + Giới hạn Role Transfer bằng Condition | 02/06/2026 | 02/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Tìm hiểu AWS Security Hub và các security benchmark <br> - Thực hành cơ bản lab Security Hub | 03/06/2026 | 03/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Nghiên cứu AWS WAF: cơ chế bảo vệ ứng dụng web và API | 04/06/2026 | 04/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Tìm hiểu AWS KMS: quản lý key mã hóa <br> - Thực hành cơ bản lab KMS | 05/06/2026 | 05/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được trong Tuần 7:
- Hiểu vai trò của AWS SSO: quản lý đăng nhập tập trung cho nhiều tài khoản AWS trong Organization thay vì tạo IAM User riêng lẻ từng tài khoản.
- Nắm được các cơ chế kiểm soát quyền nâng cao trong IAM:
  - Permission Boundary: đặt giới hạn quyền tối đa cho User/Role, kể cả khi policy cấp quyền rộng hơn
  - Dùng Condition để giới hạn việc chuyển giao Role, giảm rủi ro leo thang đặc quyền
- Biết được AWS Security Hub dùng để kiểm tra tình trạng bảo mật của tài khoản theo các security benchmark và tổng hợp cảnh báo từ nhiều dịch vụ về một nơi.
- Nắm cơ chế hoạt động của AWS WAF: bảo vệ ứng dụng web và API khỏi các cuộc tấn công phổ biến qua các rule lọc request.
- Hiểu được AWS KMS dùng để tạo và quản lý key mã hóa, và cách các dịch vụ AWS tích hợp với KMS để mã hóa dữ liệu.
- Thực hành cơ bản các lab về SSO, Security Hub và KMS.