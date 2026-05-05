# Day 1 — AI Product Strategy & Market Analysis — Practice Output

## 1. Idea reframed

Original idea:

> Hệ thống Chatbot cho trường học

Observed gap:

> Phụ huynh luôn phải đợi đến cuối học kỳ mới biết được tình trọng học tập của con họ (điểm số, xếp hạng, nhận xét của giáo viên)

Reframed as a product opportunity:

> Cơ hội đóng gói Chatbot kết nối phụ huynh và nhà trường

---

## 2. Customer / Segment Card

- **Segment name:** Trường cấp 1, cấp 2 có hệ thống update điểm số, nhận xét của giáo viên theo chu kì
- **Operational context:** Trong suốt học kỳ, giáo viên liên tục cập nhật điểm và nhận xét vào hệ thống nội bộ, nhưng phụ huynh chỉ biết thông tin khi đến kỳ tổng kết, khiến họ không kịp can thiệp khi con có dấu hiệu học sa sút.
- **Recurring workflow:** 
  - Từ góc nhìn giáo viên:  
  Nhập điểm bài kiểm tra → cập nhật nhận xét → upload lên hệ thống → lặp lại mỗi tuần / mỗi lần kiểm tra
  - Từ góc nhìn phụ huynh:  
  Nhận thông báo → (có thể) đăng nhập hệ thống → xem điểm / nhận xét của giáo viên / xếp hạng → trao đổi với con → lặp lại theo kỳ hoặc khi có vấn đề
- **Pain moment:** Phụ huynh chỉ biết tình trạng học tập của con khi đã tổng kết cuối kỳ, khiến họ mất cơ hội can thiệp sớm và dẫn đến kết quả học tập thấp hoặc tụt hạng.
- **Why now:** Các trường học đã số hóa dữ liệu học tập, nhưng việc truyền tải thông tin tới phụ huynh vẫn bị gián đoạn theo chu kỳ. Sự xuất hiện của AI cho phép tự động hóa việc tổng hợp và gửi thông tin theo thời gian thực, biến một quy trình trước đây thủ công và không kịp thời thành trải nghiệm liên tục.
- **Access path:** Tiếp cận ban giám hiệu hoặc phòng IT của trường để tích hợp vào hệ thống quản lý học tập hiện có, sau đó triển khai xuống phụ huynh thông qua kênh thông báo chính thức của nhà trường.

---

## 3. Need Map

- **Statement (JTBD):** Khi kết quả học tập của con tôi chỉ được thể hiện vào cuối kỳ, tôi muốn nắm bắt tiến độ học tập của con kịp thời để có thể can thiệp trước khi quá muộn nhằm cải thiện kết quả.
- **Current workaround:** 
  - Hỏi trực tiếp con: Phụ huynh hỏi con về tình hình học tập mỗi ngày / mỗi tuần
  - Chỉ xem khi có thông báo: Phụ huynh chỉ kiểm tra điểm khi có thông báo từ nhà trường hoặc đến kỳ họp phụ huynh
  - Nhắn giáo viên khi có vấn đề: Khi nghi ngờ con học yếu, phụ huynh chủ động nhắn tin hỏi giáo viên
- **Pain signal:** 
  - Mất cơ hội can thiệp: Phụ huynh chỉ phát hiện con học yếu khi đã quá muộn để cải thiện kết quả trong kỳ
  - Mất thời gian: Phụ huynh phải chủ động hỏi giáo viên hoặc con nhiều lần mới nắm được tình hình học tập
  - Stress vận hành (cả 2 phía): Giáo viên nhận nhiều tin nhắn hỏi riêng từ phụ huynh, gây quá tải trong việc phản hồi
  - Outcome xấu: Kết quả học tập của học sinh giảm mà không được phát hiện sớm
- **Evidence / proxy evidence:** Phụ huynh thường trao đổi trong các group lớp để hỏi thông tin về điểm số và tình hình học tập của con, và giáo viên thường xuyên nhận tin nhắn hỏi riêng, cho thấy việc tiếp cận thông tin hiện tại chưa thuận tiện và kịp thời.
- **Why underserved:** Mặc dù dữ liệu học tập đã được số hóa trong hệ thống nhà trường, phụ huynh không có thói quen truy cập thường xuyên và các hệ thống hiện tại không chủ động cung cấp thông tin theo thời gian thực, khiến nhu cầu theo dõi liên tục chưa được phục vụ tốt.

---

## 4. Strategy Statement

**Khách hàng mục tiêu:**  

Phụ huynh học sinh cấp 1–2 không có thói quen theo dõi hệ thống quản lý học tập thường xuyên

**Nhu cầu chưa được phục vụ tốt:**  

Phụ huynh cần được cung cấp thông tin học tập của con một cách kịp thời, dễ hiểu và có thể hành động ngay, thay vì phải chủ động tìm kiếm hoặc chờ các mốc thông báo định kỳ

**Kết quả cốt lõi (Core outcome):**  

Giúp phụ huynh phát hiện sớm vấn đề và can thiệp kịp thời để tránh việc kết quả học tập của con bị giảm sút

**Cách tiếp cận khác biệt (Distinct approach):**  

Biến dữ liệu học tập trong hệ thống nội bộ thành các insight dễ hiểu và chủ động phân phối tới phụ huynh theo thời gian thực, thay vì phụ thuộc vào hành vi truy cập của họ

**Giải pháp thay thế hiện tại (Current alternatives):**  

- Phụ huynh hỏi trực tiếp con về tình hình học tập  

- Nhắn tin riêng cho giáo viên khi cần thông tin  

- Chủ động đăng nhập hệ thống quản lý học tập để kiểm tra  

- Chỉ nhận thông tin tại các thời điểm như họp phụ huynh hoặc thông báo chính thức  

**Lợi thế (Advantage):**  

Khả năng tích hợp trực tiếp vào hệ thống quản lý học tập hiện có của nhà trường và tận dụng dữ liệu sẵn có để tạo ra luồng thông tin liên tục tới phụ huynh

---

## 5. Moat Hypothesis

**Moat mechanism:** Moat mechanism: domain-learning flywheel kết hợp với workflow embedding.

If we deploy many times in this vertical, the following improve:
Nếu triển khai nhiều lần trong cùng một hệ thống trường học, các yếu tố sau sẽ được cải thiện một cách hệ thống:

1. Độ chính xác của insight học tập

→ Hệ thống hiểu rõ hơn cách giáo viên chấm điểm, viết nhận xét, và pattern học tập của học sinh
2. Mức độ cá nhân hóa cho phụ huynh
→ Thông tin được trình bày phù hợp hơn với từng phụ huynh (ngắn gọn, dễ hiểu, đúng thứ họ quan tâm)
3. Khả năng dự đoán và cảnh báo sớm
→ Phát hiện sớm dấu hiệu học sa sút thay vì chỉ report sau khi đã xảy ra

Why competitors cannot easily replicate this:

> Đối thủ có thể sao chép tính năng, nhưng không thể nhanh chóng tái tạo được dữ liệu lịch sử và sự hiểu biết sâu về cách vận hành cụ thể của từng trường, vốn được tích lũy qua quá trình triển khai và sử dụng liên tục.

