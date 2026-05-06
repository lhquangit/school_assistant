# Workshop 2 — Now / Next / Later

## Cách sắp xếp

- `NOW`: lấy từ `Quick Win` và logic kiểm chứng hypothesis sớm nhất
- `NEXT`: lấy từ `Strategic Bets` trong 2x2
- `LATER`: vision lớn, rủi ro cao, có thể chưa technically khả thi hoặc chưa nên cam kết

Lưu ý: mọi mục dưới đây đều được viết dưới dạng `vấn đề cần giải`, không phải danh sách feature.

---

## Bảng Roadmap


| NOW                                                                                                                                                                                                                                                        | NEXT                                                                                                                                                                                                                                                         | LATER                                                                                                                                                                                                                                                                               |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Vấn đề:** Phụ huynh chưa nhận được insight học tập đủ rõ, đủ đáng tin và đủ “đáng hành động” để can thiệp sớm. <br> **Đang code:** Xây lớp `high-signal insight` từ dữ liệu điểm số và nhận xét hiện có, chỉ highlight các thay đổi thật sự đáng chú ý, kèm fallback guardrails để tránh false alarm. | **Vấn đề:** Sản phẩm chưa được nhúng đủ sâu vào workflow của nhà trường, nên moat vẫn yếu. <br> **Sẽ làm:** Mở rộng `read-only LMS/SIS integration + event sync` theo hướng ổn định hơn, để insight được tạo từ dữ liệu cập nhật thật. | **Vấn đề:** Hệ thống mới dừng ở mức phát hiện tín hiệu, chưa trở thành lớp hỗ trợ quyết định cá nhân hóa cho từng gia đình. <br> **Có thể làm:** Thử các hướng `predictive AI` hoặc `personalized recommendations` khi đã có đủ dữ liệu sạch, retention tốt và bằng chứng nhu cầu thật. |
| **Vấn đề:** Nhà trường đã có dữ liệu, nhưng chưa có một vòng lặp thực tế từ dữ liệu -> insight -> hành động của phụ huynh được kiểm chứng ngoài pilot. <br> **Đang code:** Dựng một `vertical slice` tối giản gồm ingest dữ liệu, insight generation, push notification và logging hành vi phụ huynh để kiểm chứng Aha Moment end-to-end. | **Vấn đề:** Phụ huynh chưa có một trải nghiệm riêng đủ đơn giản để quay lại khi có vấn đề đáng chú ý. <br> **Sẽ làm:** Hoàn thiện `app phụ huynh` như một lớp parent-facing chuyên biệt với push notification, lịch sử insight và context ngắn gọn. | **Vấn đề:** Sản phẩm mới giúp phụ huynh hành động sớm, nhưng chưa giải quyết toàn bộ vòng phối hợp giữa phụ huynh, giáo viên và nhà trường. <br> **Có thể làm:** Mở rộng sang workflow phối hợp sâu hơn như escalation sang giáo viên, lịch sử can thiệp hoặc lớp điều phối đa vai trò. |
|  | **Vấn đề:** Sau khi nhận insight, phụ huynh vẫn có thể bị kẹt ở bước “biết rồi nhưng chưa biết làm gì tiếp”. <br> **Sẽ làm:** Chuẩn hóa các hành động tiếp theo trong app như `Đã xem`, `Cần hỗ trợ thêm`, và các cue ngữ cảnh để bridge sang can thiệp thực tế. |  |


---

## NOW

### 1. Phụ huynh chưa nhận được insight học tập đủ rõ, đủ đáng tin và đủ “đáng hành động” để can thiệp sớm

**Đang code:** Xây lớp `high-signal insight` từ dữ liệu điểm số và nhận xét hiện có, chỉ highlight các thay đổi thật sự đáng chú ý, kèm fallback guardrails để tránh false alarm hoặc gửi kết luận mạnh khi dữ liệu yếu.

### 2. Nhà trường đã có dữ liệu, nhưng chưa có một vòng lặp thực tế từ dữ liệu -> insight -> hành động của phụ huynh được kiểm chứng ngoài pilot

**Đang code:** Dựng một `vertical slice` tối giản gồm ingest dữ liệu, insight generation, push notification và logging hành vi phụ huynh để kiểm chứng Aha Moment end-to-end trước khi mở rộng sang kiến trúc tích hợp sâu hơn.

---

## NEXT

### 1. Sản phẩm chưa được nhúng đủ sâu vào workflow của nhà trường, nên moat vẫn yếu

**Sẽ làm:** Mở rộng `read-only LMS/SIS integration + event sync` theo hướng ổn định hơn, để insight được tạo từ dữ liệu cập nhật thật thay vì dựa vào quy trình bán-thủ-công của pilot.

### 2. Phụ huynh chưa có một trải nghiệm riêng đủ đơn giản để quay lại khi có vấn đề đáng chú ý

**Sẽ làm:** Hoàn thiện `app phụ huynh` như một lớp parent-facing chuyên biệt với push notification, lịch sử insight và context ngắn gọn, thay vì buộc họ quay lại LMS gốc.

### 3. Sau khi nhận insight, phụ huynh vẫn có thể bị kẹt ở bước “biết rồi nhưng chưa biết làm gì tiếp”

**Sẽ làm:** Chuẩn hóa các hành động tiếp theo trong app như `Đã xem`, `Cần hỗ trợ thêm`, và các cue ngữ cảnh để bridge từ nhận biết sang can thiệp thực tế.

---

## LATER

### 1. Hệ thống mới dừng ở mức phát hiện tín hiệu, chưa trở thành lớp hỗ trợ quyết định cá nhân hóa cho từng gia đình

**Có thể làm:** Thử các hướng `predictive AI` hoặc `personalized recommendations` khi đã có đủ dữ liệu sạch, retention tốt và bằng chứng rằng phụ huynh thật sự muốn nhiều hơn insight cơ bản. Giai đoạn này `có thể bỏ` nếu độ tin cậy không đủ cao.

### 2. Sản phẩm mới giúp phụ huynh hành động sớm, nhưng chưa giải quyết toàn bộ vòng phối hợp giữa phụ huynh, giáo viên và nhà trường

**Có thể làm:** Mở rộng sang workflow phối hợp sâu hơn như escalation sang giáo viên, lịch sử can thiệp hoặc lớp điều phối đa vai trò. Đây là vision dài hạn, chưa nên cam kết cho milestone hiện tại.

---

## Tóm tắt logic ưu tiên

- `NOW` tập trung vào việc chứng minh: insight có đủ mạnh để làm phụ huynh hành động hay không.
- `NEXT` tập trung vào việc biến MVP thành hệ thống có moat hơn: nhúng sâu vào dữ liệu trường học và tạo trải nghiệm parent-facing đủ tốt.
- `LATER` giữ lại các hướng vision lớn nhưng chưa nên tiêu tốn effort khi core loop vẫn đang cần được xác thực.
