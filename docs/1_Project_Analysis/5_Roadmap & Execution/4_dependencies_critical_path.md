# Workshop 4 — Dependencies + Critical Path

## 1. 3 external dependencies có thể giết dự án trong 30 ngày tới

### Dependency 1: Quyền truy cập dữ liệu học tập từ nhà trường

**Worst-case:** Trường không cho truy cập dữ liệu thật, hoặc dữ liệu xuất ra thiếu điểm số, nhận xét hay thời điểm cập nhật, khiến pilot không thể tạo insight đáng tin.

**Plan B:** Thu hẹp pilot xuống `1 trường / 1 khối lớp`, dùng file xuất định kỳ thay cho kết nối trực tiếp, và chỉ chạy với 3 trường dữ liệu bắt buộc: điểm, nhận xét, thời gian cập nhật. Đồng thời chỉ định một đầu mối từ phía trường để kiểm tra dữ liệu mỗi tuần.

**Cost:** Khoảng `1 tuần` để chuẩn hóa file mẫu, quy trình nhận dữ liệu và kiểm tra chất lượng; chi phí tiền mặt thấp, chủ yếu là thời gian phối hợp với trường.

### Dependency 2: Kênh phân phối app và thông báo tới phụ huynh

**Worst-case:** App chưa tới được tay phụ huynh đúng lúc, hoặc phụ huynh cài app nhưng không bật thông báo, làm cho insight không tạo ra hành động trong 24 giờ.

**Plan B:** Chạy pilot qua hình thức phân phối giới hạn như nhóm thử nghiệm nội bộ và dùng một kênh nhắc tạm thời cho pilot nếu phụ huynh chưa bật thông báo. Đồng thời bổ sung hướng dẫn cài đặt ngắn 1 trang và một buổi onboarding tập trung cho nhóm phụ huynh đầu tiên.

**Cost:** Khoảng `3-5 ngày` để chuẩn bị kênh phân phối thử nghiệm, tài liệu hướng dẫn và kịch bản onboarding; chi phí tiền mặt thấp đến trung bình tùy kênh nhắc tạm thời dùng trong pilot.

### Dependency 3: Nhà cung cấp AI hoặc lớp diễn giải insight

**Worst-case:** Chất lượng diễn giải insight không ổn định hoặc dịch vụ AI bị gián đoạn, làm thông điệp gửi tới phụ huynh bị khó hiểu, sai ngữ cảnh hoặc chậm.

**Plan B:** Chuyển toàn bộ pilot sang chế độ `rule-based + template wording`, chỉ gửi các trường hợp tín hiệu rất rõ như giảm điểm liên tiếp hoặc nhận xét tiêu cực mới xuất hiện. Tạm thời hy sinh độ linh hoạt để giữ độ rõ ràng và độ tin cậy của insight.

**Cost:** Khoảng `2-3 ngày` để chuẩn hóa bộ template và rule ưu tiên; chi phí tiền mặt gần như bằng 0, chủ yếu là thời gian chỉnh nội dung và kiểm thử.

---

## 2. Nhận định nhanh theo mức độ nguy hiểm


| Dependency                                    | Mức độ               | Vì sao nguy hiểm                                                                                     |
| --------------------------------------------- | -------------------- | ---------------------------------------------------------------------------------------------------- |
| Quyền truy cập dữ liệu học tập từ nhà trường  | `Tier 1 - Critical`  | Không có dữ liệu thật thì không có insight, không có pilot, không có học nhanh.                      |
| Kênh phân phối app và thông báo tới phụ huynh | `Tier 1 - Critical`  | Có insight nhưng không tới được phụ huynh thì không tạo ra hành động, cũng không đo được Aha Moment. |
| Nhà cung cấp AI hoặc lớp diễn giải insight    | `Tier 2 - Important` | Có thể làm chất lượng giảm mạnh, nhưng vẫn còn đường lùi bằng template và rule-based logic.          |


---

## 3. Critical Path cho cột NOW

## Danh sách 7 task chính

1. Chốt trường pilot đầu tiên và phạm vi dữ liệu được phép dùng
2. Hoàn tất privacy notice, phạm vi đồng ý của phụ huynh và nguyên tắc xử lý dữ liệu
3. Nhận dữ liệu mẫu từ trường và map thành format có thể dùng ổn định
4. Xác định rule tạo insight và rule “không gửi” khi tín hiệu chưa đủ mạnh
5. Hoàn thiện vòng lặp phụ huynh nhận insight, mở app và phản hồi
6. Chạy kiểm thử end-to-end với dữ liệu thật hoặc dữ liệu mô phỏng sát thực tế
7. Mở pilot thật với nhóm phụ huynh đầu tiên và đo hành động trong 24 giờ

## Blocking relationships


| Task                                                                                 | Blocked by | Blocking ai |
| ------------------------------------------------------------------------------------ | ---------- | ----------- |
| 1. Chốt trường pilot đầu tiên và phạm vi dữ liệu được phép dùng                      | Không      | 2, 3        |
| 2. Hoàn tất privacy notice, phạm vi đồng ý của phụ huynh và nguyên tắc xử lý dữ liệu | 1          | 5, 7        |
| 3. Nhận dữ liệu mẫu từ trường và map thành format có thể dùng ổn định                | 1          | 4, 6        |
| 4. Xác định rule tạo insight và rule “không gửi” khi tín hiệu chưa đủ mạnh           | 3          | 5, 6        |
| 5. Hoàn thiện vòng lặp phụ huynh nhận insight, mở app và phản hồi                    | 2, 4       | 6, 7        |
| 6. Chạy kiểm thử end-to-end với dữ liệu thật hoặc dữ liệu mô phỏng sát thực tế       | 3, 4, 5    | 7           |
| 7. Mở pilot thật với nhóm phụ huynh đầu tiên và đo hành động trong 24 giờ            | 2, 5, 6    | Không       |


## Sơ đồ Critical Path đơn giản

```text
1. Chốt trường pilot và quyền dùng dữ liệu
   ->
2. Hoàn tất privacy / consent
   ->
3. Nhận và chuẩn hóa dữ liệu mẫu
   ->
4. Chốt rule insight + rule không gửi
   ->
5. Hoàn thiện vòng lặp phụ huynh nhận và phản hồi
   ->
6. Kiểm thử end-to-end
   ->
7. Mở pilot thật và đo hành động trong 24 giờ
```

## Critical Path được highlight

`1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7`

Đây là chuỗi dài nhất vì chỉ cần trễ một mắt xích là toàn bộ pilot bị đẩy lùi. Đặc biệt:

- `Task 1` và `Task 2` là điểm nghẽn về trường học và compliance
- `Task 3` và `Task 4` là điểm nghẽn về chất lượng insight
- `Task 5` là điểm nghẽn để biến insight thành hành vi thật

---

## 4. Kết luận thực thi

- Rủi ro lớn nhất của School Assistant trong 30 ngày tới không nằm ở việc “code có xong không”, mà nằm ở `dữ liệu thật`, `quyền dùng dữ liệu`, và `khả năng đưa insight tới tay phụ huynh`.
- Nếu phải bảo vệ tiến độ của NOW, team nên dồn lực trước vào:
  1. chốt trường pilot + dữ liệu
  2. chốt consent/compliance
  3. chốt vòng lặp end-to-end từ insight đến hành động

