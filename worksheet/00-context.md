---
title: 00 — Bối cảnh sản phẩm của nhóm
section: Day 25 — dùng lại cho mọi cuộc trò chuyện với AI
format: Nhóm
---

# 00-context.md — Bối cảnh sản phẩm của nhóm

## 1. Sản phẩm

- **Tên sản phẩm / bot**: Chatbot tư vấn tuyển sinh (website tuyển sinh trường đại học — tham chiếu FPT University)
- **Sản phẩm giúp ai làm gì**: Học sinh lớp 12 / phụ huynh tra cứu nhanh thông tin tuyển sinh (ngành, hồ sơ, học phí, học bổng, timeline, phương thức xét tuyển) và được dẫn tới **nguồn chính thức**.
- **Người dùng gặp sản phẩm ở đâu**: Website tuyển sinh chính thức (ví dụ `admissions.fpt.edu.vn`), có branding của trường → dễ tạo cảm giác “thông tin chính thống”.
- **Giai đoạn hiện tại**: Chuẩn bị triển khai / pilot cho mùa tuyển sinh 2026.

---

## 2. Phạm vi

**AI được làm gì**

- Trả lời FAQ theo **knowledge base chính thức** (trang tuyển sinh, thông báo, quy chế, học phí/học bổng).
- Tóm tắt thông tin và **trích dẫn nguồn** (link + ngày cập nhật nếu có).
- Hỏi lại để làm rõ (ngành, cơ sở, đợt xét tuyển, hệ đào tạo, năm).
- Hướng dẫn kênh hỗ trợ: hotline/email/phòng tuyển sinh; tạo “checklist chuẩn bị hồ sơ”.

**AI không được làm gì**

- Không “đoán” hoặc **bịa** deadline, học phí, chính sách học bổng, điều kiện xét tuyển.
- Không khẳng định chắc chắn “đậu / được học bổng” dựa trên thông tin thiếu.
- Không thay thế kênh xác nhận chính thức cho trường hợp đặc thù (giấy tờ, quy đổi chứng chỉ, khiếu nại).
- Không thu thập hoặc yêu cầu PII nhạy cảm (CCCD, tài khoản ngân hàng, mật khẩu); không xử lý dữ liệu của thí sinh khác.

**Vì sao có giới hạn này**

- Thông tin sai về deadline/policy → học sinh nộp sai hạn → mất cơ hội tuyển sinh/học bổng (thiệt hại khó đảo ngược).
- Website “chính thức” làm tăng mức tin tưởng → rủi ro khuếch đại khi AI sai.

---

## 3. Người dùng

- **Là ai**: Học sinh lớp 12 (17–18 tuổi) và phụ huynh; nhiều người không rành quy trình/thuật ngữ.
- **Họ hỏi AI khi nào**: Buổi tối, sát deadline, hoặc lúc cần quyết định nhanh (chọn ngành, chọn đợt nộp).
- **Họ cần quyết định gì sau khi hỏi AI**: Chuẩn bị hồ sơ, nộp đơn, đóng phí, đăng ký xét học bổng, đặt lịch tư vấn.
- **Khi nào dễ tổn thương / dễ hiểu sai**: Khi bị áp lực thời gian; khi câu hỏi mơ hồ (đợt nào/cơ sở nào); khi nghe “tin đồn” từ bạn bè.
- **Mức tin vào AI**: Cao (vì đặt trên website trường), thường làm theo ngay nếu AI trả lời chắc chắn.

---

## 4. Bối cảnh ngành

- **Sự cố tương tự**: Chatbot có thể trả lời sai chính sách/điều kiện (đặc biệt deadline) → dẫn tới khiếu nại và mất uy tín.
- **Nguồn chính thức nên ưu tiên**: Trang tuyển sinh, thông báo PDF, quy chế tuyển sinh, trang học phí/học bổng, hotline/email phòng tuyển sinh.

---

## 5. Ghi chú thêm

- “Thông tin nhạy cảm / rủi ro cao” trong dự án này: **deadline**, **điều kiện học bổng**, **lệ phí**, **yêu cầu hồ sơ**, **chính sách xét tuyển**.
- Nguyên tắc trả lời an toàn: “Có nguồn thì trả lời + dẫn nguồn; không có nguồn thì nói không chắc + hướng dẫn kênh xác nhận”.
