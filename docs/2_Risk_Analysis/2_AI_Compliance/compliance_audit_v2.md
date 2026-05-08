# AI Compliance Audit v2 — School Assistant

**Date:** 08/05/2026
**Phạm vi tài liệu đã rà soát:**  
- `docs/1_Project_Analysis/2_PRD & Product Market Fit.md`  
- `docs/1_Project_Analysis/4_Investor Buy-in & Pitch/twitter_pitch.md`  
- `docs/1_Project_Analysis/4_Investor Buy-in & Pitch/pitch_memo.md`  
- `docs/2_Risk_Analysis/1_AI_Governance_And_Risk/1_rules_rails_ritual.md`  
- `docs/2_Risk_Analysis/1_AI_Governance_And_Risk/2_risk_register_v2.md`  
- `docs/2_Risk_Analysis/1_AI_Governance_And_Risk/3_incident_playbook.md`  
- `docs/2_Risk_Analysis/2_AI_Compliance/1_marketing_claims_audit.md`  
- `docs/2_Risk_Analysis/2_AI_Compliance/2_territorial_scope.md`  
- `docs/2_Risk_Analysis/2_AI_Compliance/3_document_trail.md`

## Lưu ý pháp lý

- File này dùng khung Day 22 trong repo làm baseline cho `Điều 9 Luật AI VN`, `Điều 30 PDPL`, `Điều 198 BLHS`, `Điều 324 BLHS`.
- Mình đã đối chiếu thêm hiệu lực của `Luật Bảo vệ dữ liệu cá nhân 91/2025/QH15`, `Luật Trí tuệ nhân tạo 2025`, và `EU AI Act` từ nguồn công khai chính thức; tuy nhiên trước khi dùng file này làm tài liệu pháp lý chính thức với trường hoặc cơ quan, founder vẫn nên để luật sư rà lại mapping điều khoản chi tiết.

## Tóm tắt nhanh

School Assistant hiện có `9` điểm rủi ro tuân thủ nổi bật. Trong đó, `5` điểm nghiêm trọng nhất không nằm ở “AI có thông minh không”, mà nằm ở việc:

1. dữ liệu trẻ em có thể đi qua vendor/cloud nước ngoài khi chưa có `DPIA / CTIA` chính thức,
2. sản phẩm đã tự nhận là `high-risk education AI` nhưng chưa có compliance pack trước pilot,
3. các claim public vẫn nói như thể outcome `24 giờ`, `30-40% hành động` đã được chứng minh,
4. human oversight và consent/deletion workflow mới dừng ở ý tưởng hoặc risk note,
5. founder đã thấy dấu hiệu vendor/policy risk nhưng chưa có hồ sơ go/no-go để chứng minh mình đã thẩm định.

## Bảng tóm tắt vi phạm

| # | Tên vi phạm | Nhóm | Luật chính | Pattern VN | Mức độ |
|---|-------------|------|------------|------------|--------|
| 1 | Claim `24 giờ` như kết quả đã chứng minh | Marketing | BLHS Điều 198 | Kera | Cao |
| 2 | Claim `30-40% phụ huynh sẽ hành động` như fact | Marketing | BLHS Điều 198 | Kera | Cao |
| 3 | Claim `high-signal / tín hiệu cao` khi chưa có benchmark | Marketing | BLHS Điều 198 | Kera | Trung bình-Cao |
| 4 | Chuyển dữ liệu trẻ em ra vendor/cloud nước ngoài khi chưa có `DPIA / CTIA` | Dữ liệu cá nhân | PDPL Điều 30 | CIC | Rất cao |
| 5 | Chưa có pack `consent / withdrawal / deletion / retention` trước pilot live | Dữ liệu cá nhân | PDPL Điều 30, Điều 8 | CIC | Rất cao |
| 6 | Đã tự phân loại `Cao` nhưng chưa có bộ hồ sơ high-risk trước deploy | Phân loại rủi ro AI | Luật AI VN Điều 9 | CIC | Rất cao |
| 7 | `Human-in-the-loop` được nêu trong PRD nhưng chưa thành control vận hành thật cho case tiêu cực | Giám sát con người | Luật AI VN Điều 9 + PDPL Điều 30 | CIC | Cao |
| 8 | Founder đã thấy vendor/policy risk nhưng chưa có hồ sơ rà soát vendor và log quyết định tiếp tục/dừng | Vendor / enabler risk | BLHS Điều 324 (rủi ro analog), Luật AI VN | Pips | Cao |
| 9 | Chưa có workflow `marketing approval` có founder sign-off trước asset public | Governance | BLHS Điều 198 | Kera | Cao |

## Chi tiết từng vi phạm

### VI PHẠM 1: Claim `24 giờ` như kết quả đã chứng minh

