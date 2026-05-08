# Marketing Claims Audit — School Assistant

**Ngày rà soát:** 08/05/2026
**Người rà soát:** Founder team

## Phạm vi rà soát

- Repo hiện chưa có landing page public riêng cho School Assistant.
- Audit này dùng 3 nguồn gần nhất đang có trong repo làm proxy cho marketing materials:
  - `docs/1_Project_Analysis/4_Investor Buy-in & Pitch/twitter_pitch.md`
  - `docs/1_Project_Analysis/4_Investor Buy-in & Pitch/pitch_memo.md`
  - `docs/1_Project_Analysis/2_PRD & Product Market Fit.md`

## Bảng claim audit


| #   | Câu gốc                                                                                                        | Vị trí                             | Mức | Evidence hiện có                                                                                                 | Honest version                                                                                                                                                  | Action                                                |
| --- | -------------------------------------------------------------------------------------------------------------- | ---------------------------------- | --- | ---------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------- |
| 1   | "School Assistant biến dữ liệu LMS thành high-signal insight trong app phụ huynh"                              | Twitter pitch mở đầu               | B   | Có PRD mô tả luồng insight và fallback, nhưng chưa có pilot data chứng minh insight thật sự "high-signal"        | "School Assistant chuyển dữ liệu LMS thành insight học tập ngắn gọn cho phụ huynh; pilot đầu sẽ đo xem insight có đủ tín hiệu để phụ huynh hành động hay không" | Giữ ý, bỏ từ `high-signal` nếu chưa có dữ liệu pilot  |
| 2   | "để gia đình hành động trong 24 giờ thay vì chờ giáo viên báo"                                                 | Twitter pitch mở đầu               | C   | `24 giờ` mới là success threshold trong pitch memo, chưa phải kết quả đã đo                                      | "Mục tiêu của pilot là giúp một phần phụ huynh hành động trong vòng 24 giờ sau khi nhận insight"                                                                | Sửa ngay tuần này                                     |
| 3   | "School Assistant đọc dữ liệu mới, tạo high-signal insight, đẩy push notification vào app phụ huynh"           | Twitter script                     | B   | Có PRD nêu ingest event-based, push notification và rule/fallback; chưa có demo hoặc vận hành thật               | "School Assistant đọc dữ liệu mới từ hệ thống trường, tạo insight ngắn gọn và gửi thông báo tới app phụ huynh trong phạm vi pilot"                              | Đổi câu trên mọi tài liệu public                      |
| 4   | "phụ huynh hành động sớm"                                                                                      | Twitter script                     | B   | Đây là hypothesis hợp lý theo JTBD, nhưng chưa có bằng chứng hành vi thật                                        | "Sản phẩm được thiết kế để giúp phụ huynh phản ứng sớm hơn khi có thay đổi đáng chú ý"                                                                          | Đổi wording sang `được thiết kế để`                   |
| 5   | "chứng minh rằng 30 đến 40 phần trăm phụ huynh sẽ hành động sau mỗi insight"                                   | Twitter script                     | C   | Con số `30-40%` trong repo là success bar của pilot, không phải kết quả thực tế                                  | "Pilot sẽ kiểm tra liệu có thể đạt mức 30-40% phụ huynh thực hiện một hành động trong 24 giờ hay không"                                                         | Sửa ngay tuần này                                     |
| 6   | "phát hiện các thay đổi điểm số và nhận xét có tín hiệu cao"                                                   | Pitch memo, phần Solution          | B   | Có rule-based thesis và dữ liệu nguồn được nêu rõ trong PRD, nhưng chưa có benchmark về precision/false positive | "Phát hiện các thay đổi điểm số và nhận xét đáng chú ý theo rule ban đầu; các trường hợp yếu hoặc mâu thuẫn sẽ fallback sang thông tin trung tính"              | Giữ ý, thêm guardrail vào câu public                  |
| 7   | "AI được dùng một cách bảo thủ"                                                                                | Pitch memo, phần Solution          | B   | Có nhiều tài liệu nội bộ support claim này: PRD fallback UX, Rules/Rails, incident playbook, risk register       | "AI được dùng theo hướng bảo thủ: ưu tiên rule-based hoặc model nhẹ, và không gửi kết luận mạnh khi dữ liệu yếu hoặc mâu thuẫn"                                 | Có thể giữ, nhưng nên gắn với cơ chế cụ thể           |
| 8   | "các trường hợp dữ liệu yếu hoặc mâu thuẫn sẽ fallback sang thông tin trung tính thay vì đưa ra kết luận mạnh" | Pitch memo, phần Solution          | B   | PRD mô tả trigger fallback khá rõ; tuy nhiên chưa có bằng chứng flow đã build và vận hành đúng                   | "Trong thiết kế hiện tại, các trường hợp dữ liệu yếu hoặc mâu thuẫn sẽ được chuyển sang wording trung tính thay vì kết luận mạnh"                               | Đổi sang `trong thiết kế hiện tại` cho đến khi ship   |
| 9   | "phụ huynh có thể phát hiện sớm vấn đề và can thiệp kịp thời"                                                  | PRD Problem Statement / User Story | B   | Đây là value proposition phù hợp với JTBD, chưa có số liệu outcome thật                                          | "Mục tiêu của sản phẩm là giúp phụ huynh phát hiện sớm vấn đề hơn so với workflow hiện tại"                                                                     | Giữ trong PRD; không nên dùng như claim đã chứng minh |
| 10  | "Hệ thống sẽ xử lý và gửi insight trong vòng vài phút sau khi có dữ liệu mới (near real-time)"                 | PRD, Update frequency              | B   | Có design intent nhưng chưa có dữ liệu vận hành về latency, queue, rate limit                                    | "Mục tiêu vận hành của MVP là gửi insight trong vòng vài phút sau khi có dữ liệu mới, tùy chất lượng dữ liệu và tải hệ thống"                                   | Đổi sang mục tiêu vận hành, không nói như fact        |
| 11  | "Không tạo insight mạnh khi dữ liệu không đủ"                                                                  | PRD, Fallback UX                   | B   | Có rule/fallback documented rất rõ, nhưng chưa có audit log production                                           | "Nguyên tắc sản phẩm là không gửi insight mạnh khi dữ liệu không đủ; cần triển khai logging để kiểm chứng rule này trong pilot"                                 | Giữ và biến thành acceptance criterion                |
| 12  | "School Assistant có thể tạo ra hành vi phụ huynh hành động lặp lại chứ không chỉ tạo thêm một lớp thông báo"  | Pitch memo, phần Ask               | C   | Đây là thesis huy động vốn, chưa có proof; repo còn ghi rõ đang `pre-traction`                                   | "Khoản pilot này nhằm kiểm tra liệu School Assistant có tạo ra hành vi phụ huynh hành động lặp lại hay không"                                                   | Sửa ngay trong deck/ask                               |


