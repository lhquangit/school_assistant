# Document Trail — School Assistant

**Date:** 08/05/2026

## Nguyên tắc dùng file này

- Mục tiêu của hồ sơ chứng cứ founder không phải để "đẹp hồ sơ", mà để khi trường, luật sư hoặc cơ quan hỏi `founder có biết rủi ro này không?`, team có thể chỉ ngay ra tài liệu đã review, ngày review và người chịu trách nhiệm.
- Với School Assistant, rủi ro lớn nhất không phải thanh toán hay fraud kiểu fintech, mà là:
  - claim marketing đi quá xa so với evidence,
  - dùng vendor AI/cloud nước ngoài với dữ liệu trẻ em,
  - không chứng minh được human oversight cho luồng parent-facing insight.

## Bảng đối chiếu 5 loại hồ sơ


| #   | Loại                                            | Status | Link/Path                                                                                                                                                                                                                                                              | Deadline build |
| --- | ----------------------------------------------- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- |
| 1   | Nhật ký kiểm thử claim AI                       | ✗      | Đã có bước khởi đầu ở `docs/2_Risk_Analysis/2_AI_Compliance/1_marketing_claims_audit.md`, nhưng chưa phải nhật ký kiểm thử định kỳ theo từng feature / từng claim                                                                                                      | 15/05/2026     |
| 2   | Hồ sơ rà soát điều khoản vendor                 | ✗      | Chưa có file riêng. Hiện chỉ có tín hiệu rải rác trong `docs/2_Risk_Analysis/1_AI_Governance_And_Risk/1_rules_rails_ritual.md`, `docs/2_Risk_Analysis/1_AI_Governance_And_Risk/2_risk_register_v2.md` và `docs/2_Risk_Analysis/2_AI_Compliance/2_territorial_scope.md` | 15/05/2026     |
| 3   | Nhật ký giám sát giao dịch / hành vi bất thường | ✗      | Chưa có file riêng. Với School Assistant, nên hiểu mục này là `nhật ký giám sát insight bất thường, abuse report, escalation từ phụ huynh/trường`, dựa trên `docs/2_Risk_Analysis/1_AI_Governance_And_Risk/3_incident_playbook.md`                                     | 17/05/2026     |
| 4   | DPIA / CTIA                                     | ✗      | Đã có kết luận cần chuẩn bị trong `docs/2_Risk_Analysis/2_AI_Compliance/2_territorial_scope.md`, nhưng chưa có tài liệu nộp hoặc draft chính thức                                                                                                                      | 15/05/2026     |
| 5   | Phê duyệt nội dung marketing                    | ✗      | Chưa có file phê duyệt trước launch. `docs/2_Risk_Analysis/2_AI_Compliance/1_marketing_claims_audit.md` mới là audit, chưa có founder sign-off cho từng asset                                                                                                          | 12/05/2026     |


## TOP 1 ưu tiên

**Loại:** `#4 - DPIA / CTIA`

**Lý do:** School Assistant đang xử lý dữ liệu học tập của trẻ em và có khả năng gửi dữ liệu hoặc trace sang vendor AI/cloud nước ngoài; nếu chưa có `DPIA / CTIA`, founder gần như không có lá chắn nào khi trường hoặc cơ quan hỏi vì sao lại cho phép luồng dữ liệu đó chạy thật.

## Vì sao không ưu tiên mục khác trước

- `#1` và `#5` rất quan trọng để chống pattern `Kera`, nhưng chúng còn cứu được sau nếu team dừng claim mạnh ngay bây giờ.
- `#2` quan trọng vì vendor AI có thể đổi policy hoặc cách dùng data, nhưng nó đứng sau `DPIA / CTIA` vì vendor review vẫn là một phần của data-flow compliance.
- `#3` cần có trước pilot live, nhưng ở School Assistant hiện tại nó nên đi ngay sau `DPIA / CTIA`, vì muốn giám sát đúng thì trước hết phải chốt được luồng nào được phép chạy.

## Template build trong 1 tuần

### Người chịu trách nhiệm: Founder + Product lead + người phụ trách kỹ thuật luồng insight

### Tần suất cập nhật

- `DPIA`: tạo `1 lần` trước pilot thật, cập nhật lại khi đổi luồng dữ liệu, đổi vendor, đổi loại dữ liệu hoặc đổi bề mặt user-facing
- `CTIA`: tạo `1 lần` cho mỗi vendor/cloud nước ngoài có nhận dữ liệu hoặc trace; rà soát lại `hằng quý` hoặc ngay khi vendor đổi điều khoản

### Sample 3-5 dòng

```markdown
# DPIA / CTIA Snapshot — School Assistant
- Luồng dữ liệu: điểm số + nhận xét giáo viên -> logic insight -> vendor/model/logging nào -> app phụ huynh
- Dữ liệu gửi ra ngoài: trường nào, có chứa tên học sinh/phụ huynh hay không, có thể pseudonymize đến mức nào
- Cơ sở cho việc xử lý: pilot agreement, parent consent, school approval, founder sign-off ngày DD/MM/YYYY
- Rủi ro chính: dữ liệu trẻ em, cross-border transfer, output sai gây ảnh hưởng phụ huynh/trường
- Biện pháp giảm thiểu: data minimization, neutral fallback, manual review cho case nhạy cảm, kill switch, retention/deletion rule
```

