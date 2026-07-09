---
title: "Kiểm thử End-to-End"
date: 2026-07-08
weight: 4
chapter: false
pre: " <b> 5.4.4. </b> "
---

Bước này xác nhận toàn bộ stack LiveCap – từ trình duyệt qua CloudFront, ALB,
Fargate, Transcribe, Translate và ngược lại – hoạt động chính xác cùng nhau.

## Checklist kiểm thử

Thực hiện theo thứ tự sau. Mỗi bước dựa trên bước trước đó.

### 1. Health Endpoint

```powershell
Invoke-RestMethod https://dpeohr327wt9l.cloudfront.net/api/health
```

Kết quả mong đợi: `{"status": "healthy", "version": "1.0.0"}`

Nếu thất bại, ECS task không healthy hoặc CloudFront routing bị lỗi. Kiểm tra
trạng thái ALB target group trước tiên.

### 2. Backend có thể truy cập qua CloudFront

Health endpoint đi qua toàn bộ đường CloudFront → ALB → Fargate. Response
`200 OK` xác nhận:

- CloudFront distribution đã deploy và đang nhận request ✓
- ALB listener đang route đến ECS target group ✓
- ECS Fargate task healthy và đang phản hồi trên port 8000 ✓

### 3. Kết nối WebSocket

Mở Developer Tools (F12) → tab Network → lọc theo WS. Sau đó bấm **Start**
trong dashboard LiveCap. Bạn sẽ thấy:

- Kết nối WebSocket đến `wss://dpeohr327wt9l.cloudfront.net/ws/transcribe`
- Status: `101 Switching Protocols`
- Các frame `ping`/`pong` đều đặn mỗi 30 giây

### 4. Phiên phụ đề trực tiếp

Nói một câu rõ ràng vào microphone. Trong vòng 2–5 giây bạn sẽ thấy một
caption row song ngữ finalized xuất hiện. Dùng câu test ví dụ:

> "Live captions are working correctly for the workshop demonstration."

Bạn sẽ thấy bản gốc tiếng Anh và bản dịch tiếng Việt song song.

### 5. Export và tải xuống

1. Bấm **Stop** để kết thúc phiên.
2. Bấm **Export TXT**.
3. Xác minh tải xuống bắt đầu và file chứa các finalized row.
4. Xác minh S3 object tồn tại bằng CLI:

```powershell
aws s3 ls s3://livecap-transcripts-dev-720459752315/transcripts/ `
  --profile livecap-codex --region ap-southeast-1
```

### 6. CloudWatch Logs

Kiểm tra backend đã emit structured log trong phiên vừa rồi:

```powershell
aws logs tail livecap `
  --follow `
  --since 10m `
  --region ap-southeast-1 `
  --profile livecap-codex
```

Bạn sẽ thấy các sự kiện vòng đời phiên: mở, nhận audio chunk, kết quả
Transcribe, các lần gọi Translate, đóng phiên.

## Kết quả kiểm thử production đã xác minh

Ngày 2026-07-08, sau khi hoàn thành blue/green cutover sang kiến trúc target
(custom VPC, private subnet, NAT Gateway, WAF, scale-to-zero, budget alert),
toàn bộ luồng production đã pass tất cả bài test sau:

| Bài test | Kết quả |
|---|---|
| Health endpoint | `{"status":"healthy","version":"1.0.0"}` ✓ |
| Mở WebSocket | 101 Switching Protocols ✓ |
| Phiên âm tiếng Việt PCM 16 kHz thực | Trả về finalized text ✓ |
| Phiên âm tiếng Anh PCM 16 kHz thực | Trả về finalized text ✓ |
| Dịch tiếng Anh → tiếng Việt | Trả về bản dịch chính xác ✓ |
| Heartbeat ping/pong | Duy trì interval 30 giây ✓ |
| Kết thúc phiên sạch (nút Stop) | Session đóng, registry cleared ✓ |
| Export transcript S3 | TXT object được tạo trong bucket private ✓ |
| Tải xuống qua presigned URL | File tải thành công ✓ |
| Kiểm thử WAF blocking | XSS và Log4J probe trả về HTTP 403 ✓ |
| ECS scale-to-zero (idle 300s) | Service scale về 0 sau 5 phút không dùng ✓ |
| ECS self-healing (wake Lambda) | Scale từ 0 → 1 và healthy trong ≩60s ✓ |

![Xác minh end-to-end: phiên âm, dịch và export pass trên production](/images/5-Workshop/livecap-transcribe-translate-export-verification.png)

![Xác minh bảo mật runtime: WAF blocking và giới hạn session](/images/5-Workshop/livecap-runtime-security-verification.png)