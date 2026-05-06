# Workshop 1 — RICE + 2x2 Value-Effort

## 1. Cách mình chấm

**Nguồn gốc feature:** dựa trên [2_PRD & Product Market Fit.md](/Users/quanliver/Projects/AI_Sys/School-Assistant/docs/1_Project_Analysis/2_PRD%20%26%20Product%20Market%20Fit.md), ưu tiên 4 feature in-scope của MVP và thêm 1 feature "tempting nhưng nguy hiểm" để buộc trade-off rõ ràng đúng tinh thần Day 20.

**Giả định để chấm Reach:**

- Q1 tập trung vào pilot `3 trường`.
- Optimistic estimate: khoảng `300` phụ huynh được mời dùng app trong 1 quý đầu.
- Theo handbook Day 20, Reach phải `discount 50%` so với estimate lạc quan, nên mình chỉ chấm reach thực tế ở mức `45-180 user/quý` tùy feature.

**Giả định để chấm Confidence:**

- PRD hiện mới có hypothesis, chưa có interview log hoặc pilot data thật.
- Vì vậy, theo quy tắc Day 20, tất cả feature đều bị cap ở `50% confidence`.

**Giả định để chấm Effort:**

- Effort tính bằng `person-month`.
- Đã cộng thêm phần integration, QA, bug fix và edge cases theo tinh thần `multiply 1.5x`.

---

## 2. 5 Feature Candidates

1. `High-signal insight engine + fallback guardrails`
2. `Read-only LMS/SIS integration + event sync`
3. `Parent app + push notification + insight feed`
4. `One-tap parent actions ("Đã xem" / "Cần hỗ trợ thêm")`
5. `Predictive AI + personalized recommendations`

---

## 3. RICE Matrix


| #   | Feature                                               | Reach (user/quý) | Impact | Confidence | Effort (PM) | Score = (R x I x C) / E | Ghi chú                                                                                            |
| --- | ----------------------------------------------------- | ---------------- | ------ | ---------- | ----------- | ----------------------- | -------------------------------------------------------------------------------------------------- |
| 1   | High-signal insight engine + fallback guardrails      | 180              | 3.0    | 0.5        | 1.5         | **180.00**              | Đây là lõi của Aha Moment: phụ huynh nhận được insight đáng hành động thay vì raw data.            |
| 2   | Read-only LMS/SIS integration + event sync            | 180              | 2.0    | 0.5        | 2.5         | **72.00**               | Không sexy, nhưng là nền tảng để workflow embedding và moat với nhà trường.                        |
| 3   | Parent app + push notification + insight feed         | 150              | 2.0    | 0.5        | 2.5         | **60.00**               | Là bề mặt parent-facing để deliver value, nhưng activation risk vẫn cao vì phụ huynh phải cài app. |
| 4   | One-tap parent actions ("Đã xem" / "Cần hỗ trợ thêm") | 90               | 1.0    | 0.5        | 0.75        | **60.00**               | Không tạo insight mới, nhưng giúp đo hành động và bridge sang can thiệp thực tế.                   |
| 5   | Predictive AI + personalized recommendations          | 45               | 0.5    | 0.5        | 4.0         | **2.81**                | Hấp dẫn để demo, nhưng lệch khỏi MVP hypothesis và effort quá cao ở giai đoạn này.                 |


### Thứ tự ưu tiên theo RICE score

1. `High-signal insight engine + fallback guardrails` — `180.00`
2. `Read-only LMS/SIS integration + event sync` — `72.00`
3. `Parent app + push notification + insight feed` — `60.00`
4. `One-tap parent actions` — `60.00`
5. `Predictive AI + personalized recommendations` — `2.81`

**Tie-break note:** Feature `#3` và `#4` cùng score, nhưng nếu phải chọn trước thì `#3` quan trọng hơn vì là nơi user thật nhận insight; `#4` chỉ có ý nghĩa sau khi `#3` đã tồn tại.

---

## 4. 2x2 Value-Effort Matrix

```text
                         EFFORT
                   Low                High
              ┌────────────────┬─────────────────────────┐
High Value    │ QUICK WINS     │ STRATEGIC BETS          │
              │                │                         │
              │ 1. High-signal │ 2. LMS/SIS integration  │
              │    insight     │    + event sync         │
              │    engine      │                         │
              │                │ 3. Parent app + push    │
              │                │    notification + feed  │
              ├────────────────┼─────────────────────────┤
Low Value     │ FILL-INS       │ NON-STARTERS            │
              │                │                         │
              │ 4. One-tap     │ 5. Predictive AI +      │
              │    parent      │    personalized         │
              │    actions     │    recommendations      │
              └────────────────┴─────────────────────────┘
```

### Quick Wins

- `High-signal insight engine + fallback guardrails`

**Lý do:** Value cao nhất trong toàn bộ bảng và effort vẫn đủ thấp để làm trong MVP. Đây là thứ trực tiếp kiểm chứng hypothesis "phụ huynh có hành động khi nhận insight hay không".

### Strategic Bets

- `Read-only LMS/SIS integration + event sync`
- `Parent app + push notification + insight feed`

**Lý do:** Cả hai đều effort cao hơn, nhưng build ra moat dài hạn.
`LMS/SIS integration` tạo workflow embedding vào hệ thống trường.
`Parent app + push/feed` tạo bề mặt sản phẩm riêng, giảm phụ thuộc vào cổng thông tin thụ động của trường.

### Fill-ins

- `One-tap parent actions ("Đã xem" / "Cần hỗ trợ thêm")`

**Lý do:** Effort thấp, hữu ích cho measurement và activation funnel, nhưng bản thân nó không tạo ra giá trị cốt lõi nếu insight chưa đủ mạnh.

### Non-starters

- `Predictive AI + personalized recommendations`

**Lý do:** Đúng kiểu feature "nghe rất AI" nhưng sai thời điểm. Nó đòi nhiều data sạch, nhiều tuning, confidence hiện rất thấp, và không trực tiếp kiểm chứng riskiest assumption trong PRD. Nếu làm sớm, team sẽ đốt effort vào output thay vì outcome.

---

## 5. Kết luận bắt buộc của Workshop 1

### Quick Win — làm trước

- `High-signal insight engine + fallback guardrails`

Đây là feature nên làm đầu tiên vì nó chạm trực tiếp vào `core outcome`: phụ huynh phát hiện sớm vấn đề và hành động kịp thời.

### Strategic Bet — moat dài hạn

- `Read-only LMS/SIS integration + event sync`

Đây là strategic bet quan trọng nhất vì nó khó, không "demo-friendly", nhưng là thứ khiến School Assistant không bị xem như một app insight rời rạc.

### Non-starter — bỏ thẳng ở giai đoạn này

- `Predictive AI + personalized recommendations`

Feature này nên bỏ khỏi NOW/NEXT vì vừa high effort vừa low confidence, trong khi PRD hiện tại còn chưa chứng minh được phụ huynh có mở app và hành động với insight cơ bản hay không.

---

