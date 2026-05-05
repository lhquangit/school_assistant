# Day 2 — PRD & Product Market Fit — Day 2 Package

## 1. Workshop 1: MVP Boundary Sheet

- **Idea (1 câu):** Giúp phụ huynh nhận được thông tin học tập của con một cách kịp thời và có thể hành động ngay, mà không cần chờ phản hồi từ giáo viên

- **Killer Feature:** Tự động tạo và gửi “insight học tập” ngắn gọn, dễ hiểu cho phụ huynh mỗi khi có thay đổi quan trọng

- **Riskiest Assumption:** Phụ huynh có thực sự thấy các insight được gửi là đủ giá trị để họ thay đổi hành vi và hành động thường xuyên hay không

**In-Scope:**
> - [ ] Tự động tạo insight đơn giản từ dữ liệu học tập  
>   → (ví dụ: phát hiện điểm giảm liên tiếp, nhận xét tiêu cực)
>
> - [ ] Gửi insight tới phụ huynh qua một kênh duy nhất (ví dụ: Zalo hoặc SMS)  
>   → đảm bảo phụ huynh thực sự nhận được
>
> - [ ] Cho phép phụ huynh phản hồi đơn giản (ví dụ: "Tôi đã xem", "Tôi cần hỗ trợ")  
>   → để đo mức độ engagement / hành động

**Out-of-Scope:**
> - Dashboard xem toàn bộ điểm số và lịch sử học tập  
>   → không cần để test insight
>
> - Chat realtime giữa phụ huynh và giáo viên  
>   → không phải core hypothesis
>
> - AI phức tạp (prediction, recommendation nâng cao)  
>   → MVP chỉ cần rule-based là đủ
>
> - Cá nhân hóa sâu cho từng học sinh  
>   → chưa cần ở giai đoạn test
>
> - Hỗ trợ nhiều kênh (app, email, SMS, web)  
>   → chỉ cần 1 kênh duy nhất

**Non-Goals:**
> - Xây dựng hệ thống quản lý học tập hoàn chỉnh thay thế trường học  
> - Tạo nền tảng giao tiếp toàn diện giữa phụ huynh và giáo viên  
> - Tối ưu trải nghiệm UI/UX phức tạp cho dashboard  
> - Đạt độ chính xác AI cao ngay từ đầu

---

## 2. Workshop 2: PRD Skeleton

- **Problem Statement:** Phụ huynh học sinh cấp 1–2 thường chỉ nắm được tình hình học tập của con vào các mốc thông báo định kỳ hoặc khi chủ động hỏi, khiến việc phát hiện vấn đề diễn ra quá muộn để can thiệp hiệu quả.

- **Target User:** Phụ huynh học sinh cấp 1–2 tại các trường đã có hệ thống quản lý học tập, nhưng không có thói quen đăng nhập thường xuyên để theo dõi tiến độ học tập của con.

**User Story 1:**
> Là một phụ huynh học sinh cấp 1–2,
> Tôi muốn nhận được các insight ngắn gọn về tình hình học tập của con ngay khi có thay đổi quan trọng,
> vì tôi có thể phát hiện sớm vấn đề và can thiệp kịp thời.

**User Story 2:**
> Là một phụ huynh học sinh cấp 1–2,
> Tôi muốn có thể phản hồi nhanh sau khi nhận insight (ví dụ: đã xem hoặc cần hỗ trợ),
> vì tôi có thể xác nhận thông tin và quyết định bước tiếp theo mà không cần liên hệ thủ công.

**Success Metrics:**
> - Tỷ lệ phụ huynh thực hiện hành động sau khi nhận insight trong vòng 24 giờ
> Ngưỡng thành công: 30–40%
> - % insight được mở / đọc
> Target: ≥ 70%
> - % phụ huynh tiếp tục tương tác với insight trong tuần tiếp theo
> - % insight được đánh giá là hữu ích (nếu có feedback)

**Dependencies & Constraints:**
> - Hệ thống quản lý học tập của nhà trường  
>   → để lấy dữ liệu điểm số và nhận xét của học sinh
>
> - Kênh gửi thông tin tới phụ huynh (ví dụ: Zalo API, SMS, Mobile App)  
>   → để deliver insight trực tiếp
>
> - Nguồn dữ liệu học tập cơ bản  
>   → điểm số, nhận xét của giáo viên (có sẵn trong hệ thống)
>
> - Sự hợp tác từ phía nhà trường / giáo viên  
>   → để đảm bảo dữ liệu được cập nhật đúng và đủ

