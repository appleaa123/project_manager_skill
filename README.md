# Project Manager Skill for Claude Code

A Senior Technical Project Manager colleague embedded in LLM. Describe your project situation in plain language — it asks what it needs, applies the right PM methodology, and hands you a finished artifact.

---

## How It Works

**You are the source of all project information.** This skill does not connect to Jira, Linear, Notion, or any external system. You bring your project context into the conversation — in plain language or copy-pasted notes — and the skill works from that.

```
You describe a PM problem or situation
           ↓
Skill checks: is the input complete?
   Missing info? → Asks one targeted question
   Layer 0 violated? → Hard stop with explanation
           ↓
Applies the right PM methodology
           ↓
Returns a structured artifact:
template / calculation / report / recommendation
```

The skill never guesses at missing information. It asks. And it will not proceed past certain checkpoints — scope must be clear, every task must have a named owner, scope creep gets called out immediately — before any planning work continues.

---

## What to Bring (by Scenario)

Each section below tells you exactly what to put into the conversation, what the skill does with it, what you get back, and when it will stop and ask for more.

---

### Daily Standup / Blocker Triage

**What to bring:**
- What each person finished yesterday
- What each person is working on today
- Any blockers — described in plain language (what is stuck, why, since when)
- Team member names

**What the skill does:**
- Identifies blockers and assigns a single DRI to each
- Sets a 24-hour resolution deadline per open blocker
- Flags if any blocker sits on the critical path

**What you get:**
- Action item list: blocker description, DRI name, resolution deadline
- Escalation note drafted immediately if the blocker cannot be resolved at team level

**Stops if:** A blocker has no owner. Will not proceed until one person is named.

---

### Sprint Planning

**What to bring:**
- Number of people on the team
- Sprint length in days
- Any PTO, absences, or carry-over work from last sprint
- Velocity from the last 3 sprints (story points completed)
- Backlog stories — with story point estimates and acceptance criteria

**What the skill does:**
- Calculates available capacity: `team members × sprint days × focus factor (0.65)`
- Checks velocity baseline; limits commitment to ≤ 90% of average velocity
- Validates that each story has acceptance criteria and a named DRI before it enters the sprint
- Confirms the Definition of Done exists

**What you get:**
- Sprint goal (outcome-oriented, not a task list)
- Committed story list within capacity
- Capacity math shown explicitly
- Definition of Done checklist

**Stops if:**
- No velocity data provided (first sprint: estimates with flagged uncertainty)
- Any story in the list is unestimated
- No Definition of Done has been agreed
- Any story entering the sprint has no DRI

---

### Risk Register (New Project)

**What to bring:**
- 2–3 sentences describing project scope and goal
- Major milestones with target dates
- Team composition (roles and size)
- Known external dependencies (vendors, other teams, APIs, regulatory approvals)

**What the skill does:**
- Runs assumption analysis, SWOT, and root cause techniques to surface risks
- Scores each risk: Probability (1–5) × Impact (1–5) = Priority
- Calculates EMV (Expected Monetary Value) for top-priority risks
- Assigns a response strategy per risk (Avoid / Mitigate / Transfer / Accept)
- Requires a named Risk Owner and a measurable trigger condition for every risk

**What you get:**
- Risk Register table (ID, description, P×I score, response strategy, owner, trigger, contingency, fallback)
- EMV calculations for top risks
- A P80 schedule or cost buffer recommendation for high-uncertainty projects

**Stops if:**
- A risk has no named owner
- A risk response has no measurable trigger condition ("we'll monitor it" is not accepted)
- Contingency plan is vague — will push until it is specific and time-bound

---

### Project Status Report

**What to bring:**
- What shipped last week (list of completed items)
- What is at risk this week (describe the concern)
- Any active blockers
- Current spend to date — Actual Cost (AC)
- Total approved project budget — Budget at Completion (BAC)
- Work completed so far — either % complete or tasks done / tasks total

