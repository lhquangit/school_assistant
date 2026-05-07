# Workshop 3 — Incident Playbook

## Tình huống giả định

`9h30 sáng thứ Hai.` Một phụ huynh trong trường pilot chụp màn hình insight của School Assistant nói rằng con họ đang `sa sút rõ rệt ở môn Toán`, trong khi dữ liệu thật chỉ mới có `1 điểm kiểm tra mới` và chưa có nhận xét giáo viên. Phụ huynh gửi ảnh vào group lớp, rồi chuyển tiếp cho giáo viên chủ nhiệm và ban giám hiệu. Trong `30 phút`, trường gọi lại nói rằng `3 phụ huynh khác đang hỏi liệu app có đang kết luận sai về học sinh không`.

Đây là tình huống phù hợp nhất với School Assistant vì nó đánh trúng `KILL ZONE risk` của workshop 2: `wrong parent insight`.

---

## 1. VERIFY (0-5 phút)

### Check ở đâu

1. Mở `Langfuse` project của luồng parent insight
  URL giả định nội bộ: `https://cloud.langfuse.com/project/school-assistant/traces`
2. Filter theo:
  - `student_id`
  - `parent_id`
  - `trace time` trong `30 phút` trước lúc screenshot
3. Mở trace đúng request để xem:
  - raw input data
  - fallback flag
  - prompt/template version
  - output text cuối cùng đã gửi

### Cách verify đó là incident thật hay ảnh giả

- So khớp `timestamp` trong screenshot với trace time trong Langfuse
- So khớp nguyên văn insight trong ảnh với `final output` đã log
- So khớp `student_id` và `school_id` với case phụ huynh đang khiếu nại
- Kiểm tra input có thật chỉ có `1 điểm mới` và thiếu teacher comment hay không

### Kết luận cần có sau 5 phút

Founder phải trả lời được một câu rất cụ thể:

> `Đây có đúng là output của AI School Assistant đã gửi cho phụ huynh thật không, hay chỉ là ảnh bị chỉnh / hiểu sai ngữ cảnh?`

Nếu không xác minh được trong `5 phút`, mặc định treat như incident thật.

---

## 2. STOP THE BLEEDING (5-15 phút)

### Option được chọn: Soft kill

**Quyết định:** Chuyển toàn bộ luồng insight của trường pilot sang `rule-based fallback` ngay lập tức.

### Vì sao chọn soft kill thay vì hard kill

- `Hard kill` làm app im hoàn toàn và có thể khiến trường nghĩ sản phẩm mất kiểm soát.
- `Soft kill` vẫn giữ app hoạt động, nhưng tắt phần kết luận mạnh từ AI và chỉ cho phép:
  - insight dạng template an toàn,
  - hoặc thông báo trung tính kiểu `hiện chưa đủ dữ liệu để đánh giá xu hướng`.
- Điều này đúng với nguyên tắc Day 21: `soft kill > hard kill` khi còn giữ được service ở trạng thái degraded nhưng an toàn hơn.

### Action cụ thể trong 10 phút đầu

1. Founder nhắn vào Slack nội bộ: `incident verified, switching school pilot to fallback mode now`
2. Product/tech owner đổi config:
  - `INSIGHT_MODE=rule_based_fallback`
  - tắt mọi prompt path cho trường pilot bị ảnh hưởng
3. Tạm khóa gửi mới các insight có:
  - chỉ `1 điểm dữ liệu`,
  - không có teacher comment,
  - hoặc confidence dưới ngưỡng fallback
4. Gắn nhãn incident trong Langfuse để review toàn bộ các case cùng pattern trong ngày

### Mục tiêu sau 15 phút

- Không có thêm insight kiểu này tiếp tục được gửi ra ngoài
- Trường vẫn thấy app còn sống, nhưng đang chạy ở chế độ an toàn hơn
- Founder có thể nói với phụ huynh và nhà trường rằng: `đã chặn luồng gây lỗi`

---

## 3. CUSTOMER COMM (15-25 phút)

### DM / email cho phụ huynh bị ảnh hưởng

**Subject:** Từ founder School Assistant về insight vừa rồi

