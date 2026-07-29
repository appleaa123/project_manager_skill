# Payments Gateway Modernization — Steering Committee Notes

**Date:** 2026-06-05
**Attendees:** Angela Cho (Sponsor), Dave Okafor (PM), Marcus Webb (Eng Lead), Priya Nandakumar
(Compliance), Tom Reilly (Apex Integrators, dial-in)
**Regulatory driver:** ISO 20022 correspondent-messaging cutover — scheme-mandated, **November 20,
2026**, no extension mechanism.

## Decisions
1. Confirmed scope baseline: message-translation layer, reconciliation reporting, and
   sanctions-screening interface. No new scope added since program kickoff.
2. Approved Apex's Q2 invoice (within approved budget at time of approval).
3. Agreed to escalate the SIT environment firewall change request to the internal Infra team's
   director if not resolved by June 12 (raised by Tom Reilly / Apex).

## Status reported at meeting
- Engineering: "Development substantially complete, testing progressing, on track for November."
- QA: not present at this meeting; status relayed secondhand by Marcus Webb.
- Budget: tracking within approved baseline (per Marcus's verbal update; Finance's own numbers
  were not reconciled at this meeting).

## Risks discussed
- **R-014 (raised by Tom Reilly):** Apex staffing risk — two senior integration engineers are
  contracted through June 30 only; no formal change order yet in place to extend them past that
  date. Owner: Dave Okafor. Status: Open, no response strategy selected yet.
- **R-009:** Subcontractor (Apex) environment access dependency on internal Infra team's change
  process. Owner: Marcus Webb. Status: Open.

## Action items
| # | Action | Owner | Due |
|---|---|---|---|
| 1 | Escalate SIT firewall CR to Infra Director | Marcus Webb | 2026-06-12 |
| 2 | Confirm Apex staffing extension decision | Dave Okafor | 2026-06-20 |
| 3 | Reconcile program budget against Finance's numbers | Dave Okafor | 2026-06-15 |
| 4 | Bring current SIT/UAT test pass-rate data to next steering committee | Marcus Webb | Next mtg |

## Next steering committee: 2026-06-19
