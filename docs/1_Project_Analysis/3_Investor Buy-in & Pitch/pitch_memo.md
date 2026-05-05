# Pitch Memo

**Audience:** Seed VC

## 1. The Problem

Phụ huynh học sinh cấp 1-2 tại các trường đã số hóa dữ liệu vẫn thường chỉ biết con mình học sa sút khi đến kỳ tổng kết hoặc khi giáo viên phải chủ động báo riêng. Trong khi giáo viên cập nhật điểm và nhận xét gần như mỗi tuần, phụ huynh hiếm khi đăng nhập LMS thường xuyên, nên cơ hội can thiệp sớm bị bỏ lỡ và giáo viên bị kéo vào vòng lặp trả lời cùng một loại câu hỏi trạng thái.

## 2. The Insight

Vấn đề của thị trường này không phải thiếu dữ liệu học tập hay thiếu thêm một LMS; vấn đề là nhà trường chưa có một lớp trải nghiệm dành riêng cho phụ huynh, chỉ nổi bật các thay đổi học tập thật sự đáng hành động và đủ rõ để họ tin tưởng.

## 3. The Solution

School Assistant kết nối read-only vào hệ thống quản lý học tập của trường, phát hiện các thay đổi điểm số và nhận xét có tín hiệu cao, rồi chuyển chúng thành "insight học tập" ngắn gọn trong một app riêng cho phụ huynh, kèm push notification, context từ 2-3 lần cập nhật gần nhất và phản hồi một chạm như "Đã xem" hoặc "Cần hỗ trợ". Khác với LMS hay dashboard thụ động, sản phẩm không bắt phụ huynh tự đi tìm thông tin trong một hệ thống cồng kềnh; nó chỉ xuất hiện khi có điều gì đáng chú ý và lưu toàn bộ lịch sử insight để phụ huynh hành động đúng lúc. AI được dùng một cách bảo thủ: MVP có thể bắt đầu bằng rule-based logic cộng model nhẹ, và các trường hợp dữ liệu yếu hoặc mâu thuẫn sẽ fallback sang thông tin trung tính thay vì đưa ra kết luận mạnh.

## 4. Why Now

Các trường học hiện đã có dữ liệu điểm số, nhận xét và timestamp trong LMS/SIS, nhưng trải nghiệm phụ huynh vẫn bị mắc kẹt trong các cổng thông tin phục vụ lưu trữ hơn là can thiệp sớm. Khoảng trống của thị trường lúc này không còn ở việc số hóa dữ liệu nhà trường, mà ở việc xây một lớp parent-facing biến dữ liệu đó thành hành động kịp thời mà không yêu cầu nhà trường thay LMS.

## 5. Traction / Proof

Chúng tôi đang ở giai đoạn pre-traction, nên "proof" hiện tại không phải doanh thu mà là kế hoạch kiểm chứng có thể falsify nhanh. Chúng tôi có thể chạy pilot với 5-10 học sinh bằng prototype app đơn giản, chuẩn bị trong 2-4 ngày và quan sát phản ứng trong 2-3 ngày. Success bar đã được định nghĩa rõ: ít nhất 30-40% phụ huynh thực hiện một hành động trong vòng 24 giờ sau khi nhận insight, ít nhất 70% đánh giá insight là hữu ích hoặc dễ hiểu, và pilot phải chứng minh rằng một tỷ lệ đáng kể phụ huynh sẵn sàng cài app và giữ thông báo bật. Quan trọng hơn, bằng chứng nhu cầu đã hiện diện trong hành vi hiện tại: phụ huynh đang hỏi thông tin trong group lớp hoặc nhắn riêng giáo viên, còn giáo viên đang quá tải vì phải lặp lại cùng một luồng giải thích.

## 6. The Ask

Chúng tôi đang gọi 2 tỷ VND pre-seed để tích hợp với 3 trường đối tác đầu tiên, phát triển app phụ huynh bản đầu và chạy các pilot có đo lường để chứng minh rằng School Assistant có thể tạo ra hành vi phụ huynh hành động lặp lại chứ không chỉ tạo thêm một lớp thông báo. Trong 12 tháng tới, số vốn này sẽ được dùng để hoàn thiện lớp tích hợp dữ liệu nhà trường, tối ưu chất lượng insight, giảm friction onboarding và xây trust layer cho phụ huynh trước khi mở rộng sang nhiều trường hơn.