---

## 3. Workshop 2: AI-specific PRD

- **Model Selection:** PT-4o-mini (hoặc tương đương lightweight LLM)

**Why this model?:**
> Mục tiêu của MVP là kiểm chứng giả định về giá trị của insight đối với phụ huynh, không phải tối ưu chất lượng AI. 
> Do đó, sử dụng logic đơn giản (rule-based) hoặc model lightweight là đủ để tạo ra các insight cơ bản.
> Việc sử dụng model phức tạp ngay từ đầu sẽ làm tăng chi phí và độ phức tạp kỹ thuật, trong khi không giúp giảm rủi ro lớn nhất của sản phẩm — là việc phụ huynh có thực sự quan tâm và hành động dựa trên insight hay không.

**Accepted trade-offs:**
> - Insight có thể chưa hoàn toàn chính xác hoặc cá nhân hóa sâu
>  - Nội dung insight còn đơn giản

**Unacceptable trade-offs:**
> - Insight sai nghiêm trọng hoặc gây hiểu nhầm cho phụ huynh
> - Thời gian phản hồi chậm hoặc không ổn định

**Data Requirements:**
> **Dữ liệu cần thiết:**
> - Điểm số theo từng môn học (theo thời gian)
> - Nhận xét của giáo viên (text)
> - Thời điểm cập nhật (timestamp)
>
> **Dữ liệu bổ trợ (nếu có):**
> - Lịch kiểm tra / tần suất đánh giá
> - Thông tin môn học / giáo viên
>
> ---
>
> **Thiếu dữ liệu nào sẽ làm AI tệ đi:**
>
> - Thiếu dữ liệu theo thời gian  
>   → Không phát hiện được xu hướng (tăng/giảm)
>
> - Thiếu nhận xét của giáo viên  
>   → Insight thiếu context, chỉ là số liệu khô
>
> - Dữ liệu không nhất quán giữa các giáo viên  
>   → Insight dễ sai hoặc gây hiểu nhầm
>
> - Dữ liệu cập nhật chậm hoặc thiếu  
>   → Insight không còn “kịp thời”, mất giá trị chính của sản phẩm

**Data source:**
> - **Database nội bộ của nhà trường (primary source)**  
>   → Hệ thống quản lý học tập (LMS/SIS) chứa:
>   - Điểm số
>   - Nhận xét giáo viên
>   - Timestamp cập nhật
>
> - **API tích hợp với hệ thống trường (nếu có)**  
>   → Lấy dữ liệu theo event (khi có điểm / nhận xét mới)
>
> ---
>
> **Không sử dụng trong MVP:**
> - File upload từ giáo viên  
> - Crawl dữ liệu từ bên ngoài  
> - API bên thứ ba  
>
> → Để tránh tăng độ phức tạp và rủi ro dữ liệu

**Data owner:**
> - **Nhà trường** là đơn vị sở hữu dữ liệu học tập (điểm số, nhận xét)
> - **Giáo viên** là người tạo và chịu trách nhiệm về dữ liệu đầu vào
> - **Hệ thống MVP** chỉ có quyền truy cập dữ liệu (read-only), không chỉnh sửa

**Update frequency:**
> Dữ liệu được cập nhật theo sự kiện (event-based), mỗi khi có:
> - Điểm số mới được nhập
> - Nhận xét mới từ giáo viên
>
> Hệ thống sẽ xử lý và gửi insight trong vòng vài phút sau khi có dữ liệu mới (near real-time).

