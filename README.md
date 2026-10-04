# Medical Device Design Controls — Worked Portfolio

Design control and risk management documents produced against **ISO 13485:2016**, **ISO 14971:2019** and **EU MDR 2017/745**, applied to a real device rather than a textbook example.

> **What this is.** A self-directed learning exercise on an independent design project of my own. It is not industry work, and none of it is a controlled document under any quality management system. It is published so the reasoning can be inspected.

---

## The device

The **External Liver Assistance Platform (ELAP)** is an ex vivo perfusion system I designed independently, for the **decellularization and subsequent recellularization of a whole human liver**, built around a precision isolation manifold. It runs three phases at two temperatures: decellularization at 4 °C, an enzymatic and wash stage at 37 °C, and recellularization at 37 °C under cell culture.

It is a processing platform rather than a therapy — it never contacts a patient. Harm reaches a patient only through the scaffold it produces, which is intended for implantation.

It won Category 2 of the **D.E.S.I.G.N. for BioE3 Challenge** run by the Department of Biotechnology and BIRAC, Government of India, and two provisional patents have been filed.

It is at design and simulation stage: no prototype, no bench testing, no clinical data. Patent specifications, claims and filing documents are **not** included in this repository.

---

## Contents

| Document | Status |
|---|---|
| [ELAP-DFMEA-001 — Design FMEA, Vascular Chassis Isolation Manifold](ELAP-DFMEA-001_Vascular-Chassis-Manifold.md) | Rev 1.6 |
| [ELAP-DIS-001 — Design Input Specification](ELAP-DIS-001_Design_Input_Specification.md) | Rev 1.5 — partial by design, see below |
| [ELAP-VP-001 — Verification Protocol, inlet-line gas detection](ELAP-VP-001_Inlet_Gas_Detection_Protocol.md) | Rev 3.4 — written, not executed |
| [ELAP-TRM-001 — Bidirectional traceability matrix](ELAP-TRM-001_Traceability_Matrix.md) | Rev 1.4 |
| [ELAP-RMP-001 — Risk management plan](ELAP-RMP-001_Risk_Management_Plan.md) | Rev 1.4 |
| [ELAP-RMF-001 — Risk management file (ISO 14971)](ELAP-RMF-001_Risk_Management_File.md) | Rev 1.2 — scoped to one operating phase |
| ELAP-VP-002 — Verification protocol, chamber vent | Not started |
| ELAP-GAP-001 — Design control gap assessment, ISO 13485 - 7.3 | Not started |

The six documents present form one chain, one audit of it, and the plan that sets the criteria: a failure mode found in the DFMEA, converted into a specified risk control, written as testable requirements, given a verification protocol — and then traced end to end to find where the chain breaks. The remaining documents are listed honestly as not started rather than as "in progress". The build order for them is set by the traceability matrix, section 8 — corrected in ELAP-RMP-001 section 0, which notes that the matrix had the plan and the risk file the wrong way round against ISO 14971's clause sequence.

---

## What the DFMEA demonstrates

**Functions before failures.** Functions were listed before any failure mode was written. A DFMEA that starts from parts rather than functions misses failure modes.

**Mode, effect and cause kept distinct.** The cause in each row is a mechanism that could actually be changed, not a restatement of the failure.

**A severity-weighted action threshold, not RPN alone.** S, O and D are ordinal scales, so their product is not mathematically meaningful. The threshold actions high severity on severity, consistent with ISO 14971 where occurrence cannot be reliably estimated. It caught a failure mode at RPN 72 that a product-only rule would have passed over.

**The threshold applied in both directions.** Nine of eleven modes are actioned; two are recorded as acceptable with the reasoning stated. A sheet where everything triggers action is a sheet where the threshold is doing nothing.

**Controls at the top of the hierarchy.** Four failure modes are controlled by inherent safety in the design — asymmetric keying so incorrect assembly is physically impossible, an oversized window so misalignment cannot obstruct flow, header sizing so distribution is insensitive to tolerance, and a passive vent rather than an active pressure-relief mechanism. Under the ISO 14971 hierarchy these rank above protective measures and information for safety.

**An uncontrolled failure mode, found by correcting an assumption.** The highest-severity item in the analysis — gas in the perfusion inlet circuit reaching the organ vasculature — was originally credited to a control that cannot work. The chamber vent sits downstream of the organ, so it cannot intercept gas travelling up the inlet line. Detection was re-scored from 4 to 8 and the RPN went from 180 to 360, making it the only item to fire all three action criteria.

**A hazard the risk file had missed.** Tracing each failure effect to the risk management file showed that biliary obstruction and bile contamination of the perfusate were not represented by any existing hazard. That is the reason to run a bottom-up analysis alongside a top-down one.