```text
Chào anh/chị [Tên phụ huynh],

Em là [Tên founder] của School Assistant. Em vừa xem trực tiếp case insight về môn Toán của con anh/chị.

Việc đã xảy ra: app của bên em đã gửi một insight kết luận quá mạnh khi dữ liệu chưa đủ chắc. Điều đó là sai.

Em đang làm gì: em đã tắt ngay luồng AI này cho trường pilot và chuyển hệ thống sang chế độ an toàn hơn để không gửi thêm insight kiểu này.

Em sửa như thế nào: bên em sẽ rà lại toàn bộ các insight cùng pattern trong hôm nay, gỡ các kết luận không an toàn, và làm việc trực tiếp với nhà trường để xác nhận lại ngữ cảnh đúng.

Em gọi anh/chị trong 24h: [SĐT founder / Calendly]

-- [Tên founder]
[email founder]
```

### Vì sao message này pass

- Dùng `I / em`, không dùng giọng corporate
- Nói thẳng `đó là sai`
- Nêu action cụ thể: `đã tắt luồng AI này`
- Không đổ lỗi cho model, dữ liệu hay vendor
- Có direct contact từ founder trong `24h`

### Compensation / make-it-right

Vì School Assistant đang ở giai đoạn pilot với trường chứ chưa phải B2C paid app, compensation phù hợp nhất ở đây không phải hoàn tiền lẻ cho phụ huynh, mà là:

- founder gọi trực tiếp để xin lỗi,
- review toàn bộ insight liên quan trong ngày,
- gửi lại bản giải thích đúng sau khi xác minh với trường,
- và cam kết chuyển trường pilot sang `safer fallback mode` ngay lập tức.

---

## 4. TEAM COMM (song song trong 15-25 phút)

### Slack update nội bộ

```text
Có incident thật ở trường pilot: một insight về học sinh đã kết luận quá mạnh khi dữ liệu chưa đủ.
Mình đã verify qua Langfuse và đã chuyển pilot sang fallback mode.
Trong 2 giờ tới, không merge gì vào luồng parent-facing.
Mình sẽ update lại lúc 11h30 sau khi nói chuyện xong với phụ huynh và trường.
```

### Mục tiêu của team comm

- chặn team tự ý patch linh tinh khi chưa có chỉ đạo
- giữ mọi người cùng một narrative
- khóa bớt thay đổi ngoài incident scope

---

## 5. PUBLIC RESPONSE (25-30 phút)

Tình huống này của School Assistant nhiều khả năng không bắt đầu trên Twitter, mà bùng trước trong `group lớp` hoặc escalates nội bộ qua trường. Tuy vậy, nếu screenshot bắt đầu lan rộng công khai, founder cần một public response ngắn theo đúng format workshop.

### Founder post ngắn

```text
Hi everyone — I'm [Founder] from School Assistant. I just reviewed the parent insight issue from this morning. We've disabled that AI path for the pilot school and switched to a safer fallback while we investigate. I'm reaching out to the affected parent and school directly now.
```

### Kiểm tra nhanh

- Founder voice: có
- Có action cụ thể: `disabled that AI path`
- Không corporate PR statement: có
- Hứa bước tiếp theo rõ: có
- Dưới 280 ký tự: xấp xỉ `267` ký tự

---

## 6. 24-hour follow-up

Trong `24 giờ` đầu, founder phải làm thêm 4 việc:

1. Review toàn bộ trace có pattern tương tự trong pilot
2. Xác định root cause:
  - prompt wording quá mạnh,
  - threshold quá thấp,
  - hay fallback chưa trigger đúng
3. Gọi lại cho phụ huynh bị ảnh hưởng và đại diện trường
4. Viết internal note:
  - điều gì sai
  - đã chặn thế nào
  - rule/rail nào phải update sau incident

---

## 7. Quyết định cuối cùng của playbook

### Verify

- `Langfuse trace` theo `student_id`, `parent_id`, `timestamp`
- So khớp raw input và output để xác nhận đó là output thật

### Stop the bleeding

- Chọn `soft kill`
- Chuyển toàn bộ pilot sang `rule-based fallback`

### Customer comm

- Founder gửi message cá nhân, nói rõ `đó là sai`
- Founder để lại contact trực tiếp trong `24h`

### Public response

- Founder post ngắn, personal, không corporate

---