- **Luật áp dụng:** `BLHS`
- **Điều:** `Điều 198 khoản 1-2` theo logic Day 22 về cung cấp dịch vụ bằng thông tin sai hoặc thổi phồng so với evidence
- **Bằng chứng trong sản phẩm:**
  > "School Assistant biến dữ liệu LMS thành high-signal insight trong app phụ huynh, để gia đình hành động trong 24 giờ thay vì chờ giáo viên báo."
  
  > "Success bar đã được định nghĩa rõ: ít nhất 30-40% phụ huynh thực hiện một hành động trong vòng 24 giờ sau khi nhận insight..."
- **Pattern khớp với:** `Kera`
- **Vì sao là vi phạm:** câu public đầu tiên đang biến `success threshold của pilot` thành `outcome đã đạt`, trong khi repo còn ghi rõ startup đang `pre-traction`.
- **Hành động sửa:** đổi toàn bộ wording public từ `kết quả đã xảy ra` sang `mục tiêu pilot / giả thuyết đang đo`.
- **Deadline:** `12/05/2026`, trước mọi pitch / post / asset public tiếp theo

### VI PHẠM 2: Claim `30-40% phụ huynh sẽ hành động` như fact

- **Luật áp dụng:** `BLHS`
- **Điều:** `Điều 198 khoản 1-2`
- **Bằng chứng trong sản phẩm:**
  > "Hiện chúng tôi đang gọi 2 tỷ VND pre-seed để pilot với 3 trường và chứng minh rằng 30 đến 40 phần trăm phụ huynh sẽ hành động sau mỗi insight."
  
  > "Ngưỡng thành công: 30–40%"
- **Pattern khớp với:** `Kera`
- **Vì sao là vi phạm:** con số `30-40%` là ngưỡng nội bộ trong PRD nhưng đang bị nói như một kết quả dự kiến có xác suất rất cao hoặc gần như fact.
- **Hành động sửa:** mọi nơi phải chuyển thành `pilot sẽ kiểm tra liệu có đạt 30-40% hay không`.
- **Deadline:** `12/05/2026`

### VI PHẠM 3: Claim `high-signal / tín hiệu cao` khi chưa có benchmark

- **Luật áp dụng:** `BLHS`
- **Điều:** `Điều 198 khoản 1-2`
- **Bằng chứng trong sản phẩm:**
  > "School Assistant đọc dữ liệu mới, tạo high-signal insight..."
  
  > "phát hiện các thay đổi điểm số và nhận xét có tín hiệu cao"
  
  > "Nếu: the pilot school withholds teacher comments, timestamps, or regular exports from the LMS/SIS / Then: School Assistant cannot generate trustworthy high-signal insights..."
- **Pattern khớp với:** `Kera`
- **Vì sao là vi phạm:** chính risk register thừa nhận khả năng chưa tạo được `trustworthy high-signal insights`, nhưng marketing vẫn dùng cụm này như năng lực đã có.
- **Hành động sửa:** thay `high-signal` bằng mô tả trung tính hơn, ví dụ `insight ngắn gọn từ dữ liệu học tập`, cho tới khi có benchmark / pilot report.
- **Deadline:** `12/05/2026`

### VI PHẠM 4: Chuyển dữ liệu trẻ em ra vendor/cloud nước ngoài khi chưa có `DPIA / CTIA`

- **Luật áp dụng:** `PDPL`
- **Điều:** `Điều 30`; chế tài rủi ro theo `Điều 8`
- **Bằng chứng trong sản phẩm:**
  > "Mở `Langfuse` project của luồng parent insight  
  URL giả định nội bộ: `https://cloud.langfuse.com/project/school-assistant/traces`"
  
  > "Dùng vendor AI nước ngoài như `OpenAI`, `Anthropic` = có yếu tố `chuyển dữ liệu ra nước ngoài`."
  
  > "`CTIA = YES`"
  
  > "nhưng chưa có tài liệu nộp hoặc draft chính thức"
- **Pattern khớp với:** `CIC`
- **Vì sao là vi phạm:** repo đã nhận diện rõ việc có yếu tố cross-border transfer, nhưng document trail vẫn xác nhận chưa có `DPIA / CTIA` chính thức trước pilot.
- **Hành động sửa:** đóng băng mọi luồng gửi dữ liệu trẻ em sang vendor/cloud ngoài nội bộ cho đến khi có bản draft `DPIA / CTIA` được founder sign-off.
- **Deadline:** `15/05/2026` cho bản 0.1; hoàn tất trước `pilot live` và trong `60 ngày` kể từ khi bắt đầu xử lý nếu luồng đã chạy

### VI PHẠM 5: Chưa có pack `consent / withdrawal / deletion / retention` trước pilot live

