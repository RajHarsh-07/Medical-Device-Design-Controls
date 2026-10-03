# ELAP-TRM-001 — Bidirectional Traceability Matrix

**External Liver Assistance Platform**

| Field | Entry |
|---|---|
| Document number | ELAP-TRM-001 |
| Revision | 1.0 |
| Effective date | 03 October 2026 |
| Prepared by | Raj Harsh |
| Scope of this revision | The design control artefacts that exist: ELAP-DFMEA-001 Rev 1.3, ELAP-DIS-001 Rev 1.3, ELAP-VP-001 Rev 3.2 |

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
| HAZ- | Hazard | ELAP-RMF-001 — **does not yet exist** |
| DF- | Design FMEA line item | ELAP-DFMEA-001 Rev 1.3 |
| RC- | Risk control measure | ELAP-RMF-001 — **does not yet exist** |
| REQ- | Design input requirement | ELAP-DIS-001 Rev 1.3 |
| AC- | Acceptance criterion | ELAP-VP-001 Rev 3.2 |
| VP- | Verification protocol | ELAP-VP-001 Rev 3.2 |

**Finding, recorded by this matrix.** Two of the six identifier series in active use — HAZ- and RC- — have no source document. They are cited in three published documents but defined in none. Building this matrix is what made that visible: a reference that resolves nowhere looks fine inside the document that makes it and only fails when something tries to follow it.

---

## 3. Forward trace — hazard to evidence

| Hazard | DFMEA item | Risk control | Requirement | Verification | Evidence | Chain status |
|---|---|---|---|---|---|---|
| **HAZ-001** Gas in the perfusion circuit reaching the organ vasculature | DF-010 (S 9, O 5, D 8, RPN 360) | RC-010 — inlet-line gas detection with pump interlock | REQ-014a, REQ-014b, REQ-014c, REQ-014e | ELAP-VP-001, AC-1, AC-2, AC-3, AC-5 | None. Protocol written, not executed. | **Specified end to end. Not verified.** |
| **HAZ-002** Thermal | *No DFMEA entry* | — | — | — | — | **Not analysed.** Thermal performance is out of scope of ELAP-DFMEA-001 Rev 1.3 section 1, and is not analysed elsewhere. |
| **HAZ-003** Contamination of perfusate; infection risk | DF-001, DF-002 | *None defined* | *None* | *None* | — | **Breaks at risk control.** Both DFMEA items carry recommended actions; neither has been converted into a control. |
| **HAZ-004** Loss of perfusion, mechanical and ECM damage to the organ | DF-003, DF-004, DF-005, DF-006, DF-008, DF-009, DF-011 | *None defined* | *None* | *None* | — | **Breaks at risk control.** Seven failure modes, five of them actioned, no controls defined. |
| **HAZ-005** Erroneous measurement | DF-007 (partial) | *None defined* | *None* | *None* | — | **Breaks at risk control**, and the hazard only partially covers the failure effect — see HAZ-006. |
| **HAZ-006** Biliary obstruction and bile contamination of the perfusate | DF-007 | *None defined* | *None* | *None* | — | **Not yet in the risk file.** Identified by ELAP-DFMEA-001 and not yet written up. |

### 3.1 Derived requirement, outside the hazard chain

| Requirement | Derived from | Verification | Chain status |
|---|---|---|---|
| REQ-014d — inlet tubing bore velocity ceiling | REQ-014b and REQ-014c, per ELAP-DIS-001 Annex A.8 | ELAP-VP-001, AC-4 | Traces to a requirement, not to a hazard. It is a design constraint propagated backward from a verification limit, not a risk control. Correctly has no HAZ parent. |

---

## 4. Backward trace — acceptance criterion to hazard

| Acceptance criterion | Requirement | Risk control | Hazard | Orphan? |
|---|---|---|---|---|
| AC-1 — detection of a 0.113 mL bolus | REQ-014a | RC-010 | HAZ-001 | No |
| AC-2 — flow halted within 200 ms | REQ-014b | RC-010 | HAZ-001 | No |
| AC-3 — standoff ≥ 450 mm | REQ-014c | RC-010 | HAZ-001 | No |
| AC-4 — bulk velocity ≤ 0.45 m/s | REQ-014d | Derived constraint, not a control | HAZ-001, indirectly via REQ-014b | No |
| AC-5 — no false trigger in 30 minutes | REQ-014e | RC-010, new-risk analysis under ISO 14971 - 7.5 | HAZ-001 | No |

