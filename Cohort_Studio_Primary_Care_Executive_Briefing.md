# Cohort Studio™ for Primary Care
### Executive Briefing

**Population Health Intelligence for Cross-Specialty Care Coordination, Referral Network Visibility, and Value-Based Primary Care**

**Prepared for:** Director of Primary Care
**Platform:** Cohort Studio™
**Strategic Focus:** Making Primary Care the Coordination Hub Across a Multi-Specialty Population
**Date:** July 2026

Copyright © 2026 Katherine J. Ombrellaro
*Conceptual platform overview, prepared for strategic discussion. See closing note on scope and validation status.*

---

## Contents

- [Executive Summary](#executive-summary)
- [Strategic Context: Primary Care Under Value-Based Care](#strategic-context-primary-care-under-value-based-care)
- [Primary Care Population Intelligence](#primary-care-population-intelligence)
- [Primary Care Applications](#primary-care-applications)
- [Specialists as Population Health Partners to Primary Care](#specialists-as-population-health-partners-to-primary-care)
- [Care Gap Intelligence](#care-gap-intelligence)
- [Evidence-First Analytics](#evidence-first-analytics)
- [Privacy-Preserving Architecture](#privacy-preserving-architecture)
- [Value-Based Care Alignment](#value-based-care-alignment)
- [Executive Dashboard for Primary Care Leadership](#executive-dashboard-for-primary-care-leadership)
- [Example Strategic Use Case](#example-strategic-use-case)
- [Why This Matters for Primary Care](#why-this-matters-for-primary-care)
- [Recommended Discussion Topics for Primary Care Leadership](#recommended-discussion-topics-for-primary-care-leadership)
- [Vision](#vision)
- [About This Briefing](#about-this-briefing)

---

## Executive Summary

Primary care is the one place in the system meant to see the whole patient — but in practice, the specialists a
population is referred to (endocrinology, cardiology, vascular, OB-GYN, and others) each hold a piece of the
picture that rarely makes its way back. A diabetic patient's cardiovascular risk, a cardiology patient's vascular
comorbidity, a pregnancy's future vascular risk — these connections exist in the claims and clinical data, but not
in any single view primary care can act on.

Cohort Studio™ runs one shared population-health engine underneath multiple specialty modules, so that
cross-specialty risk, care gaps, and referral coordination surface in one place instead of four disconnected ones —
with primary care positioned as the coordination hub, not a bystander to specialist silos.

Rather than functioning as another specialty point solution or an EHR add-on, Cohort Studio helps primary care
leadership answer strategic questions:

- Which patients carry risk across more than one specialty domain, and who should coordinate their care?
- Where are care gaps occurring across the population my practice is accountable for — not just within one condition?
- How is our referral network actually functioning, and can it route smarter than "refer and hope"?
- Which specialty relationships are creating measurable value, and which are just volume?
- How do we demonstrate our coordination role under value-based, risk-bearing payment arrangements?

The platform transforms clinical measurements, claims information, referral activity, and quality indicators into
privacy-preserving, statistically validated population insight — organized around primary care's actual job:
coordinating, not just receiving referrals.

---

## Strategic Context: Primary Care Under Value-Based Care

Primary care's role under current Medicare value-based arrangements is to hold longitudinal accountability for a
population's outcomes and total cost of care — coordinating what specialists do rather than simply generating
referrals to them. The durable vehicle for this is the **Medicare Shared Savings Program (MSSP)**, alongside
practice-level frameworks like the **Patient-Centered Medical Home** model. The Innovation Center's more
capitation-based models have been considerably less stable: **ACO REACH is in its final performance year (PY
2026)**, with CMS not accepting new applicants and a successor model (**LEAD**, a 10-year design) not beginning
until 2027; two other primary-care-focused CMMI models were **terminated ahead of schedule** in the past year.
That volatility is itself a reason to build population-health infrastructure around durable capabilities —
coordination, gap closure, referral visibility — rather than around any single program's specific mechanics.

Whichever arrangement a given population sits in, the underlying requirement is the same:

- Visibility into risk and gaps across every specialty a population touches, not just one
- A referral process that routes on clinical signal, not just availability
- Defensible, aggregate-level reporting for payer and ACO conversations
- The ability to show coordination is happening, not just assume it

The strategic question for primary care shifts from:

> *"How do we generate and track referral volume?"*

to:

> *"How do we coordinate what happens after the referral, and prove it improved the outcome and the cost?"*

Cohort Studio is built around this second question.

---

## Primary Care Population Intelligence

### From Fragmented Specialty Views to One Coordinated Picture

Under a referral-volume model, primary care typically sees:

- A referral sent, with no structured signal on urgency or comorbid context
- A specialist's note, if and when it comes back, often without the underlying risk detail
- No visibility into whether the specialist flagged an unrelated risk in an adjacent domain
- No aggregate sense of how the whole attributed population is doing across specialties

Cohort Studio enables a coordinated view instead: cross-specialty risk surfaced automatically, referrals routed
with the clinical reason attached, and population-level gap closure tracked across every module — not just the
one a given visit happens to be about.

Potential signals a coordinated view surfaces include:

- A vascular patient's undiagnosed or poorly controlled diabetes
- A cardiology patient's peripheral arterial disease risk
- An endocrinology patient's cardiovascular risk factors going unaddressed
- A pregnancy with risk factors that matter for the mother's vascular health for years afterward
- Smoking status, hypertension control, and lipid data primary care already collects — feeding every specialty
  module that needs them, instead of being re-collected (or missed) at each specialist visit

The objective is not more referrals. The objective is:

> Coordinate the referrals that already happen, with the clinical context that's already known.

---

## Primary Care Applications

### 1. Cross-Specialty Care Gap Visibility

Cohort Studio runs the same absence-inference engine under all four specialty modules — a diagnosis or lab value
is only half the picture; the presence or absence of the expected follow-up claim completes it. For primary care,
this means:

- One place to see care gaps across endocrinology, cardiology, vascular, and OB-GYN populations
- Gaps distinguished from data-quality problems (a missing value routes differently than a malformed one)
- Risk tiers that never default an unmeasured patient to "low risk" — unmeasured stays visibly unmeasured

This turns four separate specialty blind spots into one list primary care can actually work.

### 2. Referral Network Intelligence

This is the feature most directly built for primary care's coordination role. Referrals in Cohort Studio are:

- **Suggested from the comorbid signal itself** — a vascular patient with a diabetes or cardiac driver is routed
  toward the specialty that matches that driver, not left for a specialist to notice independently
- **Attributed the way MIPS actually partitions care** — by TIN and TIN-NPI, group to group, matching how cost
  and quality measures are actually scored
- **Carrying structured clinical detail** — risk tier, care-gap flags, relevant risk factors — instead of a bare
  referral order with no context attached
- **Tracked as a network**, not a series of one-off handoffs — so primary care can see which cross-specialty
  patterns are showing up repeatedly across the population

### 3. The Risk-Factor Data Loop

Primary care is often the natural source of exactly the clinical detail specialist modules need — smoking status,
blood pressure control, BMI, lipids — captured during ordinary primary-care visits, not necessarily recaptured at
every downstream specialist encounter. Cohort Studio's clinical risk-factor layer is built to close that loop: data
primary care already collects feeds directly into the vascular, cardiology, endocrinology, and OB-GYN modules'
risk stratification, rather than each specialty starting from a blank slate.

### 4. Small-Population and Rural Practice Support

A primary care population — especially at a smaller or rural site — often can't produce the sample size a
standard evidence gate requires. Cohort Studio's small-cohort mode applies Student's t intervals, Wilson bounds,
and empirical-Bayes stabilization toward a broader reference rate, so a small population is *surfaced* with
honestly wide uncertainty rather than silently excluded from reporting because n fell short of a fixed threshold.

---

## Specialists as Population Health Partners to Primary Care

### Extending Coordination in Both Directions

Under value-based arrangements, primary care holds longitudinal accountability, but coordination has to run both
ways — specialists need to route relevant findings back, not just receive referrals forward. Cohort Studio
supports this by giving specialty teams the same structured tools to send information *toward* primary care:

- A referral packet that documents the clinical reason, not just "please see"
- Risk factors and comorbid drivers attached automatically, so primary care isn't reconstructing context from a
  faxed note
- A shared evidence standard, so a specialist's population-level finding is validated the same way a primary care
  one would be

The relationship reframes from:

> *"Primary care refers out, specialists report back eventually"*

to:

> *"One coordinated population view, with primary care as the hub."*

---

## Care Gap Intelligence

Cohort Studio identifies evidence-supported opportunities across every specialty a primary care population touches:

| Opportunity | Population Health Impact |
|---|---|
| Missing HbA1c or medication-management claim | Earlier diabetes control, reduced downstream vascular/cardiac risk |
| AFib with no anticoagulation on record | Reduced stroke risk, closed via referral network routing |
| Missing ABI or no statin/antiplatelet on record | Earlier PAD identification, reduced amputation risk |
| Missing postpartum vascular risk follow-up | Earlier identification of pregnancy-associated vascular risk |
| Cross-specialty comorbid drivers unaddressed | Coordinated management instead of four separate blind spots |
| High utilization patterns across any specialty | Reduced avoidable cost, visible at the population level primary care is accountable for |

Each opportunity is evaluated through statistical validation before it reaches an executive or payer-facing report.

---

## Evidence-First Analytics

### Confidence Before Coordination

A coordination strategy built on an unstable or small-sample finding is worse than no strategy — it directs
attention to a pattern that may not be real. Cohort Studio applies an evidence gate before any population finding
is surfaced. Analytics evaluate:

- Cohort size and Student's t-based confidence intervals (correctly wider at small n, not a fixed-width
  approximation)
- Variance drift against a baseline — fitted from ingested historical claims when available, illustrative
  otherwise, and the difference is always disclosed
- Bayesian evidence estimates for care-gap prevalence, with an honestly uncalibrated prior when no reference
  exists
- A dedicated small-cohort mode for populations too small for the standard gate, rather than silent exclusion

Primary care leadership receives validated coordination opportunities, not unstable observations dressed up as
findings.

---

## Privacy-Preserving Architecture

Cohort Studio separates clinical operations from executive and payer-facing analytics, and is built around real
data ingestion rather than a closed demo:

### Clinical Layer

Supports patient care, referral coordination, and clinical decision-making at the point of care.

### Ingestion Layer

Accepts patient-level claims extracts keyed by MBI (the real Medicare identifier), and clinical/EHR-sourced risk
factor data that's often keyed differently — by a facility encounter or financial number (FIN) rather than MBI.
A crosswalk resolves the two. Both identifiers are **hashed one-way at the moment of ingestion and never retained**
in the raw — not logged, not exported, not recoverable from the stored token.

### Analytical Layer

Provides population risk prevalence, care-gap frequency, referral network patterns, utilization trends, and cost
analysis — aggregate by construction.

Executive and payer-facing reporting excludes patient names, medical record numbers, addresses, and all direct
identifiers. The organization gains coordination intelligence without unnecessary exposure of Protected Health
Information.

---

## Value-Based Care Alignment

Cohort Studio supports primary care's coordination role across the domains that matter under MSSP and similar
risk-bearing arrangements.

### Quality Performance

- Cross-specialty care-gap closure, not just single-condition metrics
- Referral network completion and follow-through, not just referral volume
- Population-level risk identification, including small and rural sub-populations

### Cost Stewardship

- Total per-capita cost (TPCC) and hospital-episode spend (MSPB), CMS-HCC risk-adjusted, with the data source
  (fitted from real claims vs. illustrative default) always disclosed
- Avoidable acute spend modeled from open care gaps, split between ED and inpatient
- Aggregate reporting suitable for ACO, payer, or board-level review

### Organizational Impact

Primary care leadership can demonstrate coordination is actually happening — not assumed — across every specialty
the attributed population touches.

---

## Executive Dashboard for Primary Care Leadership

A primary-care-level dashboard could provide:

### Population Overview
- Cross-specialty risk prevalence across the attributed population
- Referral network volume and routing patterns
- Small/rural sub-population coverage, honestly labeled by evidence mode

### Coordination Opportunities
- Care gaps by specialty and by cross-specialty overlap
- Referral packets sent, with attached clinical detail, by receiving specialty

### Value-Based Care Metrics
- TPCC and MSPB, risk-adjusted, disclosed by data source
- Avoidable acute spend, split ED vs. inpatient
- Gap-closure rate as the quality-side companion to the cost view

---

## Example Strategic Use Case

### Coordinating a Cross-Specialty Risk Finding

**Traditional model**

- Vascular surgeon identifies a patient with critical limb ischemia risk and a comorbid diabetes driver
- A referral to endocrinology is sent, or isn't, depending on whether anyone thinks to make it
- Primary care learns about the coordination, if at all, well after the fact
- No population-level record of how often this pattern occurs

**Cohort Studio model**

- The vascular module surfaces the comorbid diabetes driver automatically as part of the patient's risk profile
- A referral to endocrinology is suggested with the clinical reason and risk factors attached
- The referral is attributed by TIN/NPI and logged as part of the coordinated network, visible to primary care
- The pattern — how often vascular and endocrinology risk co-occur in this population — becomes a population-level
  finding, not an anecdote

The result is a referral network primary care can actually see and manage, instead of a black box downstream of
the initial visit.

---

## Why This Matters for Primary Care

Cohort Studio positions primary care as the actual coordination hub value-based arrangements assume it is,
rather than a pass-through for specialist referrals. Potential benefits include:

- One view across every specialty a population touches, instead of four fragmented ones
- A referral network that routes on clinical signal and is visible end-to-end
- Defensible, aggregate population reporting for ACO, payer, and board conversations
- Honest treatment of small and rural sub-populations instead of silent exclusion
- A closed loop on risk-factor data primary care already collects
- Durable infrastructure that doesn't depend on any single CMMI model's continuation

---

## Recommended Discussion Topics for Primary Care Leadership

### Current State Assessment
- How is cross-specialty risk currently identified — if at all — in our attributed population?
- What does our referral network actually look like end-to-end, and who can see it?

### Coordination Opportunities
- Which specialty combinations show up most often in our population, and are they being coordinated today?
- Where is risk-factor data being recollected at each specialty visit instead of shared once?

### Value-Based Care Strategy
- Which value-based arrangement(s) is our population currently in, and what does each require from coordination?
- How would we demonstrate coordination — not just referral volume — to a payer or ACO partner?

### Analytics Deployment
- What claims and EHR data sources would need to feed this (MBI-level extracts, FIN-keyed clinical data)?
- What governance review would ingestion require before any real population is touched?

---

## Vision

The future of primary care under value-based arrangements isn't defined by how many referrals it generates — it's
defined by how well it coordinates what happens across every specialty a population touches, and whether it can
prove that coordination improved outcomes and cost.

Cohort Studio provides primary care leadership with a privacy-preserving intelligence layer that connects
cross-specialty risk, a real referral network, and value-based reporting — built to outlast any single payment
model's specific rules, because the underlying job (coordinate, don't just refer) doesn't change even when the
programs do.

---

## About This Briefing

This briefing describes Cohort Studio™ as a conceptual population health intelligence platform, prepared to
support strategic discussion with primary care leadership. The analytical patterns described — evidence-gated
cohort intelligence, four-state clinical inference, cross-specialty risk identification, referral network
coordination, and aggregate-only reporting — reflect the platform's architecture and design intent.

Cohort Studio is not a medical device and is not validated for clinical decision-making. Any organizational
deployment would require independent clinical validation, data governance review, and appropriate regulatory and
institutional oversight (including IRB review where applicable) prior to use with real patient data. Figures,
thresholds, and code sets referenced in supporting materials are illustrative unless drawn from an organization's
own validated data. References to CMS value-based care programs reflect their status as of mid-2026 and are
provided for strategic context, not as compliance, actuarial, or program-participation advice — program rules and
availability change and should be confirmed directly with CMS or a qualified advisor before any decision relying
on them.

This document is intended for strategic and planning discussions and should not be relied upon as a compliance,
coding, or clinical determination.

---

**Prepared for:** Director of Primary Care
**Platform:** Cohort Studio™
**Strategic Focus:** Making Primary Care the Coordination Hub Across a Multi-Specialty Population
