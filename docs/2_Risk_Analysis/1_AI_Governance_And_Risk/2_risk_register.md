# Workshop 2 — Risk Register

## 1. Burn rate quy đổi runway

### Burn rate dùng cho workshop

- **Base fixed burn / tháng:** khoảng `70.000.000 VND`
- Nguồn: base case trong file `3-AI-Product-Finance-Model.xlsx`
- Giả định dùng cho governance workshop: ở giai đoạn pilot, startup vẫn đang ở trạng thái `pre-traction`, nên khi có incident lớn thì fixed burn là cách đo sống còn dễ hiểu nhất

### Quy đổi nhanh

- `35.000.000 VND` mất = `0,5 tháng runway`
- `70.000.000 VND` mất = `1 tháng runway`
- `140.000.000 VND` mất = `2 tháng runway`
- `210.000.000 VND` mất = `3 tháng runway`
- `350.000.000 VND` mất = `5 tháng runway`
- `490.000.000 VND` mất = `7 tháng runway`

---

## 2. 3 risks từ 3 type khác nhau

### Risk 1 — Vendor risk

- **Type:** `Vendor`
- **If:** `OpenAI` hoặc `Anthropic` thay đổi rate limit, model behavior hoặc pricing ngay trong lúc School Assistant đang chạy pilot với trường thật
- **Then:** luồng tạo insight bị chậm, lỗi hoặc quá đắt để chạy ổn định, khiến nhà trường thấy sản phẩm thiếu tin cậy và pilot bị gián đoạn
- **Leading to:** mất khoảng `2 tháng runway` vì team phải dồn thời gian chuyển model, retest prompt/rule, hỗ trợ thủ công cho pilot và chậm ký tiếp với trường
- **Likelihood (1-5):** `3`
- **Impact (1-5):** `2`
- **Score = L x I:** `6`
- **Quadrant:** `Watch / Mitigate`
- **Vì sao chấm như vậy:** vendor change là chuyện có thật và không hiếm, nhưng với School Assistant vẫn còn đường lùi bằng `rule-based + fallback wording`, nên impact chưa tới mức giết công ty ngay.

### Risk 2 — Customer-facing AI risk

- **Type:** `Customer-facing`
- **If:** hệ thống gửi một insight sai hoặc quá tự tin về học sinh thật khi dữ liệu còn yếu, thiếu nhận xét hoặc mâu thuẫn
- **Then:** phụ huynh phản ứng sai với con, khiếu nại lên giáo viên hoặc ban giám hiệu, và trường kết luận rằng sản phẩm không đủ an toàn để tiếp tục pilot
- **Leading to:** mất khoảng `4 tháng runway` vì mất trường pilot, phải hoàn tiền/compensate, founder dành nhiều tuần chữa cháy trust và kế hoạch gọi vốn bị chậm
- **Likelihood (1-5):** `4`
- **Impact (1-5):** `4`
- **Score = L x I:** `16`
- **Quadrant:** `KILL ZONE`
- **Vì sao chấm như vậy:** đây là risk sát nhất với thesis sản phẩm. School Assistant đang bán `trust + timeliness`, nên chỉ vài insight sai cũng đủ làm pilot sụp và narrative investor bị thủng.

### Risk 3 — Founder-bandwidth risk

- **Type:** `Founder-bandwidth`
- **If:** founder hoặc một người duy nhất đang giữ prompt, threshold, fallback logic và quan hệ với trường bị ốm hoặc unavailable `3 ngày` đúng lúc có incident hoặc vendor issue
- **Then:** không ai đủ context để verify log, tắt luồng AI, nói chuyện với trường và đưa ra quyết định containment trong giờ đầu
- **Leading to:** mất khoảng `3 tháng runway` vì incident kéo dài hơn mức cần thiết, trường mất niềm tin và team bị đứng hình ở đúng giai đoạn pilot
- **Likelihood (1-5):** `4`
- **Impact (1-5):** `3`
- **Score = L x I:** `12`
- **Quadrant:** `Watch / Mitigate`
- **Vì sao chấm như vậy:** đây là single-point-of-failure rất thật với startup nhỏ. Nó chưa chắc xảy ra hàng tuần, nhưng khi xảy ra thì damage lớn vì cả quyết định sản phẩm lẫn quyết định quan hệ trường đều đang dồn vào founder.

---

## 3. Bảng tổng hợp risk register


| Risk                            | Type              | If                                                                 | Then                                                      | Leading to       | Likelihood | Impact | Score | Quadrant         |
| ------------------------------- | ----------------- | ------------------------------------------------------------------ | --------------------------------------------------------- | ---------------- | ---------- | ------ | ----- | ---------------- |
| Model vendor instability        | Vendor            | OpenAI/Anthropic đổi rate limit, behavior hoặc pricing trong pilot | Insight chậm, lỗi hoặc cost tăng mạnh; pilot bị gián đoạn | `2 tháng runway` | 3          | 2      | 6     | Watch / Mitigate |
| Wrong parent insight            | Customer-facing   | Insight sai hoặc quá tự tin được gửi cho phụ huynh                 | Phụ huynh khiếu nại; trường dừng pilot                    | `4 tháng runway` | 4          | 4      | 16    | **KILL ZONE**    |
| Founder single point of failure | Founder-bandwidth | Founder hoặc owner duy nhất của AI flow unavailable 3 ngày         | Incident không ai contain đủ nhanh                        | `3 tháng runway` | 4          | 3      | 12    | Watch / Mitigate |


---

## 4. 2x2 matrix nhanh

```text
                         LIKELIHOOD
                   Low                High
              ┌────────────────┬─────────────────────────┐
High Impact   │ WATCH          │ KILL ZONE               │
(>3 months)   │                │                         │
              │                │ 2. Wrong parent insight │
              │                │    (Score 16)           │
              ├────────────────┼─────────────────────────┤
Lower Impact  │ ACCEPT / WATCH │ WATCH / MITIGATE        │
(<=3 months)  │                │                         │
              │                │ 1. Model vendor         │
              │                │    instability (6)      │
              │                │ 3. Founder single point │
              │                │    of failure (12)      │
              └────────────────┴─────────────────────────┘
```

---

## 5. Risk nào vào KILL ZONE?

### KILL ZONE risk

- `Wrong parent insight` — Score `16`

### Vì sao đây là priority cao nhất cho Workshop 3

- Nó là risk gần nhất với core value proposition của School Assistant.
- Nó có thể làm mất `trust` từ cả phụ huynh lẫn nhà trường chỉ trong một incident.
- Nó không chỉ là bug sản phẩm; nó là risk phá pilot, phá fundraising story và phá motion bán hàng cùng lúc.

Workshop 3 nên viết incident playbook cho đúng risk này:  
`9h30 sáng, phụ huynh hoặc trường chụp màn hình một insight sai và bắt đầu escalates công khai`.

---

## 6. Kết luận nhanh

- School Assistant hiện có `1 KILL ZONE risk` rất rõ: AI gửi insight sai cho phụ huynh.
- Vendor risk và founder-bandwidth risk chưa ở mức kill zone, nhưng đều cần mitigation sớm vì chúng có thể kết hợp với nhau và đẩy incident xấu đi nhanh hơn.
- Nếu phải ưu tiên một thứ trong tuần này, đó không phải là làm thêm tính năng mới, mà là giảm xác suất của `wrong parent insight` và giảm phụ thuộc vào một cá nhân duy nhất trong giờ đầu của incident.

