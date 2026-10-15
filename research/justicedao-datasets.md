# JusticeDAO Hugging Face datasets — sizes and 100 GB local budget

**Checked:** 2026-10-14. **Project decision:** Use JusticeDAO's published datasets **as-is**. No new scraping, rebuilding, or recomputing embeddings/indexes is part of the chosen approach.

**Source:** [JusticeDAO Hugging Face organization](https://huggingface.co/justicedao), which showed about **250 published datasets** when checked. This page inventories 15 datasets relevant to earlier research; **it is not a complete census of all 250**.

## Dataset inventory: publisher-reported total file sizes

Sizes below are from each Hugging Face dataset landing page **“Total file size”**, checked in this session. These are repository file totals, **not** measured local footprint and not necessarily corpus-only sizes. Decimal GB/MB displayed on the Hub are used for the arithmetic.

| # | Dataset | Hub total size | GB for budget* | What it contains / note |
|---:|---|---:|---:|---|
| 1 | [ipfs_uscode](https://huggingface.co/datasets/justicedao/ipfs_uscode) | **3.81 GB** | 3.81000 | U.S. Code; corpus + BM25 + vectors + graph; dataset viewer presently has a config-name error |
| 2 | [ipfs_state_admin_rules](https://huggingface.co/datasets/justicedao/ipfs_state_admin_rules) | **4.76 GB** | 4.76000 | State administrative rules; Hub viewer reports invalid Parquet footer for part of the release |
| 3 | [american_municipal_law](https://huggingface.co/datasets/justicedao/american_municipal_law) | **19.2 GB** | 19.20000 | US county / municipal legal materials and embeddings |
| 4 | [ipfs_court_rules](https://huggingface.co/datasets/justicedao/ipfs_court_rules) | **3.67 MB** | 0.00367 | Court rules; README describes 7 states (MN, MO, ND, NH, NJ, OH, OR), **no NY** |
| 5 | [federal-register-full-graphrag-v20260810](https://huggingface.co/datasets/justicedao/federal-register-full-graphrag-v20260810) | **14.3 GB** | 14.30000 | Federal Register snapshot, GraphRAG/BM25/vectors; through 2026-08-10 |
| 6 | [patent-legal-corpus](https://huggingface.co/datasets/justicedao/patent-legal-corpus) | **14.3 MB** | 0.01430 | 35 USC, 37 CFR, USPTO / MPEP-related materials |
| 7 | [patent-legal-ir-graphrag](https://huggingface.co/datasets/justicedao/patent-legal-ir-graphrag) | **164 MB** | 0.16400 | Ready-made patent legal retrieval artifacts; ~2,174 source documents according to release card |
| 8 | [patent-legal-bm25](https://huggingface.co/datasets/justicedao/patent-legal-bm25) | **77.1 MB** | 0.07710 | Separate sparse / keyword index artifacts |
| 9 | [patent-legal-vectors](https://huggingface.co/datasets/justicedao/patent-legal-vectors) | **14.4 MB** | 0.01440 | Vector artifacts |
| 10 | [patent-legal-knowledge-graph](https://huggingface.co/datasets/justicedao/patent-legal-knowledge-graph) | **31.8 MB** | 0.03180 | Patent legal graph artifacts |
| 11 | [wetwijzer_netherlands_legal_corpus](https://huggingface.co/datasets/justicedao/wetwijzer_netherlands_legal_corpus) | **1.06 GB** | 1.06000 | Netherlands law; not necessary for a US-only workload |
| 12 | [legal-ir-autoencoder-checkpoints](https://huggingface.co/datasets/justicedao/legal-ir-autoencoder-checkpoints) | **2.51 GB** | 2.51000 | Research model/checkpoint artifacts, **not** primary law |
| 13 | [ipfs_state_laws_normalized_graphrag](https://huggingface.co/datasets/justicedao/ipfs_state_laws_normalized_graphrag) | **8.93 GB** | 8.93000 | State statutes and existing BM25/vector/graph structures; dataset card warns snapshots may not be current |
| 14 | [open-us-law-autoformal-span-cache](https://huggingface.co/datasets/justicedao/open-us-law-autoformal-span-cache) | **477 MB** | 0.47700 | Uncompiled preparation spans, **not** a court-rules or case-law corpus |
| 15 | [open-us-law-sparse-graphrag](https://huggingface.co/datasets/justicedao/open-us-law-sparse-graphrag) | **5.14 GB** | 5.14000 | State-law retrieval release with corpus, sparse index, vector routes and graphs; viewer has schema/config errors |

\* Budget conversion uses 1 GB = 1,000 MB for display consistency, not GiB.

### Totals

- **All 15 listed repositories:** **60.49227 GB** by displayed-file-size arithmetic.
- **Against a nominal 100 GB storage cap:** **39.50773 GB** nominal space remains **before** downloads/caches/application DB/working files/LLM weights.
- **Excluding #15** (if only comparing the 14 earlier catalog entries): **55.35227 GB**.
- **Not counted:** `justicedao/ipfs_state_laws`, because its original page did not load in the current check; do not treat it as a verified downloadable repo/size.
- **Not counted:** the org's remaining 235-ish datasets or its separate bucket. Actual all-JusticeDAO total could be far beyond 100 GB.
- **Overlapping publications:** the two state-law GraphRAG repos overlap conceptually; the patent corpus + BM25 + vectors + graph may overlap with the patent IR release. The 60.49 GB number is a **sum of repository storage**, not unique legal content and not a suggested selection.

### 100 GB feasibility

The researched 15 repo totals are below 100 GB **on paper**. They are **not a safe promise** that all will fit locally as deployed. A clone/snapshot can need extra space for download caches, conversion/temp files, application/database state and updates. Running a local LLM also consumes additional space. A cloud API-based LLM avoids local model-weight downloads.

**No data has been downloaded or deployed by this research work.** The 100 GB limitation is a user-supplied planning ceiling, not a measured free-space reading from the user's computer.

## As-is usage: preserve published release artifacts

- Use the original Hugging Face dataset repositories and their `manifest.json`, `data/`, `indexes/`, etc. where available.
- Prefer the **publisher's documented query client** for prebuilt BM25/vector/graph releases. Do not generate replacement embeddings/indexes on behalf of the project unless explicitly requested.
- If using local storage, the HF CLI supports a dry-run to inspect proposed downloads:

```bash
# Estimate files from upstream before downloading
hf download justicedao/ipfs_uscode --repo-type dataset --dry-run

# Example: download published files as-is, to a chosen local directory
hf download justicedao/ipfs_uscode --repo-type dataset \
  --local-dir ./data/justicedao/ipfs_uscode
```

Confirm the CLI version supports `--dry-run` using [the current Hugging Face CLI documentation](https://huggingface.co/docs/huggingface_hub/guides/cli).

Relevant **publisher-provided** retrieval commands appear on the [open-us-law-sparse-graphrag](https://huggingface.co/datasets/justicedao/open-us-law-sparse-graphrag), [state-laws-normalized-graphrag](https://huggingface.co/datasets/justicedao/ipfs_state_laws_normalized_graphrag), [Federal Register GraphRAG](https://huggingface.co/datasets/justicedao/federal-register-full-graphrag-v20260810), and [patent-legal-ir-graphrag](https://huggingface.co/datasets/justicedao/patent-legal-ir-graphrag) dataset cards. Some example client scripts reside in upstream `ipfs_datasets_py` / release tooling rather than in a simple `datasets.load_dataset()` call. **Viewer errors do not prove the raw artifacts are unusable**; similarly, listing a size is not validation of the files.

### Important usage and licensing caveats

- Several datasets list Hugging Face license **`other`**; public availability does not automatically grant permission to redistribute underlying records in commercial products.
- Patent corpus and artifacts may show CC0 and some related repositories MIT; check **each repository's current license** and source terms separately.
- JusticeDAO describes multiple releases as **research snapshots**; none automatically establish the current rule or good-law status.
- Court rules bundle includes only 7 states and is **not a New York court-rules engine**.
- `ipfs_state_admin_rules` viewer presently reports a Parquet-format error. `ipfs_uscode` and `open-us-law-sparse-graphrag` also have viewer/config issues. These need read-path verification *when using them*, without rewriting the source corpus.
- A Hugging Face dataset is **not** the firm's live court docket, source of sealed filings, or court-filing access.

## Additional Hugging Face sources discussed, but not JusticeDAO

- [docketx/us-caselaw](https://huggingface.co/datasets/docketx/us-caselaw) — judicial opinions.
- [docketx/us-dockets](https://huggingface.co/datasets/docketx/us-dockets) — historic docket records.
- [docketx/court-rules](https://huggingface.co/datasets/docketx/court-rules) — separate court rules data.
- [vaquill/open-us-law](https://huggingface.co/datasets/vaquill/open-us-law) — independent US primary-law release (dataset page has shown 4.09 GB in v2026.08).
- [free-law/Caselaw_Access_Project](https://huggingface.co/datasets/free-law/Caselaw_Access_Project) — historical case law.

These are **research references**, **not a replacement plan** for the owner's JusticeDAO-as-is choice, and they are **excluded** from the 60.49 GB total.

## Size-check provenance

Every figure above was read from the linked official Hugging Face dataset landing page on 2026-10-14, not inferred from record count or a previous conversation's stale size. Previous research mentioned **6.24 GB** for `ipfs_uscode` and **21.7 MB** for `ipfs_court_rules`; newer page labels showed **3.81 GB** and **3.67 MB** respectively. Sizes can change over time. The current page and actual download manifest take precedence.
