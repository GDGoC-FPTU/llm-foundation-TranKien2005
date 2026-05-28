# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Khi temperature thấp như 0.0, phản hồi thường ổn định, trực tiếp và ít sáng tạo hơn. Khi tăng lên 1.0 hoặc 1.5, câu trả lời có xu hướng đa dạng, giàu màu sắc hơn nhưng cũng dễ lan man hoặc kém nhất quán hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ đặt khoảng 0.2–0.4 cho chatbot hỗ trợ khách hàng, vì loại chatbot này cần trả lời chính xác, nhất quán và ít bịa thông tin. Mức này vẫn đủ tự nhiên nhưng không quá ngẫu nhiên như các tác vụ sáng tạo.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Workload có 10.000 × 3 = 30.000 lần gọi API/ngày. Nếu mỗi lần khoảng 350 token thì tổng cộng khoảng 10.500.000 token/ngày. Dựa trên bảng giá trong bài, GPT-4o có giá input/output cao hơn GPT-4o-mini khoảng 33 lần, nên với cùng lượng token GPT-4o đắt hơn xấp xỉ 33 lần.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o xứng đáng khi tác vụ cần suy luận tốt, độ chính xác cao hoặc ảnh hưởng trực tiếp tới quyết định quan trọng, ví dụ phân tích tài liệu phức tạp hoặc tư vấn kỹ thuật. GPT-4o-mioại tini phù hợp hơn cho các tác vụ số lượng lớn, đơn giản và cần tối ưu chi phí như phân ln nhắn, trả lời FAQ cơ bản hoặc tóm tắt ngắn.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất khi phản hồi dài hoặc người dùng cần cảm giác hệ thống đang trả lời ngay, ví dụ chatbot, trợ lý viết nội dung, giải thích code hoặc tạo báo cáo dài. Nó giúp giảm cảm giác chờ đợi vì người dùng thấy từng phần phản hồi xuất hiện dần. Non-streaming phù hợp hơn khi phản hồi ngắn, cần xử lý toàn bộ kết quả trước khi hiển thị, hoặc khi hệ thống cần parse JSON/format cố định để dùng trong backend.


## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
