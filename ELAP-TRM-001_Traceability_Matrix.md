# ELAP-TRM-001 — Bidirectional Traceability Matrix

**External Liver Assistance Platform**

| Field | Entry |
|---|---|
| Document number | ELAP-TRM-001 |
| Revision | 1.4 |
| Effective date | 03 October 2026 |
| Prepared by | Raj Harsh |
| Scope of this revision | ELAP-DFMEA-001 Rev 1.6, ELAP-DIS-001 Rev 1.5, ELAP-VP-001 Rev 3.4, ELAP-RMP-001 Rev 1.3, ELAP-RMF-001 Rev 1.2 |
| Operating phase | **Decellularization at 4 °C only.** ELAP-RMF-001 section 1.4. |

*Self-directed exercise on an independent design project. Not industry work. Not a controlled document under any quality management system.*

---

## 1. Purpose

ISO 13485:2016 - 7.3.6 and 21 CFR 820.30(f) require design verification to confirm that design outputs meet design inputs. A traceability matrix is how that confirmation is demonstrated rather than asserted.

Traceability is **bidirectional**, and each direction answers a different question:

| Direction | Chain | Question it answers | What it catches |
|---|---|---|---|
| **Forward** | Hazard → failure mode → risk control → requirement → verification → evidence | Has every hazard been controlled, and has every control been verified? | Gaps. A hazard with no control, or a control with no test. |
| **Backward** | Acceptance criterion → requirement → risk control → hazard | Why does this test exist? | Orphans. A test verifying nothing that was specified, and scope creep. |

A matrix that only runs forward finds gaps but not orphans. One that only runs backward finds orphans but not gaps. Both are required.

---

## 2. Identifier scheme

| Prefix | Meaning | Source document |
|---|---|---|
| HAZ- | Hazard | ELAP-RMF-001 Rev 1.0 |
| DF- | Design FMEA line item | ELAP-DFMEA-001 Rev 1.3 |
| RC- | Risk control measure | ELAP-RMF-001 Rev 1.0 |
| REQ- | Design input requirement | ELAP-DIS-001 Rev 1.3 |
| AC- | Acceptance criterion | ELAP-VP-001 Rev 3.2 |
| VP- | Verification protocol | ELAP-VP-001 Rev 3.2 |

**Closed in Rev 1.2.** Rev 1.0 of this matrix recorded that two identifier series in active use — `HAZ-` and `RC-` — had no source document: cited in three published documents and defined in none. ELAP-RMF-001 Rev 1.0 now defines HAZ-001 to HAZ-008 and RC-001 to RC-024, and ELAP-RMP-001 section 8.1 records the assignment rule for each series. The finding stands as a record of what the matrix was for: a reference that resolves nowhere looks fine inside the document that makes it, and only fails when something tries to follow it.

---

## 3. Forward trace — hazard to evidence

| Hazard | Sev | DFMEA items | Risk controls | Requirements | Verification | Evidence | Chain status |
|---|---|---|---|---|---|---|---|
| **HAZ-001** Gas in the perfusion inlet circuit | S4 | DF-010 | RC-001 | REQ-014a/b/c/e | ELAP-VP-001 AC-1/2/3/5 | None — not executed | **Specified end to end. Not verified.** |
| **HAZ-002** Cold external surfaces | S2 | *None* | RC-002 | *None* | *None* | — | Breaks at requirement |
| **HAZ-003** Loss of the sterile barrier | S5 | DF-001, DF-002 | RC-003, RC-004, RC-005, RC-006 | *None* | *None* | — | Breaks at requirement |
| **HAZ-004** Mechanical loading of the organ | S4 | DF-003, DF-005, DF-009 | RC-007, RC-008, RC-009, RC-010 | *None* | *None* | — | Breaks at requirement |
| **HAZ-005** Viability measurement misrepresenting the organ | S5 | DF-007, partial | RC-019, RC-020, RC-021 | *None* | *None* | — | **Out of scope for phase 1** — no hepatocytes, so no bile and no indicator. Live only in phase 3. |
| **HAZ-006** Fluid outside the intended biliary drainage path | **S5** | DF-007 | RC-016, RC-017, RC-018 | *None* | *None* | — | Breaks at requirement. Severity raised in RMF Rev 1.1: retained **detergent** reaches a patient by a route the wash phases do not clear. |
| **HAZ-007** Loss of thermal control of the perfusate | S4 | *None* | RC-022, RC-023, RC-024 | *None* | *None* | — | Breaks at requirement |
| **HAZ-008** Non-physiological pressure or flow distribution | S4 | DF-004, DF-006, DF-008, DF-011 | RC-011 … RC-015 | *None* | *None* | — | Breaks at requirement |
| **HAZ-009** Perfusate cooled toward freezing | S4 | *None* | RC-025, RC-024 | *None* | *None* | — | Breaks at requirement. **Introduced by RC-023** under clause 7.5. |

