# AI classification, drafting, retrieval and datasets

**Compiled:** 2026-10-14. **Owner decision:** **JusticeDAO Hugging Face releases as-is** are the preferred prebuilt legal retrieval data. This document records options, not an instruction to build new indexes or scrape a new legal corpus.

## Difference between decision models and drafting models

| Component | Typical task | Candidate / link | Source model |
|---|---|---|---|
| Decisions/classification | Route inbound court email: EBT, motion, order, other | [OpenAI Decisions API](https://developers.openai.com/api/docs/guides/decisions) | Hosted/proprietary; API |
| Decisions/classification | Same decision task; scores and alternatives | [JEV](https://jev-ai.org/docs/) | Hosted/proprietary; API |
| Generative drafting | Draft notice, demand letter, motion or discovery response | [OpenAI Responses API](https://developers.openai.com/api/docs/guides/responses) | Hosted/proprietary; API |
| Local legal retrieval | Lookup from JusticeDAO's published datasets, preserving existing search artifacts | [JusticeDAO datasets](https://huggingface.co/justicedao) | Public HF dataset repos, separate per-dataset licenses |
| Optional firm-private file retrieval | Search only documents the firm is authorized to use | [OpenAI File Search](https://developers.openai.com/api/docs/guides/tools-file-search) | Hosted/proprietary storage and retrieval feature |
| Document assembly | Populate approved form fields / produce files | [docassemble](https://docassemble.org/), [python-docx-template](https://github.com/elapouya/python-docx-template) | Open source |

**OpenAI Decisions and JEV are decision-oriented APIs, not full legal drafting models and not case-law databases.** Use them for triage, review flags, document classification and priority, not as legal sources or deadline calculators.

## OpenAI Decisions vs JEV (earlier research comparison)

- OpenAI Decisions public beta appeared in October 2026 with `gpt-6-luna`; supports `predicate`, `choice` and `score` question types; see [official guide](https://developers.openai.com/api/docs/guides/decisions).
- JEV publishes a [decision API](https://jev-ai.org/docs/) supporting classification/structured judgments. Check current model versions, rate limits, supported modalities, data retention and license before an implementation commitment.
- Previous comparison claimed OpenAI can batch up to 200 questions versus JEV 20. **Treat limits as changeable and verify with current API documentation** rather than hardcoding them.
- The team can test either or both providers against a *labeled* set of real, properly redacted work items. No empirical accuracy benchmark was completed in this research.
- Model output probabilities are not guarantees of correctness; review criteria must be explicit.

### Safe routing example

Incoming court communication:
- determine document type (court order, EBT scheduling request, motion, other);
- flag whether **a date appears** or **an explicit obligation appears**;
- distinguish confidence/uncertainty;
- route to docket clerk or attorney.

Do **not** turn `contains_date=true` directly into an enforceable calendar deadline without verifying the governing rule/order.

## Retrieval: JusticeDAO as published

JusticeDAO's releases include some prebuilt **BM25 postings, embedding vectors, graph edges and compact routing manifests**. The user wants to **use those, as-is**; there is no requirement to rebuild an index, train embeddings or develop a new case-law corpus.

Detailed URLs, dataset coverage, 15 verified repository sizes and the **60.49 GB / 100 GB** budget arithmetic are in [justicedao-datasets.md](justicedao-datasets.md).

Data types encountered in the research:
- U.S. Code and state statutes;
- administrative regulations and municipal laws;
- subset of state court rules;
- patent-law-specific indexed records;
- Federal Register snapshots;
- international datasets and autoencoder research artifacts.

### What is not included by default

A general state-statute corpus does **not** necessarily contain court opinions, live NYSCEF filings, complete NY court procedural rules or privileged matter files. A published snapshot also does not continuously update itself or validate subsequent legal amendments. Record these as dataset scope boundaries, not as a directive to replace the selected dataset.

## Document and legal-research APIs surveyed earlier

**Research-only alternatives or companion public endpoints** (not chosen replacements for JusticeDAO):
- [CourtListener REST API](https://www.courtlistener.com/api/rest-info/) — judicial opinions, dockets and searchable case law; account/rate limits.
- [PACER](https://pacer.uscourts.gov/) — federal court access with fees/rules; filings are separate authorization.
- [New York statutes API](https://legislation.nysenate.gov/) — statutes/legislative records.
- [GovInfo API](https://api.govinfo.gov/docs/) — federal governmental publications.
- [NYSCEF](https://iapps.courts.state.ny.us/nyscef/) / [NY eCourts](https://iapps.courts.state.ny.us/webcivil/ecourtsMain) — official current case/court sources; no assumption that they expose unrestricted scraping or e-filing APIs.

## How drafting would conceptually consume the selected assets

1. Matter-specific input arrives.
2. Classifier categorizes and routes; source files remain unchanged.
3. Prebuilt JusticeDAO retrieval capability returns passages, published citations and provenance (if available).
4. Generative model prepares a document grounded in retrieved passages and approved case facts.
5. Template engine fills in caption, court and witness facts without hallucinating unknown fields.
6. Validation checks citations, source passage, dates, names, court formatting and missing information.
7. Attorney reviews and approves.
8. Case system stores draft history and records approved changes.

This is an *illustrative workflow*, not a mandate to build a new retrieval engine. Reuse publisher search tools as supplied.

## Confidentiality and production responsibilities

- Verify OpenAI/JEV data use and retention terms for the actual account, endpoint and contract.
- Privileged material: minimize/redact where feasible, encrypt in transit and at rest, isolate matters and audit access.
- Human legal judgment remains essential for deadline verification, privilege calls, legal arguments, settlements, and authorized service/filing.
- Keep authoritative citations and the actual quoted passage/source URL for review; a retrieved answer cannot guarantee an authority remains good law.
- Store API credentials in a secrets system; never commit them.

## Other legal NLP benchmark datasets mentioned

[CUAD](https://github.com/The-Atticus-Project/cuad), [LegalBench](https://github.com/HazyResearch/legalbench), [LexGLUE](https://github.com/coastalcph/lex-glue). These support testing NLP models; they are not complete operative law libraries.

## Model/pricing note

Previous conversation compared GPT-6 Luna, Sol and Astra as possible hosted tasks and reported prices. Because model/pricing availability changes quickly, **this repository intentionally preserves role distinctions but does not pin those earlier prices as validated requirements**. Check [OpenAI pricing](https://openai.com/api/pricing/) for deployment costing.