**No orphan tests.** Every acceptance criterion in ELAP-VP-001 traces to a requirement in ELAP-DIS-001. AC-5 was an orphan in an earlier revision of the protocol — it tested a behaviour that no requirement specified — and REQ-014e was written to close it. That correction is recorded in ELAP-DIS-001 Rev 1.3.

---

## 5. Verification of risk control — the second trace

ISO 14971:2019 requires each risk control to be verified twice: that it was **implemented**, and that it is **effective**. A single tick against a control is not sufficient, because a control can be correctly fitted and still not work.

| Risk control | Implementation verified by | Effectiveness verified by | Status |
|---|---|---|---|
| RC-010 | ELAP-VP-001 steps 1, 2, 2a; AC-3 | ELAP-VP-001 steps 6–11; AC-1, AC-2, AC-5 | Both routes specified. Neither executed. |

---

## 6. Coverage summary

| Measure | Result |
|---|---|
| Hazards with a complete chain to a verification protocol | **1 of 6** (HAZ-001) |
| Hazards with a DFMEA entry but no risk control | **4 of 6** (HAZ-003, 004, 005, 006) |
| Hazards with no analysis at all | **1 of 6** (HAZ-002, thermal — out of scope and stated as such) |
| Acceptance criteria tracing to a requirement | **5 of 5** |
| Orphan tests | **0** |
| Requirements with no verification | **0** of those written |
| Risk controls verified as implemented | **0 of 1** — protocol written, not executed |
| Risk controls verified as effective | **0 of 1** — protocol written, not executed |

---

## 7. Findings

**Forward coverage is poor and backward coverage is complete.** That asymmetry is the expected signature of a design file built depth-first: one hazard has been taken all the way from analysis to an executable protocol, and the rest stop at the DFMEA. It is the honest shape of the work rather than a failure of the matrix.

**Two identifier series are undefined.** HAZ- and RC- are used throughout the published documents and defined in none of them, because ELAP-RMF-001 does not exist. Until it does, every hazard reference in the DFMEA and every RC-010 reference in DIS-001 and VP-001 points at nothing. This is the highest-priority gap the matrix found, and it was not visible from inside any individual document.

**HAZ-006 exists only as a note.** It was identified by the DFMEA as a hazard the risk file had missed, and it has still not been written into a risk file. A hazard recorded only in the document that found it is not controlled.

**Four hazards break at the same link.** HAZ-003, 004, 005 and 006 all have DFMEA entries with recommended actions and none have risk controls. The DFMEA produced nine actioned failure modes; one has been converted into a control. The conversion step, not the analysis, is where this design file is thin.

**Nothing has been verified.** Every chain that exists ends at a written protocol with no executed record. The matrix should not be read as evidence of verification — it is evidence of what *would* be verified if the protocols were run.

---

## 8. What this matrix determines should be built next

In order, because each unblocks the next:

1. **ELAP-RMF-001** — gives HAZ-001 to HAZ-006 and RC-010 a source document, and writes up HAZ-006. Closes the dangling references in three published documents.
2. **ELAP-RMP-001** — risk acceptability criteria, without which residual risk cannot be evaluated.
3. **Risk controls for HAZ-003 and HAZ-004** — converting DFMEA recommended actions into controls and requirements, the step this matrix shows is missing.
4. **ELAP-VP-002** — the chamber vent protocol created by DF-011.

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
| 1.0 | 03 Oct 2026 | Initial issue. Covers ELAP-DFMEA-001 Rev 1.3, ELAP-DIS-001 Rev 1.3 and ELAP-VP-001 Rev 3.2. Records that the HAZ- and RC- identifier series have no source document, that HAZ-006 exists only as a note in the DFMEA, and that four of six hazards break the chain at the risk control step. | Raj Harsh |