**Data quality risk:**
> - **Dữ liệu không đầy đủ**
>   → Giáo viên chưa nhập điểm hoặc nhận xét kịp thời  
>   → Insight có thể sai hoặc không được tạo
>
> - **Dữ liệu không nhất quán**
>   → Mỗi giáo viên có cách chấm điểm và viết nhận xét khác nhau  
>   → Khó chuẩn hóa và dễ hiểu sai context
>
> - **Dữ liệu thiếu ngữ cảnh**
>   → Điểm số đơn lẻ không phản ánh toàn bộ quá trình học  
>   → Insight có thể quá đơn giản hoặc gây hiểu nhầm
>
> - **Dữ liệu sai hoặc nhập nhầm**
>   → Lỗi nhập liệu dẫn đến insight sai  
>   → Làm giảm độ tin cậy của hệ thống
>
> - **Dữ liệu cập nhật chậm**
>   → Insight không còn “kịp thời”  
>   → Mất giá trị cốt lõi của sản phẩm

**Fallback UX:**
> **Chiến lược:**
> Human-in-the-loop + Expectation Management
>
> ---
>
> ### 1. Khi nào fallback xảy ra? (Trigger)
>
> - Khi chỉ có 1 điểm dữ liệu (không đủ để xác định xu hướng)
> - Khi không có nhận xét từ giáo viên
> - Khi dữ liệu mâu thuẫn (ví dụ: điểm tăng nhưng nhận xét tiêu cực)
> - Khi hệ thống không phát hiện được pattern rõ ràng
>
> ---
>
> ### 2. User sẽ thấy gì?
>
> **Trường hợp thiếu dữ liệu:**
> > "Hiện chưa có đủ dữ liệu để đánh giá xu hướng học tập của học sinh."
>
> **Trường hợp độ tin cậy thấp:**
> > "Có một số thay đổi trong kết quả học tập, tuy nhiên thông tin này mang tính tham khảo. Nên kiểm tra thêm với giáo viên để có đánh giá chính xác."
>
> ---
>
> ### 3. User làm tiếp được gì?
>
> - Nhấn "Đã xem" để xác nhận
> - Nhấn "Cần hỗ trợ thêm" (trigger hành động tiếp theo)
> - Chủ động liên hệ giáo viên nếu cần
>
> ---
>
> ### 4. Hệ thống có chuyển sang người thật không?
>
> - Không tự động chuyển sang giáo viên trong MVP (tránh tăng độ phức tạp)
> - Nếu user chọn "Cần hỗ trợ thêm":
>   → Hệ thống gợi ý: "Bạn có thể liên hệ giáo viên chủ nhiệm để trao đổi thêm"
> - (Optional future): có thể tích hợp chuyển tiếp sang giáo viên ở giai đoạn sau
>
> ---
>
> ### 5. Nguyên tắc thiết kế
>
> - Không tạo insight mạnh khi dữ liệu không đủ
> - Ưu tiên thông tin trung tính thay vì suy đoán
> - Luôn giữ quyền quyết định cuối cùng cho phụ huynh

**Fallback strategy:**
> Sử dụng chiến lược kết hợp giữa **Expectation Management** và **Human-in-the-loop (ở mức tối thiểu)**.
>
> Khi hệ thống không có đủ dữ liệu hoặc độ tin cậy thấp, thay vì cố gắng tạo insight có thể gây hiểu nhầm, hệ thống sẽ:
> - Không đưa ra kết luận mạnh
> - Hiển thị thông tin trung tính hoặc thông báo thiếu dữ liệu
> - Cho phép phụ huynh tự quyết định hành động tiếp theo (ví dụ: liên hệ giáo viên)
>
> Hệ thống không tự động thay thế con người, mà đóng vai trò hỗ trợ cung cấp thông tin khi có đủ độ tin cậy.

**Fallback trigger:**
> Fallback được kích hoạt khi hệ thống không đủ điều kiện để tạo insight đáng tin cậy.
>
> ---
>
> **1. Thiếu dữ liệu tối thiểu**
> - Chỉ có 1 điểm số gần nhất (không đủ để xác định xu hướng)
> - Không có nhận xét từ giáo viên
>
> → Không thể tạo insight có ý nghĩa
>
> ---
>
> **2. Không phát hiện được pattern rõ ràng**
> - Điểm số không có xu hướng tăng/giảm rõ
> - Không có thay đổi đáng kể so với trước
>
> → Không có insight đáng để gửi
>
> ---
>
> **3. Dữ liệu mâu thuẫn**
> - Điểm số tăng nhưng nhận xét tiêu cực (hoặc ngược lại)
>
> → Insight có nguy cơ gây hiểu nhầm
>
> ---
>
> **4. Dữ liệu quá cũ**
> - Không có cập nhật trong một khoảng thời gian dài (ví dụ: > 2–3 tuần)
>
> → Insight không còn kịp thời
>
> ---
>
> **5. Logic insight không đạt ngưỡng tin cậy**
> - Rule-based condition không đủ mạnh (ví dụ: chỉ 1 lần giảm điểm)
>
> → Không nên đưa ra kết luận

