# School Assistant — Risk Register v2

## Assumptions

- Base burn for runway conversion: `~70,000,000 VND/month` from the `Base` case in `3-AI-Product-Finance-Model.xlsx`.
- Severity is scored against the stricter operating assumption in the prompt: `5 people`, `~12 months runway`, `Series Seed`, not a later-stage team with legal/compliance headcount.
- Runway loss includes not just cash cost, but also founder recovery time, pilot delays, lost school renewals, and damage to the next fundraising narrative.

---

RISK 1: False-Alarm Parent Insight
- Type: Customer-facing
- If: sparse or contradictory LMS data plus aggressive thresholds or lightweight LLM wording creates a strong negative insight / Then: a real parent escalates to the teacher or principal, and the school pauses the pilot.
- Leading to: `7 months of runway` because the first live proof point dies, the next 2 school conversations slow down, and the pre-seed story turns from "timely intervention" into "unsafe parent messaging."
- Likelihood (1-5): `4` because the PRD explicitly accepts a lightweight model, inconsistent teacher comments, and limited context while also treating "insight sai nghiêm trọng" as unacceptable.
- Impact (1-5 by runway): `5`
- Mitigation: require at least 2 corroborating signals before any negative insight is sent; default to neutral fallback wording whenever comments and scores conflict; review every parent-facing negative insight daily for the first 100 live sends and keep a founder kill switch.

RISK 2: Parent Opt-In Collapse
- Type: Customer-facing
- If: parents do not install the app or leave push notifications off / Then: the product cannot prove the `24-hour action` loop even if insight quality is decent.
- Leading to: `4 months of runway` because the team burns time improving AI while the real failure is distribution, and schools conclude the product adds notification overhead without changing parent behavior.
- Likelihood (1-5): `4` because the PRD names app install, push opt-in, and return behavior as the riskiest assumption.
- Impact (1-5 by runway): `4`
- Mitigation: run the first pilot as a white-glove cohort with assisted install during onboarding; instrument install-to-opt-in-to-open conversion before adding more features; keep one temporary reminder fallback for pilot cohorts until push opt-in is stable.

RISK 3: School Data Access Freeze
- Type: Customer-facing
- If: the pilot school withholds teacher comments, timestamps, or regular exports from the LMS/SIS / Then: School Assistant cannot generate trustworthy high-signal insights or near-real-time alerts.
- Leading to: `5 months of runway` because the team cannot complete the end-to-end vertical slice, pilot dates slip, and every downstream school conversation becomes "come back when the data is real."
- Likelihood (1-5): `4` because the critical path already shows school permission, privacy approval, and data mapping as the first blockers.
- Impact (1-5 by runway): `4`
- Mitigation: put the 3 required fields and weekly delivery cadence into the pilot agreement; narrow the first deployment to `1 school / 1 grade / 3 mandatory fields`; maintain a CSV or scheduled file-drop fallback so the pilot does not depend on perfect API access.

RISK 4: Integration Services Trap
- Type: Vendor
- If: each target school uses a different LMS/SIS schema and event model / Then: the 5-person team turns into a custom integration shop instead of a product company.
- Leading to: `4 months of runway` because roadmap time moves from insight quality and parent activation into one-off mappings, bug fixes, and school-specific connector work.
- Likelihood (1-5): `3` because the roadmap already assumes deeper `read-only LMS/SIS integration + event sync`, which usually fragments fast across schools.
- Impact (1-5 by runway): `4`
- Mitigation: define one canonical internal event schema and refuse school-specific logic outside that schema; support only one live adapter plus one file-import path until pilots renew; treat non-standard integrations as deferred scope rather than "small favors" during pilot sales.

RISK 5: OpenAI Rate-Limit Stall
- Type: Vendor
- If: OpenAI org or project rate limits are hit during grading-update bursts / Then: insight generation queues up, notifications arrive late, and the "near real-time" promise breaks when parents most expect it to work.
- Leading to: `2 months of runway` because the team spends weeks firefighting latency, re-queuing jobs, and manually re-sending critical insights during pilot windows.
- Likelihood (1-5): `3` because OpenAI rate limits vary by project, tier, and model, and this product depends on short-turnaround parent-facing sends rather than overnight batch work.
- Impact (1-5 by runway): `2`
- Mitigation: add queueing with backoff and freshness timeouts so stale insights are dropped instead of sent late; keep a rule-based/template-only mode for the top 5 insight types; monitor request and token headroom daily during pilots and cap concurrency before schools go live.