## Đề xuất cấu trúc đầy đủ cho 5 hồ sơ

### 1. Nhật ký kiểm thử claim AI

**Mục tiêu:** Chứng minh founder không marketing quá sự thật và có evidence review trước khi nói AI làm được gì.

**Nên chứa:**

- Tên claim
- Asset chứa claim
- Evidence link
- Kết luận `A/B/C`
- Người duyệt
- Ngày duyệt

**Mẫu 1 dòng:**

> Claim: `giúp phụ huynh phản ứng sớm hơn` | Asset: `twitter_pitch.md` | Evidence: `pilot target only` | Status: `B` | Action: `đổi wording trước 12/05/2026`

### 2. Hồ sơ rà soát điều khoản vendor

**Mục tiêu:** Chứng minh founder đã biết vendor nào đang đụng vào dữ liệu trẻ em, data retention ra sao, log ở đâu, ai chịu trách nhiệm nếu policy đổi.

**Nên chứa:**

- Vendor name
- Mục đích dùng
- Dữ liệu nào đi qua vendor
- Quốc gia / vùng xử lý
- Điều khoản privacy / retention / training
- Risk note
- Quyết định tiếp tục hay không

**Vendor cần vào hồ sơ đầu tiên:**

- `OpenAI`
- `Anthropic` nếu dùng
- `Langfuse Cloud`
- Bất kỳ cloud nào lưu log / push / app telemetry ngoài Việt Nam

### 3. Nhật ký giám sát giao dịch / hành vi bất thường

**Mục tiêu:** Với School Assistant, mục này là bằng chứng founder không làm ngơ khi có dấu hiệu abuse, output lạ hoặc escalation từ trường/phụ huynh.

**Nên đổi tên vận hành nội bộ thành:**
`Abnormal Insight & Escalation Review Log`

**Nên chứa:**

- Ngày giờ
- Trường / pilot cohort
- Dấu hiệu bất thường
- Ảnh hưởng dự kiến
- Action đã làm
- Kết quả follow-up

**Ví dụ dấu hiệu cần log:**

- insight tiêu cực được gửi khi chỉ có `1 điểm`
- fallback tăng đột biến
- phụ huynh báo insight sai
- trường yêu cầu tạm dừng luồng AI

### 4. DPIA / CTIA

**Mục tiêu:** Chứng minh founder đã đánh giá tác động dữ liệu cá nhân và việc chuyển dữ liệu ra nước ngoài trước khi chạy pilot thật.

**Nên chứa:**

- sơ đồ data flow
- loại dữ liệu cá nhân
- vendor nhận dữ liệu
- căn cứ pháp lý và consent
- risk rating
- biện pháp giảm thiểu
- owner và ngày review lại

### 5. Phê duyệt nội dung marketing

**Mục tiêu:** Chặn founder/team/KOL nói quá trong pitch, demo day, landing page, livestream hoặc sales deck.

**Nên chứa:**

- asset name
- link asset
- claim nhạy cảm
- evidence link
- trạng thái `approved / revise / blocked`
- founder ký ngày nào

**Nguyên tắc bắt buộc:**

- Không asset public nào được lên nếu chưa có `1` người review evidence và `1` founder sign-off
- Mọi con số như `24 giờ`, `30-40%`, `70% hữu ích`, `near real-time` phải ghi rõ là `pilot target`, `internal goal` hoặc `measured result`

## Kế hoạch build trong 7 ngày

1. `09/05/2026`: tạo folder hoặc cụm file evidence riêng cho compliance trail
2. `10/05/2026`: chốt data-flow map cho luồng `school -> insight -> parent`
3. `11/05/2026`: draft `DPIA / CTIA` bản 0.1 cho OpenAI/Langfuse
4. `12/05/2026`: tạo form `marketing approval` và review lại toàn bộ pitch hiện có
5. `13/05/2026`: tạo `vendor review sheet` cho từng vendor đang dùng hoặc có kế hoạch dùng
6. `14/05/2026`: tạo `abnormal insight review log` và gắn vào incident workflow
7. `15/05/2026`: founder review toàn bộ, ký version đầu tiên và set lịch review định kỳ

## Kết luận

- Nếu chỉ được làm `1` bộ hồ sơ trong tuần này, hãy làm `DPIA / CTIA` trước.
- Nếu có thêm sức, thứ tự tiếp theo cho School Assistant nên là:
  1. `Phê duyệt nội dung marketing`
  2. `Hồ sơ rà soát điều khoản vendor`
  3. `Nhật ký giám sát insight bất thường`
  4. `Nhật ký kiểm thử claim AI`
- Lý do rất thực tế: startup này đang bán `trust` cho trường và phụ huynh, trên dữ liệu trẻ em, qua AI parent-facing. Không có document trail thì founder gần như không chứng minh được mình đã `biết rủi ro, đã review, đã giới hạn và đã theo dõi`.