**Fallback action:**
> Khi fallback trigger xảy ra, hệ thống sẽ không tạo insight mạnh mà thực hiện các hành động sau:
>
> ---
>
> **1. Không tạo insight (Suppress strong output)**
> - Không gửi cảnh báo hoặc kết luận về tình hình học tập
> - Tránh đưa ra thông tin có thể gây hiểu nhầm
>
> ---
>
> **2. Hiển thị thông tin trung tính**
> - Thay bằng thông báo như:
>   → "Hiện chưa có đủ dữ liệu để đánh giá xu hướng học tập của học sinh."
>   hoặc
>   → "Chưa ghi nhận thay đổi đáng kể trong kết quả học tập gần đây."
>
> ---
>
> **3. Gắn disclaimer khi độ tin cậy thấp**
> - Với trường hợp borderline:
>   → "Thông tin mang tính tham khảo, nên kiểm tra thêm với giáo viên."
>
> ---
>
> **4. Cho phép user hành động tiếp**
> - Nút:
>   - "Đã xem"
>   - "Cần hỗ trợ thêm"
>
> ---
>
> **5. Ghi nhận hành vi người dùng**
> - Log lại:
>   - user đã xem insight
>   - user yêu cầu hỗ trợ thêm
>
> → phục vụ phân tích và cải thiện logic insight
>
> ---
>
> **6. Không escalate tự động (MVP constraint)**
> - Không tự động liên hệ giáo viên
> - Không mở chat hoặc ticket

**User override:**
> Người dùng (phụ huynh) có quyền bỏ qua hoặc không tin tưởng insight do hệ thống cung cấp, và tự quyết định hành động tiếp theo.
>
> ---
>
> **1. Các hình thức override trong MVP:**
>
> - **Bỏ qua insight**
>   → User có thể không hành động dù hệ thống đưa ra cảnh báo
>
> - **Yêu cầu hỗ trợ thêm**
>   → Nhấn "Cần hỗ trợ thêm" để chuyển sang hành động ngoài hệ thống (liên hệ giáo viên)
>
> - **Không bị ép hành động**
>   → Hệ thống không tự động thực hiện bất kỳ hành động nào thay cho user
>
> ---
>
> **2. Hệ thống xử lý như thế nào:**
>
> - Ghi nhận khi user:
>   - bỏ qua insight
>   - yêu cầu hỗ trợ thêm
>
> - Không:
>   - ép user xác nhận insight
>   - ép user làm theo khuyến nghị
>
> ---
>
> **3. Nguyên tắc thiết kế:**
>
> - User luôn là người ra quyết định cuối cùng
> - Insight chỉ mang tính hỗ trợ, không mang tính bắt buộc
> - Tránh tạo cảm giác “AI biết đúng tuyệt đối”

**Override UX:**
> **1. Khi hiển thị insight**
>
> Ví dụ:
> > "Điểm Toán của học sinh giảm trong 2 lần kiểm tra gần nhất — có dấu hiệu sa sút."
>
> ---
>
> **2. Các lựa chọn mà user thấy (override options)**
>
> - [Đã xem]  
> - [Cần hỗ trợ thêm]  
> - (Implicit) Không làm gì / bỏ qua insight  
>
> ---
>
> **3. Khi user override (các hành vi cụ thể)**
>
> **a. User bỏ qua (không tương tác):**
> - Hệ thống không ép hành động
> - Insight sẽ không được gửi lại ngay lập tức
>
> ---
>
> **b. User nhấn "Đã xem":**
> - Hệ thống ghi nhận: user đã nhận thông tin
> - Không thực hiện thêm hành động nào
>
> ---
>
> **c. User nhấn "Cần hỗ trợ thêm":**
> - Hệ thống ghi nhận nhu cầu hỗ trợ
> - Hiển thị hướng dẫn:
>   > "Bạn có thể liên hệ giáo viên chủ nhiệm để trao đổi thêm"
> - Không tự động gửi tin nhắn hoặc mở chat (MVP constraint)
>
> ---
>
> **4. Nguyên tắc UX**
>
> - Không ép user xác nhận hoặc hành động
> - Không auto-trigger hành động thay user
> - Luôn cho phép user bỏ qua insight
> - Insight mang tính gợi ý, không mang tính quyết định

