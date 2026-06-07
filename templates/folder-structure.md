# Cowork folder structures that work

*Worked taxonomies from the [Claude Cowork setup guide for small business](../README.md). The folder design is the safety model: what Claude can reach defines what can go wrong.*

## Universal rules

1. One dedicated workspace folder. Grant nothing else.
2. Exclude by default — see the [guardrails policy](guardrails-policy.md) §2 for what never enters.
3. Numbered prefixes keep ordering stable and make prompts unambiguous ("file it under 2-finance").
4. An `0-inbox/` drop zone gives every workflow a predictable place to read from and write to.
5. `9-archive/` keeps history reachable without cluttering active context.

## Services business (consultants, agencies, professionals)

```
cowork-workspace/
├── 0-inbox/                  # drop zone + workflow outputs
├── 1-clients/
│   ├── _template/            # standard engagement folder skeleton
│   └── <client-name>/        # one per active client
├── 2-finance/
│   ├── invoices-out/
│   └── bills-in/             # NOT payroll, NOT bank credentials
├── 3-marketing/              # content drafts, social queue, website copy
├── 4-operations/             # SOPs, proposals, templates, checklists
└── 9-archive/
```

## Trades business (builders, electricians, plumbers)

```
cowork-workspace/
├── 0-inbox/
├── 1-jobs/
│   ├── _quoting/             # leads awaiting quotes
│   └── <job-address>/        # one per active job: quote, variations, photos list, invoices
├── 2-finance/
│   ├── invoices-out/
│   └── supplier-bills/
├── 3-compliance/             # licences, insurance certificates, SWMS templates
├── 4-templates/              # quote templates, standard inclusions, T&Cs
└── 9-archive/                # completed jobs
```

## E-commerce / product business

```
cowork-workspace/
├── 0-inbox/
├── 1-products/               # listings copy, specs, pricing sheets
├── 2-finance/
│   ├── invoices-out/
│   └── supplier-bills/
├── 3-marketing/
│   ├── content-queue/
│   └── campaigns/
├── 4-customer-service/       # reply templates, FAQ, returns policy — not customer identity data
├── 5-operations/             # supplier contacts, reorder points, SOPs
└── 9-archive/
```

## What to deliberately leave out (every business)

| Keep out | Why |
|---|---|
| Payroll, HR files | Privacy obligations; no workflow needs them |
| Scans of IDs, licences with personal data | Identity-theft surface |
| Password managers, `.env` files, API keys | Credentials never belong in an AI workspace |
| The accounting system's own data directory | Connect via the official connector instead — scoped and auditable |
| Ten years of legacy files | Stale context degrades output; archive separately and add back only what workflows need |
