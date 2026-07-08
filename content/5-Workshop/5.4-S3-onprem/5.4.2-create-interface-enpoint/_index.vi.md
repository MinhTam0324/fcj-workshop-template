---
title: "Phụ đề trực tiếp – Transcribe & Translate thực chiến"
date: 2026-07-08
weight: 2
chapter: false
pre: " <b> 5.4.2. </b> "
---

## Pipeline thời gian thực hoạt động như thế nào

Khi người dùng bấm **Start**, chuỗi sự kiện sau diễn ra tự động:

```
Microphone trình duyệt
  → Web Audio API worklet (resample về 16 kHz)
  → Các chunk PCM nhị phân gửi qua WebSocket (WSS)
  → CloudFront /ws/transcribe
  → Application Load Balancer
  → FastAPI trên ECS Fargate (port 8000)
  → Amazon Transcribe Streaming (hai stream song song: vi-VN và en-US)
  → Amazon Translate (chỉ finalized segment)
  → Caption row trả về qua đường WebSocket ngược lại
  → Dashboard phụ đề trình duyệt
```

Microphone chỉ bắt đầu thu âm **sau khi** health check backend pass và kết nối
WebSocket đã được thiết lập. Audio được tạo ra lúc socket chưa mở sẽ bị drop
thay vì buffer.

## Chế độ dual-stream song ngữ

Với `BILINGUAL_DUAL_STREAM=true`, backend chia mỗi chunk PCM vào hai Amazon
Transcribe stream song song:

1. **`vi-VN`** – nhận dạng giọng tiếng Việt
2. **`en-US`** – nhận dạng giọng tiếng Anh

Một bộ arbitrator chọn ngôn ngữ có finalized segment trước, rồi gửi text đó
đến Amazon Translate để tạo ngôn ngữ còn lại. Kết quả là một caption row song
ngữ:

```
[Tiếng Việt gốc]  |  [Bản dịch tiếng Anh]
[Tiếng Anh gốc]   |  [Bản dịch tiếng Việt]
```

Chỉ các segment **finalized** mới trở thành caption row vĩnh viễn. Kết quả
partial (interim) có thể hiển thị tạm thời trên UI nhưng không bao giờ được lưu.

## Khả năng phục hồi kết nối

| Sự kiện | Hành vi |
|---|---|
| Hoạt động bình thường | Frontend gửi `ping` mỗi 30 giây; backend trả lời `pong` |
| Mất kết nối bất ngờ | Frontend thử lại tối đa 3 lần: 1 s, 2 s, 4 s backoff |
| Kết nối lại thành công | Session backend mới bắt đầu; finalized row được giữ nguyên trên UI |
| Hết lần thử lại | Âm thanh dừng thu; người dùng phải bấm Start lại |
| Timeout 30 phút | Backend đóng session; frontend hiển thị "Phiên đã kết thúc" |

## Giới hạn session

Backend từ chối kết nối mới khi vượt giới hạn:

- **4 session đồng thời** toàn hệ thống (một ECS task, bộ nhớ process)
- **1 session trên mỗi client IP**

Các giới hạn này ngăn chặn chi phí Transcribe/Translate phát sinh ngoài kiểm
soát cho MVP. Trước khi scale lên nhiều task hơn, registry session phải chuyển
sang DynamoDB hoặc Redis (state chung giữa các task).

## Bắt đầu phiên phụ đề trực tiếp

1. Mở `https://dpeohr327wt9l.cloudfront.net`
2. Bấm **Start captioning** để đến `/app`
3. Bấm **Start** – frontend wake backend nếu cần, rồi poll health
4. Cho phép microphone khi trình duyệt hỏi
5. Nói tiếng Anh hoặc tiếng Việt
6. Xem caption row song ngữ finalized xuất hiện trên dashboard:

![Dashboard phụ đề LiveCap hiển thị caption row song ngữ](/images/3-Project/livecap-dashboard.png)

Dashboard production sẵn sàng bắt đầu phiên:

![Dashboard production – điều khiển phiên và trạng thái trước khi bắt đầu](/images/5-Workshop/livecap-production-dashboard-ready.png)

## Nếu microphone bị chặn?

Nếu trình duyệt chặn truy cập microphone, LiveCap dừng trước khi mở bất kỳ
stream nào và hiển thị thông báo lỗi rõ ràng thay vì để một session lỗi đang mở:

![Frontend hiển thị lỗi yêu cầu quyền microphone](/images/5-Workshop/livecap-microphone-permission-required.png)

Trong trường hợp này, cho phép microphone trong cài đặt site của trình duyệt
và tải lại `/app`.