---

## 4. Workshop 3: Hypothesis Table

**Hypothesis 1:**
> Nếu phụ huynh nhận được các insight học tập ngắn gọn và kịp thời về con của họ,
> thì họ sẽ thực hiện hành động (phản hồi hoặc can thiệp) trong vòng 24 giờ.
>
> ---
>
> **Metric đo lường:**
> - % phụ huynh thực hiện hành động sau khi nhận insight
>
> ---
>
> **Ngưỡng thành công:**
> - ≥ 30–40% phụ huynh hành động trong 24 giờ
>
> ---
>
> **Cách test:**
> - Gửi insight (có thể giả lập) cho một nhóm phụ huynh
> - Theo dõi:
>   - họ có đọc không
>   - họ có phản hồi hoặc hành động không

- **Riskiest Assumption behind #1:** Phụ huynh sẽ thấy các insight học tập được gửi là đủ giá trị và đáng tin để họ thay đổi hành vi và hành động, thay vì tiếp tục dựa vào các cách hiện tại như hỏi con hoặc giáo viên.

**Cheapest test for #1:**
> **Phương pháp:**
> Wizard-of-Oz (giả lập hệ thống)
>
> ---
>
> **Cách thực hiện:**
> - Thu thập dữ liệu học tập đơn giản (điểm số, nhận xét) từ 5–10 học sinh
> - Tự viết các insight ngắn gọn (bằng tay, không cần AI)
> - Gửi insight cho phụ huynh qua Zalo / SMS / Mobile App như một tin nhắn bình thường
>
> ---
>
> **Đo lường:**
> - Phụ huynh có đọc không
> - Phụ huynh có phản hồi / hành động không
> - Phụ huynh có hỏi thêm hoặc liên hệ giáo viên không
>
> ---
>
> **Chi phí:**
> - Gần như bằng 0 (không cần build hệ thống)
> - Chỉ tốn thời gian viết insight và gửi tin nhắn
>
> ---
>
> **Thời gian:**
> - 1–2 ngày để chuẩn bị
> - 2–3 ngày để quan sát phản ứng

**Hypothesis 2:**
> Nếu insight học tập được trình bày rõ ràng, có context và giải thích lý do,
> thì phụ huynh sẽ hiểu và tin tưởng insight đó, thay vì nghi ngờ hoặc bỏ qua.
>
> ---
>
> **Metric đo lường:**
> - % phụ huynh đánh giá insight là hữu ích / dễ hiểu
>
> ---
>
> **Ngưỡng thành công:**
> - ≥ 70% phụ huynh đánh giá insight là hữu ích

- **Riskiest Assumption behind #2:** Insight được tạo ra từ dữ liệu học tập có thể được diễn giải một cách đủ rõ ràng và dễ hiểu để phụ huynh tin tưởng và sử dụng, dù họ không có chuyên môn sư phạm.

**Cheapest test for #2:**
> **Phương pháp:**
> A/B test nội dung insight (viết tay)
>
> ---
>
> **Cách thực hiện:**
> - Tạo 2 phiên bản insight cho cùng một dữ liệu:
>
> Version A (raw):
> → "Điểm Toán: 6"
>
> Version B (insight):
> → "Điểm Toán của con bạn giảm trong 2 lần gần nhất, có dấu hiệu sa sút — nên xem lại phần đại số"
>
> - Gửi cho phụ huynh (hoặc hỏi trực tiếp)
>
> ---
>
> **Đo lường:**
> - Họ hiểu version nào hơn?
> - Họ tin version nào hơn?
> - Họ muốn hành động với version nào?
>
> ---
>
> **Chi phí:**
> - Gần như 0 (chỉ viết nội dung)
>
> ---
>
> **Thời gian:**
> - 1–2 ngày test