- **Luật áp dụng:** `PDPL`
- **Điều:** `Điều 30`; rủi ro chế tài theo `Điều 8`
- **Bằng chứng trong sản phẩm:**
  > "Hoàn tất privacy notice, phạm vi đồng ý của phụ huynh và nguyên tắc xử lý dữ liệu"
  
  > "If: the startup cannot show valid child-data consent, cross-border processing clarity, deletion and withdrawal handling, and human-oversight logs / Then: a school counsel, regulator, or procurement review blocks or suspends the pilot."
  
  > "ship a founder-owned consent and data-flow pack before the first live pilot"
- **Pattern khớp với:** `CIC`
- **Vì sao là vi phạm:** roadmap và risk register đều nói các tài liệu này là blocker hoặc mitigation, tức là ở trạng thái hiện tại School Assistant chưa chứng minh được quyền xử lý dữ liệu trẻ em một cách audit-ready.
- **Hành động sửa:** tạo ngay bộ `pilot agreement + parent consent + withdrawal workflow + deletion SLA + retention rule`.
- **Deadline:** `15/05/2026` và phải xong trước `first live parent send`

### VI PHẠM 6: Đã tự phân loại `Cao` nhưng chưa có bộ hồ sơ high-risk trước deploy

- **Luật áp dụng:** `Luật AI VN`
- **Điều:** `Điều 9`
- **Bằng chứng trong sản phẩm:**
  > "Phân loại: `Cao`"
  
  > "Nghĩa vụ tương ứng:
  - đánh giá phù hợp trước khi deploy
  - đăng ký / thông báo vào CSDL AI quốc gia theo yêu cầu của Luật AI VN
  - thiết kế `human oversight`...
  - lưu log đầy đủ..."
  
  > "DPIA / CTIA ... chưa có tài liệu nộp hoặc draft chính thức"
- **Pattern khớp với:** `CIC`
- **Vì sao là vi phạm:** repo đã kết luận School Assistant là `high-risk education AI`, nhưng các artifact bắt buộc để chứng minh `conformity + notification + oversight + logs` vẫn chưa tồn tại ở mức vận hành.
- **Hành động sửa:** build `high-risk compliance pack` riêng cho School Assistant trước khi coi pilot là đủ điều kiện chạy thật.
- **Deadline:** bản đầu `16/05/2026`; hoàn thiện trước `pilot live`; mốc luật dài hạn theo note giáo dục trong repo là `01/09/2027`

### VI PHẠM 7: `Human-in-the-loop` được nêu trong PRD nhưng chưa thành control vận hành thật cho case tiêu cực

- **Luật áp dụng:** `Luật AI VN` + `PDPL`
- **Điều:** `Điều 9 Luật AI VN`; `Điều 30 PDPL`
- **Bằng chứng trong sản phẩm:**
  > "**Chiến lược:** Human-in-the-loop + Expectation Management"
  
  > "- Không tự động chuyển sang giáo viên trong MVP (tránh tăng độ phức tạp)"
  
  > "require manual review or template-only sends for severe negative cases"
- **Pattern khớp với:** `CIC`
- **Vì sao là vi phạm:** PRD dùng cụm `Human-in-the-loop`, nhưng control thực tế lại là `không tự động chuyển sang người thật`. Nghĩa là với insight tiêu cực, repo chưa chứng minh được một người thật review trước khi gửi.
- **Hành động sửa:** thêm gate bắt buộc `manual review hoặc template-only` cho mọi negative insight / low-confidence insight trước parent send.
- **Deadline:** `16/05/2026` và trước `100 live sends` đầu tiên

### VI PHẠM 8: Founder đã thấy vendor/policy risk nhưng chưa có hồ sơ rà soát vendor và log quyết định tiếp tục/dừng

- **Luật áp dụng:** `BLHS` (rủi ro analog theo pattern enabler liability) + `Luật AI VN`
- **Điều:** `Điều 324 BLHS` ở mức cảnh báo pattern; chưa đủ cơ sở để kết luận hiện tại đã cấu thành tội
- **Bằng chứng trong sản phẩm:**
  > "OpenAI's current usage policies already restrict automation of high-stakes decisions in sensitive areas including education without human review."
  
  > "Không để `OpenAI` hoặc `Anthropic` model gửi insight thẳng cho phụ huynh..."
  
  > "Hồ sơ rà soát điều khoản vendor | ✗"
- **Pattern khớp với:** `Pips`
- **Vì sao là vi phạm:** giống pattern `biết dấu hiệu, vẫn để hạ tầng chạy`, founder đã tự ghi nhận vendor/policy risk nhưng chưa có hồ sơ để chứng minh ai đã review, review khi nào, và tại sao vẫn cho tiếp tục hoặc dừng.
- **Hành động sửa:** lập `vendor review sheet + go/no-go log + escalation log` cho mọi vendor đụng tới dữ liệu hoặc parent-facing output.
- **Deadline:** `15/05/2026`, trước khi cho phép bất kỳ direct vendor path nào chạy live với dữ liệu thật

