## 1. RICE Matrix


| #   | Feature                                               | Reach (user/quý) | Impact | Confidence | Effort (PM) | Score = (R x I x C) / E | Ghi chú                                                                                            |
| --- | ----------------------------------------------------- | ---------------- | ------ | ---------- | ----------- | ----------------------- | -------------------------------------------------------------------------------------------------- |
| 1   | High-signal insight engine + fallback guardrails      | 180              | 3.0    | 0.5        | 1.5         | **180.00**              | Đây là lõi của Aha Moment: phụ huynh nhận được insight đáng hành động thay vì raw data.            |
| 2   | Read-only LMS/SIS integration + event sync            | 180              | 2.0    | 0.5        | 2.5         | **72.00**               | Không sexy, nhưng là nền tảng để workflow embedding và moat với nhà trường.                        |
| 3   | Parent app + push notification + insight feed         | 150              | 2.0    | 0.5        | 2.5         | **60.00**               | Là bề mặt parent-facing để deliver value, nhưng activation risk vẫn cao vì phụ huynh phải cài app. |
| 4   | One-tap parent actions ("Đã xem" / "Cần hỗ trợ thêm") | 90               | 1.0    | 0.5        | 0.75        | **60.00**               | Không tạo insight mới, nhưng giúp đo hành động và bridge sang can thiệp thực tế.                   |
| 5   | Predictive AI + personalized recommendations          | 45               | 0.5    | 0.5        | 4.0         | **2.81**                | Hấp dẫn để demo, nhưng lệch khỏi MVP hypothesis và effort quá cao ở giai đoạn này.                 |


## 2. 2x2 Value-Effort Matrix

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