**Open inputs recorded, not assumed.** Section 8 lists what the analysis needs and does not have. Each is named rather than filled with a plausible number.

---

## What the requirements and protocol demonstrate

**A recommended action carried through to a verifiable requirement.** DF-010 recommended inlet-line gas detection. That was adopted as risk control RC-001, specified as four separately testable requirements, and given a protocol. The chain is traceable end to end in the three documents.

**A requirement defect found and recorded.** The original REQ-014 combined a detection threshold and a response time in one sentence with both numbers blank — not independently testable, and nothing to test against. It was split into four requirements and the defect recorded in the specification's section 4, which is what ISO 13485 - 7.3.3 asks for.

**Scores deliberately not improved.** DF-010 still carries detection 8 and RPN 360 in Rev 1.3, even though a control has now been specified. A control that is specified but neither built nor verified reduces no risk. Re-scoring on a decision rather than on evidence is the most common way an FMEA becomes optimistic.

**Two errors in my own work, both found by checking rather than by writing.** The first: Rev 2.0 of the protocol derived the sensor standoff from bulk *mean* flow velocity. Both lines run laminar, so the centreline velocity is twice the mean and a small bolus travels at twice the bulk speed — the real margin at 250 mm was 1.48x, not the 2.97x stated. Standoff increased to 450 mm.

The second, found in a line-by-line review of the corrected document: the 2x centreline case cannot apply to the hepatic artery line at all. The detection threshold of 0.113 mL is twice the largest sphere its 4.76 mm bore will hold, so every bolus the control is specified to detect there is a *slug* spanning the bore, travelling at roughly the mean. Any bolus small enough to ride the centreline is below the detection threshold and explicitly out of scope. The binding case is the portal vein line at 0.561 m/s, needing 281 mm. The 450 mm standoff is retained, but it is now honest about what justifies it — margin over an unquantified slug drift, not a calculated minimum.

Both errors are in the revision histories with the reasoning, rather than quietly corrected. The second one matters more than the first: the arithmetic was right both times. What was wrong was the physical model the arithmetic was applied to, which no amount of recomputation would have caught.

**A conflict surfaced by doing the calculation.** The device is specified to operate at 4 °C, but the vascular flow rates every velocity limit rests on are published targets for normothermic perfusion at 37 °C. Flow and viscosity both differ. Every velocity-dependent limit is marked provisional until the operating temperature is settled.

**One derivation, one place.** The calculation chain lives in the design input specification; the protocol cites it rather than repeating it. Two copies of the same arithmetic in two documents will diverge at the first change.

**A requirement that existed only to satisfy a test.** The protocol's AC-5 checks that the detector does not halt perfusion on noise — a sound ISO 14971 concern, since a control that introduces a new hazard is not a control. But it traced to no requirement; nothing in the specification prohibited false triggering. REQ-014e was added so the acceptance criterion tests something that was actually specified.

**A traceability matrix that found what the documents could not show on their own.** Running the chain forward — hazard, failure mode, risk control, requirement, verification, evidence — showed that only one of six hazards reaches a verification protocol, and that four break at the same link: they have DFMEA entries with recommended actions and no risk controls. Running it backward showed zero orphan tests. The most useful finding was structural: the `HAZ-` and `RC-` identifier series are used throughout all three documents and defined in none of them, because the risk management file does not yet exist. A reference that resolves nowhere looks correct inside the document that makes it, and only fails when something tries to follow it.

**A plan written to a clause list rather than a template.** ELAP-RMP-001 is structured against the seven things ISO 14971:2019 clause 4.4 actually requires, with its sections numbered to match, so conformance can be checked rather than asserted. Three decisions in it are worth naming. Probability of occurrence of harm cannot be estimated for this device — no unit exists, no test data, no predecessor — so risk is evaluated on severity alone, which is what clause 4.4 d) exists to permit. The DFMEA's severity-weighted action threshold then becomes a consequence of the plan rather than a rule invented separately for the DFMEA. And there is no ALARP band, because ISO 14971:2019 removed cost as grounds for stopping risk reduction and EU MDR Annex I GSPR 4 requires reduction as far as possible without economic consideration.

**Two required things the plan declines to claim.** Overall residual risk is not evaluated, because no risk control in the file has been verified — the method is defined and stated to be inapplicable. And production and post-production information is marked not applicable with the reason given, rather than left blank. A required clause element silently blank is a gap; marked with its reason, it is a scope decision.

