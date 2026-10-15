# Automated legal drafting: product research and use cases

**Checked / compiled:** 2026-10-14. The project wants automated drafting integrated into Litigation OS, while **reusing JusticeDAO datasets as-is** for public legal retrieval. The products here are competitors, potential integrations or implementation references; listing them is not a technology decision.

## Document types

| Draft | Matter inputs | Appropriate automation |
|---|---|---|
| Summons and complaint | Matter facts, parties, causes of action, venue | Approved forms + fact-grounded draft; attorney review |
| Answer and affirmative defenses | Allegations, pleadings, matter record | Issue mapping and proposed responses; attorney review |
| Motions, briefs and oppositions | Evidence, docket/orders, legal authorities | Research-connected drafting, verify all citations |
| EBT/deposition notices | Caption, deponent, time/place, procedural constraints | Deterministic approved notice template |
| Deposition outlines | Pleadings, exhibits, transcripts, timeline | AI-generated draft topics/questions, attorney review |
| Interrogatories / RFPs / RFAs | Case facts, procedural limits and templates | Template + AI assistance |
| Discovery responses and objections | Requests, responsive records, privilege review | Proposed draft only; review by qualified staff |
| Subpoenas | Venue-specific forms and authorized witness details | Form-fill + jurisdictional validation |
| Stipulations and adjournment letters | Agreement/order and dates | Deterministic forms + factual review |
| Demand letters | Damages, causation, records, negotiations | AI-assisted narrative tied to evidence |
| Settlement agreements | Agreed material terms and approved clauses | Clause assembly + approvals |
| Attorney correspondence | Matter events and approval rules | Reusable templates + drafting |

## Eighteen proprietary drafting products researched

| Product | Link | Specialty |
|---|---|---|
| Gavel | https://www.gavel.io/ | Guided interviews and automated legal documents |
| Clio Draft | https://www.clio.com/ | Firm forms and document drafting |
| HotDocs | https://www.hotdocs.com/ | Rules-driven document assembly |
| BRYTER | https://bryter.com/ | Workflows, document and compliance automation |
| ClauseBase | https://www.clausebase.com/ | Contract clauses and drafting |
| Litera Draft | https://www.litera.com/ | Word-centric legal drafting and review |
| Legito | https://www.legito.com/ | Smart templates and document workflows |
| Knackly | https://www.knackly.io/ | Document assembly |
| Avvoka | https://www.avvoka.com/ | Contract drafting and lifecycle |
| Harvey | https://www.harvey.ai/ | AI legal drafting and research |
| CoCounsel Legal | https://legal.thomsonreuters.com/ | Research and drafting assistance |
| Lexis+ with Protégé | https://www.lexisnexis.com/ | Research-supported drafting |
| Briefpoint | https://briefpoint.ai/ | Written discovery responses/requests |
| Clearbrief | https://clearbrief.com/ | Evidence-linked briefs and exhibits |
| Eve | https://www.eve.legal/ | Plaintiff litigation drafting and case work |
| Supio | https://www.supio.com/ | PI evidence-to-document workflow |
| Spellbook | https://www.spellbook.legal/ | AI Word-based contract drafting |
| Juro | https://juro.com/ | Contract creation and negotiation |

These 18 are treated as **commercial proprietary SaaS/software** for purposes of this research; licensing/tier access should be independently confirmed before procurement.

## Eight open-source / source-available drafting components

| Project | Code/documentation | Role | License note |
|---|---|---|---|
| docassemble | https://github.com/jhpyle/docassemble | Legal interviews and form assembly | MIT, verify current repo |
| Suffolk Document Assembly Line | https://github.com/SuffolkLITLab/docassemble-AssemblyLine | Legal court-form workflows | Check per-repo license |
| ALWeaver | https://github.com/SuffolkLITLab/docassemble-ALWeaver | Bootstrap forms automation | Check per-repo license |
| python-docx-template | https://github.com/elapouya/python-docx-template | DOCX/Jinja templates | LGPL-2.1; obligations apply |
| Accord Project | https://github.com/accordproject/template-engine | Structured contract/legal logic | Apache-2.0 for referenced engine |
| OpenContracts | https://github.com/Open-Source-Legal/OpenContracts | Analysis/extraction and RAG components | MIT in cited core repo, verify |
| DocuSeal | https://github.com/docusealco/docuseal | Fillable templates and signatures | AGPL / additional commercial terms |
| Documenso | https://github.com/documenso/documenso | Signature approval and workflow | AGPL community / commercial edition |

**Open-source is not synonymous with a finished autonomous lawyer.** These projects support assembly, search, analysis or signatures; novel litigation arguments still depend on a language model, source grounding, source verification, and lawyer review.

## Drafting workflow researched

Matter data + incoming event → identify the document needed → retrieve approved template and published JusticeDAO legal corpus artifacts **as-is** → AI extracts facts and proposes language → document assembly formats DOCX/PDF → validate parties, caption, dates, source citations and unresolved placeholders → lawyer review/approval → store version and update matter. **Do not automatically file or serve without authorization.**

### Conceptual separation of responsibilities

1. **Decision/classification:** OpenAI Decisions or JEV determines the work category, priority or review queue; it does not generate entire motions.
2. **Generative drafting:** OpenAI Responses API or another explicitly selected generative model.
3. **Legal retrieval:** Prebuilt JusticeDAO artifacts chosen by project owner; no rebuilding assumed.
4. **Document assembly:** Approved template engine, structured matter data, Word/PDF generator.
5. **Validation and review:** Factual/citation checks and attorney sign-off.

Read [AI and retrieval](ai-and-retrieval.md) for APIs and [JusticeDAO sizes](justicedao-datasets.md) for disk planning.

## Relevant evaluation datasets (not a replacement for firm templates)

- [CUAD](https://github.com/The-Atticus-Project/cuad): contract clause extraction/evaluation.
- [LegalBench](https://github.com/HazyResearch/legalbench): legal reasoning benchmark tasks.
- [LexGLUE](https://github.com/coastalcph/lex-glue): legal NLP benchmarks.

These are not complete private law firm pleadings libraries and do not authorize republishing client documents.

## Additional existing code discovered after the original 26-tool drafting comparison

[JusticeDAO-LLC/complaint-generator](https://github.com/JusticeDAO-LLC/complaint-generator) is a public proof-of-concept that describes question-driven intake, evidence gathering, legal authority research, complaint generation and a multi-provider AI backend. It is **supplementary**, not one of the 18 commercial or 8 open/source-available drafting options counted above. Its root license was not found in the checked path; do not assume redistribution rights. See [JusticeDAO-related code](justicedao-related-code.md) for GitHub-reported repository sizes and limitations.
