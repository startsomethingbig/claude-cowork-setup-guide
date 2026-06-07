# Claude Cowork setup guide for small business

**A step-by-step guide to setting up Claude Cowork for a small business: folder design, plugins, connectors, your first working workflows, scheduled tasks, and the guardrails that keep it safe.**

Claude Cowork is the agentic mode of the Claude desktop app. Instead of answering one prompt at a time, Claude takes on whole tasks: it works with files in folders you grant it, connects to your email, calendar, accounting and CRM tools, runs multi-step workflows, and executes scheduled tasks automatically. Out of the box, though, it is an empty desk. This guide turns it into a working part of your business.

> Maintained by [Automata AI](https://www.automataai.com.au/claude-cowork-setup?utm_source=github&utm_medium=readme&utm_campaign=cowork-guide), a Sydney-based Claude consultancy. We run our own business on Cowork — content pipeline, CRM, filing, reporting — and this guide is the setup we use ourselves.

**Last updated: 8 June 2026 · Tested with Claude desktop app (Cowork GA release, April 2026 onward)**

---

## Contents

1. [Who this guide is for](#who-this-guide-is-for)
2. [What you need before starting](#what-you-need-before-starting)
3. [Step 1 — Design your folders before anything else](#step-1--design-your-folders-before-anything-else)
4. [Step 2 — Write your business context file](#step-2--write-your-business-context-file)
5. [Step 3 — Connect your tools](#step-3--connect-your-tools)
6. [Step 4 — Install plugins and skills](#step-4--install-plugins-and-skills)
7. [Step 5 — Build your first two workflows](#step-5--build-your-first-two-workflows)
8. [Step 6 — Set up scheduled tasks](#step-6--set-up-scheduled-tasks)
9. [Step 7 — Put your guardrails in writing](#step-7--put-your-guardrails-in-writing)
10. [Multi-person setups without Enterprise](#multi-person-setups-without-enterprise)
11. [Usage limits and cost budgeting](#usage-limits-and-cost-budgeting)
12. [Keeping your setup healthy](#keeping-your-setup-healthy)
13. [Troubleshooting and failure modes](#troubleshooting-and-failure-modes)
14. [FAQ](#faq)

---

## Who this guide is for

Small business owners and operators (roughly 1 to 20 people) who want Claude Cowork doing real work: the Monday brief, invoice chasing, inbox triage, CRM upkeep, report production. You do not need technical skills or an IT department. If you run a larger team with Enterprise role-based access controls, Anthropic's [Team and Enterprise Cowork documentation](https://support.claude.com/en/articles/13455879) covers what this guide does not.

## What you need before starting

- **The Claude desktop app** on macOS or Windows. Cowork is not available on the web or mobile, although on Pro and Max plans you can [assign tasks from your phone](https://support.claude.com/en/articles/13947068) to a running desktop session.
- **Any paid Claude plan.** Since 9 April 2026, Cowork is included on Pro, Max, Team and Enterprise ([release notes](https://support.claude.com/en/articles/12138966-release-notes)). Pro is US$20/month (US$17/month billed annually); Team standard seats are US$25/month or US$20/month annually. In Australia expect roughly A$30–35 per user per month — confirm the exact figure in your billing screen, as Anthropic does not publish AUD pricing on a public page.
- **An internet connection throughout, and a computer that stays awake.** Cowork sessions stop if the app closes or the computer sleeps, per Anthropic's [getting started guide](https://support.claude.com/en/articles/13345190-get-started-with-claude-cowork).
- **Access to the tools you want connected** — your email, calendar, accounting software, CRM.

One fact worth being clear about, because several popular guides get it wrong: Cowork does not "run locally so your data stays private". Your prompts and granted files are processed on Anthropic's servers. What is true: on Team and Enterprise plans Anthropic does not train models on your data by default, and on Pro and Max you can opt out ([pricing page](https://claude.com/pricing), [regional compliance](https://claude.com/regional-compliance)). Plan accordingly rather than comfortably.

## Step 1 — Design your folders before anything else

Cowork acts on real files in folders you grant it. The folder design IS the safety model: what Claude can reach defines what can go wrong. Design it before Claude touches anything.

Principles that hold for every business type:

- **One dedicated workspace folder.** Never grant your whole Documents folder, desktop, or a drive root.
- **Exclude by default.** Payroll, HR records, anything with customer identity documents, and credentials never enter the granted folder. If Claude should not read it, it should not be reachable.
- **Mirror your business functions, not your file history.** A clean small-business taxonomy beats ten years of accumulated folders.

A worked starting point (full versions per business type in [templates/folder-structure.md](templates/folder-structure.md)):

```
cowork-workspace/
├── 0-inbox/          # drop zone: things for Claude to process
├── 1-clients/        # one folder per active client/job
├── 2-finance/        # invoices out, bills in — NOT payroll
├── 3-marketing/      # content, social, website copy
├── 4-operations/     # SOPs, templates, checklists
└── 9-archive/        # completed work, read-mostly
```

When you grant the folder, Cowork asks for permission and offers two modes: "Ask before acting" and "Act without asking". Start with ask-first; deletion always requires approval in both modes ([Anthropic safety guidance](https://support.claude.com/en/articles/13364135-use-claude-cowork-safely)).

## Step 2 — Write your business context file

Without context, every session starts from scratch. A context file at the root of your workspace folder tells Claude who you are, what the business does, how you work, and what the rules are. Copy [templates/context-file-template.md](templates/context-file-template.md) and fill in the placeholders: business name and what you sell, your customers, tone of voice, tools you use, currency and date formats, and your standing rules (for example: "draft, never send" for anything customer-facing).

Two levels work together: global instructions in the app's settings (short, stable facts) and the workspace context file (richer, edited as the business changes). Note that Cowork's memory currently persists within projects only — it does not carry across standalone sessions ([getting started guide](https://support.claude.com/en/articles/13345190-get-started-with-claude-cowork)) — which makes the written context file the reliable backbone of your setup.

## Step 3 — Connect your tools

Connectors give Cowork scoped access to the tools your business runs on: Gmail or Microsoft 365, Google Calendar, accounting software, your CRM, and dozens more. Connect each one from within a conversation or via Settings, authorising through the provider's own login.

Rules of thumb:

- **Connect what your first two workflows need. Nothing else.** You can always add more; un-granting trust is harder than granting it.
- **Prefer the verified directory.** Anthropic advises sticking to reviewed connectors, because local MCP servers run with the same permissions as any program on your computer ([safety guidance](https://support.claude.com/en/articles/13364135-use-claude-cowork-safely)).
- **Scope to read where read is enough.** A workflow that summarises your inbox does not need send rights.

## Step 4 — Install plugins and skills

Plugins bundle skills, connectors and commands for a domain of work. Anthropic publishes free first-party packs — including a small-business plugin (invoice chasing, cash-flow snapshots, customer pulse, month-end prep), plus marketing, sales, productivity and others — installable from the app via Customize → Browse plugins ([plugins documentation](https://support.claude.com/en/articles/13837440), [open-source plugin repo](https://github.com/anthropics/knowledge-work-plugins)).

For a small business, start with: **small-business**, **productivity**, and whichever of **marketing** or **sales** matches where your hours go. Skills are invoked with "/" in a conversation, or trigger automatically when a task matches. Resist installing everything — each plugin adds choices Claude must weigh, and an unused plugin is configuration debt.

## Step 5 — Build your first two workflows

Pick two workflows with three properties: repetitive, document- or data-shaped, and annoying. Build them interactively first — delegate the task in a normal Cowork session, watch what Claude does, correct it, and refine your context file with what you learn. Only then automate (Step 6).

Two worked examples we run ourselves:

**The Monday morning brief.** "Read 1-clients/ and 2-finance/, check my calendar and inbox via connectors, and produce monday-brief.md in 0-inbox/: cash position, this week's commitments, top three things needing attention, anything overdue." Ten minutes of setup, and the week starts already summarised.

**Invoice follow-up drafts.** "Check 2-finance/invoices-out/ against payments, and for anything 14+ days overdue draft a reminder email matched to the customer's history — gentle for good payers, firmer for repeat late payers. Save drafts to 0-inbox/ for my approval. Never send." The "never send" is not decoration; it is the policy (Step 7).

More prompt patterns: [templates/scheduled-task-prompts.md](templates/scheduled-task-prompts.md).

## Step 6 — Set up scheduled tasks

Scheduled tasks run your proven workflows automatically — hourly, daily, weekdays, weekly, or manual — each run in its own fresh session, with an optional working folder and model choice ([scheduled tasks documentation](https://support.claude.com/en/articles/13854387)). Create them with /schedule or from the Scheduled page.

What the docs say that most guides miss: tasks only run while the computer is awake with the app open. Missed runs are skipped, then run automatically once the computer wakes or the app reopens, with a notification when the skipped run happens; skipped runs also appear in the task's history. So design for "visible if missed": every scheduled task we run writes an output file with a date stamp, so a silent gap is noticeable by its absence. Start with two scheduled tasks, not ten — each run consumes usage (Cowork is heavier than chat), and ten automations you half-watch are worse than two you trust.

## Step 7 — Put your guardrails in writing

The difference between a safe setup and a mess is rarely the software; it is whether the operating rules exist in writing. Copy [templates/guardrails-policy.md](templates/guardrails-policy.md) — a one-page policy a 5-person business can adopt as-is. The defaults it encodes:

- **Draft, never send.** Anything customer-facing (email, invoices, social posts) is produced as a draft for human approval. No exceptions in the first 90 days; most businesses keep it permanently.
- **Folder boundaries.** What is granted, what is excluded, and who may change that list.
- **Approval gates.** What runs autonomously (read-and-report tasks) versus what always asks (anything that creates, sends, spends, or deletes).
- **Review habit.** Outputs of autonomous runs get human eyes within one business day.
- **What never enters the workspace:** credentials, payroll, identity documents, anything you would not hand a new contractor on day one.

Anthropic's own safety documentation is candid that prompt-injection risk "is still non-zero" and the user remains responsible for Claude's actions ([safety guidance](https://support.claude.com/en/articles/13364135-use-claude-cowork-safely)). Written guardrails are how a small business carries that responsibility without an IT department.

## Multi-person setups without Enterprise

Enterprise plans have role-based permissions; a 2–10 person business on Pro or Team does not, and no official guide covers this. The pattern that works:

- **Shared source of truth, individual Cowork.** The workspace folder lives on a shared drive (Google Drive, OneDrive, Dropbox); each person grants their own synced copy to their own Cowork.
- **One shared context file, versioned.** The business context file is owned by one person; everyone else inherits it. Edits go through that owner, exactly like an SOP.
- **Scheduled tasks have a single owner each.** Two people running the same invoice-chase automation produces duplicate reminders and confused customers. Keep a one-line register of who owns which task in the context file.
- **Same guardrails policy for everyone.** One page, signed off, revisited quarterly.
- On Team plans, admins can manage plugin availability centrally via [organisation plugin management](https://support.claude.com/en/articles/13837433).

## Usage limits and cost budgeting

Cowork consumes usage faster than chat — Anthropic says so plainly, and you will notice it. Rough planning guidance for a small business on Pro:

- Light scheduled tasks (a daily brief, a weekly summary): comfortable on Pro.
- Heavy document production (long reports, spreadsheet builds) plus several daily automations: you will hit Pro limits; budget for Max (from US$100/month) for the heaviest user, not for everyone.
- A sensible pattern: owner on Max, staff on Pro or Team standard seats. Review after a month of real usage rather than guessing up front.

## Keeping your setup healthy

Cowork setups drift. The product ships changes frequently (plugins arrived February 2026, computer use March 2026, GA April 2026 — see [release notes](https://support.claude.com/en/articles/12138966-release-notes)), and your business changes too. A monthly 15-minute review keeps the setup honest:

1. Re-read the granted-folders list. Remove anything no longer needed.
2. Prune scheduled tasks that no longer earn their usage.
3. Update the context file: new tools, new staff, changed rules.
4. Skim the release notes for anything that changes your setup.
5. Check connector authorisations are still scoped to what workflows need.

## Troubleshooting and failure modes

| Symptom | Likely cause | Fix |
|---|---|---|
| Scheduled task did not run | Computer asleep or app closed — missed runs are skipped by design | It re-runs automatically on wake (watch for the notification); schedule for times the machine is reliably awake |
| Session stopped mid-task | App closed, sleep, or lost connection | Restart the task; keep long jobs on mains power with sleep disabled |
| Claude cannot see a file you can see | File outside the granted folder, or cloud-only placeholder not synced locally | Move it into the workspace; force the file to sync/download |
| Output quality dropped | Context file stale, or task outgrew its prompt | Refresh context; split the task into smaller steps |
| Hitting usage limits mid-week | Too many scheduled tasks or heavy document jobs | Prune tasks; move heaviest user to a higher plan |
| Claude proposed deleting something unexpected | Working as designed — deletion always asks | Decline, then narrow the folder grant or tighten the task prompt |

Worth internalising: community reports of agentic-AI accidents (the widely shared "deleted 11GB" story) trace back to broad folder grants and act-without-asking mode in the same setup. The guardrails in Step 7 exist because of stories like that.

## FAQ

### Is Claude Cowork available on Windows?

Yes. Cowork reached general availability on both macOS and Windows on 9 April 2026. It requires the desktop app; there is no web or mobile version, though Pro and Max users can dispatch tasks from the mobile app to a running desktop session.

### Which Claude plan do I need for Cowork?

Any paid plan: Pro, Max, Team or Enterprise. Pro is enough to start. Heavy daily automation pushes you toward Max for the heaviest user.

### How much does Claude Cowork cost for a small business?

The software is included in your Claude subscription (Pro at US$20/month per user; roughly A$30–35 in Australia — confirm in your billing screen). The real cost question is setup time: a careful self-setup using this guide takes a few evenings. Done-for-you setup services in Australia run from roughly A$1,500 to A$5,000 depending on depth; [ours](https://www.automataai.com.au/claude-cowork-setup?utm_source=github&utm_medium=readme&utm_campaign=cowork-guide) is a fixed A$3,500 including training and two working workflows.

### Is my business data used to train Claude?

On Team and Enterprise plans, no — not by default. On Pro and Max (consumer plans), data may be used unless you opt out in settings. Check your plan's data settings before granting business folders.

### Does Claude Cowork store data in Australia?

No. There is no Australian data residency for Cowork today. Anthropic has said it is exploring expanded compute capacity in Australia (Sydney office announcement, March 2026), and API-level AU residency exists via AWS Bedrock and Google Vertex — but that is a different product. Any provider telling you Cowork keeps your data onshore is wrong.

### Can Claude Cowork send emails or invoices by itself?

Technically yes, if you grant send-capable connectors and act-without-asking mode. You should not. The draft-never-send rule in the guardrails template exists because approval gates on outbound communication are what make the rest of the autonomy safe.

### Claude Cowork vs Claude Code — which do I need?

Code is for software engineering in a terminal; Cowork is the same agentic capability pointed at business work through the desktop app. A small business wants Cowork. If you also build software, they share plugins and patterns.

---

## About this guide

Written and maintained by [Automata AI](https://www.automataai.com.au/?utm_source=github&utm_medium=readme&utm_campaign=cowork-guide), a Sydney-based Claude consultancy (Claude Code rollouts, Claude training, Cowork implementation for Australian businesses). The workflows in this guide are the ones we run our own consultancy on.

- Found an error? [Open an issue](../../issues) — accuracy is the point of this guide.
- Licence: [CC BY 4.0](LICENSE) — reuse freely with attribution.
- Want it set up for you? [Claude Cowork setup for Australian small businesses](https://www.automataai.com.au/claude-cowork-setup?utm_source=github&utm_medium=readme&utm_campaign=cowork-guide) — fixed fee, one week.
