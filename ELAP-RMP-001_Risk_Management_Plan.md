# ELAP-RMP-001 — Risk Management Plan

**External Liver Assistance Platform**

| Field | Entry |
|---|---|
| Document number | ELAP-RMP-001 |
| Revision | 1.4 |
| Effective date | 04 October 2026 |
| Prepared by | Raj Harsh |
| Standard | ISO 14971:2019, Clause 4 |

*Self-directed exercise on an independent design project. Not industry work. Not a controlled document under any quality management system.*

---

## 0. Why this document exists, and why it comes first

ISO 14971:2019 **Clause 4.4** requires a risk management plan, and specifies seven things it must contain. Sections 1 to 7 below are numbered to match those seven requirements so that conformance can be checked rather than asserted.

The plan comes before the risk management file because it defines the **criteria** that risk evaluation measures against. A risk management file written first can identify hazards and estimate risk but cannot evaluate anything — there is nothing to evaluate against.

ELAP-TRM-001 Rev 1.0 lists this document second in its build order and ELAP-RMF-001 first. That ordering was wrong and is corrected in ELAP-TRM-001 Rev 1.1.

---

## 1. Scope (clause 4.4 a)

**Device.** The External Liver Assistance Platform, an ex vivo perfusion system for the **decellularization and subsequent recellularization of a whole human liver**, built around the Vascular Chassis isolation manifold. The intended use is stated in full in **ELAP-RMF-001 section 1.1**, which this plan does not duplicate.

The device is a processing platform, not a therapy. It never contacts a patient; harm reaches a patient only through the scaffold it produces, which is intended for implantation. The recipient is therefore **in scope for harm**, confirmed 04 October 2026.

**Three operating phases at two temperatures:** decellularization at 4 °C, an enzymatic and wash stage at 37 °C, and recellularization at 37 °C under cell culture. Thermal control is a **range** requirement, not a setpoint.

**Life cycle phases covered by this plan.**

| Phase | In scope | Reason |
|---|---|---|
| Design and development | **Yes** | The only phase the project has reached |
| Risk analysis of operating phase 1, decellularization at 4 °C | **Yes** | Analysed in ELAP-RMF-001 Rev 1.1 |
| Risk analysis of operating phases 2 and 3, at 37 °C | **No** | Not analysed. ELAP-RMF-001 section 1.4 records the scope limit and its consequences. |
| Production and process validation | No | No production exists or is planned at this stage |
| Post-production, including market surveillance | No | No units in use; see section 7 |
| Decommissioning and disposal | No | Not analysed; recorded as a gap in section 9 |

**Physical boundary.** Manifold body and internal flow channels; inlet and outlet ports; port isolation features; sealing interfaces; chamber, cradle, base and lid; the chamber vent; the bile drainage path.

**Outside the boundary.** Perfusion pump, tubing set, oxygenator, temperature control equipment, sensors, control software and user interface. The organ scaffold itself and biological variability in it.

This boundary matches ELAP-DFMEA-001 Rev 1.3 section 1 deliberately, so that the two analyses cover the same object.

---

## 2. Responsibilities and authorities (clause 4.4 b)

| Role required by ISO 14971 | Assigned to | Status |
|---|---|---|
| Risk management activities | Raj Harsh | Performed |
| Independent review of risk management | — | **Not available** |
| Top management approval of the risk management plan | — | **Not applicable** — there is no organisation |
| Approval of risk acceptability criteria against a manufacturer policy | — | **Not available** — see section 9 |

**This is the most significant structural limitation of the exercise, and it is not a formality.** ISO 14971 expects risk acceptability criteria to derive from a manufacturer's documented policy, and expects review by someone other than the person who performed the analysis. Neither exists here. Every acceptability judgement in this plan is one person's, unreviewed.

---

## 3. Requirements for review of risk management activities (clause 4.4 c)

Review is required at each of these points, and recorded in the revision history of the affected document:

| Trigger | What is reviewed |
|---|---|
| Completion of a hazard analysis | That hazard, sequence of events, hazardous situation and harm are distinct and correctly assigned |
| Any design change | Whether the change introduces a new hazard, or invalidates an existing risk control or its verification |
| Completion of any verification protocol | Whether the risk control is verified as implemented **and** as effective |
| Adoption of a new risk control measure | New or increased risks the control itself introduces, per clause 7.5 |
| Before publication of any part of the risk management file | That no document cites an identifier defined nowhere |

