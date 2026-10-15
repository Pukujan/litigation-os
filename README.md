# Litigation OS — legal operations automation research

**Project-owned research repository.** Last research update: **2026-10-14**.

> **Owner's explicit direction:** Use the existing JusticeDAO Hugging Face datasets **as published/as-is**. Do not substitute a newly scraped/rebuilt/indexed legal corpus unless the owner later requests it. **Local storage may be limited to 100 GB.** The owner chooses architecture and data sources; alternatives in these notes are only research references, not instructions to change that choice.

## Research index

| Document | Contents |
|---|---|
| [JusticeDAO-related existing code](research/justicedao-related-code.md) | JusticeDAO-LLC complaint generator and publisher-linked query tooling; separate from dataset sizes |
| [JusticeDAO Hugging Face dataset inventory](research/justicedao-datasets.md) | Direct dataset URLs, sizes, coverage, license warnings, 100 GB calculations, as-is retrieval notes |
| [Law firm operations and calendar / docketing / EBT](research/operations-and-workflows.md) | Clerk duties, workflow taxonomy, event-driven processes, controls |
| [100 legal software and data systems](research/legal-software-100.md) | The 100-option market landscape: proprietary tools, open-source projects and datasets |
| [Automated legal drafting](research/automated-drafting.md) | 18 proprietary drafting tools, 8 source-available/open-source projects, document types and workflows |
| [AI models, Decisions, JEV and retrieval](research/ai-and-retrieval.md) | OpenAI Decisions versus JEV, drafting models, retrieval, APIs, constraints |
| [Sources and verification record](research/sources.md) | Primary-source links, validation status, and date-dependent limitations |

## Scope

Litigation OS research covers a unified law-firm operational interface for:
- client intake, conflict checks, matter management;
- court notices, docket monitoring, deadline review, litigation calendars;
- examinations before trial (**EBTs**, New York deposition terminology), scheduling, court reporters and transcripts;
- pleading, motion, discovery, correspondence and settlement drafting;
- document storage, search, OCR, eDiscovery and attorney approval;
- legal research and citation-backed retrieval;
- task assignment, communications, billing, trust accounting and reporting.

**Important distinction:** Case-management platforms are not the same as automated legal drafting software, and legal research datasets are not a substitute for authorized court-filing integrations or verified court-rule calculation.

## User-selected dataset approach

- Prefer to **consume JusticeDAO's published retrieval artifacts as-is** (Parquet, BM25, vectors, graph, manifests) without regenerating their indexes.
- Do **not** silently switch to CourtListener, a custom scraper, or an independently rebuilt corpus.
- Look at **publisher-reported disk sizes** before downloading. Keep a 100 GB ceiling in view.
- Downloading/hosting legal datasets is **not** the same thing as hosting an LLM. API-hosted drafting/decision models do not require local model weights.
- The 15 verified JusticeDAO repo-size labels in this research total **approximately 60.49 GB**, treating GB/MB as publisher-displayed decimal units. This is **not** a guaranteed real-world disk footprint, excludes local caches, extracted/index runtime files, applications and model weights, and may double-count datasets that overlap in content.
- JusticeDAO's profile currently shows around **250 datasets**; the 15 entries are a **researched subset**, not a complete 250-dataset storage census. See [dataset inventory](research/justicedao-datasets.md).

## MVP workflow on record (research concept, not imposed architecture)

Incoming court email/notice → identify matter and type → extract scheduling/deadline data → human validation of court orders/deadlines → prepare appropriate legal draft from approved documents + source retrieval → attorney review → store and schedule approved outputs. No autonomous court filing, service, privilege decisions or dispositive deadlines without appropriate authorization and verification.

## Research limitations

These notes summarize an exploratory technology scan. Product availability, commercial pricing, terms, API access, OSS licenses, dataset size, coverage and currentness may change. The listed 100 items include **commercial platforms, modules, general open-source infrastructure and data sources**; they are not 100 turnkey end-to-end alternatives. Explicitly distinguish direct source verification from previously assembled candidates.

## Original research workbook

The original [100-product research workbook](research/law_firm_automation_100_tools_research.xlsx) is committed here in native `.xlsx` format (4 worksheets). Its contents are also summarized in searchable Markdown under [the 100-tool inventory](research/legal-software-100.md).

## Repository conventions

Research goes under `research/`. This repository contains no client data, secrets, privileged case files or scraped licensed content. Public links are references, not a representation that every linked source is permitted for commercial redistribution.
