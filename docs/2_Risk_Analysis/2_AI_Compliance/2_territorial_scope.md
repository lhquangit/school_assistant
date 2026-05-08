# Territorial Scope — School Assistant

**Date:** 08/05/2026

## Câu hỏi 1: User EU?

- User EU hiện tại: `0` 
- Kế hoạch mở rộng EU 12 tháng: `NO` 
- **Kết luận:** `EU AI Act áp dụng trực tiếp cho phạm vi khách hàng hiện tại = NO`

## Câu hỏi 2: Dữ liệu Việt Nam?

### Loại dữ liệu cá nhân đang xử lý

1. **Dữ liệu định danh phụ huynh:** tên, số điện thoại, email, trạng thái phản hồi như `Đã xem` / `Cần hỗ trợ`
2. **Dữ liệu định danh học sinh và ngữ cảnh trường học:** tên học sinh, lớp, môn học, giáo viên, quan hệ phụ huynh-học sinh
3. **Dữ liệu học tập của trẻ em:** điểm số theo môn, nhận xét giáo viên, lịch sử thay đổi, timestamp cập nhật
4. **Dữ liệu hành vi sử dụng app:** mở push notification, mở insight, lịch sử tương tác, thời điểm phản hồi
5. **Dữ liệu kỹ thuật/phân phối:** push token, device/app identifiers, IP hoặc log truy cập ở mức hạ tầng

### Loại dữ liệu chưa thấy trong scope hiện tại

- `Biometric`: chưa thấy trong PRD/pitch
- `Tài chính / thẻ`: chưa thấy trong PRD/pitch

### Có chuyển ra nước ngoài: `YES`

### Căn cứ cho kết luận chuyển dữ liệu

- Incident playbook có URL `Langfuse cloud`, cho thấy trace/log có khả năng đi qua dịch vụ cloud ngoài hệ thống trường.
- Dùng vendor AI nước ngoài như `OpenAI`, `Anthropic` = có yếu tố `chuyển dữ liệu ra nước ngoài`.

### Kết luận

- `PDPL áp dụng = YES`
- `CTIA = YES`

### Vì sao kết luận này gần như chắc chắn

- Sản phẩm xử lý dữ liệu học tập gắn với trẻ em và phụ huynh tại Việt Nam.
- Sản phẩm không chỉ lưu trữ mà còn xử lý, diễn giải và gửi insight từ dữ liệu cá nhân.
- Khi dữ liệu hoặc trích đoạn dữ liệu được gửi sang vendor AI/cloud nước ngoài để sinh insight, trace hoặc monitoring, rủi ro cross-border transfer đã phát sinh.

## Câu hỏi 3: Tầng rủi ro Luật AI VN?

- Phân loại: `Cao`
- Lập luận: School Assistant hoạt động trong `giáo dục`, tạo insight học tập parent-facing từ dữ liệu thật của trẻ em, và output có thể ảnh hưởng trực tiếp tới cách phụ huynh, giáo viên và nhà trường đánh giá hoặc can thiệp với học sinh. Dù sản phẩm không phải hệ thống chấm điểm tự động hoàn toàn, nó vẫn nằm sát nhóm use case giáo dục mà handbook xếp vào tầng `Cao`.
- Nghĩa vụ tương ứng:
  - đánh giá phù hợp trước khi deploy
  - đăng ký / thông báo vào CSDL AI quốc gia theo yêu cầu của Luật AI VN
  - thiết kế `human oversight` cho các insight nhạy cảm hoặc tiêu cực
  - lưu log đầy đủ cho input, output, fallback reason và thời điểm gửi
  - có quy trình báo cáo sự cố và kill switch cho parent-facing AI

## 4 deadlines cần note vào Notion

- `1/1/2026` — PDPL hiệu lực (đã qua)
- `1/3/2026` — Luật AI VN hiệu lực (đã qua)
- `2/8/2026` — EU AI Act high-risk hiệu lực đầy đủ
- `1/3/2027` — Mốc checklist theo workshop template cho lĩnh vực không thuộc health/edu/finance

### Note riêng cho School Assistant

- Vì School Assistant thuộc `giáo dục`, handbook ghi nhóm `health/edu/finance` có ân hạn `18 tháng` kể từ `1/3/2026`.
- Mốc founder nên theo dõi thêm là `1/9/2027` nếu áp dụng đúng logic ân hạn riêng cho giáo dục.

## Hành động founder nên làm ngay tuần này

1. Chốt data-flow map chỉ rõ trường dữ liệu nào đi vào model/vendor nước ngoài và trường dữ liệu nào phải giữ nội bộ.
2. Chuẩn bị `CTIA + DPIA` cho luồng parent insight trước pilot thật.
3. Gắn nhãn nội bộ rằng School Assistant đang ở `high-risk education AI`, không để team tự mặc định đây chỉ là `chatbot trung bình`.
4. Tạo founder-owned evidence pack cho human oversight: ai duyệt case nhạy cảm, khi nào fallback, log lưu ở đâu, kill switch là gì.