The last trigger exists because exactly that failure occurred: ELAP-DFMEA-001, ELAP-DIS-001 and ELAP-VP-001 were published citing `HAZ-` and `RC-` identifiers that had no source document. It was found by ELAP-TRM-001, after publication rather than before.

---

## 4. Criteria for risk acceptability (clause 4.4 d)

### 4.1 Severity scale

| Level | Descriptor | Criterion |
|---|---|---|
| **S5** | Catastrophic | Death |
| **S4** | Critical | Life-threatening injury, permanent impairment, or loss of the graft rendering it untransplantable |
| **S3** | Serious | Injury or organ damage requiring medical or surgical intervention |
| **S2** | Minor | Temporary injury or degradation not requiring intervention |
| **S1** | Negligible | Inconvenience or nuisance; no injury |

**Mapping to the ten-point scale used in ELAP-DFMEA-001.** A design FMEA conventionally scores severity 1 to 10; this plan uses five levels. Two scales without a stated mapping is a defect, so the mapping is fixed here:

| This plan | ELAP-DFMEA-001 |
|---|---|
| S5 | 10 |
| S4 | 8 – 9 |
| S3 | 6 – 7 |
| S2 | 4 – 5 |
| S1 | 1 – 3 |

### 4.2 Probability of occurrence of harm — and why it is not used

ISO 14971 estimates risk from severity and the probability of occurrence of harm, which is itself the product of **P1**, the probability of the hazardous situation arising, and **P2**, the probability that the hazardous situation leads to harm.

**Neither P1 nor P2 can be estimated for this device.** No physical unit has been built. There is no test data, no field history, and no predecessor device in this configuration. Any probability figure would be an invention presented as an estimate.

Clause 4.4 d) requires this plan to state criteria for accepting risk **when the probability of occurrence of harm cannot be estimated**. The criteria below are those criteria. Risk is evaluated on **severity alone** until probability can be estimated from test or field data, at which point this plan is revised.

### 4.3 Acceptability criteria

| Severity | Acceptability | Required control |
|---|---|---|
| **S5, S4** | **Not acceptable** without risk control. No tolerable band. | Risk must be reduced as far as possible. Information for safety alone is never sufficient. Inherently safe design or a protective measure is required. |
| **S3** | Not acceptable without risk control. | A protective measure or inherently safe design is required. Information for safety alone is insufficient. |
| **S2** | Acceptable with risk control at any tier, including information for safety. | Control recorded with its reasoning. |
| **S1** | Acceptable without further control. | Recorded, with the reason for accepting it stated. |

**Acceptability and hierarchy are separate requirements.** Where a tier 1 or tier 2 control is practicable it shall be used, per ISO 14971 clause 7.1 priority order, **irrespective of the severity level**. The criteria above determine whether a residual risk is tolerable; they do not authorise a lower control tier. Neither complexity nor cost is a ground for moving down the hierarchy — see section 4.4.

This was added in Rev 1.1. As Rev 1.0 stood, the S2 row read "acceptable with risk control at any tier" and so permitted information for safety alone for an S2 hazard even where inherently safe design was available — which contradicted section 4.4. The conflict surfaced while working HAZ-002, where an operator-contact cold surface was initially controlled by protective gloves despite insulation being practicable and the exterior material still being unselected.

**Consequence for ELAP-DFMEA-001.** That document actions any failure mode with severity ≥ 8 regardless of RPN. On the mapping in 4.1 that is S4 and above — the same rule as this table, expressed on the ten-point scale. The DFMEA's action threshold is therefore a **consequence of this plan**, not a separate rule invented for the DFMEA.

### 4.4 Why there is no ALARP band

Many risk management plans use three zones, with a middle band where risk is tolerated if reduced "as low as reasonably practicable". This plan does not, for two reasons:

- **ISO 14971:2019 removed cost as grounds** for stopping risk reduction. That was a deliberate change from the 2007 edition.
- **EU MDR 2017/745 Annex I GSPR 4** requires risks to be reduced **"as far as possible"** without economic consideration.

A "reasonably practicable" band carries an implicit cost judgement that sits badly against both. Two zones with no tolerable band for high severity avoids the problem.

---

## 5. Method for evaluating overall residual risk (clause 4.4 e)