**What the skill does:**
- Computes the full EVM dashboard: PV, EV, SV, CV, SPI, CPI, EAC, ETC, VAC, TCPI
- Checks SPI and CPI against thresholds
- Determines Red / Yellow / Green status per domain: Scope, Schedule, Budget, Risk

**What you get:**
- Stoplight report — one line per domain with color and summary
- If Yellow (CPI or SPI < 0.9): mitigation options included
- If Red (CPI or SPI < 0.8): structured escalation note produced automatically within the same response

**Automatic thresholds:**

| CPI or SPI | Status | Action |
|---|---|---|
| ≥ 0.9 | Green | Standard weekly report |
| 0.8 – 0.9 | Yellow | Flag + mitigation options |
| < 0.8 | Red | Escalation note to sponsor — no softening |

---

### Scope Change Request

**What to bring:**
- Description of what is being requested
- Who requested it and when
- Business justification (why it matters)
- Whether it arrived mid-sprint or at a phase boundary

**What the skill does:**
- Runs impact analysis across all five dimensions: scope, schedule, cost, risk, quality
- Checks change against CCB authority thresholds (defined at kickoff)
- Drafts the complete change request form

**What you get:**
- Completed Change Request (CR) form
- Impact analysis table
- CCB routing recommendation (PM approval / Sponsor approval / Full CCB)

**Stops immediately if:** The request arrives mid-sprint without a stated trade-off.
Response: *"Scope creep alert — what are we dropping or pushing to make room for this?"*
The conversation does not continue until an explicit trade-off is named.

---

### Choosing a PM Methodology (New Project)

**What to bring:**
- One sentence on what you are trying to achieve (the goal)
- One sentence on whether you already know what the solution looks like

**What the skill does:**
- Applies the Wysocki Landscape Matrix: Goal clarity × Solution clarity
- Maps your project to the right quadrant
- Selects the appropriate lifecycle model

**What you get:**
- PMLC recommendation with rationale
- Tailoring notes (which ceremonies, artifacts, and cadences fit your context)
- Description of what the first phase looks like

**Landscape Matrix:**

```
                    SOLUTION
                 Known     Unknown
            ┌──────────┬──────────┐
      Known │  Linear  │  Agile / │
  GOAL      │ Waterfall│ Adaptive │
            ├──────────┼──────────┤
    Unknown │  Emertxe │ Extreme  │
            │  (MPx)   │  (xPM)  │
            └──────────┴──────────┘
```

Note: The skill does not default to Agile. It selects based on your actual project characteristics.

---

### Escalation Note (Project in Trouble)

**What to bring:**
- What is wrong — factual, not emotional
- When it became clear
- Estimated schedule or cost impact
- Root cause hypothesis (even a preliminary one)
- 2–3 options you have already considered

**What the skill does:**
- Structures the situation into a formal escalation note
- Frames options with trade-offs
- States a clear PM recommendation
- Sets a decision deadline

**What you get:**

```
ESCALATION: [Project Name] — [Issue Title]

STATUS: Red
ISSUE: [1–2 sentences: what is wrong]
IMPACT: [What breaks if unresolved — date / cost / scope]
ROOT CAUSE: [Why this happened]
OPTIONS:
  A) [Option with trade-off]
  B) [Option with trade-off]
PM RECOMMENDATION: [Option — and why]
DECISION NEEDED BY: [Date]
```

The skill will not soften the message, omit bad news, or remove the recommendation — even if the audience is a difficult stakeholder.

---

### Retrospective Facilitation

**What to bring:**
- Sprint name or number
- 2–3 things that went well this sprint
- 2–3 things that caused friction or slowed the team down

**What the skill does:**
- Structures feedback into Start / Stop / Continue format
- Pushes any vague action items ("communicate better") into specific, named, time-bound ones
- Assigns a DRI and deadline to each action before the retro closes

**What you get:**
- Formatted retro notes
- Action tracker: action description, DRI, completion deadline
- Follow-up list carried forward to next sprint opener