---

## 5. Workshop 3: PMF Scorecard

- **Aha Moment:** Phụ huynh nhận được một insight về vấn đề học tập của con và ngay lập tức thực hiện một hành động cụ thể (phản hồi, hỏi thêm, hoặc can thiệp).

**Actionable Metric:**
> Tỷ lệ phụ huynh thực hiện hành động (phản hồi, yêu cầu hỗ trợ, hoặc can thiệp) trong vòng 24 giờ sau khi nhận insight
>
> Target:
> ≥ 30–40%

**PMF Method:**
> Retention-based PMF (dựa trên hành vi lặp lại)
>
> Đo lường việc phụ huynh có tiếp tục tương tác và hành động dựa trên các insight được gửi trong nhiều lần liên tiếp hay không.

**PMF success threshold:**
> - ≥ 30% phụ huynh thực hiện hành động trong lần nhận insight đầu tiên  
> - ≥ 25% phụ huynh tiếp tục hành động trong ≥ 3 lần nhận insight liên tiếp  
>
> → Cho thấy hành vi không chỉ xảy ra một lần, mà đang trở thành thói quen

- **First PMF measurement:** Thực hiện sau khi phụ huynh đã nhận và tương tác với ít nhất 3–5 insight liên tiếp trong vòng 1–2 tuần.

**Vanity Metrics to avoid:**
> - Số lượng phụ huynh đăng ký tài khoản  
> → Không phản ánh việc họ có sử dụng hoặc thấy giá trị hay không
>
> - Số lượng insight được gửi đi  
> → Là output của hệ thống, không phải hành vi người dùng
>
> - Tỷ lệ mở tin nhắn (open rate)  
> → Người dùng có thể đọc nhưng không hành động
>
> - Số lượt xem / click  
> → Không chứng minh được user có thay đổi hành vi
>
> - Số lượng user hoạt động trong ngày (DAU)  
> → Có thể truy cập nhưng không tạo ra giá trị thực
>
> - Thời gian sử dụng ứng dụng  
> → Không liên quan trực tiếp đến việc phụ huynh có hành động hay không

- **North Star Metric:** Số lượng phụ huynh thực hiện hành động (phản hồi, trao đổi với con, hoặc liên hệ giáo viên) dựa trên insight mỗi tuần

---

## 6. Final Reflection: AI Critique Log

**Issue 1 + action:**
> ### Issue 1
> Các insight được tạo ra có thể chưa đủ rõ ràng hoặc chưa đủ giá trị để khiến phụ huynh thực sự hành động, dẫn đến tỷ lệ engagement và retention thấp.
>
> **Action:**
>
> - Thực hiện test Wizard-of-Oz để thử nghiệm nhiều cách viết insight khác nhau
> - A/B test các phiên bản insight (raw data vs contextual insight)
> - Thu thập feedback trực tiếp từ phụ huynh về mức độ hiểu và hữu ích
> - Iteration nhanh dựa trên phản hồi để cải thiện cách diễn giải insight

**Issue 2 + action:**
> ### Issue 2
>
> Phụ huynh có thể không thay đổi hành vi, tiếp tục sử dụng các cách quen thuộc như hỏi trực tiếp con hoặc giáo viên, thay vì tin và hành động dựa trên insight từ hệ thống.
>
> **Action:**
>
> - Thiết kế insight tập trung vào các trường hợp có dấu hiệu rõ ràng (high-signal cases)
> - Tăng độ tin cậy bằng cách hiển thị context (ví dụ: so sánh 2–3 lần gần nhất)
> - Bổ sung cơ chế "Cần hỗ trợ thêm" để bridge sang hành động thực tế
> - Theo dõi hành vi lặp lại để đánh giá mức độ hình thành thói quen

- **Biggest change between A and B:** Chuyển từ việc tập trung vào cải thiện giao tiếp giữa phụ huynh và giáo viên (communication-driven) sang việc cung cấp insight chủ động giúp phụ huynh hành động kịp thời (insight-driven).

- **Weakest link now:** Chất lượng và mức độ “đáng hành động” của insight — liệu các insight được tạo ra có đủ rõ ràng, đáng tin và đủ quan trọng để khiến phụ huynh thực sự hành động hay không.