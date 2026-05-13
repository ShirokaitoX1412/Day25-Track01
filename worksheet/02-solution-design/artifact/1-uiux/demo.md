---
artifact: 1 — Demo UI/UX
format: ASCII wireframe + flow
---

# demo.md — Demo UI/UX cho câu hỏi deadline/policy

## 1) ASCII wireframe (trong chat)

```text
User: Hạn chót nộp hồ sơ học bổng Data & AI 2026 là ngày nào? Em cần ngày chính xác.

Bot:
  [⚠ Chưa thể xác minh ngày chính xác]
  Mình chưa tìm thấy thông báo chính thức về “Học bổng Data & AI 2026” trong nguồn dữ liệu hiện tại,
  nên mình không thể đưa ra một ngày cụ thể để tránh bạn bị nộp sai hạn.

  Bạn có thể xác minh nhanh theo 1 trong 2 cách:
  1) Mở trang thông báo học bổng (nguồn chính thức)  -> [Mở trang nguồn]
  2) Liên hệ phòng tuyển sinh                               -> [Gọi hotline] [Gửi email]

  (Gợi ý) Nếu bạn cho mình biết tên học bổng chính xác + cơ sở + đợt xét tuyển, mình có thể giúp bạn tìm đúng trang nguồn.
```

## 2) Trạng thái “Đã xác minh” khi có nguồn

```text
Bot:
  [✅ Đã xác minh]
  Deadline nộp hồ sơ: 01/06/2026
  Nguồn: Thông báo học bổng (PDF) — cập nhật 01/05/2026  -> [Mở PDF]
  Nếu bạn cần xác nhận lần cuối:                           [Gọi hotline]
```

## 3) UI flow (tóm tắt)

```text
User hỏi -> Risk router phát hiện "deadline/policy"
  -> Nếu có nguồn + đủ mới: hiển thị badge ✅ + nguồn + CTA
  -> Nếu thiếu/nguồn cũ:  hiển thị badge ⚠ + không nêu ngày + CTA escalate
```
