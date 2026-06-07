# Scheduled task prompts that work

*Six tested prompts from the [Claude Cowork setup guide for small business](../README.md). Each follows the same pattern: scoped inputs, a dated output file, and explicit boundaries. Prove every task interactively before scheduling it ([how scheduled tasks work](https://support.claude.com/en/articles/13854387)).*

## 1. Monday morning brief (weekly, Monday 7:00)

> Read 1-clients/ and 2-finance/, check my calendar and email via connectors. Produce `0-inbox/YYYY-MM-DD-monday-brief.md`: cash position from invoices vs bills, this week's calendar commitments, top 3 things needing my attention, anything overdue (invoices, replies, deliverables). Plain English, under one page. Do not send anything.

## 2. Invoice follow-up drafts (weekdays, 8:00)

> Check 2-finance/invoices-out/ against payment records. For invoices 14+ days overdue, draft a reminder email matched to the customer's history — gentle for first-time or reliable customers, firmer for repeat late payers. Save each as a draft file in `0-inbox/` named YYYY-MM-DD-reminder-<customer>.md. Never send. If nothing is overdue, write a one-line no-op note in the same file pattern.

## 3. Inbox triage (weekdays, 7:30)

> Read unread email from the last 24 hours via the connector. Produce `0-inbox/YYYY-MM-DD-inbox-triage.md` with three lists: needs my reply today (with a 1-line suggested angle each), can wait, ignore/unsubscribe candidates. Draft nothing unless I ask. Flag anything that looks like an invoice, a complaint, or a legal notice at the top.

## 4. CRM hygiene sweep (weekly, Friday 16:00)

> Via the CRM connector, list deals/contacts with no activity in 14+ days, missing next steps, or past-due close dates. Produce `0-inbox/YYYY-MM-DD-crm-hygiene.md` with a suggested next action per item. Make no changes to CRM records — report only.

## 5. Content queue check (weekly, Tuesday 9:00)

> Read 3-marketing/content-queue/. Produce `0-inbox/YYYY-MM-DD-content-status.md`: what is drafted and ready for review, what is scheduled this week, gaps in the next 2 weeks, and 3 topical suggestions based on what customers asked about recently (from inbox triage outputs). Publish nothing.

## 6. Weekly money close (weekly, Friday 17:00)

> From 2-finance/ and the accounting connector: invoices sent this week, payments received, bills due in the next 14 days, and a simple cash position. Produce `0-inbox/YYYY-MM-DD-weekly-close.md`. Flag anything anomalous (duplicate bill, unusually large invoice, customer paying in parts) rather than interpreting it.

## The pattern behind all six

1. **Scoped inputs** — named folders and connectors, nothing open-ended.
2. **Dated output file** — a silent failure becomes visible by the missing file.
3. **Explicit boundaries** — "never send", "report only", "publish nothing".
4. **No-op handling** — the task says what to do when there is nothing to do.
5. **One owner per task** — recorded in your [context file](context-file-template.md) register.
