# Cohort Studio™
### Engineering Brief

**High-Impact Clinical Intelligence Functions — Privacy-Preserving Population Health Analytics Engine**

**Prepared for:** Engineering & Product Stakeholders
**Platform:** Cohort Studio™
**Strategic Focus:** Evidence-Gated Population Health Intelligence
**Date:** July 2026 (updated)

Copyright © 2026 Katherine J. Ombrellaro
*Conceptual platform overview, prepared for strategic discussion. See closing note on scope and validation status.*

---

## Contents

- [Overview](#overview)
- [1. Evidence-Gated Cohort Intelligence](#1-evidence-gated-cohort-intelligence)
- [2. Four-State Clinical Inference Engine](#2-four-state-clinical-inference-engine)
- [3. Cross-Specialty Risk Intelligence](#3-cross-specialty-risk-intelligence)
- [4. Care Gap Intelligence](#4-care-gap-intelligence)
- [5. Real Data Ingestion Architecture](#5-real-data-ingestion-architecture)
- [6. Clinical Risk Factors & WIfI Staging](#6-clinical-risk-factors--wifi-staging)
- [7. Referral Network Intelligence](#7-referral-network-intelligence)
- [8. Aggregate-Only Privacy Architecture](#8-aggregate-only-privacy-architecture)
- [9. MIPS Cost Intelligence](#9-mips-cost-intelligence)
- [10. Scaling Architecture: From Pilot to Platform](#10-scaling-architecture-from-pilot-to-platform)
- [Engineering Differentiator](#engineering-differentiator)
- [About This Briefing](#about-this-briefing)

---

## Overview

Cohort Studio™ is a clinical analytics layer designed to transform fragmented healthcare data into evidence-validated population intelligence. The platform does not replace the EHR or clinical workflow; it provides an analytical framework that identifies high-impact opportunities for quality improvement, care coordination, and CMS Value-Based Care performance.

The core engineering principle is:

> *Compute before display. Evidence before conclusions.*

Rather than presenting raw counts or unvalidated trends, Cohort Studio applies statistical and clinical reasoning before generating executive-level insights. That principle now extends through every layer added since the platform's initial architecture: real data ingestion, clinical risk factors, and referral coordination all follow the same discipline — classify before coercing, disclose what's illustrative versus real, and never fabricate precision a dataset doesn't support.

---

## 1. Evidence-Gated Cohort Intelligence

The platform does not simply find patients — it determines whether a finding is reliable.

Each clinical cohort is evaluated through an analytical evidence gate incorporating:

- Cohort size sufficiency, evaluated with **Student's t intervals** rather than a fixed normal approximation — correctly wider at small n, converging to the standard interval as n grows
- Variance drift against a baseline — **fitted from ingested historical claims when available, illustrative otherwise**, with the source always disclosed rather than presented as uniformly authoritative
- Bayesian evidence evaluation via an exact Beta–Binomial posterior for care-gap prevalence, with an explicitly labeled, weakly-informative, uncalibrated prior

Only statistically supported findings progress to reporting — with one deliberate exception:

**Small-cohort mode.** A population too small for the standard gate (a rural site, a small practice, a narrow filter) is not silently dropped. A dedicated mode surfaces it instead, using a Wilson score interval alongside the exact Beta–Binomial posterior, and an empirical-Bayes shrinkage step that stabilizes the small cohort's estimate toward a broader specialty-wide reference rate — disclosed with its shrinkage weight, never presented as equally precise to a large-sample finding.

### Clinical Impact

Prevents organizations from acting on:

- Unstable small cohorts
- Misleading prevalence estimates
- Random variation mistaken for clinical need
- Silent exclusion of populations too small for a one-size-fits-all threshold

Enables leadership to prioritize interventions supported by measurable evidence, at any population size.

---

## 2. Four-State Clinical Inference Engine

Missing data is treated as information — not just absence.

Traditional analytics often classify missing values as a single condition. Cohort Studio distinguishes:

| State | Meaning |
|---|---|
| Numeric | A valid, in-range clinical observation |
| Absent | Measurement not performed or unavailable |
| Unparseable | Present but malformed — a data-quality problem, not a clinical absence |
| Out-of-range | A valid observation outside the expected threshold — the signal that drives a care-gap flag |

Risk tiers derived from these states — including an explicit "unknown" tier for unmeasured patients — are never defaulted to a low-risk assumption; an unmeasured patient is treated as indeterminate, not reassured-well.

**Direction-aware thresholds.** Not every measure is worse when higher. The engine supports both directions explicitly — HbA1c, CHA₂DS₂-VASc, and systolic BP are worse when higher, while ABI is worse when lower (current cut points: high tier ≤0.75, critical ≤0.50). The tiering, care-gap, and control-rate logic all read a per-specialty `direction` flag rather than assuming one convention.

### Clinical Impact

Allows organizations to differentiate:

- True care gaps
- Incomplete screening
- Documentation problems
- Upstream data failures

*Example: a missing ABI may represent an opportunity for PAD screening, or it may represent an extraction failure. The system prevents these scenarios from being incorrectly combined.*

---

## 3. Cross-Specialty Risk Intelligence

Disease does not occur in specialty silos. Cohort Studio identifies overlapping clinical risk patterns across domains.

### Cardiovascular + Diabetes

- Poor glycemic control
- Cardiovascular risk
- Medication management gaps

### Cardiology + Vascular

- Systemic atherosclerotic disease burden
- PAD risk
- Cardiovascular prevention opportunities

### Vascular + OB-GYN

- Pregnancy-associated vascular risk (preeclampsia, gestational diabetes)
- Postpartum risk follow-up gaps
- Early-life cardiovascular/vascular prevention opportunities

### Vascular + COPD

- Shared smoking-related atherosclerotic and pulmonary risk
- Elevated perioperative and functional risk in combined PAD/COPD populations
- A fourth cross-specialty domain alongside diabetes, cardiovascular disease, and OB-GYN — surfaced with the same toggle-able domain selection

### Primary Care + Specialty Services

- Populations requiring coordinated management

### Clinical Impact

Moves organizations from referral-based thinking toward population-based intervention planning.

---

## 4. Care Gap Intelligence

Converts clinical observations into actionable improvement opportunities. The engine identifies evidence-supported opportunities such as:

| Specialty | Example Opportunity |
|---|---|
| Cardiology | Atrial fibrillation risk management — anticoagulation compliance, direct or claims-inferred |
| Vascular | PAD risk identification, ABI opportunities, and WIfI-based limb-threat staging |
| Endocrinology | HbA1c monitoring gaps |
| OB-GYN | Pregnancy-associated hypertension and vascular risk follow-up |
| Primary Care | Chronic disease management opportunities |

### Clinical Impact

Supports proactive identification of populations most likely to benefit from intervention.

---

## 5. Real Data Ingestion Architecture

The platform is built for real claims and clinical data, not only the synthetic demonstration set it ships with. Three ingestion layers exist, each following the same discipline: classify a value before any numeric coercion, count and disclose what's skipped, and never silently fabricate a default.

### Patient-level extract, keyed by MBI

A CSV of patient-level records — the shape a claims warehouse or registry vendor would export before rolling data up into an aggregate MIPS submission — replaces the synthetic generator for whichever specialties it covers. Recognized columns include the core measure value, claims (with alias normalization — e.g. "statin," "antiplatelet" both resolve to the same internal code), demographics, cost fields, and comorbidity reasons. Cost is built into the same shape the synthetic generator produces, so every downstream view works unmodified regardless of source; rows without cost columns fall back to a clearly-tagged modeled estimate rather than a blank.

### FIN → MBI crosswalk

Clinical and EHR systems commonly key by a facility encounter or financial number (FIN) rather than MBI. A crosswalk ingestion resolves FIN to the same patient token MBI-based ingestion produces, so a risk-factor extract sourced from a clinical system — which may never carry MBI at all — can still join correctly. A FIN with no crosswalk entry is counted as a crosswalk miss and disclosed, never silently dropped or guessed.

### Historical claims, for a fitted baseline

Prior-period claims can be ingested to fit a real baseline variance per specialty, replacing the illustrative constant used for drift detection. A fitted baseline is only trusted once it clears its own minimum-n bar (n ≥ 8) — thin history falls back to the illustrative default rather than presenting a weak fit as solid, and the funding brief and exported evidence always name which source (fitted vs. illustrative) was used.

### Identifier security model

MBI and FIN are **hashed one-way (SHA-256, namespace-separated per identifier type) at the moment a row is read** and never retained in the raw — not in application state, not in browser storage, not in any export. This is explicitly a demo-grade one-way hash, not the keyed, server-held-key HMAC pseudonymisation a production deployment would require — there is no server in this architecture to hold such a key. The synthetic demo tokens use a separate, deliberately *invertible* transform (safe only because a synthetic seed carries no real identity), which is never applied to a real MBI or FIN.

### Clinical Impact

Lets an organization move from demonstration to a real pilot without changing the analytical layer — the evidence gate, referral system, and cost views all operate identically on ingested or synthetic data, because they were built against the same shape from the start.

---

## 6. Clinical Risk Factors & WIfI Staging

A second, joinable ingestion layer captures clinical risk factors — smoking status, hypertension and control status, LDL cholesterol, atrial fibrillation as a vascular risk factor, hypercoagulable state, carotid stenosis, proximal aortic/carotid aneurysm or dissection for vascular; BMI, diabetes duration, nephropathy, and retinopathy for endocrinology; prior stroke/TIA, heart failure history, vascular disease history, and bleeding risk for cardiology; pregestational diabetes, multiple gestation, and prior preeclampsia for OB-GYN — matched to already-ingested patients by hashed MBI or, via the crosswalk, by FIN.

Every field is defined once in a shared, data-driven configuration (key, label, type, applicable specialties) rather than hand-maintained per view, so the ingestion parser, the patient detail display, and the referral packet all read from the same source of truth.

### WIfI (Wound, Ischemia, foot Infection) staging

For vascular patients, the platform computes the three Society for Vascular Surgery WIfI component grades:

- **Ischemia** is derived automatically from the patient's own ABI, using the published hemodynamic thresholds (grade 0: ABI ≥0.80; grade 1: 0.60–0.79; grade 2: 0.40–0.59; grade 3: <0.40) — verified boundary-by-boundary against the primary literature. An override is accepted for extracts that grade ischemia by toe pressure or TcPO₂ instead.
- **Wound** and **foot infection** grades are ingested directly (0–3), when available.

The official composite 1–4 clinical stage is a 64-combination expert-consensus (Delphi) table from the primary publication (Mills et al., *J Vasc Surg* 2014) — **deliberately not reproduced in-app**, since reconstructing a 64-cell clinical staging table from partial secondary sources risks misstating it. The platform surfaces the three verifiable component grades and a "severe component present" flag, with an explicit note directing to the official SVS table or app for the definitive stage.

### Clinical Impact

Enriches the per-patient clinical picture and referral packets without altering tier or gap logic, which remains tied to the measure value and claims exactly as validated — clinical severity is shown alongside the cost-risk view, not silently blended into it.

---

## 7. Referral Network Intelligence

A care-coordination layer sits on top of the cohort engine, reflecting how MIPS actually partitions attribution — by group (TIN) and provider (TIN-NPI) — rather than treating referral as an informal handoff.

- **Suggested routing.** For a vascular patient, the specialty suggestions are ordered by the patient's actual comorbid drivers first (diabetes, cardiovascular, OB-GYN), then the remaining specialties — routing toward the specialty that matches the clinical reason, not a fixed list.
- **Structured packets.** A referral carries risk tier and measure, care-gap flags with routing, MSPB episode cost at the active window, TPCC/HCC risk (or an honest "not available" when no HCC score was ingested), condition/EBCM spend, and clinical risk factors including the WIfI profile — an auto-drafted, editable reason ties the referral to the specific driver found.
- **TIN/NPI attribution.** Every referral records the sending and receiving group and provider identifiers, mirroring how a real MIPS-attributed handoff would be scored.
- **Persistence.** Referrals are saved to per-user storage and restored across sessions, with a clear-all control — distinct from the session-only nature of the rest of the demo state.
- **Boundary discipline.** A referral packet is explicitly a patient-level care-coordination artifact, contrasted throughout the UI with the funding brief's aggregate-only export — the two are never conflated.

### Clinical Impact

Moves specialty coordination from an informal, easily-dropped handoff to a structured, attributable, auditable record — the same evidence and privacy discipline applied to population reporting, applied to the individual handoff.

---

## 8. Aggregate-Only Privacy Architecture

Intelligence without unnecessary exposure of patient identity. The platform separates:

### Clinical Operations

Patient-level workflows remain within appropriate systems.

### Population Intelligence

Executive analytics provide only:

- Cohort size
- Prevalence estimates
- Quality metrics
- Utilization trends
- Financial measures
- Statistical confidence

The reporting layer excludes:

- Names
- Medical record numbers
- Addresses
- Direct identifiers — including MBI and FIN, both hashed one-way on ingest and never retained in the raw (see Section 5)

### Clinical Impact

Enables organizational analytics, quality reporting, and grant-supported population assessment while maintaining privacy boundaries — now extending to real ingested identifiers, not only the synthetic demonstration set.

---

## 9. MIPS Cost Intelligence

Cohort Studio models cost the way CMS actually structures it under MIPS — not a single aggregate dollar figure, but three distinct, risk-adjusted lenses, each disclosed by data source.

### Total Per-Capita Cost (TPCC)

Per-capita cost, CMS-HCC risk-adjusted. The HCC risk score and the observed/expected (O/E) ratio are computed the same way whether the score is a real ingested `hcc_risk_score` or a modeled fallback — but the two are never presented identically: every O/E figure discloses whether it reflects a real risk score or an illustrative one, and patients with no HCC score at all are excluded from the mean/O-E calculation rather than silently coerced to zero.

### Medicare Spending Per Beneficiary (MSPB)

Hospital-episode spend, anchored on an index admission with a **configurable window** — 3-day pre-admission through index only, 30-day, or 90-day post-discharge. Only patients with an admission count as episodes; when the underlying data supplies only a lump-sum inpatient figure (no pre/post breakdown), the platform reports the index-stay cost alone and discloses that the window isn't available, rather than fabricating a plausible-looking split.

### Episode-Based Measures (EBCM)

Specialty-specific procedural measures where they exist — Elective Outpatient PCI for cardiology, Revascularization for Lower-Extremity Chronic Critical Limb Ischemia for vascular — tied to condition-attributed spend. Endocrinology and OB-GYN are framed as TPCC-attributed where no matching CMS episode measure exists, rather than inventing one.

### Avoidable spend, split by care setting

Modeled avoidable acute spend from open care gaps is split between ED and inpatient rather than reported as one figure, since an averted admission and an averted ED visit carry very different cost weight.

### Clinical Impact

Gives a specialty program a real-time view of the cost lens CMS won't return in a feedback report for roughly two years, structured so a physician or CMO can see immediately which figures are grounded in real ingested data and which remain illustrative.

---

## 10. Scaling Architecture: From Pilot to Platform

Sections 2 and 5 describe the ingestion discipline this platform was built with — classify before coercing, disclose what's illustrative versus real, never fabricate precision. The additions below extend that same discipline outward to three specific questions a pilot-to-production transition raises: *does an ingested file actually match what we expect, before we process a single row of it; how do claims and procedure codes get resolved consistently as new sources come online; and how does the platform avoid recomputing the same derived clinical value four different ways in four different views.* Each is built and shipping today; each also has an explicitly scoped next step, described honestly below rather than presented as already in place.

### Event-driven, contract-first ingestion

Claims and procedure-code resolution now runs through an internal typed-event stream rather than inline stat-counting: each code token emits a distinct event as it resolves — mapped, resolved to a standard concept the platform doesn't yet act on, unmapped, matched by exact alias, matched by approximate string similarity, or unmatched — consumed by a default listener that aggregates ingestion statistics, with the same stream available to additional listeners (an audit log, a live coverage view) without touching the parsing logic itself. This is the internal decoupling a server-side, message-bus-based ingestion pipeline would extend at scale — same event contract, additional subscribers — not a claim that a distributed event bus exists today; none does, by design, in a client-side application.

Every ingestion path — patient extract, historical claims baseline, FIN→MBI crosswalk, clinical risk factors — is now gated by a declarative data contract: a required-columns check, run once against the file's header, **before a single row is processed**. A file structurally missing what an ingestion path needs (e.g., no recognizable measure-value column) is rejected immediately with a specific diagnostic naming exactly which column is missing and what would satisfy it — replacing what previously would have been a silent "0 patients ingested" outcome, discoverable only by reverse-engineering skip counters.

A second, independent gate runs after row-level parsing completes: if fewer than a defined floor of rows in a structurally valid file actually yield a usable value, the file is rejected outright rather than silently accepted at near-zero yield. The floor is tuned per ingestion type, not uniform — a 5% minimum for patient extracts, historical baselines, and the FIN→MBI crosswalk, where near-zero yield is a strong signal of a wrong file or a wrong column mapping; a deliberately lower 1% floor for the clinical risk-factor extract, which by design sometimes covers only a narrow, legitimate subset of already-ingested patients.

**Engineering Impact:** these two contract layers target the two most common real-world ingestion failure modes — wrong file, wrong column mapping — catching them at the moment of upload instead of downstream, where they previously would have surfaced only as a suspiciously small or empty cohort with no direct explanation. *A specific downstream-failure-reduction percentage belongs here once measured against real pilot uploads — e.g., the share of previously silent near-empty ingestions this now catches and explains at upload time. That figure is intentionally left unstated rather than estimated in advance; see the closing note on scope and validation status.*

### OMOP-inspired concept mapping

Claim and procedure codes now resolve through a two-stage lookup modeled directly on how a real OMOP Common Data Model deployment resolves a source code to a clinical fact: a source-vocabulary code (RxNorm, CPT, HCPCS) maps to a standard concept, which in turn maps to one of the platform's internal care-gap detection codes. Three distinct outcomes are tracked, not collapsed into one "unrecognized" bucket — a code that resolves cleanly, a code that reaches a real standard clinical concept the platform doesn't yet have gap-detection logic for, and a code that doesn't resolve at all. A string-similarity fallback additionally catches dosage- or frequency-decorated free text that misses an exact match (e.g., "metformin 500mg bid") — though not a true synonym with no surface-form overlap, such as a brand name; that specific gap is the documented rationale for the embedding-based concept-linking service on the roadmap below.

**Current scope, stated plainly:** this is concept-code normalization for claims and procedure codes — it is not conformance with the full OMOP CDM table structure (`PERSON`, `CONDITION_OCCURRENCE`, `MEASUREMENT`, `DRUG_EXPOSURE`, and the rest of the schema), and the standard concept identifiers used today are illustrative placeholders rather than a vendored real-world vocabulary load. Extending to full OMOP CDM conformance — a real vocabulary load, adoption of the complete CDM table set — is a scoped, described next step, not a characteristic of the current build.

### Feature store for optimized cohort query

Every patient attribute the platform computes — the primary clinical measure, ingested risk factors, WIfI component grades, comorbid cross-risk flags, claims-derived care-gap flags, cost and risk-adjustment figures — is now materialized once per patient into a single, entity-keyed, provenance-tagged feature vector, rather than independently recomputed by each view that needs it. This closed a real correctness gap along the way: the WIfI clinical composite had previously been computed separately in four different UI locations, with no structural guarantee all four stayed in sync if the derivation logic changed in only one place.

A feature-coverage view surfaces, per feature and per cohort, how much of the underlying data is ingested, derived, overridden, synthetic, modeled, or genuinely absent — never fabricated to fill a gap — giving a reviewer a direct, aggregate read on data completeness rather than one inferred from scattered skip counts. This single-computation, entity-keyed structure is also what makes a cohort query fast and consistent at scale: a query such as "vascular patients with an overridden ischemia grade" reads one canonical structure once, instead of re-deriving the same answer independently in every view that asks it.

**Current scope, stated plainly:** this is an entity-attribute store, not a full feature-store platform. It has no point-in-time correctness (no timestamped history — every value reflects the current ingestion session, not a specific past date), no offline/online serving split (one in-memory computation, not a training store paired with a low-latency serving layer), and no non-tabular feature types (image, physiologic waveform, time-series, or free-text features). Each of those is a scoped, condition-gated next step — including the specific conditions that would need to be true before building any of them — described in the platform's internal future-state design document.

### Roadmap: multi-modal ingestion and a lakehouse-centric data layer

Two further extensions are designed but deliberately not built, because neither is warranted at current pilot scale:

- **A server-side, embedding-based concept-linking service** — a biomedical-tuned embedding model paired with a vector index, called through a thin API — would close the one gap the client-side string-similarity fallback structurally cannot: catching a true clinical synonym with no surface-form overlap to a known code (a brand name, a differently-phrased diagnosis). This requires infrastructure with no place inside a client-side application — a hosted model, a vector database, an API layer holding credentials — and is scoped as a standalone service the platform would call, not a feature to be built into it directly.
- **Multi-modal feature types** — a vision-model-inferred WIfI wound grade from an ingested photograph, physiologic waveform features (ABI Doppler tracings, ECG rhythm strips), and time-series features (continuous glucose monitoring, home blood-pressure logs) — are designed as extensions to the feature store above, each requiring its own provenance category and, critically, its own privacy review: none of these carry the same re-identification risk profile as a hashed identifier, and none would be safe to build without a de-identification plan specific to binary and high-dimensional data.
- **A lakehouse-centric data layer** (open table formats — Iceberg, Delta, or Hudi — with compute decoupled from storage) is the natural backing store for both extensions above, once real conditions are met: multiple recurring ingestion sources, a genuine need for audit-grade time-travel, a second consuming engine beyond this platform, or a vector/feature corpus that has outgrown ad hoc storage. Adopting one before any of those conditions hold would trade this platform's current simplicity for infrastructure it doesn't yet need — a lakehouse is a response to demonstrated scale, not a default architecture chosen in advance of it.

### Engineering Impact

Event-driven contract-gated ingestion, OMOP-inspired concept mapping, and the entity-keyed feature store each extend the platform's founding discipline — classify before coercing, disclose what's illustrative versus real, never fabricate precision — outward to the ingestion boundary itself. Each capability above is real and shipping; each roadmap item is explicitly scoped and condition-gated rather than assumed inevitable, consistent with how every other capability in this briefing is presented.

---

## Engineering Differentiator

Most healthcare dashboards answer:

> *"What happened?"*

Cohort Studio is designed to answer:

> *"Which population-level opportunities are sufficiently supported by evidence to act upon — and can we prove it, coordinate on it, and pay for it, using the same discipline throughout?"*

By combining:

- Clinical inference
- Statistical validation, including honest treatment of small and rural populations
- Cross-specialty intelligence
- Real data ingestion with the same never-fabricate discipline as the synthetic demonstration set
- Referral coordination structured around real MIPS attribution
- Privacy-preserving analytics, from raw identifier to aggregate report
- A scaling architecture — contract-gated ingestion, OMOP-inspired concept mapping, and an entity-keyed feature store — built to extend, not replace, that same discipline as the platform moves from pilot to production scale

Cohort Studio provides a foundation for proactive population health management and measurable Value-Based Care improvement.

---

## About This Briefing

This briefing describes Cohort Studio™ as a conceptual population health intelligence platform, prepared to support strategic discussion with engineering and product leadership. The analytical patterns described — evidence-gated cohort intelligence, four-state clinical inference, cross-specialty risk identification, real data ingestion, contract-gated scaling architecture, referral coordination, and aggregate-only reporting — reflect the platform's architecture and design intent.

Cohort Studio is not a medical device and is not validated for clinical decision-making. Any organizational deployment would require independent clinical validation, data governance review, and appropriate regulatory and institutional oversight (including IRB review where applicable) prior to use with real patient data. Figures, thresholds, and code sets referenced in supporting materials are illustrative unless drawn from an organization's own validated data. WIfI staging reflects only the three verifiable component grades; the composite 1–4 clinical stage requires the official Society for Vascular Surgery combination table, not reproduced here. Standard concept identifiers referenced in Section 10 are illustrative placeholders, not a vendored OMOP vocabulary load; multi-modal feature types and a lakehouse-centric data layer are described there as a scoped roadmap, not a current capability.

This document is intended for strategic and planning discussions and should not be relied upon as a compliance, coding, or clinical determination.

---

**Platform:** Cohort Studio™
**Architecture:** Evidence-Gated Population Health Intelligence
**Primary Use:** Quality Improvement • Care Coordination • CMS Value-Based Care Analytics