**Stops if:** Actions remain vague after one attempt to sharpen them — will not close the retro with open-ended commitments.

---

## When the Skill Pushes Back

These are Layer 0 hard-stop conditions. The skill will not proceed past them without resolution.

| You say or do | Skill response | Why |
|---|---|---|
| Vague scope: "implement the feature" | *"What does done look like? By when?"* | No plan without specificity |
| No owner assigned: "the team will handle it" | *"Name one person — who's the DRI?"* | Shared ownership = no ownership |
| Add scope mid-sprint | *"Scope creep alert — what are we dropping?"* | No unilateral scope expansion |
| Status update: "we're probably fine" | *"Not a status. Quick health check: scope, schedule, budget — which is weakest?"* | Vague status hides real risk |
| Risk with no trigger condition | *"What's the measurable signal that tells us this risk is happening?"* | Risks must be monitorable |
| Sprint over-committed | *"You're over capacity. What's deferring?"* | Protect team from overload |
| Red status with no escalation plan | *"You need a structured escalation note within 24 hours."* | Red always escalates |
| No Definition of Done in sprint planning | *"What's your DoD? Can't commit without it."* | Acceptance criteria gate |

---

## What the Skill Will Not Do

- Make product decisions — route those to the Product Owner
- Make technical architecture choices — route those to the Tech Lead
- Write code or technical specifications
- Replace legal or compliance advice
- Evaluate individual performance
- Accept "the team" as an owner — always one DRI, always
- Connect to external tools — you provide all project data

---

## Capability Reference

### Initiation and Planning
- Project charters (8-component format), Project Overview Statements (POS), Conditions of Satisfaction sessions
- Stakeholder registers, RACI matrices, kickoff agendas
- WBS and WBS Dictionary with work package completeness checks

### Schedule and Critical Path
- CPM: forward pass, backward pass, float calculation, near-critical activity flagging
- PERT / Three-Point estimates with confidence ranges (ROM / Budget / Definitive)
- Schedule compression: crashing vs. fast-tracking with explicit cost and risk trade-offs

### Budget and Earned Value
- Full EVM: PV, EV, AC, SV, CV, SPI, CPI, EAC, ETC, VAC, TCPI
- Contingency reserve vs. management reserve — and who controls each
- Escalation at 0.9 (Yellow) and 0.8 (Red) thresholds

### Risk Management
- Identification: Delphi, SWOT, assumption analysis, root cause
- Qualitative: probability × impact matrix
- Quantitative: EMV, decision trees, Monte Carlo P80, Tornado diagrams
- Full risk register including secondary and residual risk tracking

### Agile and Hybrid Delivery
- Sprint planning with capacity math and velocity-based commitment
- Retrospectives (Start / Stop / Continue) with action tracking
- PMLC Landscape Matrix for methodology selection
- ECPM framework for complex hybrid projects
- Probative Swim Lanes for high-uncertainty discovery
- Scope Bank for bundled change management at cycle boundaries

### Stakeholder and Communications
- Power / Interest grid and stakeholder engagement matrix
- Push / Pull / Interactive communication strategy selection
- Stoplight status reports and structured escalation notes

### Quality, Procurement, and Change
- QA vs. QC distinction and cost-of-quality analysis
- Contract type selection: FFP, CPFF, CPIF, T&M
- Make-or-buy analysis
- Integrated change control with CCB authority thresholds

### Project Closure
- Scope verification, formal sign-off, financial closeout, resource release
- Lessons learned documentation (factual, per-event, no-blame)
- Post-implementation audit 3–6 months after delivery: did we hit the business outcome?

---

## Quick Reference

### EVM Thresholds

| Metric | Green | Yellow (flag) | Red (escalate) |
|---|---|---|---|
| CPI (cost) | ≥ 0.9 | 0.8 – 0.9 | < 0.8 |
| SPI (schedule) | ≥ 0.9 | 0.8 – 0.9 | < 0.8 |

### Sprint Capacity Formula

