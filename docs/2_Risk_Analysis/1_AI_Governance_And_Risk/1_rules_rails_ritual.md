# Workshop 1 — Rules, Rails, Ritual

## Risk lớn nhất của School Assistant

`AI gửi một insight học tập sai hoặc quá tự tin tới phụ huynh khi dữ liệu còn yếu, mâu thuẫn hoặc thiếu context.`

Đây là risk lớn nhất vì School Assistant đang bán `trust` cho nhà trường. Chỉ cần vài insight sai về học sinh thật, phụ huynh sẽ mất niềm tin, giáo viên phải chữa cháy, và trường có thể dừng pilot ngay. Với startup ở giai đoạn này, đó là risk có thể đốt `3-6 tháng runway` nhanh hơn nhiều so với một bug UI thông thường.

---

## R1 — RULES

1. **Cấm cụ thể:** Không để `OpenAI` hoặc `Anthropic` model gửi insight thẳng cho phụ huynh nếu dữ liệu chỉ có `1 điểm`, thiếu nhận xét giáo viên, hoặc có mâu thuẫn rõ giữa điểm số và comment.
2. **Allowed alternative:** Khi dữ liệu yếu hoặc mâu thuẫn, bắt buộc chuyển sang `rule-based + template fallback` của nội bộ; mọi thay đổi prompt/rule phải đi qua `Promptfoo Community` trước khi merge. Cost: `$0/tháng`.
3. **Hậu quả vi phạm:** Lần 1 founder talk `1-1` và ghi note; lần 2 mất quyền merge vào luồng `parent-facing AI`; lần 3 `let go`.
4. **Update mechanism:** Founder là người duy nhất cập nhật rule này trong Notion page `School Assistant / Ops / AI Safety Rules` mỗi khi đổi prompt, threshold, fallback wording hoặc vendor policy; update trong `cùng ngày`.

---

## R2 — RAILS

### Rail 1 — Promptfoo Community trong CI

- **Tool:** `Promptfoo Community`
- **Cost:** `$0/tháng`
- **Cách chặn risk:** Mỗi PR đụng tới prompt, rule, template wording hoặc threshold phải chạy bộ test cố định trước khi merge. PR sẽ `fail` nếu model:
  - kết luận mạnh khi chỉ có 1 điểm dữ liệu,
  - bỏ qua fallback ở case thiếu comment,
  - hoặc viết insight quyết đoán khi dữ liệu mâu thuẫn.
- **Vì sao hợp với School Assistant:** Risk chết người của sản phẩm không phải “AI trả lời xấu”, mà là “AI nói quá chắc về học sinh thật”. Promptfoo giúp biến các failure mode này thành test có thể chặn trước khi release.

### Rail 2 — Langfuse Hobby

- **Tool:** `Langfuse Hobby`
- **Cost:** `$0/tháng`
- **Cách chặn risk:** Log toàn bộ generation của luồng insight trong pilot để founder hoặc product lead review mỗi ngày các case:
  - insight bị phụ huynh bấm `Cần hỗ trợ`,
  - insight bị fallback quá nhiều,
  - insight bị giáo viên/phụ huynh report là sai hoặc thiếu context.
- **Vì sao hợp với School Assistant:** Nếu vẫn có case lọt qua trước production rail, team cần thấy ngay mẫu sai lặp lại để tắt prompt, siết threshold hoặc chuyển toàn bộ flow sang fallback wording trong ngày, trước khi trust với trường bị thủng lớn.

### Tổng cost Rails

- `Promptfoo Community`: `$0/tháng`
- `Langfuse Hobby`: `$0/tháng`
- **Tổng:** `$0/tháng`

---

## R3 — RITUAL

### Weekly ritual: Parent Truth Friday

Mỗi thứ Sáu, founder và product lead dành `30 phút` để review `5 insight thật` từ tuần đó:

- `2 insight` phụ huynh đã mở và hành động bình thường
- `2 insight` bị fallback hoặc bị bỏ qua
- `1 insight` có khiếu nại, nghi ngờ hoặc bị bấm `Cần hỗ trợ`

Sau review, founder phải gọi hoặc nhắn trực tiếp cho `1 phụ huynh` hoặc `1 đại diện trường` trong pilot để hỏi đúng một câu:

> `Insight nào tuần này làm anh/chị thấy sai, quá mạnh, hoặc thiếu context nhất? Lúc đó anh/chị đã làm gì sau khi đọc nó?`

### Vì sao ritual này đáng làm

- Nó ép founder nghe `truth from the edge`, không chỉ nhìn dashboard đẹp.
- Nó giúp team phát hiện sớm loại insight làm mất trust trước khi trường escalates chính thức.
- Nó implement được ngay trong `1 tuần`, không cần budget hay quy trình corporate.

---

## Self-check

- **Tổng cost Rails dưới $500/tháng?** Có. Tổng hiện tại là `$0/tháng`.
- **Ritual implement được trong 1 tuần?** Có. Chỉ cần chốt owner, chọn 5 insight review mỗi tuần, và lên lịch `30 phút` cố định vào thứ Sáu.