## Thống kê

- Tổng số claim: `12`
- Mức A: `0`
- Mức B: `9`
- Mức C: `3`

## TOP 3 priority sửa ngay

1. Mọi câu đang nói như thể `24 giờ` và `30-40% hành động` đã là kết quả thật phải đổi lại thành `mục tiêu pilot` hoặc `success threshold`.
2. Bỏ hoặc làm mềm mọi từ tuyệt đối/gây hiểu lầm như `high-signal`, `hành động sớm`, `tạo ra hành vi lặp lại` nếu chưa có A/B test, pilot report hoặc case study.
3. Với mọi claim về safety như `AI dùng bảo thủ` hoặc `fallback`, phải gắn kèm cơ chế cụ thể: `rule-based trước`, `không gửi kết luận mạnh khi dữ liệu yếu`, `human review / neutral wording cho case nhạy cảm`.

## Rewrite ngắn gọn đề xuất cho câu public quan trọng nhất

**Bản hiện tại:**

> School Assistant biến dữ liệu LMS thành high-signal insight trong app phụ huynh, để gia đình hành động trong 24 giờ thay vì chờ giáo viên báo.

**Bản honest hơn:**

> School Assistant chuyển dữ liệu LMS thành insight học tập ngắn gọn cho phụ huynh và đang chạy pilot để đo liệu các insight này có giúp gia đình phản ứng sớm hơn hay không.

## Ghi chú tuân thủ

- Nếu founder muốn dùng các con số như `30-40%`, `70% hữu ích`, hoặc `vài phút`, cần tạo một gói evidence riêng:
  - pilot report
  - event log
  - dashboard conversion
  - sample size
  - ngày đo và điều kiện đo
- Theo tinh thần Day 22, chưa có evidence thì không được biến hypothesis thành kết quả.

