# Law firm operations: calendar, docketing and EBT clerk

**Project context:** Litigation OS aims to automate recurring firm operations through a unified interface. These are **workflow definitions and research notes**, not claims that any existing single product implements every step.

## What the clerk does

In New York litigation **EBT = Examination Before Trial**, commonly called a **deposition** elsewhere.

| Function | Representative work | Inputs | Outputs |
|---|---|---|---|
| Litigation calendar | Schedule appearances, conferences, motion returns, trials and appointments; detect conflicts | Orders, notices, counsel schedules | Master matter calendar, alerts |
| Docketing | Log filings, court orders, deadlines, adjournments; reconcile court activity with internal docket | NYSCEF/eTrack, docket entries, emails, firm documents | Updated matter register; verified deadline events |
| EBT coordination | Propose dates, schedule parties, witnesses, court reporters and interpreters, reserve location/remote link | Counsel availability, deposition notices, orders | Confirmations, deposition notices, reminders |
| EBT follow-up | Track transcripts, errata, exhibits, objections, follow-on deadlines | Reporter delivery, transcripts | Tasks and evidence references |
| Attorney assistance | Generate routine confirmations and draft forms, escalate ambiguities | Case matter and approved templates | Reviewable draft documents |
| Reporting | Deadline calendars, attorney workloads and exceptions | Approved matter events | Reports and escalations |

## High-level clerk flow

1. Inbound court filing / electronic notice / email arrives.
2. Match its court, index/docket number, caption and parties to exactly one matter; send uncertain matches to review.
3. Identify event type(s), dates, ordered obligations, parties, source document and provenance.
4. **Do not equate any date in a document with a verified legal deadline.** Classify court-ordered, rule-calculated, negotiated, calendar event or internal reminder.
5. Compute legal due dates with applicable **court rule, trigger event, service method, calendar-day vs business-day logic, holidays, extensions, exceptions and court-specific order**.
6. Review rule calculations and source documents; record approver and version.
7. Update matter docket / attorney calendars / reminders only after the required verification.
8. For EBTs: coordinate witnesses, opposing counsel, attorney, reporter, video and location; send appropriate reviewed notices and confirmations.
9. Watch for superseding orders, adjournments, cancellations and rescheduled EBTs; link old/new event history rather than overwriting source history.
10. Track the transcript and subsequent tasks.

## Drafting opportunities tied to events

- EBT date proposed → draft confirmation correspondence.
- EBT agreed / ordered → prepare notice of examination before trial, caption and service details for approval.
- Discovery served → generate response checklist, proposed responses and objections for attorney review.
- Stipulation reached → prepare structured stipulation/letter from approved form.
- Court order received → prepare summary, attorney checklist and calendar events.
- Motion assigned → assemble a draft motion packet with referenced records, forms and verified citations.

## Additional firm-wide operational modules

Client intake and conflicts; case opening and assignment; client communications; document and matter search; email/file routing; timekeeping; invoicing; trust accounting; e-signatures; discovery intake and productions; research; attorney review; settlement administration; case closure; workload and audit reporting.

## Risk and approval controls

- Attorney-supervised drafting and strategic decisions.
- Matter-level authorization and privilege/confidentiality controls.
- Deadlines require source attachment, originating rule/order, change log and second review policy as appropriate.
- Courts' public browsing/search pages are not unrestricted filing APIs.
- Keep original source files; drafts must not be silently finalized or served.
- Plan for fallback alerts, human acknowledgment, retries, idempotency and audit logs.

## NY-specific references

- [NYSCEF](https://iapps.courts.state.ny.us/nyscef/) — NY electronic filing.
- [New York eCourts](https://iapps.courts.state.ny.us/webcivil/ecourtsMain) — court information interfaces.
- [N.Y. CPLR 3107](https://www.nysenate.gov/legislation/laws/CVP/3107) — deposition notices; scope depends on courts/orders and statutory exceptions.
- [New York Court Rules](https://www.nycourts.gov/rules/) — official rule entry point.

## Research examples: commercially available clerk tooling

- [CourtAlert](https://www.courtalert.com/) — court alerting / docketing.
- [CourtDrive](https://www.courtdrive.com/) — legal notices and calendar workflows.
- [LawToolBox](https://lawtoolbox.com/) — rules-based deadline calculation.
- [CalendarRules](https://www.calendarrules.com/) — court rule calendar software.
- [Filevine](https://www.filevine.com/) — litigation case workflow.
- [Clio](https://www.clio.com/) — multi-module practice management.

The owner has **not selected** any of these commercial products as required dependencies. They serve as functional benchmarks and possible integrations.