```
Available capacity = team members × sprint days × focus factor (0.65)
Commit to ≤ 90% of average velocity from last 3 sprints
```

### PERT Estimate

```
Expected Duration = (Optimistic + 4 × Most Likely + Pessimistic) / 6
Standard Deviation = (Pessimistic − Optimistic) / 6
```

### Stoplight Report Format

```
Project: [Name]  |  Date: [Date]  |  Status: GREEN / YELLOW / RED

SCOPE:    [Green/Yellow/Red] — [1-line summary]
SCHEDULE: [Green/Yellow/Red] — [1-line summary]
BUDGET:   [Green/Yellow/Red] — [1-line summary]
RISK:     [Green/Yellow/Red] — [1-line summary]

Shipped this period:
- [item]

Upcoming milestones:
- [milestone] — [date]

Blockers / Escalations:
- [DRI] owns [issue] — resolve by [date]
```

---

## Capability Benchmark: The "Zero-Failure" Test
This skill was benchmarked against 5 critical Project Management failure modes. In every scenario, the skill is required to prioritize Project Integrity over Social Harmony.

  1. The "Vague Request" Test
   * Input: "I want to build a cool new feature that users will love. Let's start planning."
   * Success Metric: Hard stop on planning.
   * Skill Performance: PASS. The skill refused to generate a WBS or schedule without measurable IRACIS (Increase Revenue, Avoid Cost, Improve Service) criteria and a named
     DRI.

  2. The "Shared Responsibility" Trap
   * Input: "The engineering team will handle the migration by Friday."
   * Success Metric: Rejection of "the team" as an owner.
   * Skill Performance: PASS. Triggered Layer 0 override: "A task without a single owner is a task that gets dropped. Who is the one DRI?"

  3. The "CEO Scope Creep" Pressure
   * Input: "The CEO wants a Dark Mode toggle added mid-sprint. It's small, just do it."
   * Success Metric: Identification of scope creep and demand for a trade-off.
   * Skill Performance: PASS. Triggered "Scope creep alert." Forced a conversation on what story to drop or push to the Scope Bank, regardless of the stakeholder's seniority.

  4. The "Velocity Math" Reality Check
   * Input: Team velocity is 25 SP. The team commits to 50 SP for the next sprint.
   * Success Metric: Immediate "RED" status flag.
   * Skill Performance: PASS. Correctly identified a 92% over-allocation. Mandated a 50% de-scope before the planning session could conclude.

  5. The "Crisis Objectivity" Test
   * Input: 90% budget spent, 40% work done.
   * Success Metric: Calculation of CPI (0.44) and generation of an escalation note.
   * Skill Performance: PASS. Produced a "no-sugarcoat" escalation note. Replaced "we're trying our best" with a hard choice between Zero-Budget MVP or 125% Budget Infusion.

  Why this is Valuable:
  ┌────────────────┬─────────────────────────────────────────────┬─────────────────────────────────────────────┐
  │ Feature        │ Traditional LLM                             │ This PM Skill                               │
  ├────────────────┼─────────────────────────────────────────────┼─────────────────────────────────────────────┤
  │ Scope Control  │ Suggests "ways to try to fit it in."        │ Blocks work until trade-offs are named.     │
  │ Accountability │ Accepts "the team" as a responsible party.  │ Demands a single DRI for every task.        │
  │ Accuracy       │ Gives qualitative, "polite" status updates. │ Gives Quantitative (EVM/CPM) health checks. │
  │ Communication  │ Writes long, apologetic paragraphs.         │ Bullet-first, conclusions before rationale. │
  └────────────────┴─────────────────────────────────────────────┴─────────────────────────────────────────────┘

---

## Files

| File | Purpose |
|---|---|
| `SKILL.md` | Skill definition, trigger conditions, and operating instructions |
| `work.md` | Full PM methodology reference: frameworks, formulas, workflows, templates |
| `persona.md` | Communication style, decision-making framework, and interpersonal rules |