Individual residual risk is what remains for one hazardous situation after its controls. **Overall residual risk is the risk from the device as a whole**, and it is evaluated separately because many individually acceptable risks can be collectively unacceptable.

**Method.** Once every individual residual risk is acceptable under section 4.3, the set is evaluated together against:

| Consideration | Question |
|---|---|
| Interaction between controls | Does any control defeat, degrade or depend on another? |
| Cumulative severity | Do several independently controlled S4 hazards remain, such that the aggregate probability of a critical outcome is material even if each is individually acceptable? |
| Burden of information for safety | Do the warnings and instructions across the device amount to more than an operator can reasonably follow? |
| Completeness | Has any reasonably foreseeable hazardous situation been omitted rather than evaluated? |

**Criterion.** Overall residual risk is acceptable only when no hazard remains at S4 or S5 without a control verified as both implemented and effective, and none of the four considerations above raises an unresolved concern.

**This conclusion cannot currently be reached.** No risk control in this design file has been verified — ELAP-VP-001 is written and not executed. Overall residual risk is therefore **not evaluated**, and this plan does not claim that it is.

---

## 6. Requirements for verification of risk control measures (clause 4.4 f)

Every risk control requires **two** verifications, separately evidenced:

| Verification | What is confirmed | Why one is not enough |
|---|---|---|
| **Implementation** | The control is present in the device as designed and built | A control can be absent from the build while present in the drawing |
| **Effectiveness** | The control actually reduces the risk it was introduced to reduce | A control can be correctly fitted and still not work — an alarm that is installed but inaudible in the use environment is implemented and ineffective |

Additionally, per clause 7.5, **each control must be analysed for new or increased risks it introduces**, and any new risk goes back through the full cycle of estimation, evaluation and control.

ELAP-VP-001 section 12 is the worked example: it splits implementation and effectiveness onto separate evidence routes, and REQ-014e exists because RC-001 introduces a new risk — a false trigger halting perfusion unnecessarily.

---

## 7. Production and post-production information (clause 4.4 g)

**Not applicable at this stage, and recorded as such rather than omitted.** There is no production, no units in use, no complaints channel and no surveillance data.

If this device proceeded to production, this section would require: complaint handling, feedback from CAPA, production process monitoring, post-market surveillance per EU MDR Article 83, periodic safety update reporting under Article 86, and a defined route by which any of that information triggers re-evaluation of the risk management file.

A required element of clause 4.4 left silently blank is a gap. Marked not applicable with the reason stated, it is a scope decision.

---

## 8. The risk management file

ELAP-RMF-001 is the risk management file. The documents constituting it, and their status:

| Document | Role in the file | Status |
|---|---|---|
| ELAP-RMP-001 | This plan | Rev 1.4 |
| ELAP-RMF-001 | Hazard analysis, risk estimation, risk control, residual risk. Also holds the intended use, foreseeable misuse and safety characteristics. | **Rev 1.2.** Defines `HAZ-001` to `HAZ-009` and `RC-001` to `RC-025`. Scoped to operating phase 1. |
| ELAP-DFMEA-001 | Bottom-up failure mode analysis feeding harms into the file | Rev 1.5 |
| ELAP-DIS-001 | Requirements derived from risk controls | Rev 1.5 |
| ELAP-VP-001 | Verification of RC-001 | Rev 3.4, written, not executed |
| ELAP-TRM-001 | Traceability across the file | Rev 1.4 |

---

## 8.1 Identifier conventions

Each series has exactly one source document. A document may cite an identifier only if that source document defines it.

| Prefix | Meaning | Source document | Assignment rule |
|---|---|---|---|
| HAZ- | Hazard | ELAP-RMF-001 | Sequential in order of identification |
| RC- | Risk control measure | ELAP-RMF-001 | **Sequential in order of definition**, independently of hazard and DFMEA numbering |
| DF- | Design FMEA line item | ELAP-DFMEA-001 | Sequential within the analysis |
| REQ- | Design input requirement | ELAP-DIS-001 | Sequential; lettered suffixes where one requirement splits into several |
| AC- | Acceptance criterion | The verification protocol that contains it | Sequential within that protocol |
| VP- | Verification protocol | Its own document number | Sequential in order of issue |

**Why risk control identifiers are not mirrored from the hazard or the failure mode.** A single control can mitigate more than one hazard — RC-002 addresses HAZ-002 and, through the cleanable surface it introduces, feeds HAZ-003. A mirrored scheme has no honest identifier for that case. A mirrored scheme also implies identifiers that do not exist: RC-010, named after DF-010, implied nine earlier risk controls that were never defined. It was renumbered to RC-001 in Rev 1.1 of this plan and in the four documents citing it.

