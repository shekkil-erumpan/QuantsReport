# 00 — Master Index
## Quants Report — Documentation Repository Entry Point
**Capinfy Private Limited (CIN U72900KL2020PTC065408)**

---

## Table of Contents

1. [Purpose of This Document](#1-purpose-of-this-document)
2. [Project Overview](#2-project-overview)
3. [Current Project Status](#3-current-project-status)
4. [Document Map](#4-document-map)
5. [Document Descriptions](#5-document-descriptions)
6. [Recommended Reading Order](#6-recommended-reading-order)
7. [How These Documents Relate to One Another](#7-how-these-documents-relate-to-one-another)
8. [Glossary](#8-glossary)
9. [Abbreviations](#9-abbreviations)
10. [Known Assumptions — Not Yet Independently Verified](#10-known-assumptions--not-yet-independently-verified)
11. [Documentation Still Needed](#11-documentation-still-needed)
12. [Master File Index Table](#12-master-file-index-table)

---

## 1. Purpose of This Document

This is the entry point for the entire Quants Report documentation repository. A reader arriving here is assumed to have **no prior context** on the project. This document explains what Quants Report is, what has been decided so far, where every piece of that knowledge lives, in what order to read it, how the pieces connect, and — equally important — what has **not** yet been written down or independently verified. This document does not repeat the full content of any other document; it tells the reader where that content lives and what to expect when they get there.

---

## 2. Project Overview

**Quants Report** is an AI-powered market intelligence platform for active NSE (National Stock Exchange of India) traders, being built by **Capinfy Private Limited**, a company incorporated in Kerala, India (CIN U72900KL2020PTC065408, MCA Active, incorporated 29 October 2020). The Founder, CEO, and Managing Director is **Shekkil Erumpantakath** (DIN 08939493), who is building this as a part-time, after-hours venture alongside a full-time role at HDFC Life Insurance Company, with the intent to transition to full-time once the product is validated.

The product's core thesis: most trading platforms deliver more data; Quants Report instead converts data, news, sentiment, and trading knowledge into **measurable, explained intelligence**. It is explicitly designed not to be — until and unless specific features are formally licensed to operate as one — an investment adviser, a stock recommendation engine, or a signal provider. The platform's stated job is to explain market conditions and let the trader decide; it does not decide for them.

The architecture is organized around a small number of **engines**, each with a narrow, well-defined responsibility, communicating only through a shared database rather than calling each other directly. A **Widget Layer** sits above the engines as the actual user-facing product — each widget addresses one specific, founder-validated trading pain point.

The project also operates under a deliberate three-party working structure: the **Founder/CEO** sets vision and makes final decisions; **CRAO** (Chief Risk & Architecture Officer — the role held by Claude in this documentation set) provides architecture, research, and critical review; a parallel AI architect referred to as **CAIO** (Chief Architect & Intelligence Officer) has also contributed drafts at various points; and downstream engineering platforms (Replit, and more recently Codex) are tasked with implementation against specifications produced by the CRAO role.

---

## 3. Current Project Status

- **Company and founder identity:** independently verified against MCA records and a registry cross-check. Not in question.
- **Compliance strategy:** a path is defined (SEBI Research Analyst registration via NISM-Series-XV for market-level intelligence; a separate, not-yet-pursued Investment Adviser registration for anything personalized to a user's specific holdings). Registration itself has **not yet been completed** — the Founder has committed to sitting the NISM-XV exam, but no date is confirmed in this documentation set.
- **Architecture:** has gone through multiple full review cycles, including the Founder's own hand-drawn diagram and three rounds of correction to it. The engine-level design is considered finalized as of the Engine Specification document (Section 5 below) — **with one explicitly flagged open item** (Intelligence Engine has no persistence path of its own; see Section 10 of that document).
- **Build status:** no production code has been written. Two Python modules exist as architectural reference implementations (`market_data_connector.py`, `historical_data_store.py`) — these were written to demonstrate and lock in a design pattern, not as part of a running application.
- **V1 scope:** has been deliberately narrowed to a single feature (a live, customizable option chain with calculated Greeks), for the Founder's own use only, with a full Non-Goals list excluding everything else discussed in this project to date.
- **Stage 1 (Pain Point Discovery):** complete, with genuine first-person Founder validation (not a generic restatement) — this is documented in detail and is the foundation for why the option-chain widget was selected as V1.
- **Several major features have been designed in conversation but not yet formalized into their own documents** — see Section 11. This includes the Market Thesis concept, the decision to split user data into a separate database, the admin panel feature list, the user login/plan structure, the order-routing workflow, and the personal knowledge base ("bring your own knowledge") feature. Their design rationale exists; their written specifications do not yet.

---

## 4. Document Map

Documents are grouped by category. Filenames are exact and link directly to the file.

### A. Business & Vision
- [`quants-report-knowledge-doc.md`](./quants-report-knowledge-doc.md) — Product Knowledge Document (Markdown, AI-context-oriented)
- [`quants-report-knowledge-base.html`](./quants-report-knowledge-base.html) — same content, styled HTML for human reading
- [`quants-report-pillars.pdf`](./quants-report-pillars.pdf) — Six Product Pillars reference

### B. Architecture
- [`quants-report-architecture-vision.html`](./quants-report-architecture-vision.html) — North Star Architecture Vision (earlier-stage; see Section 7 on terminology drift)
- [`quants-report-architecture.pdf`](./quants-report-architecture.pdf) — System Architecture reference (same generation as the above)
- [`quants-report-architecture-diagram.mermaid`](./quants-report-architecture-diagram.mermaid) — the corrected, Founder-confirmed high-level architecture diagram
- [`quants-report-engine-specification.md`](./quants-report-engine-specification.md) / [`.docx`](./quants-report-engine-specification.docx) — Engine Specification & Data Handling Matrix — **the most current and authoritative architecture document**

### C. Requirements
- [`quants-report-srs.pdf`](./quants-report-srs.pdf) — Software Requirements Specification (numbered FR/NFR requirements)
- [`quants-report-v1-codex-brief.md`](./quants-report-v1-codex-brief.md) — V1 Build Brief, narrowly scoped, the current build target

### D. Process & Governance
- [`quants-report-crao-review.html`](./quants-report-crao-review.html) — CRAO Review Response to the Product Milestone & Risk Review, with CEO response logged
- [`quants-report-claude-custom-instructions.html`](./quants-report-claude-custom-instructions.html) — Governing protocol for the CRAO role
- [`quants-report-documentation-standards-checklist.md`](./quants-report-documentation-standards-checklist.md) — gap analysis against ISO/IEC documentation standards

### E. Data & Infrastructure
- [`quants-report-stage4-free-data.html`](./quants-report-stage4-free-data.html) — free data sources for prototyping
- [`market_data_connector.py`](./market_data_connector.py) — reference code, data source abstraction
- [`historical_data_store.py`](./historical_data_store.py) — reference code, persistence layer
- [`quants-report-replit-induction.md`](./quants-report-replit-induction.md) — induction document written for the Replit engineering platform

### F. Legal / Commercial
- [`quants-report-booking-terms-draft.md`](./quants-report-booking-terms-draft.md) — draft pre-launch booking/advance terms

### G. Pain Point Research
- [`quants-report-stage1-pain-point-discovery.html`](./quants-report-stage1-pain-point-discovery.html) — Stage 1, including genuine first-person Founder validation

### H. Supplementary Research (not project documentation, but referenced in decisions above)
- [`deepseek-v4-vs-claude-sonnet-4-6.html`](./deepseek-v4-vs-claude-sonnet-4-6.html) — model comparison referenced when selecting the AI engine for the prototype phase

---

## 5. Document Descriptions

**`quants-report-knowledge-doc.md` / `quants-report-knowledge-base.html`**
The consolidated business and product reference: entity details, product vision, the six pillars, the (earlier-generation) five-engine architecture, compliance strategy, data sourcing findings, roadmap status, the open risk register, and working principles. Two formats of identical content — the Markdown version was deliberately written dense and unstyled for AI context-loading; the HTML version is the same material styled for human reading.

**`quants-report-pillars.pdf`**
The six product pillars (Market Intelligence, Portfolio Intelligence, Execution Assistance, Position Management Intelligence, Strategy Intelligence, Knowledge Intelligence), each with build status, capabilities, and compliance notes, plus the founder-validated-pain-point-to-pillar mapping.

**`quants-report-architecture-vision.html`**
An early-stage architecture document: the original five-engine model (Data, Knowledge, Intelligence, Process, UI/UX), the "build vs. publish" compliance principle, and the recommended SEBI Research Analyst registration path. Largely superseded in technical detail by the Engine Specification (below), but still the most complete record of the compliance reasoning and the original "no number without a defensible methodology" principle.

**`quants-report-architecture.pdf`**
A PDF-formatted companion to the above, from the same point in the project's evolution.

**`quants-report-architecture-diagram.mermaid`**
The single most load-bearing diagram in the project. Originated as an AI-drafted diagram, then was entirely redrawn by the Founder by hand and corrected across three rounds of review (channel routing, the database-as-communication-bus principle, the numeric/text processing split inside each engine, and the LLM-vs-fixed-calculator distinction for each engine's processor). This is the diagram that the Engine Specification document describes in prose.

**`quants-report-engine-specification.md` / `.docx`**
**The current, authoritative architecture reference.** Documents, for each of the five engines (Storage, Knowledge, Process, Intelligence, and the UI/UX Widget Layer): its participants, behavior, exact data flow in and out, processing nature (fixed calculator vs. swappable LLM), and storage responsibility. Also contains the full Data Handling Matrix — an item-by-item table of every distinct piece of data in the system, who handles it, how, and where it goes next. Explicitly flags one open architectural question (Intelligence Engine has no database write path yet). The `.docx` version is the polished, downloadable version of the same content with a cover page and table of contents field.

**`quants-report-srs.pdf`**
A formal Software Requirements Specification: introduction, scope, definitions, product description, numbered functional requirements (FR-1 through FR-9), non-functional requirements, external interface requirements, a dedicated compliance section, and a widget catalogue appendix with build-readiness tags.

**`quants-report-v1-codex-brief.md`**
The current, active build target. Deliberately narrow: one feature only (the option chain + Greeks widget), for the Founder's own use, with an explicit Non-Goals section excluding every other feature discussed in this project. Contains a functional spec, a data model for one new table, a pointer to the two existing reference code modules, and acceptance criteria including a known-correct Black-Scholes test case.

**`quants-report-crao-review.html`**
A formal review of a Product Milestone & Risk Review document, with findings on registration classification, broker data redistribution restrictions, process-gate integrity, and recommended build sequencing — followed by a logged response from the Founder, with items marked accepted, refined, or still open.

**`quants-report-claude-custom-instructions.html`**
A formal governance document defining the CRAO role's scope, communication standard (the Founder addressed as "Sir"), operating principles (no code without instruction, challenge weak assumptions, no number without a defensible methodology), the compliance standard, the documentation standard, how to engage with the parallel AI architect, and escalation expectations.

**`quants-report-documentation-standards-checklist.md`**
Maps the project's existing documents against recognized international software documentation standards (ISO/IEC/IEEE 12207, 29148, 25010, and ISO/IEC 29110 — the lightweight profile for organizations under 25 people). Identifies which standard categories of documentation already exist and which are still missing (database schema, test plan, security/privacy documentation, among others).

**`quants-report-stage4-free-data.html`**
Documents the free data sources usable for prototyping (`jugaad-data` for historical and live NSE data via the exchange's own public website), the explicit caveat that this is unofficial and internal-use-only, and the reasoning for why Greeks/IV are calculated locally rather than sourced externally.

**`market_data_connector.py`**
Reference Python implementation of an adapter-pattern interface (`MarketDataConnector`) so data sources can be swapped without changing downstream code, with a `LicenseStatus` enum and an `assert_safe_to_publish()` method that enforces the build-vs-publish compliance boundary in code.

**`historical_data_store.py`**
Reference Python implementation of a cleaning/validation/persistence layer that consumes `MarketDataConnector` output, rejects malformed data, and ensures license status travels with stored data rather than being lost on write.

**`quants-report-replit-induction.md`**
An onboarding document written specifically for an AI engineering platform (Replit) audience: summarizes the vision, pillars, architecture, founder-validated pain points, already-built code, compliance boundaries that affect code directly, and the recommended first build.

**`quants-report-booking-terms-draft.md`**
A draft terms document for collecting a pre-launch "Founding Access" booking advance from prospective users, structured to fit the Companies Act, 2013 exemption for advances against future goods/services rather than being classified as a deposit, and deliberately excluding any reference to gated, unregistered features.

**`quants-report-stage1-pain-point-discovery.html`**
The pain point discovery record for the project's first formal development stage. Contains an original hypothesis-level draft, and — critically — a later section containing the Founder's own first-person account of real trading losses and frustrations, which is the actual evidentiary basis for selecting the option-chain/Greeks widget as the first build.

**`deepseek-v4-vs-claude-sonnet-4-6.html`**
A factual comparison of two AI models considered for use during prototyping, covering price, benchmark performance, context window, and data-hosting considerations relevant to a regulated financial entity.

---

## 6. Recommended Reading Order

For a new reader joining this project, the following order builds context correctly, each document assuming only what came before it:

1. **`quants-report-knowledge-doc.md`** — orient on what the project is and who is building it.
2. **`quants-report-stage1-pain-point-discovery.html`** — understand why the first feature was chosen; read to the Founder validation section specifically.
3. **`quants-report-pillars.pdf`** — see the full intended product shape and what's deliberately on hold.
4. **`quants-report-architecture-diagram.mermaid`** — view the diagram before reading any prose description of it.
5. **`quants-report-engine-specification.md`** — the authoritative technical detail behind the diagram just viewed.
6. **`quants-report-srs.pdf`** — formal requirements layered on top of the architecture.
7. **`quants-report-crao-review.html`** and **`quants-report-claude-custom-instructions.html`** — process and governance context, useful but not blocking for technical understanding.
8. **`quants-report-v1-codex-brief.md`** — the actual, current build target, now that full context exists to understand why it's scoped the way it is.
9. **`market_data_connector.py`** and **`historical_data_store.py`** — the concrete code patterns the build target must extend.
10. Everything else (booking terms, documentation checklist, model comparison) is reference material, relevant when its specific topic comes up rather than required up front.

---

## 7. How These Documents Relate to One Another

- The **knowledge base** (A) is the stable business/product layer that the **architecture** documents (B) implement and the **requirements** documents (C) formalize into buildable units.
- The **architecture diagram** is the single source of visual truth; the **Engine Specification** is its prose/tabular expansion. Where any other document's architectural description conflicts with these two, the diagram and the Engine Specification win — they are the most recently corrected.
- **Important terminology note for a new reader:** the earlier architecture documents (`quants-report-architecture-vision.html`, `quants-report-architecture.pdf`) describe a five-engine model using the name **"Data Engine."** The Founder's own diagram and the later, authoritative Engine Specification instead use the name **"Storage Engine"** for the engine that owns persistence, with "Data" no longer used as an engine name. These refer to the same role in the architecture, not two different components — but a reader moving between older and newer documents should expect this name change and not assume a discrepancy in function.
- The **SRS** and the **V1 Codex Brief** both describe buildable scope, but at different points in time and different breadth: the SRS describes Pillar 1 broadly; the V1 Brief narrows this further to a single widget and explicitly excludes things the SRS does not rule out (such as AI explanation/narration).
- The **CRAO Review** and the **Custom Instructions** document are process/governance artifacts — they describe how decisions get made and reviewed, not what the product does.
- The **booking terms draft** depends on the compliance reasoning established in the knowledge base and architecture documents (specifically, that registered/gated features must not be referenced as something being sold).
- The two **Python reference modules** are the only artifacts in this repository that are actual code rather than documentation about intended code. The V1 Codex Brief explicitly instructs that these be extended, not replaced.

---

## 8. Glossary

| Term | Meaning |
|---|---|
| Intelligence System | The project's self-description, deliberately contrasted with "a collection of trading tools" — the platform's job is to explain and quantify, not to provide more raw data. |
| Engine | A component with one narrow, well-defined responsibility, communicating with other engines only through the shared database. |
| Widget Layer | The user-facing product layer sitting above the engines; each widget addresses one specific, founder-validated pain point and consumes engine outputs without performing its own calculation or reasoning. |
| Buffer (IN-BUFFER / OUT-BUFFER) | A stateless, temporary holding point inside each engine. Originally called "Room" in early diagrams; renamed to "Buffer" for clarity, since nothing permanently resides there. |
| Processor | The middle stage inside each engine's buffer pair — either a Fixed Calculator or an LLM, never ambiguously either. |
| Fixed Calculator | A deterministic, non-AI calculation component. Process Engine's processor is always this; it is never swappable. |
| LLM Processor | An AI-model-based processing component, swappable via an administrative setting, used in Storage, Knowledge, and Intelligence Engines. |
| License Status | A tag carried by every piece of data describing what it is permitted to be used for (e.g., internal use only, licensed for research, licensed for display, or tied to one user's personal broker access). Enforced in code via `assert_safe_to_publish()`. |
| Build vs. Publish | The core compliance principle: building and internally testing a capability is unrestricted; showing its output to anyone other than the Founder is gated until the relevant registration is complete. |
| Internal Testing | Defined strictly as use confined to the Founder's own account and credentials — not a beta group, however small or trusted. |
| Market Thesis | A proposed product concept: a structured, evolving view on an instrument (direction, confidence, supporting evidence, and explicit invalidation conditions), as an alternative to a simple buy/sell signal. Discussed in depth in conversation; not yet formalized into its own document. |
| BYOB (Bring Your Own Broker) | The model in which each user connects their own broker account and credentials, so the platform consumes data the user is already personally entitled to receive, rather than the platform itself holding a market-data redistribution license. |
| Generation-Tagging | The practice of tagging every AI-generated embedding with which model produced it, so that swapping the embedding model later never causes incompatible vectors to be compared against each other. |
| Database as Communication Bus | The architectural principle that engines never call one another directly; every engine writes to the shared database, and engines read from it as needed. |

---

## 9. Abbreviations

| Abbreviation | Full Form |
|---|---|
| RA | Research Analyst (SEBI registration category) |
| IA | Investment Adviser (SEBI registration category) |
| SEBI | Securities and Exchange Board of India |
| NISM | National Institute of Securities Markets |
| NSE | National Stock Exchange (of India) |
| BSE | Bombay Stock Exchange |
| GDFL | Global Datafeeds (a licensed market data vendor) |
| RAASB | Research Analyst Administration and Supervision Body |
| DPDP Act | Digital Personal Data Protection Act, 2023 |
| CRAO | Chief Risk & Architecture Officer (role held by Claude in this project) |
| CAIO | Chief Architect & Intelligence Officer (parallel AI architect role) |
| MD | Managing Director |
| CIN | Corporate Identity Number |
| DIN | Director Identification Number |
| OI | Open Interest |
| IV | Implied Volatility |
| OHLC | Open, High, Low, Close (price data) |
| SRS | Software Requirements Specification |
| FR / NFR | Functional Requirement / Non-Functional Requirement |
| VSE | Very Small Entity (an ISO/IEC 29110 term, for organizations of 25 people or fewer) |
| LLM | Large Language Model |
| RAG | Retrieval-Augmented Generation |
| ToS | Terms of Service |
| ERD | Entity-Relationship Diagram |
| BYOB | Bring Your Own Broker |
| PMRR | Product Milestone & Risk Review (a document reviewed earlier in this project) |

---

## 10. Known Assumptions — Not Yet Independently Verified

The following are currently treated as true in project decisions, but have not been confirmed against a primary source as of this document:

- That Zerodha's free "Personal" Kite Connect tier covers holdings, positions, and order data without requiring the paid Connect subscription. Repeatedly flagged as something to verify directly on the developer portal; no confirmation is recorded in this documentation set.
- That `jugaad-data`, an unofficial library reading NSE's public website, will continue to function reliably through the prototype phase. Explicitly known to be without any uptime guarantee.
- That the Founder qualifies for the NISM-Series-XV exam via the "five years' relevant experience" alternate eligibility route rather than the postgraduate-qualification route. Plausible given the stated trading background, but not confirmed against NISM's actual eligibility criteria.
- That the WebEyeSoft VPS hosting provider's reliability is acceptable for the prototype phase. Independent reviews found during research were mixed, including at least one report of frequent downtime.
- That the domain `QuantsReport.com` is available for registration. No definitive availability check (e.g., a WHOIS lookup) is recorded; only that no conflicting live site was found in searches.
- That NSE Data & Analytics Limited's "Non-Display Data" and "Paid Analytical Products" licensing categories are a good fit for an analytics platform. This was identified as a promising lead worth a direct inquiry; no quote or confirmation from NSE Data is recorded.
- That the relationship between Capinfy Private Limited and the `capinfy.com` domain (reported by the Founder as real but expired) is fully resolved. This was raised once, accepted on the Founder's word, and not independently re-verified afterward.

---

## 11. Documentation Still Needed

The following have been substantively discussed and decided in conversation, but do **not** yet exist as a written, standalone document:

- **Market Thesis specification** — concept, full lifecycle state model, and confirmation of its data flow (Database → Intelligence Engine → back to Database, routed through Storage Engine).
- **Updated Engine Specification reflecting the separate User Data database** — the decision to split personal/broker data into its own database, distinct from the central database, was made after the current Engine Specification document was finalized, and is not yet reflected in it.
- **Admin Panel specification** — the founder-provided feature list (profile management, user/super-user management, news/knowledge/market-data source management, LLM management, usage monitoring, broker management) exists only as a conversational list, not a formal spec.
- **User login and subscription plan specification** — broker OAuth, the four-tier plan structure, and the explicit rule that Market Thesis/probability features are never paywalled, exist only in conversation.
- **Order routing workflow specification** — the eight-step flow (login through execution-status display) has been described precisely in conversation but not written into its own document.
- **Personal Knowledge Base ("bring your own knowledge") feature specification** — including the ownership-tagging requirement, its storage location, and the UI labeling rule distinguishing user-uploaded content from platform-generated analysis.
- **Investment Adviser registration pathway** — the Research Analyst pathway has been researched in detail (NISM-Series-XV, RAASB registration, Form A). The Investment Adviser pathway, required for any future personalized/portfolio-level feature, has been named but not yet researched to the same depth.
- **Full database schema** (column-level, both databases) — explicitly marked out of scope in the Engine Specification as a separate, follow-on document.
- **Test Plan** — identified as a gap in the Documentation Standards Checklist; still does not exist.
- **Security architecture / threat model**, beyond the general agreement to follow OWASP-aligned practice.
- **Privacy Policy and full Terms of Service** — only a narrow booking-terms draft exists.
- **API specification** — no formal contract yet for what each engine reads or writes, beyond the prose description in the Engine Specification.
- **UI/UX design system** — wireframes or a visual design specification for the Widget Layer do not yet exist.
- **Backup and disaster recovery plan** — backups are agreed in principle; no written schedule or procedure exists.

---

## 12. Master File Index Table

| Filename | Category | Status |
|---|---|---|
| quants-report-knowledge-doc.md | Business/Vision | Current |
| quants-report-knowledge-base.html | Business/Vision | Current |
| quants-report-pillars.pdf | Business/Vision | Current |
| quants-report-architecture-vision.html | Architecture | Superseded in technical detail |
| quants-report-architecture.pdf | Architecture | Superseded in technical detail |
| quants-report-architecture-diagram.mermaid | Architecture | Current, authoritative |
| quants-report-engine-specification.md / .docx | Architecture | Current, authoritative — pending update (see Section 11) |
| quants-report-srs.pdf | Requirements | Current |
| quants-report-v1-codex-brief.md | Requirements | Current, active build target |
| quants-report-crao-review.html | Governance | Current |
| quants-report-claude-custom-instructions.html | Governance | Current |
| quants-report-documentation-standards-checklist.md | Governance | Current |
| quants-report-stage4-free-data.html | Data/Infrastructure | Current |
| market_data_connector.py | Data/Infrastructure | Current, reference code |
| historical_data_store.py | Data/Infrastructure | Current, reference code |
| quants-report-replit-induction.md | Data/Infrastructure | Current |
| quants-report-booking-terms-draft.md | Legal/Commercial | Draft |
| quants-report-stage1-pain-point-discovery.html | Research | Current, complete |
| deepseek-v4-vs-claude-sonnet-4-6.html | Supplementary | Reference only |

*End of Master Index. This document should be updated whenever a new document is added to the repository or an existing one is superseded.*
