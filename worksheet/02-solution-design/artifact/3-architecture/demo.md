---
artifact: 3 — Demo kiến trúc dữ liệu/RAG
format: Mermaid + mô tả ngắn
---

# demo.md — Demo kiến trúc “deadline/policy phải có nguồn”

## 1) Sơ đồ luồng (Mermaid)

```mermaid
flowchart TD
  U[User] --> Q[User question]
  Q --> R{Risk router\n(deadline/policy/tuition?)}

  R -- No --> LLM1[LLM answer\n(normal FAQ)]
  LLM1 --> UI1[UI response]

  R -- Yes --> RET[Retriever\nquery KB]
  RET --> KB[(Authoritative KB\npages + PDFs\nwith last_updated)]
  KB --> RET
  RET --> F{Freshness gate\nsource exists & not stale?}

  F -- Yes --> LLM2[LLM grounded answer\nmust cite source]
  LLM2 --> UI2[UI shows ✅ verified\nsource + date]

  F -- No --> H[Human handoff\n(hotline/email/agent queue)]
  H --> UI3[UI shows ⚠ cannot verify\nno specific date + CTA]

  UI2 --> LOG[(Telemetry/logs)]
  UI3 --> LOG
  UI1 --> LOG
  LOG --> QA[Review failures\nupdate KB/tests]
```

## 2) Thành phần chính (tóm tắt)

| Thành phần | Nhận gì? | Làm gì? | Trả ra gì? |
|---|---|---|---|
| Risk router | Câu hỏi | Phân loại “risk-high” (deadline/policy/tiền) | Nhánh normal vs risk-high |
| KB | Nội dung chính thức | Lưu trang tuyển sinh/PDF + `last_updated` + `url` | Document chunks |
| Retriever | Query | Lấy đoạn liên quan + metadata nguồn | Context + citations |
| Freshness gate | Context + metadata | Chặn trả lời ngày cụ thể nếu thiếu nguồn/nguồn stale | allow / block |
| Human handoff | Case risk-high bị block | Điều hướng hotline/email/tư vấn viên | Kênh xác nhận |
| Telemetry | Logs | Ghi FAIL/UNCLEAR + loại câu hỏi | Input cho cải thiện |
