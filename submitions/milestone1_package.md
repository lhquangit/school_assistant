# School Assistant — Milestone 1 Package

**Project:** School Assistant  
**Stage:** Pre-seed / pre-traction  
**Package date:** 2026-05-06  
**Audience:** Seed VC, internal reviewers, pilot-school stakeholders

---

## 1. Cover + Twitter Pitch

### One-line thesis

School Assistant biến dữ liệu học tập đã có trong LMS/SIS của nhà trường thành các `high-signal insight` cho phụ huynh, để gia đình hành động trong vòng `24 giờ` thay vì chỉ biết khi đã cuối kỳ.

### Twitter Pitch

> Phụ huynh thường chỉ biết con tụt lại khi đã cuối kỳ. School Assistant biến dữ liệu LMS thành high-signal insight trong app phụ huynh, để gia đình hành động trong 24 giờ thay vì chờ giáo viên báo. Gọi 2 tỷ VND pre-seed để pilot với 3 trường.

### What we are building

School Assistant không phải là một LMS mới. Đây là một `parent-facing action layer` gắn read-only vào hệ thống dữ liệu sẵn có của trường, phát hiện các thay đổi học tập đủ đáng chú ý, rồi gửi chúng đến phụ huynh qua app riêng với push notification, context ngắn gọn và phản hồi một chạm.

### Why it matters

Trong bối cảnh hiện tại, giáo viên đã cập nhật điểm và nhận xét gần như hàng tuần, nhưng phụ huynh lại không có thói quen chủ động đăng nhập LMS thường xuyên. Khoảng trống không nằm ở việc thiếu dữ liệu, mà nằm ở việc thiếu một lớp trải nghiệm đủ đơn giản, đủ đúng lúc và đủ đáng tin để biến dữ liệu đó thành hành động sớm.

### Current ask

Chúng tôi đang gọi `2 tỷ VND pre-seed` để:

- tích hợp với `3 trường` đầu tiên,
- hoàn thiện app phụ huynh bản đầu,
- chạy pilot có đo lường,
- và chứng minh rằng phụ huynh sẽ hành động lặp lại sau insight thay vì chỉ đọc thông báo.

---

## 2. Pitch Memo + Market + PRD

### Problem

Phụ huynh học sinh cấp 1-2 tại các trường đã số hóa dữ liệu vẫn thường chỉ biết con mình học sa sút khi đến kỳ tổng kết hoặc khi giáo viên phải chủ động báo riêng. Trong khi giáo viên cập nhật điểm và nhận xét gần như mỗi tuần, phụ huynh hiếm khi đăng nhập LMS thường xuyên. Hệ quả là cơ hội can thiệp sớm bị bỏ lỡ, còn giáo viên bị kéo vào vòng lặp trả lời cùng một loại câu hỏi trạng thái.

### Core insight

Thị trường này không thiếu dữ liệu học tập, cũng không thiếu LMS. Vấn đề thực sự là nhà trường chưa có một lớp trải nghiệm dành riêng cho phụ huynh, chỉ làm nổi bật những thay đổi học tập thật sự đáng hành động và đủ rõ để họ tin tưởng. Nói cách khác, phụ huynh không cần full transparency mọi lúc; họ cần `high-signal academic moments` có đủ context để hành động đúng lúc.

### Product solution

School Assistant kết nối read-only vào LMS/SIS của trường, phát hiện các thay đổi điểm số và nhận xét có tín hiệu cao, rồi chuyển chúng thành “insight học tập” ngắn gọn trong app phụ huynh. Mỗi insight có:

- push notification để kéo phụ huynh quay lại đúng lúc,
- context từ `2-3 lần` cập nhật gần nhất,
- và phản hồi một chạm như `Đã xem` hoặc `Cần hỗ trợ`.

Khác với LMS hay dashboard thụ động, sản phẩm không bắt phụ huynh tự đi tìm thông tin trong một hệ thống cồng kềnh; nó chỉ xuất hiện khi có điều gì đáng chú ý và lưu lại lịch sử insight để phụ huynh có thể phản ứng nhanh.

### Target market and access path

Người dùng cuối là `phụ huynh học sinh cấp 1-2` tại các trường đã có hệ thống quản lý học tập. Tuy nhiên, khách hàng trả tiền và cổng phân phối ban đầu là `nhà trường`. Access path của sản phẩm đi qua ban giám hiệu hoặc phòng IT của trường để tích hợp vào hệ thống hiện có, sau đó triển khai xuống phụ huynh thông qua app và kênh thông báo chính thức của trường.

### Market gap

Hiện nay phụ huynh thường dùng các workaround rất thủ công:

- hỏi trực tiếp con,
- nhắn riêng giáo viên khi nghi ngờ có vấn đề,
- chỉ kiểm tra điểm khi có thông báo,
- hoặc đợi tới họp phụ huynh và cuối kỳ.

