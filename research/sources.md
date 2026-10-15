# Sources, links and verification notes

**Research cutoff:** 2026-10-14. Prefer official documentation or project repos. Dataset sizes were **individually rechecked** on their Hugging Face landing pages on that date and recorded in [justicedao-dataset-sizes.csv](justicedao-dataset-sizes.csv).

## Main official datasets (size-provenance links)

1. https://huggingface.co/datasets/justicedao/ipfs_uscode
2. https://huggingface.co/datasets/justicedao/ipfs_state_admin_rules
3. https://huggingface.co/datasets/justicedao/american_municipal_law
4. https://huggingface.co/datasets/justicedao/ipfs_court_rules
5. https://huggingface.co/datasets/justicedao/federal-register-full-graphrag-v20260810
6. https://huggingface.co/datasets/justicedao/patent-legal-corpus
7. https://huggingface.co/datasets/justicedao/patent-legal-ir-graphrag
8. https://huggingface.co/datasets/justicedao/patent-legal-bm25
9. https://huggingface.co/datasets/justicedao/patent-legal-vectors
10. https://huggingface.co/datasets/justicedao/patent-legal-knowledge-graph
11. https://huggingface.co/datasets/justicedao/wetwijzer_netherlands_legal_corpus
12. https://huggingface.co/datasets/justicedao/legal-ir-autoencoder-checkpoints
13. https://huggingface.co/datasets/justicedao/ipfs_state_laws_normalized_graphrag
14. https://huggingface.co/datasets/justicedao/open-us-law-autoformal-span-cache
15. https://huggingface.co/datasets/justicedao/open-us-law-sparse-graphrag

Organization: https://huggingface.co/justicedao . The earlier `justicedao/ipfs_state_laws` URL did not return a usable landing page in this check, so the release's size is **unknown / excluded**, not zero.

### Verified Hugging Face documentation

- https://huggingface.co/docs/huggingface_hub/guides/cli — `hf download`, `--repo-type dataset`, `--dry-run`, `--local-dir`, cache verification.
- Individual dataset cards — release layouts, documented limitations, file size and license tags. Read each release's current manifest and dataset card before relying on it.

## AI, decision and document assembly

- https://developers.openai.com/api/docs/guides/decisions — Decisions API, question types and response formats.
- https://developers.openai.com/api/docs/guides/responses — generative Responses API.
- https://developers.openai.com/api/docs/guides/tools-file-search — hosted file retrieval option.
- https://openai.com/api/pricing/ — official changing model/API prices.
- https://jev-ai.org/docs/ — JEV decision API documentation.
- https://docassemble.org/ and https://github.com/jhpyle/docassemble
- https://github.com/SuffolkLITLab/docassemble-AssemblyLine
- https://github.com/SuffolkLITLab/docassemble-ALWeaver
- https://github.com/elapouya/python-docx-template
- https://github.com/accordproject/template-engine
- https://github.com/Open-Source-Legal/OpenContracts
- https://github.com/docusealco/docuseal
- https://github.com/documenso/documenso

## Legal procedure, court interfaces and legal data

- https://www.nysenate.gov/legislation/laws/CVP/3107 — NY CPLR 3107.
- https://www.nycourts.gov/rules/ — NY rules.
- https://iapps.courts.state.ny.us/nyscef/ — NYSCEF.
- https://iapps.courts.state.ny.us/webcivil/ecourtsMain — NY eCourts.
- https://legislation.nysenate.gov/ — New York legislative API.
- https://pacer.uscourts.gov/ — PACER.
- https://www.courtlistener.com/api/rest-info/ — CourtListener APIs.
- https://api.govinfo.gov/docs/ — GovInfo APIs.
- https://github.com/freelawproject/juriscraper — public court data collection components.
- https://github.com/freelawproject/eyecite — legal citation extraction.

## Market-landscape sources

- https://www.courtalert.com/
- https://www.courtdrive.com/
- https://lawtoolbox.com/
- https://www.filevine.com/
- https://www.clio.com/
- https://briefpoint.ai/
- https://www.eve.legal/
- https://www.gavel.io/
- https://www.hotdocs.com/
- https://www.harvey.ai/

The [100-tool inventory](legal-software-100.md) is a **shortlist**, not a product-by-product procurement verification report. Its entries were assembled across earlier research in the project conversation, and not all 100 sites were re-opened during this GitHub documentation update.

## Confidence, data integrity and risks

**Verified directly on 2026-10-14:** User repo write access; empty repo at start; JusticeDAO landing-page sizes for the 15 recorded repos; publisher-described court-rules jurisdictions; upstream documented HF CLI dry-run; official OpenAI Decisions and JEV docs available.

**Research-only / not tested:** Exact downloaded bytes, integrity/checksums of the datasets, full data coverage, completeness and freshness of statutes/court rules, runtime requirements for publisher query clients, actual commercial-use rights of each underlying legal source, accuracy of AI models, licensing/pricing of all 100 products, full JusticeDAO 250-dataset total.

**Important corrections from earlier assistant replies:** Earlier answers reported 6.24 GB for `ipfs_uscode`, 21.7 MB for `ipfs_court_rules`, and cited `ipfs_state_laws` as a usable repository. The current checks resulted in **3.81 GB**, **3.67 MB**, and **no confirmed size/availability** for the old `ipfs_state_laws` link. The current inventory reflects the newer read and keeps the discrepancy documented.

**Source precedence:** Authoritative current law and actual court orders govern procedural actions; publisher legal datasets are snapshot research materials. A dataset's claimed coverage is not an independent audit of current legal effect.

## Owner's project choice and resource ceiling

No model training, replacement legal corpus, new embeddings, new scrapers, case data upload, local LLM hosting or large dataset download was done in preparing this repository. The project owner expressly chose **JusticeDAO as-is** and communicated **approximately 100 GB local capacity**.
