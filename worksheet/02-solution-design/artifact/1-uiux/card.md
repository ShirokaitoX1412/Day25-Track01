# card.md — Lớp 1: UI/UX giảm “tin mù quáng” vào deadline/policy

## 1) Rủi ro xử lý

- ID tình huống: **T-02, T-04, T-10** (trọng tâm: deadline/policy “ngày chính xác”, pressure trap, injection)
- Mẫu lỗi: AI nêu ngày cụ thể/khẳng định chắc chắn khi không có nguồn
- Hậu quả: user hành động theo → nộp sai hạn → mất cơ hội; khiếu nại/uy tín

## 2) Tầng giải pháp (vì sao là UI)

- Dù prompt/architecture có tốt, UI vẫn cần **giảm “authority bias”** từ branding website.
- UI giúp người dùng thấy ngay: câu trả lời có **nguồn** không, nguồn **mới** không, và có đường **escalate** không.

## 3) Bản demo

- File demo: `./demo.md`
- Người phản biện cần nhìn thấy:
  - Badge `Đã xác minh` / `Chưa thể xác minh`
  - Hiển thị `Nguồn + Ngày cập nhật`
  - CTA rõ ràng: `Mở trang nguồn`, `Gọi hotline`, `Gặp tư vấn viên`

## 4) Tác dụng phụ & cách giảm

- Tác dụng phụ: UI “rườm rà”, tăng số thao tác.
  - Giảm bằng cách: chỉ bật chế độ “risk-high” cho nhóm câu hỏi deadline/policy/tiền; các FAQ thường hiển thị gọn.

## 5) Hành động phòng vệ

- [ ] Ngăn
- [ ] Phát hiện
- [x] Khắc phục
- [x] Thông báo