Những hành vi này cho thấy nhu cầu đã tồn tại, nhưng trải nghiệm hiện tại chưa đủ chủ động và chưa đủ kịp thời. Đây là lý do School Assistant được định vị như một lớp `intervention layer`, không phải một cổng thông tin hay chatbot giáo dục chung chung.

### Moat hypothesis

Moat giả thuyết của School Assistant đến từ ba lớp:

1. `Workflow embedding`: sản phẩm gắn sâu vào luồng dữ liệu thật của nhà trường thay vì chỉ là một app rời.
2. `Trust layer`: sản phẩm ưu tiên độ rõ ràng và tỷ lệ false positive thấp, có fallback guardrails khi dữ liệu yếu hoặc mâu thuẫn.
3. `School-specific signal quality`: qua nhiều lần triển khai, hệ thống học được pattern chấm điểm, nhận xét và nhịp cập nhật đặc thù của từng trường, từ đó tăng chất lượng insight theo thời gian.

Đối thủ có thể sao chép tính năng push hay tóm tắt, nhưng khó tái tạo nhanh quy trình dữ liệu, sự tin cậy vận hành và hiểu biết ngữ cảnh tích lũy trong từng môi trường trường học.

### MVP boundary

#### In-scope

- Tự động tạo insight đơn giản từ dữ liệu học tập.
- App phụ huynh với push notification và feed insight gần nhất.
- Phản hồi đơn giản như `Đã xem` và `Cần hỗ trợ`.

#### Out-of-scope

- dashboard phức tạp cho nhà trường hoặc giáo viên,
- chat realtime giữa phụ huynh và giáo viên,
- predictive AI hoặc recommendation nâng cao,
- cá nhân hóa sâu cho từng học sinh,
- đa kênh Zalo/SMS/email song song.

### Data and AI approach

MVP không tối ưu bằng AI phức tạp ngay từ đầu. Logic được thiết kế theo hướng `rule-based trước, model nhẹ sau`. Dữ liệu đầu vào cốt lõi gồm:

- điểm số theo thời gian,
- nhận xét giáo viên,
- timestamp cập nhật,
- và ngữ cảnh môn học nếu có.

Khi dữ liệu không đủ mạnh, hệ thống fallback sang thông tin trung tính thay vì đưa ra kết luận mạnh. Đây là một quyết định sản phẩm quan trọng vì niềm tin của phụ huynh quan trọng hơn độ “AI-looking”.

### PMF hypotheses and success thresholds

Vì dự án đang ở giai đoạn pre-traction, các con số hiện tại là `pilot thresholds`, không phải traction thật. Các ngưỡng thành công đang được dùng để falsify hypothesis gồm:

- `30-40%` phụ huynh thực hiện một hành động trong vòng `24 giờ` sau khi nhận insight,
- `>=70%` phụ huynh đánh giá insight là hữu ích hoặc dễ hiểu,
- và một tỷ lệ đáng kể phụ huynh sẵn sàng cài app, bật thông báo và quay lại đủ nhiều lần.

Nếu các tín hiệu này không xuất hiện trong pilot, luận điểm giá trị cốt lõi của sản phẩm sẽ bị đặt lại ngay từ sớm.

---

## 3. Financial Unit Economics

### Assumption snapshot


| Metric                      | Optimistic      | Base            | Pessimistic     |
| --------------------------- | --------------- | --------------- | --------------- |
| ARPU / school / month       | `5,200,000`     | `4,600,000`     | `4,000,000`     |
| Adoption rate / month       | `0.3%`          | `0.2%`          | `0.12%`         |
| TAM / schools               | `3,000`         | `2,500`         | `2,000`         |
| Total COGS / school / month | `700,000`       | `850,000`       | `1,150,000`     |
| Monthly churn               | `2%`            | `2%`            | `4%`            |
| CAC / school                | `12,000,000`    | `15,000,000`    | `20,000,000`    |
| Fixed cost / month          | `61,000,000`    | `70,000,000`    | `87,000,000`    |
| Initial investment          | `300,000,000`   | `350,000,000`   | `450,000,000`   |
| Initial cash                | `1,700,000,000` | `1,650,000,000` | `1,500,000,000` |


### Base-case unit economics

Từ cột `Base`, các chỉ số kinh tế đơn vị suy ra như sau:

- ARPU: `4,600,000 VND / trường / tháng`
- COGS: `850,000 VND / trường / tháng`
- Gross profit: `3,750,000 VND / trường / tháng`
- Gross margin: khoảng `81.5%`
- Average lifetime: `50 tháng`
- LTV: khoảng `187,500,000 VND / trường`
- CAC: `15,000,000 VND / trường`
- LTV/CAC: khoảng `12.5x`
- CAC payback: khoảng `4 tháng`
- New schools per month ở base case: khoảng `5 trường`

