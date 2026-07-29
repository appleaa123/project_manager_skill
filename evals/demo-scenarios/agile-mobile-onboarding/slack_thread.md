# #onboarding-redesign (Slack export, 2026-06-11 to 2026-06-13)

**Sam Patel** (PM) — 2026-06-11 09:02
Morning team, day 8 of the sprint. How's everyone tracking against the sprint goal (ship v1 of the
new onboarding flow to internal beta by Friday)?

**Raj Malhotra** (Eng) — 2026-06-11 09:05
Basically done on my end. Screens 1-4 are wired up, just some polish left.

**Priya Lin** (Eng) — 2026-06-11 09:20
I wouldn't say basically done — the account-linking screen (screen 2) still throws an error on the
sandbox bank integration about 1 in 5 times. Haven't root-caused it yet. Also we haven't touched
the analytics events for the new flow at all.

**Raj Malhotra** — 2026-06-11 09:24
Fair, I meant the UI is basically done. Backend's got some rough edges still.

**Sam Patel** — 2026-06-11 09:30
Can someone demo current state in standup tomorrow? Want to see it working, not just hear "mostly
there."

**Priya Lin** — 2026-06-12 11:47
FYI saw Lena's research email — the confusion on screen 2 ordering is a real pattern, not a fluke.
2 of 8 dropped off exactly there in testing.

**Raj Malhotra** — 2026-06-12 11:52
If we reorder screens 2/3 that's more than "polish," that's rework on navigation logic we already
built. Worth talking about before we just replan mid-sprint.

**Jordan Reyes** — 2026-06-12 16:10
Hey all, since you're already touching the flow — any chance the referral-code screen I emailed
Sam about could slot in too? Would love to not wait for the next sprint if possible 🙏

**Priya Lin** — 2026-06-12 16:15
We haven't even resolved the screen-2 reorder question or the sandbox error yet, that feels like a
lot to add on top this sprint.

**Sam Patel** — 2026-06-13 08:15
Agreed, let's not decide any of this in Slack threads. Also — quick note, nobody's picked up the
"analytics events for new flow" backlog item from planning, it's still unassigned. Same with the
API-versioning spike from last retro, still nobody owns it either.

**Raj Malhotra** — 2026-06-13 08:20
Yeah that spike's been sitting for 2 sprints now, keeps falling through the cracks.
