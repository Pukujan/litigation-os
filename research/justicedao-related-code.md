# JusticeDAO-related code projects found during drafting research

**Checked:** 2026-10-14. The JusticeDAO Hugging Face dataset releases remain the **owner-selected as-is data sources**; this page records potentially related *software*, not an instruction to replace the selected datasets or to build an index.

## 1) JusticeDAO-LLC / complaint-generator

- **Repository:** https://github.com/JusticeDAO-LLC/complaint-generator
- **README:** https://github.com/JusticeDAO-LLC/complaint-generator/blob/master/README.md
- **Status claimed by its README:** proof-of-concept for legal complaints; research evidence and claim support, questionnaire-driven intake, legal authority gathering, complaint generation, an AI provider router and review dashboards.
- **Backend examples named upstream:** OpenAI, OpenRouter, Gemini, Hugging Face local/inference, and Codex.
- **Legal-source examples named upstream:** US Code, Federal Register, RECAP, Brave Search, Common Crawl.
- **GitHub API repository `size` checked:** **16,438 KiB** (~16.1 MiB) as repository metadata. **Not** a measured local checkout, and excludes runtime/model/databases, submodule contents and downloaded datasets.
- **License:** A root `LICENSE` file was **not found** by the direct checked path; do not assume it is openly licensed for redistribution/commercial incorporation just because code is public.
- **Maintenance/production status:** README describes proof of concept and several incomplete tasks; claims and tests have not been independently reproduced.
- **Identity caveat:** GitHub org `JusticeDAO-LLC` and HF account `justicedao` share branding and related tool references; **formal ownership/affiliation was not independently confirmed**.

## 2) endomorphosis / ipfs_datasets_py

- **Repository:** https://github.com/endomorphosis/ipfs_datasets_py
- **Relationship to data releases:** Dataset cards refer to upstream query clients and ingestion tooling from this project, and `complaint-generator` references an `ipfs_datasets_py` submodule.
- **GitHub API `size`:** **3,642,545 KiB** (~3.47 GiB) as repository metadata. This is **not an actual local clone measurement**; repository history, LFS and submodules can alter space used.
- **License:** `LICENSE` in main branch is **GNU AGPL-3.0**, verified from file contents. Any commercial incorporation needs license review.
- **Selected-data fit:** May contain the *publisher's existing read/query scripts*. Using the query client with JusticeDAO's **published** corpus/index artifacts is consistent with the owner's **as-is** direction; rebuilding scrapers/indexes is **not** required.

## Why record these separately?

The **60.49227 GB** budget in [justicedao-datasets.md](justicedao-datasets.md) is the **sum of 15 Hugging Face dataset repository size labels only**. It does **not** include GitHub code repositories, history, model weights, runtime data, clone/temp files or user case documents.

The 100-product inventory remains 100 items; these are **supplementary code references discovered after** that inventory was compiled.