---

## 9. Open items and limitations

| Item | Consequence |
|---|---|
| No manufacturer risk policy exists | ISO 14971 expects acceptability criteria to derive from a documented organisational policy. The criteria in section 4 are one person's judgement with nothing behind them. |
| No independent review | Every judgement in this plan is unreviewed, including the acceptability criteria themselves. |
| Probability cannot be estimated | Risk is evaluated on severity alone. This is permitted by clause 4.4 d) but it is a weaker evaluation than severity and probability together. |
| No clinical benefit data | Benefit-risk analysis under clause 7.4 cannot be performed. Where a residual risk would need to be weighed against clinical benefit, it cannot be. |
| Decommissioning and disposal not in scope | A real risk management plan would cover the end of life of a single-use device contaminated with biological material and detergent residue. |
| Operating phases 2 and 3 not analysed | ELAP-RMF-001 covers decellularization at 4 °C only. Contamination risk worsens in the 37 °C culture phase, and the thermal hazard inverts. |
| Use-related risk not controlled | ELAP-RMF-001 section 1.2 records nine foreseeable misuse cases, none with a risk control and none planned. Two reach harms assessed at S4 and S5, so the acceptability criteria in section 4.3 are not met for them. IEC 62366-1 usability engineering is outside the scope of every document in this set. |
| Overall residual risk not evaluated | No control is verified, so section 5 defines a method that cannot yet be applied. |

---

## 10. Review and approval

| Role | Name | Signature | Date |
|---|---|---|---|
| Prepared by | Raj Harsh | R.H. | 04 Oct 2026 |
| Reviewed by | | | |
| Approved by | | | |

Independent review and approval cannot be performed in a single-person exercise. Both roles are left unsigned deliberately. See section 2.

---

## Revision history

| Rev | Date | Description | By |
|---|---|---|---|
| 1.4 | 04 Oct 2026 | Document list updated for ELAP-RMF-001 Rev 1.2, which adds HAZ-009 and RC-025. Limitation on use-related risk sharpened to record that two of the nine misuse cases reach S4 and S5 harms, so the acceptability criteria of section 4.3 are not met for them and the decision not to control them is a limitation rather than an acceptability judgement. | Raj Harsh |
| 1.3 | 04 Oct 2026 | Section 1 scope rewritten against the intended use established in ELAP-RMF-001 Rev 1.1: a three-phase decellularization and recellularization platform at two temperatures, so thermal control is a range requirement rather than a setpoint. Recipient confirmed in scope for harm. Lifecycle table now distinguishes operating phase 1, analysed, from phases 2 and 3, not analysed. Three limitations added in section 9: phases 2 and 3 unanalysed, use-related risk uncontrolled, and detergent residue at disposal. | Raj Harsh |
| 1.2 | 04 Oct 2026 | Document list in section 8 updated: ELAP-RMF-001 Rev 1.0 is issued, so the HAZ- and RC- identifier series now have a source document and the gap recorded in Rev 1.1 is closed. | Raj Harsh |
| 1.1 | 04 Oct 2026 | Section 4.3 amended to separate acceptability from control hierarchy: a tier 1 or tier 2 control must be used where practicable irrespective of severity, so the acceptability criteria no longer authorise a lower tier. The conflict with section 4.4 was found while working HAZ-002. Section 8.1 added, recording the identifier conventions and the rule that risk control identifiers are assigned sequentially in order of definition. RC-010 renumbered to RC-001 throughout. | Raj Harsh |
| 1.0 | 04 Oct 2026 | Initial issue. Written against the seven requirements of ISO 14971:2019 clause 4.4, with sections numbered to match. Establishes a five-level severity scale with an explicit mapping to the ten-point scale in ELAP-DFMEA-001. Records that probability of occurrence of harm cannot be estimated for this device and sets severity-only acceptability criteria accordingly, per clause 4.4 d). Two-zone criteria with no ALARP band, on the basis that ISO 14971:2019 removed cost as grounds for stopping risk reduction and EU MDR Annex I GSPR 4 requires reduction as far as possible. Records that overall residual risk cannot be evaluated because no risk control has been verified. | Raj Harsh |
