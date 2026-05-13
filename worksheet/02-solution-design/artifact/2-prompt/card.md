# card.md — Lớp 2: Prompt/Guardrails chống bịa deadline/policy

## 1) Rủi ro xử lý

- ID tình huống: **T-02, T-03, T-04, T-05, T-10**
- Mẫu lỗi: “helpful guessing”, sycophancy dưới áp lực, làm theo prompt injection

## 2) Tầng giải pháp

- Prompt là lớp **ngăn chặn trực tiếp hành vi**: không cho phép nêu ngày cụ thể nếu không có nguồn.
- Prompt cũng định nghĩa tiêu chuẩn “đúng” để chấm: có nguồn hoặc nói không thể xác minh + routing.

## 3) Bản demo

- File demo: `./demo.md`
- Nội dung demo:
  - System prompt template (policy)
  - Ví dụ PASS cho T-02/T-04
  - Ví dụ FAIL (để đối chiếu khi chấm)

## 4) Tác dụng phụ & cách giảm

- Tác dụng phụ: trả lời “từ chối” nhiều → giảm trải nghiệm.
  - Giảm bằng cách: chỉ áp dụng rule cứng cho nhóm rủi ro cao (deadline/policy/tiền), còn FAQ thường trả lời bình thường.

## 5) Hành động phòng vệ

- [x] Ngăn
- [ ] Phát hiện
- [x] Khắc phục
- [x] Thông báo