### VI PHẠM 9: Chưa có workflow `marketing approval` có founder sign-off trước asset public

- **Luật áp dụng:** `BLHS`
- **Điều:** `Điều 198`
- **Bằng chứng trong sản phẩm:**
  > "Chưa có file phê duyệt trước launch. `1_marketing_claims_audit.md` mới là audit, chưa có founder sign-off cho từng asset"
  
  > "Tạo template phê duyệt marketing — founder ký mỗi launch"
- **Pattern khớp với:** `Kera`
- **Vì sao là vi phạm:** startup đã có pitch materials public nhưng chưa có chứng cứ founder duyệt từng claim trước khi đem ra ngoài.
- **Hành động sửa:** tạo `marketing approval log` và khóa mọi asset public cho tới khi log này tồn tại.
- **Deadline:** `12/05/2026`

## TOP 5 nghiêm trọng nhất và 3 hành động sửa cho mỗi cái

### TOP 1 — Vi phạm 4: Cross-border child-data processing chưa có `DPIA / CTIA`

1. Tạo sơ đồ data flow đầy đủ cho luồng `school -> transform -> model/logging -> parent app`.
2. Tối thiểu hóa dữ liệu gửi ra ngoài: pseudonymize hoặc bỏ hẳn `tên học sinh / phụ huynh` nếu chưa thật sự cần.
3. Founder ký `DPIA / CTIA` bản 0.1 và freeze luồng live cho tới khi tài liệu này tồn tại.

### TOP 2 — Vi phạm 6: `High-risk education AI` nhưng chưa có compliance pack

1. Viết memo phân loại rủi ro 1 trang: vì sao School Assistant là `Cao`, use case nào nhạy cảm nhất, luồng nào phải review tay.
2. Tạo checklist `pre-live` cho high-risk AI: oversight, logs, fallback, incident owner, data owner.
3. Chuẩn bị hồ sơ thông báo/đăng ký nội bộ để sẵn sàng làm việc với trường và cơ quan khi cần.

### TOP 3 — Vi phạm 5: Thiếu `consent / withdrawal / deletion / retention` pack

1. Tạo parent consent form và school pilot appendix mô tả rõ dữ liệu nào được dùng để tạo insight.
2. Tạo workflow rút consent, xóa dữ liệu và thời hạn phản hồi nội bộ.
3. Viết retention rule rõ cho raw input, output, trace và log incident.

### TOP 4 — Vi phạm 1 + 2: Claim public đi trước evidence

1. Sửa ngay mọi asset public: `24 giờ`, `30-40%`, `high-signal` phải đổi thành `mục tiêu pilot`, `giả thuyết`, hoặc bỏ hẳn.
2. Tạo `marketing approval log` với cột `claim / evidence / owner / approved?`.
3. Không cho CMO/founder/pitch deck phát hành claim mới nếu chưa có evidence link hoặc honest version.

### TOP 5 — Vi phạm 8: Vendor review blind spot kiểu `Pips`

1. Tạo `vendor review sheet` cho `OpenAI`, `Anthropic` nếu dùng, `Langfuse Cloud`, và mọi cloud telemetry ngoài Việt Nam.
2. Tạo `go / pause / stop` decision log: khi có policy change, school objection hoặc parent report thì ai được phép quyết định tiếp tục chạy.
3. Gắn `abnormal insight & escalation review log` vào ritual review hằng tuần để founder có bằng chứng mình đã thấy và đã xử lý dấu hiệu.

## Kết luận điều hành

- Nếu School Assistant chạy pilot live tuần này mà chưa vá các điểm `4, 5, 6, 8`, rủi ro lớn nhất không phải bug sản phẩm mà là `không chứng minh được quyền xử lý + không chứng minh được oversight + không chứng minh được founder đã thẩm định vendor`.
- Nếu chỉ có `48 giờ`, thứ tự sửa nên là:
  1. freeze cross-border child-data path cho tới khi có draft `DPIA / CTIA`
  2. sửa toàn bộ claim public kiểu `24 giờ`, `30-40%`, `high-signal`
  3. chốt consent / deletion / retention pack
  4. viết high-risk memo + manual review gate cho negative insight
  5. tạo vendor review log + marketing approval log

## Nguồn kiểm tra ngoài repo

- Hiệu lực `Luật Bảo vệ dữ liệu cá nhân 91/2025/QH15`: CSDL VBPL quốc gia
- Hiệu lực `Luật Trí tuệ nhân tạo` từ `01/03/2026`: cổng thông tin Bộ Tư pháp / Chinhphu.vn
- `EU AI Act`: EUR-Lex, Regulation (EU) 2024/1689