**The break has moved.** In Rev 1.0, four of six hazards broke at the **risk control** step — they had DFMEA entries and no controls. ELAP-RMF-001 Rev 1.0 defined twenty-four controls, so every hazard now has one. The chain now breaks one link later, at the **requirement** step: twenty-three of twenty-four controls have no requirement in ELAP-DIS-001, and so nothing to verify against.

That is progress of a specific and limited kind. A control that exists only as a sentence in a risk file is not implemented, and the matrix should not be read as saying otherwise.

### 3.1 Derived requirement, outside the hazard chain

| Requirement | Derived from | Verification | Chain status |
|---|---|---|---|
| REQ-014d — inlet tubing bore velocity ceiling | REQ-014b and REQ-014c, per ELAP-DIS-001 Annex A.8 | ELAP-VP-001 AC-4 | Traces to a requirement, not to a hazard. A design constraint propagated backward from a verification limit, not a risk control. Correctly has no HAZ parent. |

---

## 4. Backward trace — acceptance criterion to hazard

| Acceptance criterion | Requirement | Risk control | Hazard | Orphan? |
|---|---|---|---|---|
| AC-1 — detection of a 0.113 mL bolus | REQ-014a | RC-001 | HAZ-001 | No |
| AC-2 — flow halted within 200 ms | REQ-014b | RC-001 | HAZ-001 | No |
| AC-3 — standoff ≥ 450 mm | REQ-014c | RC-001 | HAZ-001 | No |
| AC-4 — bulk velocity ≤ 0.45 m/s | REQ-014d | Derived constraint, not a control | HAZ-001, indirectly via REQ-014b | No |
| AC-5 — no false trigger in 30 minutes | REQ-014e | RC-001, new-risk analysis under ISO 14971 - 7.5 | HAZ-001 | No |

**No orphan tests.** Every acceptance criterion in ELAP-VP-001 traces to a requirement in ELAP-DIS-001. AC-5 was an orphan in an earlier revision of the protocol — it tested a behaviour that no requirement specified — and REQ-014e was written to close it. That correction is recorded in ELAP-DIS-001 Rev 1.3.

---

## 5. Verification of risk control — the second trace

ISO 14971:2019 requires each risk control to be verified twice: that it was **implemented**, and that it is **effective**. A single tick against a control is not sufficient, because a control can be correctly fitted and still not work.

| Risk control | Implementation verified by | Effectiveness verified by | Status |
|---|---|---|---|
| RC-001 | ELAP-VP-001 steps 1, 2, 2a; AC-3 | ELAP-VP-001 steps 6–11; AC-1, AC-2, AC-5 | Both routes specified. Neither executed. |
| RC-002 … RC-025 | *No protocol* | *No protocol* | **24 of 25 controls have no verification route at all.** ELAP-VP-002, which would verify RC-014, is not written. |

---

## 6. Coverage summary