### Interpretation

Đọc theo góc nhìn đầu tư sớm, mô hình hiện tại đang kể một câu chuyện khá rõ:

- gross margin cao vì đây là lớp phần mềm nhẹ gắn trên dữ liệu sẵn có,
- CAC vẫn đủ lớn để phản ánh sales motion qua trường học,
- payback dưới `12 tháng`, thậm chí khoảng `4 tháng` ở base case,
- và ngay cả pessimistic case thì LTV/CAC vẫn trên `3x`.

Điều đáng lưu ý là phần đẹp của unit economics này chưa phải bằng chứng thị trường. Nó chỉ cho thấy rằng nếu motion bán hàng, adoption và churn diễn ra gần với giả định hiện tại, mô hình tài chính có thể trở nên hấp dẫn. Vì vậy, phần cần được kiểm chứng trước không phải là “IRR có cao không”, mà là:

- có chốt được trường thật không,
- phụ huynh có cài app và giữ notification không,
- và insight có đủ mạnh để tạo ra hành động lặp lại hay không.

### How the raise is intended to work

Khoản gọi vốn `2 tỷ VND` được narrative hiện tại gắn với ba mục tiêu de-risk rõ ràng:

- tích hợp với `3 trường` đầu tiên,
- phát triển app phụ huynh bản đầu,
- và chạy pilot có đo lường để kiểm chứng activation, trust và repeat action.

Về nguyên tắc, đây là một use of funds nhất quán với product thesis: không đốt tiền vào AI phức tạp quá sớm, mà đốt tiền vào việc chốt trường, dữ liệu, insight quality và end-to-end parent loop.

---

## 4. Roadmap + OKRs

### Prioritization summary

Bảng RICE và ma trận 2x2 cho thấy ba kết luận rất rõ:

- `Quick Win`: `High-signal insight engine + fallback guardrails`
- `Strategic Bet`: `Read-only LMS/SIS integration + event sync`
- `Non-starter`: `Predictive AI + personalized recommendations`

Điều này phản ánh đúng triết lý của dự án: sản phẩm phải chứng minh được `Aha Moment` trước khi mở rộng sang các lớp AI hấp dẫn nhưng rủi ro cao.

### Now / Next / Later

#### NOW

1. Phụ huynh chưa nhận được insight học tập đủ rõ, đủ đáng tin và đủ đáng hành động để can thiệp sớm.
  Đang làm: xây lớp `high-signal insight` từ điểm số và nhận xét hiện có, kèm guardrails để tránh false alarm.
2. Nhà trường đã có dữ liệu, nhưng chưa có một vòng lặp thực tế từ dữ liệu đến insight rồi đến hành động của phụ huynh được kiểm chứng ngoài pilot.
  Đang làm: dựng `vertical slice` tối giản gồm ingest dữ liệu, insight generation, push notification và logging hành vi phụ huynh.

#### NEXT

1. Sản phẩm chưa được nhúng đủ sâu vào workflow của nhà trường, nên moat vẫn yếu.
2. Phụ huynh chưa có một trải nghiệm riêng đủ đơn giản để quay lại khi có vấn đề đáng chú ý.
3. Sau khi nhận insight, phụ huynh vẫn có thể bị kẹt ở bước “biết rồi nhưng chưa biết làm gì tiếp”.

#### LATER

1. Hệ thống mới dừng ở mức phát hiện tín hiệu, chưa trở thành lớp hỗ trợ quyết định cá nhân hóa cho từng gia đình.
2. Sản phẩm mới giúp phụ huynh hành động sớm, nhưng chưa giải quyết toàn bộ vòng phối hợp giữa phụ huynh, giáo viên và nhà trường.

### OKR for the current quarter

#### Objective

Biến School Assistant thành cách nhanh nhất để phụ huynh phát hiện sớm vấn đề học tập của con và hành động kịp thời cùng nhà trường.

#### Key Results

1. `Leading`: Ít nhất `35%` phụ huynh trong nhóm pilot thực hiện một hành động trong vòng `24 giờ` sau khi nhận insight đầu tiên.
2. `Lagging`: Đạt `3 trường` chạy thử nghiệm đang hoạt động và có ít nhất `1 trường` đồng ý tiếp tục triển khai sau giai đoạn thử nghiệm đầu tiên.
3. `Quality`: Ít nhất `70%` phụ huynh đánh giá insight là hữu ích hoặc dễ hiểu, và ít nhất `25%` tiếp tục hành động trong `3 lần` nhận insight liên tiếp.

### Why these OKRs matter

Bộ OKR này không đo output như số feature hay số dòng code. Nó đo đúng ba lớp outcome mà dự án đang cần:

- user behavior change,
- business validation từ phía trường,
- và chất lượng đủ tốt để hình thành thói quen thay vì phản ứng nhất thời.

