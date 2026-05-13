---
artifact: 1 — Map + Format
bai-tap: 2 — Thiết kế giải pháp
phase: Chốt kết quả Bài 2
nop-cuoi: Có — file cuối Bài 2
---

# 1 — Thiết kế 3 lớp giải pháp (UI/Prompt/Architecture)

## Thông tin nhóm

- **Chủ đề**: Track 1 — Chatbot tư vấn tuyển sinh đại học (website tuyển sinh)
- **Thành viên**: Lê Quang Minh (2A202600381), Nguyễn Việt Hoàng (2A202600455)
- **Ngày**: 2026-05-13

---

## Phần A — Chọn rủi ro chính từ bộ test

**Rủi ro chính**: AI bịa hoặc khẳng định sai **deadline/policy tuyển sinh–học bổng** khi user cần “ngày chính xác” hoặc đang bị áp lực thời gian.

- ID đại diện trong bộ test: **T-02, T-04, T-10**
- Hậu quả: người dùng tin vì website “official” → hành động ngay → **mất cơ hội** (khó đảo ngược) + khiếu nại + giảm uy tín.

---

## Phần B — Nguyên nhân gốc (root cause)

### Failure pattern (1 câu)

Khi user hỏi deadline/policy cho năm/đợt mới và cần “ngày chính xác”, chatbot không lấy được nguồn chính thức hoặc nguồn bị stale → model suy đoán để “helpful” → UI không làm rõ mức chắc chắn và không có đường escalation → user tin và làm theo.

### Các nguyên nhân gốc (3 nhóm)

1) **Dữ liệu/grounding**

- Knowledge base không đầy đủ hoặc cập nhật chậm theo mùa tuyển sinh.
- Retrieval không bắt buộc “nguồn + ngày cập nhật” cho câu hỏi rủi ro cao.

2) **Hành vi model/prompt**

- Không có quy tắc cứng: “không có nguồn thì không được nêu ngày cụ thể”.
- Dễ sycophancy dưới áp lực (“cứ cho em ngày gần đúng”).

3) **Giao diện & vận hành**

- UI không hiển thị trạng thái “đã xác minh/chưa xác minh”.
- Thiếu nút/kênh chuyển sang tư vấn viên cho case rủi ro cao.

---

## Phần C — 3 lớp giải pháp (song song, bổ sung cho nhau)

### Lớp 1 — UI/UX (artifact/1-uiux)

- Mục tiêu: **Thông báo + Khắc phục** (giảm “tin tuyệt đối” và tăng khả năng tự xác minh)
- Giải pháp chính:
  - Badge trạng thái: `Đã xác minh` / `Chưa thể xác minh`
  - Bắt buộc hiển thị `Nguồn + Ngày cập nhật` với câu hỏi rủi ro cao
  - CTA: `Mở trang nguồn`, `Gọi hotline`, `Gặp tư vấn viên`
- Demo: `worksheet/02-solution-design/artifact/1-uiux/demo.md`
- Trạng thái: **Xong**

### Lớp 2 — Prompt/Guardrails (artifact/2-prompt)

- Mục tiêu: **Ngăn + Từ chối + Hỏi lại** (chặn bịa/đoán)
- Giải pháp chính:
  - Rule: “Không có nguồn → không nêu ngày cụ thể/điều kiện cụ thể”
  - Rule: “Deadline/policy → luôn trả lời kèm nguồn hoặc escalate”
  - Anti-sycophancy: từ chối “gần đúng”
- Demo: `worksheet/02-solution-design/artifact/2-prompt/demo.md`
- Trạng thái: **Xong**

### Lớp 3 — Kiến trúc dữ liệu / RAG (artifact/3-architecture)

- Mục tiêu: **Ngăn + Phát hiện + Khắc phục** (bảo đảm “có nguồn thì trả lời; thiếu nguồn thì fallback an toàn”)
- Giải pháp chính:
  - Knowledge base “authoritative” + versioning + `last_updated`
  - Router: nhận diện câu hỏi rủi ro cao (deadline/policy/tiền) → bắt buộc retrieval
  - Freshness gate: nguồn quá cũ → không trả lời ngày cụ thể; chuyển human
  - Logging: ghi lại FAIL/UNCLEAR để cập nhật KB
- Demo: `worksheet/02-solution-design/artifact/3-architecture/demo.md`
- Trạng thái: **Xong**

---

## Tổng kiểm tra

| Câu hỏi | Trả lời |
|---|---|
| Rủi ro chính đã chọn là gì? | Hallucination/overconfidence về deadline/policy (T-02/T-04/T-10) |
| Nguyên nhân gốc là gì? | KB/RAG không đảm bảo nguồn + prompt không chặn đoán + UI thiếu tín hiệu & escalation |
| 3 lớp có bổ sung nhau không? | Có: UI giảm tin mù quáng; Prompt chặn bịa; Architecture đảm bảo có nguồn & fallback |
| 4 hành động đã bao phủ chưa? | Ngăn: Prompt/Architecture; Phát hiện: Architecture; Khắc phục: UI/Architecture; Thông báo: UI |