| Measure | Rev 1.0 | Rev 1.2 |
|---|---|---|
| Hazards identified | 6 | **9** |
| Hazards with a DFMEA entry | 5 of 6 | 6 of 9 |
| Hazards with at least one risk control | **1 of 6** | **9 of 9** |
| Hazards with a requirement written | 1 of 6 | **1 of 9** |
| Hazards with a complete chain to a verification protocol | 1 of 6 | **1 of 9** |
| Hazards in scope for the analysed operating phase | — | **8 of 9** — HAZ-005 cannot arise in phase 1 |
| Foreseeable misuse cases identified | 0 | **9** |
| Foreseeable misuse cases with a risk control | — | **0 of 9** |
| Risk controls defined | 1 | **25** |
| Risk controls with a written requirement | 1 of 1 | **1 of 25** |
| Risk controls verified as implemented | 0 | **0 of 25** |
| Risk controls verified as effective | 0 | **0 of 25** |
| Acceptance criteria tracing to a requirement | 5 of 5 | **5 of 5** |
| Orphan tests | 0 | **0** |
| Individual residual risks acceptable | — | **0 of 9** |
| Overall residual risk evaluated | No | **No — and cannot be, per ELAP-RMP-001 section 5** |

---

## 7. Findings

**The risk control gap is closed and the requirement gap has opened.** Rev 1.0's headline finding was that four of six hazards had DFMEA entries and no risk controls. Twenty-four controls now exist. But only one has been written as a requirement, so twenty-three sit in a risk file with nothing in the design input specification obliging the device to have them. A control with no requirement is an intention, not a control.

**Sixteen of twenty-five controls are tier 1.** Inherently safe design rather than protective measures or warnings. One tier 3 control exists and it is a supplement at S5, not relied on. That distribution is the strongest single fact about this design file.

**Two hazards are at S5, and neither has a requirement.** HAZ-003 loss of the sterile barrier and HAZ-005 viability measurement misrepresenting the organ. ELAP-RMP-001 section 4.3 forbids information for safety alone at that severity and requires reduction as far as possible; neither condition can currently be demonstrated.

**Four of nine hazards were not found by the design FMEA.** HAZ-002 and HAZ-007 are outside its scope — it starts from component functions, and neither an operator's hands nor ambient heat ingress is a component. HAZ-006 was found by this matrix's own traceability check in Rev 1.0. HAZ-009 was introduced by a risk control rather than existing in the design at all. That four of nine came from outside the primary method — and one from a control measure — is evidence the hazard set is not demonstrably complete, which ELAP-RMF-001 section 15 records as a limitation.

**Every control that crosses the enclosure boundary degrades HAZ-003.** The RC-001 sensor housing, RC-002 insulation, RC-015 pressure taps and RC-017 bile separation each add an interface to the sterile barrier. This is the clearest interaction between controls in the file and ELAP-RMF-001 section 11 records it as the one that would dominate an overall residual risk evaluation.

**Two controls act on the same parameter in opposite directions.** RC-023 increases cooling to control HAZ-007; RC-025 limits cooling capacity to control HAZ-009. The band satisfying both is undetermined. This is a control conflict rather than a traceability gap, and it is the kind a matrix surfaces by listing controls against hazards side by side.

**Backward traceability remains complete.** Five of five acceptance criteria trace to a requirement; no orphan tests. That has held through three revisions.

**Nothing is verified.** Every chain that exists ends at a written protocol with no executed record. This matrix is evidence of what *would* be verified if the protocols were run.

**A new category of gap, and nothing covers it.** ELAP-RMF-001 Rev 1.1 records nine reasonably foreseeable misuse cases, M-1 to M-9, and **none has a risk control**. These are not failures — the device works correctly and harm follows anyway: a single-use chassis cleaned and reused, a wash phase shortened, an arterial line connected to the portal vein. They need IEC 62366-1 usability engineering, which no document in this set covers. The DFMEA scopes use errors out and the risk file cannot control them alone, so this gap is structural rather than an omission.

**One hazard is out of scope rather than uncontrolled.** HAZ-005 depends on bile output as a viability indicator, and phase 1 has no hepatocytes to produce bile. Recording it as out of scope is different from recording it as a gap, and the distinction matters: the chain is not broken, it does not apply.

---

## 8. What this matrix determines should be built next

The break is now at the requirement step, so the next work is conversion of controls into design inputs — not more analysis.