**An intended use statement that invalidated part of the analysis — and the sequence that let that happen.** ISO 14971 puts intended use first, in clause 5.2, because severity cannot be judged without knowing what the device is for. The risk file was built from the DFMEA upward and that step was skipped. Writing it afterwards changed four hazards: gas in the circuit harms a decellularizing organ by leaving cellular material behind, not by causing ischaemia, there being no living tissue; a temperature excursion at 4 °C degrades the matrix through endogenous protease activity, not through warm ischaemia; bile output cannot indicate viability in a phase with no hepatocytes, so that hazard is out of scope rather than uncontrolled; and the fluid escaping the biliary path is cytotoxic detergent rather than bile, which raised its severity. The error and the correction are both in the revision history.

**A hazard created by a risk control, and a control conflict it exposed.** Active cooling was adopted to stop the organ warming. Active cooling can also over-cool toward freezing, which destroys the matrix — a new hazard the control introduced, which ISO 14971 clause 7.5 exists to catch. It is controlled by sizing the cooling capacity so sub-zero operation is physically unachievable, which removes the capability rather than detecting the fault. That control then conflicts with the one it was added alongside: the two adjust cooling capacity in opposite directions, and the band satisfying both is recorded as undetermined rather than assumed to exist.

**A rejected control option, recorded with what the rejection does not establish.** A bubble trap would remove gas rather than merely detecting it, ranking higher in the control hierarchy. It was rejected on three grounds — an extra interface in the sterile barrier, a deliberate gas reservoir that a transient can release downstream, and an added use step in a device whose use-related risk is uncontrolled. The file records the rejection *and* records that the trade is unquantified, so reduction as far as possible is argued rather than demonstrated and the residual risk cannot be called acceptable on that basis.

**Nine foreseeable misuse cases, none controlled, recorded as such.** Misuse is not failure — the device works correctly and harm follows anyway: a single-use chassis cleaned and reused, a wash phase shortened to save time, an arterial line connected to the portal vein. Controlling them needs IEC 62366-1 usability engineering, which no document in this set covers. Two reach harms assessed at S4 and S5, so the file states plainly that declining to control them does not make them acceptable — it means use-related risk cannot be concluded acceptable, and the file does not attempt to.

**A limit set marked provisional rather than quietly carried.** The velocity limits in the design input specification derive from normothermic preservation flow rates, and the device performs cold decellularization. Worse, whole human liver decellularization is pressure-controlled at 120 mmHg — flow is an *output* that rises through the run as scaffold resistance falls, so there is no fixed maximum flow to design against. The derivation method survives; the input does not. The annex keeps the superseded figures so the chain stays readable, with a banner saying what is sound, what is not, and that the error direction is conservative.

**A risk management file, and what tracing it revealed.** ELAP-RMF-001 identifies nine hazards and defines twenty-five risk controls, sixteen of them tier 1 inherently safe design rather than protective measures or warnings. Four of the nine hazards were not found by the design FMEA: two fall outside its scope, since it starts from component functions and neither an operator's hands nor ambient heat ingress is a component, and the third was found by the traceability matrix. The seven failure modes the DFMEA had mapped to a single hazard are split into mechanical and hydraulic sources, on the basis that a hazard is defined by its source and the two need different controls.

**The chain break moved one link, and the matrix says so.** Rev 1.0 of the traceability matrix found that four of six hazards had DFMEA entries and no risk controls. Twenty-four controls now exist, so every hazard has one — and the break moves to the requirement step, where twenty-three of twenty-four controls have nothing in the design input specification obliging the device to have them. A control with no requirement is an intention, not a control. The coverage table shows Rev 1.0 against Rev 1.2 side by side so the change is visible rather than claimed.

**An identifier scheme fixed after it had already failed twice.** A verification protocol was numbered VP-007 when no VP-001 to VP-006 existed, and a risk control was numbered RC-010 after the DFMEA item it came from, implying nine earlier controls that were never defined. Both implied documents that did not exist. ELAP-RMP-001 section 8.1 now records one source document per identifier series and the rule that risk control identifiers are assigned sequentially in order of definition — not mirrored from a hazard or a failure mode, because a single control can serve several hazards and a mirrored scheme has no honest number for that.

**What the numbers do not establish.** The design input specification ends with what the arithmetic rests on and cannot support: an assumed organ mass, the unresolved operating temperature, an unvalidated bubble transport model, a detection threshold set by what a sensor can detect rather than by what an organ can tolerate, an unstated tubing bore tolerance, a chosen rather than derived response-time budget, and a safety factor named as covering three error sources none of which is quantified. Correct arithmetic on unestablished inputs produces a precise answer, not a right one.

---

## Standards referenced

ISO 13485:2016 · ISO 14971:2019 · EU MDR 2017/745 · 21 CFR 820.30 / QMSR · IEC 62304

---

## About

**Raj Harsh** — engineer working in safety-critical rail systems, moving into medical device quality and verification and validation.

[LinkedIn](https://www.linkedin.com/in/raj-harsh-73905615a)
