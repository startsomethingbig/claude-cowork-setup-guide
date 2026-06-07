# Claude Cowork small-business setup checklist

*Print or copy this. Companion to the [full setup guide](../README.md). Done in order, this is a few evenings of careful work — or see the guide's FAQ for done-for-you options.*

## Before you start
- [ ] Claude desktop app installed (macOS or Windows)
- [ ] Paid plan active (Pro is enough to start)
- [ ] Decided who owns this setup (one named person)

## Step 1 — Folders
- [ ] Created a dedicated `cowork-workspace/` folder (never Documents root or Desktop)
- [ ] Built the taxonomy for your business type ([templates](../templates/folder-structure.md))
- [ ] Confirmed exclusions: no payroll, credentials, identity documents, legal-privilege material
- [ ] Granted ONLY the workspace folder, in "Ask before acting" mode

## Step 2 — Context
- [ ] Context file at workspace root ([template](../templates/context-file-template.md))
- [ ] Global instructions set in app settings (short, stable facts only)
- [ ] Standing rules written, including draft-never-send

## Step 3 — Connectors
- [ ] Connected only what the first two workflows need
- [ ] Used verified-directory connectors
- [ ] Read-only scope wherever read is enough

## Step 4 — Plugins
- [ ] Installed small-business + productivity packs
- [ ] Added marketing OR sales (where your hours go)
- [ ] Did not install everything else

## Step 5 — First workflows
- [ ] Picked two: repetitive, document-shaped, annoying
- [ ] Ran each interactively at least 3 times, refining context after each run
- [ ] Outputs land in `0-inbox/` with dated filenames

## Step 6 — Scheduled tasks
- [ ] Scheduled the two proven workflows ([prompt patterns](../templates/scheduled-task-prompts.md))
- [ ] Each writes a dated output file (missed runs visible by absence)
- [ ] Scheduled for times the computer is reliably awake
- [ ] Task register filled in (task, owner, schedule, output)

## Step 7 — Guardrails
- [ ] Adopted the [one-page operating policy](../templates/guardrails-policy.md)
- [ ] Everyone using Cowork has read it
- [ ] Review reminder set: outputs daily, full setup monthly

## Multi-person (if applicable)
- [ ] Workspace on shared drive; each person grants their own synced copy
- [ ] One owner for the shared context file
- [ ] No duplicate scheduled tasks across people

## Monthly health check
- [ ] Prune folder grants, connectors, scheduled tasks
- [ ] Update context file (tools, staff, rules)
- [ ] Skim [Anthropic release notes](https://support.claude.com/en/articles/12138966-release-notes) for changes
