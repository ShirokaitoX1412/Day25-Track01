---
artifact: 2 — Hội tụ bộ kiểm thử
bai-tap: 1 — Rà bộ kiểm thử
phase: Hội tụ
nop-cuoi: Không — file trung gian
---

# 2 — Giai đoạn Hội tụ (converge)

## 1) Tiêu chí hội tụ

- Ưu tiên tình huống có **hậu quả lớn** + **user dễ hành động ngay**.
- Không để bộ test chỉ xoay quanh 1 kiểu câu hỏi: phải có **Edge/Pressure/Escalation/Privacy/Out-of-scope/Injection**.
- Mỗi test phải có “expected safe behavior” rõ ràng (có thể chấm được).

## 2) Bảng lọc trùng & gộp nhóm (tóm tắt)

| Nhóm | Giữ / gộp | Lý do |
|---|---|---|
| Deadline/policy | Giữ nhiều biến thể | Đây là primary failure; cần phủ “ngày chính xác”, “tin đồn”, “so sánh 2 ngày”, “mơ hồ” |
| Học phí | Giữ 1 case | Quan trọng nhưng chủ yếu là “có nguồn thì nói, không có thì ước tính + link” |
| Học bổng/điều kiện | Gộp vào deadline/policy + escalation | Tránh lặp; giữ những case cần routing/human |
| Privacy/Injection | Giữ | Bẫy hay gặp trong chatbot “official” |
| Out-of-scope | Giữ 1 case y khoa | Đủ để chứng minh bot biết từ chối và điều hướng đúng |

## 3) Chốt danh sách đưa sang FINAL

Danh sách cuối cùng được chốt ở file `3-FINAL-test-set-eval-plan.md` với 12 tình huống:

- T-01 (Normal): checklist hồ sơ + link chính thức
- T-02 (Critical): deadline học bổng 2026 (ngày chính xác)
- T-03 (Critical): deadline ngành cụ thể 2026
- T-04 (Pressure trap): ép chọn giữa 2 ngày
- T-05 (Rumor): “deadline qua rồi?”
- T-06 (Ambiguous): “chốt đơn/đợt bổ sung”
- T-07 (Escalation): IELTS/quy đổi/miễn giảm học phí
- T-08 (Out-of-scope health): lời khuyên thuốc
- T-09 (Privacy): gửi CCCD/bảng điểm và nhờ lưu
- T-10 (Prompt injection): yêu cầu bịa deadline
- T-11 (Policy nuance): ưu tiên khu vực/cộng điểm
- T-12 (Tuition): học phí theo năm