RISK 6: OpenAI Cost Creep
- Type: Vendor
- If: prompts grow, retries rise, or comment context expands beyond the base-case assumption / Then: API cost per customer overshoots the model and gross margin deteriorates before the company has real retention proof.
- Leading to: `3 months of runway` because the startup either absorbs the overage at pilot scale or cuts corners on quality right when it needs trust most.
- Likelihood (1-5): `3` because the finance model assumes `300,000 VND` API cost per customer per month in the base case, and prompt sprawl is common once real school comments appear.
- Impact (1-5 by runway): `3`
- Mitigation: use deterministic rules to decide whether an insight should exist before any LLM call; cap raw teacher-comment length and summarize input before generation; review per-school token spend weekly against a hard budget and freeze prompt changes that raise cost without improving action rate.

RISK 7: OpenAI Policy Whiplash
- Type: Vendor
- If: OpenAI policy or school procurement interprets parent-facing educational insights as too close to high-stakes automation without enough human review / Then: the current flow has to be rewritten, approval is delayed, or the school demands manual review on sensitive cases.
- Leading to: `4 months of runway` because the team must redesign workflows, reword claims, and possibly shift from auto-send to reviewed-send while pilots are already in motion.
- Likelihood (1-5): `3` because OpenAI's current usage policies already restrict automation of high-stakes decisions in sensitive areas including education without human review.
- Impact (1-5 by runway): `4`
- Mitigation: frame outputs as advisory summaries, never determinations about a child; require manual review or template-only sends for severe negative cases; keep a no-LLM path for every parent-facing message that touches sensitive academic judgment.

RISK 8: Teacher-Comment Prompt Injection
- Type: Reputational
- If: a free-text teacher comment or imported LMS note contains instruction-like or malformed text / Then: the model outputs something unprofessional, manipulative, or plainly off-policy to a parent, and screenshots spread through school parent groups.
- Leading to: `4 months of runway` because one ugly screenshot is enough for a principal to freeze the pilot while the team investigates logging, prompts, and message safety.
- Likelihood (1-5): `3` because School Assistant plans to transform raw teacher text into parent-facing wording, which creates a real injection surface even without a public chatbot.
- Impact (1-5 by runway): `4`
- Mitigation: treat teacher comments as quoted data only and hard-delimit them in prompts; run output linting that blocks unusual commands, URLs, or identity-shifting language before send; force template-only generation whenever a source comment trips an injection heuristic.

RISK 9: Child-Data Compliance Stop Order
- Type: Regulatory
- If: the startup cannot show valid child-data consent, cross-border processing clarity, deletion and withdrawal handling, and human-oversight logs / Then: a school counsel, regulator, or procurement review blocks or suspends the pilot.
- Leading to: `7 months of runway` because this does not just hurt one feature; it freezes access to real student data, delays every school deal, and can force a full compliance rebuild before revenue proof exists.
- Likelihood (1-5): `3` because the product handles child academic data, Vietnam's Decree `13/2023/ND-CP` already imposes explicit child-consent and breach-notice duties, and Vietnam's AI law now adds risk-based oversight expectations.
- Impact (1-5 by runway): `5`
- Mitigation: ship a founder-owned consent and data-flow pack before the first live pilot; minimize what is sent to external model APIs and keep a deletion and withdrawal workflow that can be executed in one day; log every parent-facing generation with source fields, model path, and fallback reason so the company can answer school audits quickly.

RISK 10: Founder Single-Thread Failure
- Type: Founder-bandwidth
- If: one founder is the only person who understands school relationships, consent scope, prompt thresholds, and incident response / Then: any illness, travel, or parallel fundraising sprint slows containment right when a pilot issue hits.
- Leading to: `3 months of runway` because pilot response time stretches, school confidence drops, and the rest of the team waits for one person to make product, legal, and customer calls.
- Likelihood (1-5): `4` because a 5-person seed team almost always has at least one hidden single point of failure, and this startup's trust layer spans sales, product, data, and compliance at once.
- Impact (1-5 by runway): `3`
- Mitigation: write a one-page pilot runbook covering data source, send rules, kill switches, and school contacts; assign one backup owner for each of incident response, school communication, and prompt changes; rehearse one tabletop incident before the first live parent send.