Nếu cả ba lớp này cùng tiến triển, School Assistant có thể bước từ bài toán “prototype tốt” sang “sản phẩm có dấu hiệu PMF sớm”.

---

## 5. Dependency + Critical Path

### External dependencies that can kill the next 30 days

#### 1. Access to school data

Worst case là trường không cho truy cập dữ liệu thật, hoặc dữ liệu xuất ra thiếu điểm số, nhận xét hay thời điểm cập nhật. Khi đó pilot không thể tạo insight đáng tin.

Plan B là thu hẹp xuống `1 trường / 1 khối lớp`, dùng file xuất định kỳ thay cho kết nối trực tiếp, và chỉ yêu cầu ba trường dữ liệu bắt buộc: điểm, nhận xét, thời gian cập nhật.

#### 2. App distribution and parent notification

Worst case là app chưa tới được tay phụ huynh đúng lúc, hoặc phụ huynh cài app nhưng không bật thông báo, khiến insight không tạo ra hành động trong `24 giờ`.

Plan B là phân phối qua nhóm thử nghiệm giới hạn, dùng kênh nhắc tạm thời cho pilot và tổ chức onboarding ngắn cho nhóm phụ huynh đầu tiên.

#### 3. AI / insight rendering layer

Worst case là chất lượng diễn giải insight không ổn định hoặc dịch vụ AI bị gián đoạn, khiến thông điệp gửi tới phụ huynh bị khó hiểu hoặc sai ngữ cảnh.

Plan B là chuyển toàn bộ pilot sang `rule-based + template wording`, chỉ gửi các trường hợp tín hiệu rất rõ để giữ độ tin cậy.

### Risk ranking

- `Tier 1 - Critical`: quyền truy cập dữ liệu học tập từ nhà trường
- `Tier 1 - Critical`: kênh phân phối app và thông báo tới phụ huynh
- `Tier 2 - Important`: nhà cung cấp AI hoặc lớp diễn giải insight

Nói ngắn gọn, rủi ro lớn nhất trong 30 ngày tới không phải “code có xong không”, mà là `dữ liệu thật`, `quyền dùng dữ liệu` và `khả năng đưa insight tới tay phụ huynh`.

### Critical path

Chuỗi công việc chính của cột NOW hiện tại là:

1. Chốt trường pilot đầu tiên và phạm vi dữ liệu được phép dùng
2. Hoàn tất privacy notice, phạm vi đồng ý của phụ huynh và nguyên tắc xử lý dữ liệu
3. Nhận dữ liệu mẫu từ trường và map thành format có thể dùng ổn định
4. Xác định rule tạo insight và rule “không gửi” khi tín hiệu chưa đủ mạnh
5. Hoàn thiện vòng lặp phụ huynh nhận insight, mở app và phản hồi
6. Chạy kiểm thử end-to-end với dữ liệu thật hoặc dữ liệu mô phỏng sát thực tế
7. Mở pilot thật với nhóm phụ huynh đầu tiên và đo hành động trong `24 giờ`

Critical path đầy đủ là:

`1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7`

Điểm nghẽn quan trọng nhất nằm ở ba nơi:

- `Task 1-2`: chốt trường và compliance,
- `Task 3-4`: đảm bảo dữ liệu đủ sạch để insight có giá trị,
- `Task 5`: biến insight thành hành vi thật, không chỉ là notification đẹp.

### Execution takeaway

Nếu cần bảo vệ tiến độ milestone hiện tại, team nên dồn lực theo đúng thứ tự:

1. chốt trường pilot và quyền dùng dữ liệu,
2. chốt consent/compliance,
3. chốt vòng lặp end-to-end từ insight đến hành động.

Đó là ba mắt xích nếu trượt sẽ làm toàn bộ câu chuyện sản phẩm, PMF và tài chính mất ý nghĩa.

---

## Closing Summary

School Assistant đang theo đuổi một thesis rõ ràng: `schools already have the data, but no parent-facing layer turns that data into timely intervention`. Tài liệu hiện tại đã thống nhất ở năm điểm:

- pain thật nằm ở độ trễ hành động, không phải thiếu dữ liệu,
- sản phẩm là một action layer cho phụ huynh, không phải LMS mới,
- motion thương mại đi qua trường, nên model tài chính phải dùng đơn vị `trường`,
- roadmap ưu tiên insight quality và end-to-end loop trước AI nâng cao,
- và rủi ro thực thi lớn nhất nằm ở dữ liệu, distribution và trust.

Nếu pilot chứng minh được rằng phụ huynh thực sự hành động lặp lại sau insight, School Assistant sẽ có nền tảng đủ chắc để bước từ pre-seed story sang một case mở rộng có moat rõ hơn trong edtech infrastructure + parent engagement.