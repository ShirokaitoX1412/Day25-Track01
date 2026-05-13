# card.md — Lớp 3: Kiến trúc dữ liệu/RAG đảm bảo “có nguồn thì trả lời”

## 1) Rủi ro xử lý

- ID tình huống: **T-02, T-03, T-04, T-11, T-12**
- Mẫu lỗi: model trả lời theo “tri thức chung” hoặc dữ liệu stale, không kèm nguồn chính thức

## 2) Tầng giải pháp

Nếu không có hệ dữ liệu/grounding tốt, prompt chỉ giảm rủi ro chứ không đảm bảo trả lời đúng.
Kiến trúc cần đảm bảo:

- Câu hỏi rủi ro cao → **bắt buộc** truy xuất nguồn chính thức
- Nguồn quá cũ/không có → **không được** nêu ngày/điều kiện → fallback an toàn (escalate)

## 3) Bản demo

- File demo: `./demo.md`
- Người phản biện cần thấy:
  - Router nhận diện “deadline/policy”
  - Retrieval từ KB có `last_updated`
  - Freshness gate + human handoff
  - Logging để cải thiện KB

## 4) Tác dụng phụ & cách giảm

- Tác dụng phụ: phụ thuộc chất lượng KB; tăng chi phí vận hành/cập nhật; có thể trả lời chậm hơn.
  - Giảm bằng cách: cache câu hỏi phổ biến; batch update theo lịch; chỉ bật freshness gate cho “risk-high”.

## 5) Hành động phòng vệ

- [x] Ngăn
- [x] Phát hiện
- [x] Khắc phục
- [ ] Thông báo