1. **ELAP-DIS-001 requirements for the two S5 hazards first** — RC-003 to RC-006 under HAZ-003, and RC-019 to RC-021 under HAZ-005. Highest severity, no requirements.
2. **ELAP-DIS-001 requirements for the tier 1 mechanical and hydraulic controls** — RC-007 to RC-014. These are dimensioning decisions and most are blocked only on the open inputs in ELAP-RMF-001 section 12.
3. **ELAP-VP-002**, the chamber vent protocol, verifying RC-014. Blocked on the maximum credible fill rate.
4. **ELAP-GAP-001**, the §7.3 gap assessment. Last, because it assesses the set rather than adding to it.

Two actions are executable now with no hardware and no open inputs, both against the existing CFD model: the worst-case tolerance study for RC-011 and the maximum-offset study for RC-012.

---

## 9. Review and approval

| Role | Name | Signature | Date |
|---|---|---|---|
| Prepared by | Raj Harsh | R.H. | 03 Oct 2026 |
| Reviewed by | | | |
| Approved by | | | |

Independent review and approval cannot be performed in a single-person exercise. Both roles are left unsigned deliberately.

---

## Revision history

| Rev | Date | Description | By |
|---|---|---|---|
| 1.4 | 04 Oct 2026 | Updated for ELAP-RMF-001 Rev 1.2. HAZ-009 added, introduced by risk control RC-023 under clause 7.5 and controlled by RC-025. Counts revised to 9 hazards and 25 controls. Findings record the control conflict between RC-023 and RC-025, which adjust cooling capacity in opposite directions. | Raj Harsh |
| 1.3 | 04 Oct 2026 | Rebuilt against ELAP-RMF-001 Rev 1.1, which adds the intended use and scopes the analysis to decellularization at 4 degC. HAZ-005 marked out of scope for the analysed phase rather than broken, there being no hepatocytes to produce bile. HAZ-006 severity raised to S5. Two measures added to the coverage summary: nine foreseeable misuse cases identified, none controlled. Findings now record use-related risk as a structural gap no document in the set covers. | Raj Harsh |
| 1.2 | 04 Oct 2026 | Rebuilt against ELAP-RMF-001 Rev 1.0. The HAZ- and RC- identifier series now have a source document, closing Rev 1.0's principal finding. Hazard count 6 to 8: thermal split into HAZ-002 and HAZ-007, and the single hazard absorbing seven DFMEA modes split into HAZ-004 mechanical and HAZ-008 hydraulic. Forward trace rebuilt: all 8 hazards now have risk controls, so the chain break moves from the risk control step to the requirement step, with 23 of 24 controls having no design input. Coverage summary now shows Rev 1.0 against Rev 1.2 so the change is visible. Section 8 build order replaced — the next work is converting controls into requirements, not further analysis. | Raj Harsh |
| 1.1 | 04 Oct 2026 | Risk control identifier renumbered from RC-010 to RC-001. The original number mirrored DFMEA item DF-010 and so implied RC-001 to RC-009, none of which was ever defined. Risk control identifiers are now assigned sequentially in order of definition, independently of hazard and DFMEA numbering, so that a single control serving more than one hazard has an honest identifier. Convention recorded in ELAP-RMP-001 section 8.1. Build order in section 8 corrected: ELAP-RMP-001 precedes ELAP-RMF-001, because ISO 14971 Clause 4 defines the risk acceptability criteria that Clause 6 evaluation measures against. ELAP-RMP-001 Rev 1.1 is now published; ELAP-RMF-001 remains unwritten, so the HAZ- and RC- identifier series still have no published source document and the finding in section 2 stands. | Raj Harsh |
| 1.0 | 03 Oct 2026 | Initial issue. Covers ELAP-DFMEA-001 Rev 1.3, ELAP-DIS-001 Rev 1.3 and ELAP-VP-001 Rev 3.2. Records that the HAZ- and RC- identifier series have no source document, that HAZ-006 exists only as a note in the DFMEA, and that four of six hazards break the chain at the risk control step. | Raj Harsh |
