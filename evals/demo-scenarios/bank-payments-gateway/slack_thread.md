# #payments-gateway-modernization (Slack export, 2026-06-09 to 2026-06-11)

**Dave Okafor** (PM) — 2026-06-09 08:31
Morning all — steering committee prep. Quick pulse check: are we still green for November 20?

**Marcus Webb** (Eng Lead, message-translation layer) — 2026-06-09 08:34
Yep, on track. Team's moving well, no major blockers on our side.

**Sarah Kim** (QA Lead) — 2026-06-09 08:52
@Marcus wait, I want to flag something before this goes into the steering deck. Current SIT pass
rate on the ISO 20022 field-mapping test suite is 61%. We've had 14 failed test cases for two
weeks now on the remittance-info truncation edge case — nobody's picked up the defect tickets.
That doesn't feel like "on track" to me, more like "in progress with real open risk."

**Marcus Webb** — 2026-06-09 09:10
Those are known issues, we'll get to them. I wouldn't call it a blocker yet.

**Sarah Kim** — 2026-06-09 09:14
14 failing cases on a regulatory field-mapping suite two weeks running, with the SIT environment
itself unstable per Apex, feels like it should at least be a documented risk, not "no major
blockers." I don't want to be the one explaining in October why nobody flagged this in June.

**Priti Shah** (Retail Payments Product) — 2026-06-10 14:02
Hey team — while I have you, can we also slot in support for the new instant-refund reporting
field the retail team asked for last month? Shouldn't be a big lift since you're already touching
the message-mapping layer for ISO 20022. Would love to get it in before November if possible.

**Dave Okafor** — 2026-06-10 14:20
@Priti Can you send that as a written request? Want to make sure it goes through proper review
before anything gets added to the build.

**Priti Shah** — 2026-06-10 14:22
Sure, will do — but flagging now so it's on the radar, since I know timelines are tight.

**Marcus Webb** — 2026-06-11 09:47
FYI Apex says 2 of their senior engineers roll off June 30 unless we extend. Also heads up their
SIT access has been flaky, might explain some of the failed test runs Sarah mentioned.
