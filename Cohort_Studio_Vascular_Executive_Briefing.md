# Cohort Studio™ for Vascular Services
### Executive Briefing

**Population Health Intelligence for Vascular Disease Management, Care Coordination, and Value-Based Care**

**Prepared for:** Director, Vascular Services
**Platform:** Cohort Studio™
**Strategic Focus:** Facilitating Value-Based Care Through Population Health Intelligence
**Date:** July 2026

Copyright © 2026 Katherine J. Ombrellaro
*Conceptual platform overview, prepared for strategic discussion. See closing note on scope and validation status.*

---

## Contents

- [Executive Summary](#executive-summary)
- [Strategic Context: Vascular Medicine in Value-Based Care](#strategic-context-vascular-medicine-in-value-based-care)
- [Vascular Population Intelligence](#vascular-population-intelligence)
- [Vascular Services Applications](#vascular-services-applications)
- [Supporting Primary Care Partnerships](#supporting-primary-care-partnerships)
- [Care Gap Intelligence](#care-gap-intelligence)
- [Evidence-First Analytics](#evidence-first-analytics)
- [Privacy-Preserving Architecture](#privacy-preserving-architecture)
- [Value-Based Care Alignment](#value-based-care-alignment)
- [Executive Dashboard for Vascular Leadership](#executive-dashboard-for-vascular-leadership)
- [Example Strategic Use Case](#example-strategic-use-case)
- [Why This Matters for Vascular Services](#why-this-matters-for-vascular-services)
- [Recommended Discussion Topics for Vascular Leadership](#recommended-discussion-topics-for-vascular-leadership)
- [Vision](#vision)
- [About This Briefing](#about-this-briefing)

---

## Executive Summary

Vascular disease represents one of the clearest examples of why healthcare organizations are transitioning from episodic specialty care toward population-based management models.

Peripheral arterial disease (PAD), cardiovascular disease, diabetes, and associated vascular risk conditions often remain underdiagnosed until advanced disease develops. Traditional specialty workflows frequently identify patients only after referral, symptomatic progression, or acute utilization events.

Cohort Studio™ provides a population health intelligence layer that enables vascular programs to identify disease burden earlier, quantify unmet clinical need, and support coordinated intervention across primary care and specialty services.

Rather than functioning as a referral-generation platform or replacing existing clinical systems, Cohort Studio helps vascular leaders answer strategic questions:

- Where does vascular disease risk exist within our attributed population?
- Which care gaps represent opportunities for quality improvement?
- Which populations contribute to avoidable utilization and cost?
- Where can vascular expertise improve outcomes under CMS Value-Based Care models?
- How can vascular services demonstrate measurable organizational impact?
- Which limbs carry the highest amputation risk, and how is that risk staged and communicated?

The platform transforms clinical measurements, claims information, utilization patterns, and quality indicators into privacy-preserving, statistically validated population insights.

---

## Strategic Context: Vascular Medicine in Value-Based Care

CMS Value-Based Care increasingly rewards healthcare organizations for improving outcomes across defined populations rather than increasing procedural volume.

For vascular services, strategic success depends on:

- Earlier identification of vascular risk
- Prevention of disease progression
- Improved chronic disease management
- Reduced avoidable emergency utilization
- Coordinated management with primary care
- Measurable improvement in quality outcomes

The central question shifts from:

> *"How can we increase referrals to vascular services?"*

to:

> *"How can vascular expertise improve population outcomes, reduce total cost of care, and close measurable care gaps?"*

Cohort Studio is designed around this population health model.

---

## Vascular Population Intelligence

### Moving From Reactive Identification to Proactive Risk Identification

Traditional vascular care pathways often identify patients after:

- Claudication develops
- Wounds become difficult to heal
- Vascular imaging is ordered
- Emergency utilization occurs
- Complications require intervention

Cohort Studio enables organizations to identify populations with elevated vascular risk before advanced disease progression.

Potential signals include:

- Abnormal or missing ABI measurements
- Diabetes burden
- Cardiovascular disease history
- Hypertension
- Smoking-related risk indicators
- Prior vascular events
- History of preeclampsia or gestational hypertension
- History of gestational diabetes
- Utilization patterns
- Medication management gaps

The objective is not indiscriminate referral. The objective is:

> Identify where targeted clinical intervention can improve population outcomes.

---

## Vascular Services Applications

### 1. Peripheral Arterial Disease Population Identification

Cohort Studio can support identification of populations requiring further evaluation through:

- PAD risk stratification
- ABI measurement opportunities
- Diabetes-associated vascular risk assessment
- Cardiovascular risk integration

This enables vascular programs to better understand:

- Estimated disease burden
- Potentially unidentified populations
- Geographic or organizational variation
- Opportunities for preventive intervention

### 2. Diabetes and Vascular Risk Integration

Diabetes is a major driver of vascular complications.

Cohort Studio connects vascular intelligence with metabolic risk by identifying overlapping populations with:

- Diabetes
- Poor glycemic control
- Peripheral vascular risk
- Medication management gaps
- Increased utilization

This supports coordinated approaches between:

- Primary care
- Endocrinology
- Cardiology
- Vascular medicine

### 3. Cardiovascular-Vascular Risk Intersection

Many vascular patients exist within broader cardiovascular disease pathways.

The platform identifies overlapping populations involving:

- Atrial fibrillation
- Cardiovascular disease
- Hypertension
- Vascular disease
- Stroke risk

This allows vascular services to participate in broader organizational strategies for:

- Cardiovascular prevention
- Chronic disease management
- Utilization reduction

### 4. Vascular Risk Intersection with OB-GYN

Pregnancy-associated conditions are increasingly recognized — including in AHA and ACOG guidance — as early indicators of future cardiovascular and vascular risk, often preceding traditional risk factors by years.

The platform identifies overlapping populations involving:

- Prior preeclampsia or eclampsia
- Gestational hypertension
- Gestational diabetes
- Gaps in postpartum vascular risk follow-up

This allows vascular services to participate in coordinated strategies for:

- Early-life vascular risk identification
- OB-GYN and primary care partnership
- Prevention-focused, sex-specific risk stratification

### 5. Vascular-COPD Risk Intersection

Smoking is the shared root cause behind both atherosclerotic vascular disease and chronic obstructive pulmonary disease, and the two commonly co-occur in the same patient. Cohort Studio treats COPD as a fourth cross-specialty comorbid domain alongside diabetes, cardiovascular disease, and OB-GYN risk — surfaced through the same toggle-able domain selection used for the others.

This supports identification of:

- Combined PAD/COPD populations carrying elevated perioperative and functional risk
- Shared smoking-cessation intervention opportunities across both conditions
- A more complete comorbidity picture feeding the population's overall risk stratification

### 6. WIfI Limb-Threat Staging

For patients at risk of chronic limb-threatening ischemia, the platform computes the three component grades of the Society for Vascular Surgery's WIfI (Wound, Ischemia, foot Infection) classification:

- **Ischemia** — derived automatically from the patient's own ABI, using the published hemodynamic grading thresholds, so no additional data entry is required for this component
- **Wound** and **foot infection** — graded 0–3 when ingested from clinical or wound-care documentation

Consistent with the platform's evidence-first design, the official 1–4 composite clinical stage — a 64-combination expert-consensus table from the original SVS publication — is **not reproduced in-app**. Reconstructing a clinical staging table of that complexity from partial sources risks misstating it. Cohort Studio instead surfaces the three verifiable component grades and flags when a severe (grade 3) component is present, directing to the official SVS table or app for the definitive stage and amputation-risk estimate — accurate and useful without overstating what's been computed.

### 7. Clinical Risk Factor Intelligence

Beyond the core ABI measure, the platform ingests the clinical risk factors vascular leadership identified as most relevant to population risk stratification:

- Smoking status
- Hypertension and control status
- LDL cholesterol
- Atrial fibrillation, as a vascular risk factor
- Hypercoagulable state / clotting disorder
- Carotid stenosis, from duplex imaging
- Proximal aortic or carotid aneurysm or dissection

These enrich the per-patient clinical picture and are included in referral packets sent to other specialties — so a receiving cardiologist or endocrinologist sees the relevant risk factors already gathered, not just a bare referral order.

---

## Supporting Primary Care Partnerships

### Vascular Services as a Population Health Partner

Under Value-Based Care, primary care remains responsible for longitudinal population management. Specialists contribute expertise where it improves outcomes.

Cohort Studio supports this relationship with a structured referral network, not an informal handoff:

- Referral targets are **suggested from the patient's own comorbid drivers** — a vascular patient with a diabetes or cardiac signal is routed toward the specialty that matches it
- Referrals are **attributed by TIN and TIN-NPI**, mirroring how MIPS actually partitions care between groups and providers
- A referral packet carries the risk tier, care-gap flags, relevant cost detail, and clinical risk factors (including the WIfI profile where available) — structured detail, not a bare order

The platform reframes specialty contribution from:

> *"Receiving referrals"*

to:

> *"Helping the organization improve measurable health outcomes."*

---

## Care Gap Intelligence

Cohort Studio identifies evidence-supported opportunities such as:

| Opportunity | Population Health Impact |
|---|---|
| Missing ABI assessment | Earlier PAD identification |
| Poor diabetes control | Reduced vascular complications |
| Cardiovascular risk gaps | Improved prevention |
| Medication management gaps | Improved chronic disease control |
| High utilization patterns | Reduced avoidable cost |
| Missing postpartum vascular risk follow-up | Earlier identification of pregnancy-associated vascular risk |
| Severe WIfI component (wound, ischemia, or infection) with no vascular follow-up | Earlier limb-salvage intervention, reduced amputation risk |
| Uncontrolled risk factors (smoking, uncontrolled hypertension, elevated LDL) | Targeted prevention alongside PAD management |

Each opportunity is evaluated through statistical validation before executive reporting.

---

## Evidence-First Analytics

### Confidence Before Action

Healthcare organizations often face a challenge: a reported trend does not always represent a meaningful clinical signal.

Cohort Studio applies an evidence gate before displaying organizational findings. Analytics evaluate:

- Cohort size, using Student's t-based confidence intervals that widen appropriately at small n rather than a fixed-width approximation
- Statistical confidence
- Uncertainty
- Variance drift against a baseline — fitted from real historical claims when available, illustrative otherwise, with the source always disclosed
- Bayesian evidence estimates
- Stability over time

A dedicated **small-cohort mode** extends this to rural sites and small practices: rather than excluding a population that falls short of the standard evidence threshold, it surfaces the finding with a Wilson interval and empirical-Bayes stabilization toward a broader reference rate — honestly wide, but visible instead of silently dropped.

Leadership receives validated opportunities rather than unstable observations.

---

## Privacy-Preserving Architecture

Cohort Studio separates:

### Clinical Operations

Patient-level workflows remain within appropriate clinical systems. Examples:

- Patient outreach
- Provider communication
- Clinical decision-making
- Referral management

### Population Intelligence

Executive analytics contain only aggregate information. Examples:

- Vascular risk prevalence
- Care gap frequency
- Utilization trends
- Cost patterns
- Quality measures

No executive report contains:

- Patient identifiers
- Medical record numbers
- Addresses
- Direct identifiers

The platform is built to accept real patient-level claims extracts (keyed by MBI) and clinical risk-factor data (keyed by a facility encounter/financial number, resolved to the correct patient through a crosswalk) — not only the synthetic demonstration set. Both identifier types are hashed one-way at the moment of ingestion and never retained in the raw.

---

## Value-Based Care Alignment

Cohort Studio supports vascular program alignment with CMS priorities.

### Quality Performance

Potential measures include:

- Disease identification
- Preventive intervention opportunities
- Chronic disease control
- Care gap closure

### Cost Stewardship

Analytics support understanding of:

- Emergency department utilization
- Inpatient utilization
- Avoidable complications
- Total cost of care
- Observed versus expected expenditures

### Organizational Impact

Vascular leadership can demonstrate:

- Population need
- Intervention opportunities
- Quality improvement contribution
- Financial impact

---

## Executive Dashboard for Vascular Leadership

A vascular services dashboard could provide:

### Population Overview

- Vascular disease prevalence
- PAD risk population
- Diabetes-associated vascular risk
- Cardiovascular overlap
- Pregnancy-associated vascular risk (OB-GYN overlap)
- COPD overlap
- WIfI severe-component prevalence, where wound/infection data is available
- Clinical risk-factor coverage (smoking, hypertension control, LDL) across the population

### Quality Opportunities

- Screening gaps
- Management gaps
- Preventive opportunities

### Operational Intelligence

- Referral patterns
- Utilization trends
- Intervention opportunities

### Value-Based Care Metrics

- Cost trends
- Avoidable utilization
- Quality improvement impact

---

## Example Strategic Use Case

### Identifying Undetected PAD Risk

**Traditional model**

- Patient develops symptoms
- Primary care identifies concern
- Referral occurs
- Vascular evaluation begins

**Cohort Studio model**

- Population analytics identify elevated PAD risk
- Evidence validation confirms a statistically meaningful cohort
- Primary care receives actionable population insight
- Appropriate vascular evaluation pathways are activated
- Outcomes and utilization are measured

The result is movement from reactive specialty care toward proactive population management.

---

## Why This Matters for Vascular Services

Cohort Studio enables vascular programs to become strategic partners in organizational health improvement. Potential benefits include:

- Earlier disease identification
- Stronger primary care relationships
- Improved multidisciplinary coordination
- Measurable quality contributions
- Improved CMS Value-Based Care performance
- Better understanding of population needs
- Evidence-based program development

---

## Recommended Discussion Topics for Vascular Leadership

### Current State Assessment

- How is vascular disease burden currently measured?
- What populations remain unidentified?

### Population Opportunities

- Which conditions represent the highest opportunity for intervention?
- Where are care gaps occurring?

### Primary Care Integration

- How can vascular expertise support attributed populations?

### Value-Based Care Strategy

- Which vascular interventions influence quality and total cost?

### Analytics Deployment

- What existing data sources could support implementation?

---

## Vision

The future of vascular services is not defined only by procedural excellence. It is defined by the ability to improve vascular health across entire populations.

Cohort Studio provides vascular leaders with a privacy-preserving intelligence platform that connects clinical expertise, population health strategy, and CMS Value-Based Care objectives.

By transforming fragmented clinical information into statistically validated population insight, vascular programs can move from reactive disease treatment toward proactive prevention, coordinated management, and measurable organizational impact.

---

## About This Briefing

This briefing describes Cohort Studio™ as a conceptual population health intelligence platform, prepared to support strategic discussion with vascular services leadership. The analytical patterns described — evidence-gated cohort intelligence, four-state clinical inference, cross-specialty risk identification, and aggregate-only reporting — reflect the platform's architecture and design intent.

Cohort Studio is not a medical device and is not validated for clinical decision-making. Any organizational deployment would require independent clinical validation, data governance review, and appropriate regulatory and institutional oversight (including IRB review where applicable) prior to use with real patient data. Figures, thresholds, and code sets referenced in supporting materials are illustrative unless drawn from an organization's own validated data.

This document is intended for strategic and planning discussions and should not be relied upon as a compliance, coding, or clinical determination.

---

**Prepared for:** Director, Vascular Services
**Platform:** Cohort Studio™
**Strategic Focus:** Facilitating Value-Based Care Through Population Health Intelligence
