# Medical Device Design Controls — Worked Portfolio

Design control and risk management documents produced against **ISO 13485:2016**, **ISO 14971:2019** and **EU MDR 2017/745**, applied to a real device rather than a textbook example.

> **What this is.** A self-directed learning exercise on an independent design project of my own. It is not industry work, and none of it is a controlled document under any quality management system. It is published so the reasoning can be inspected.

---

## The device

The **External Liver Assistance Platform (ELAP)** is an ex vivo organ perfusion system I designed independently, built around a precision isolation manifold for decellularised organ scaffolds.

It won Category 2 of the **D.E.S.I.G.N. for BioE3 Challenge** run by the Department of Biotechnology and BIRAC, Government of India, and two provisional patents have been filed.

It is at design and simulation stage: no prototype, no bench testing, no clinical data. Patent specifications, claims and filing documents are **not** included in this repository.

---

## Contents

| Document | Status |
|---|---|
| [ELAP-DFMEA-001 — Design FMEA, Vascular Chassis Isolation Manifold](ELAP-DFMEA-001_Vascular-Chassis-Manifold.md) | Complete, Rev 1.3 |
| [ELAP-DIS-001 — Design Input Specification](ELAP-DIS-001_Design_Input_Specification.md) | Rev 1.3 — partial by design, see below |
| [ELAP-VP-001 — Verification Protocol, inlet-line gas detection](ELAP-VP-001_Inlet_Gas_Detection_Protocol.md) | Rev 3.2 — written, not executed |
| [ELAP-TRM-001 — Bidirectional traceability matrix](ELAP-TRM-001_Traceability_Matrix.md) | Rev 1.0 |
| ELAP-RMF-001 — Risk management file (ISO 14971) | Not started |
| ELAP-RMP-001 — Risk management plan | Not started |
| ELAP-VP-002 — Verification protocol, chamber vent | Not started |
| ELAP-GAP-001 — Design control gap assessment, ISO 13485 - 7.3 | Not started |

The four documents present form one chain and one audit of it: a failure mode found in the DFMEA, converted into a specified risk control, written as testable requirements, given a verification protocol — and then traced end to end to find where the chain breaks. The remaining documents are listed honestly as not started rather than as "in progress". The traceability matrix sets the build order for them, in its section 8.

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

**A recommended action carried through to a verifiable requirement.** DF-010 recommended inlet-line gas detection. That was adopted as risk control RC-010, specified as four separately testable requirements, and given a protocol. The chain is traceable end to end in the three documents.

**A requirement defect found and recorded.** The original REQ-014 combined a detection threshold and a response time in one sentence with both numbers blank — not independently testable, and nothing to test against. It was split into four requirements and the defect recorded in the specification's section 4, which is what ISO 13485 - 7.3.3 asks for.

**Scores deliberately not improved.** DF-010 still carries detection 8 and RPN 360 in Rev 1.3, even though a control has now been specified. A control that is specified but neither built nor verified reduces no risk. Re-scoring on a decision rather than on evidence is the most common way an FMEA becomes optimistic.

**Two errors in my own work, both found by checking rather than by writing.** The first: Rev 2.0 of the protocol derived the sensor standoff from bulk *mean* flow velocity. Both lines run laminar, so the centreline velocity is twice the mean and a small bolus travels at twice the bulk speed — the real margin at 250 mm was 1.48x, not the 2.97x stated. Standoff increased to 450 mm.

The second, found in a line-by-line review of the corrected document: the 2x centreline case cannot apply to the hepatic artery line at all. The detection threshold of 0.113 mL is twice the largest sphere its 4.76 mm bore will hold, so every bolus the control is specified to detect there is a *slug* spanning the bore, travelling at roughly the mean. Any bolus small enough to ride the centreline is below the detection threshold and explicitly out of scope. The binding case is the portal vein line at 0.561 m/s, needing 281 mm. The 450 mm standoff is retained, but it is now honest about what justifies it — margin over an unquantified slug drift, not a calculated minimum.

Both errors are in the revision histories with the reasoning, rather than quietly corrected. The second one matters more than the first: the arithmetic was right both times. What was wrong was the physical model the arithmetic was applied to, which no amount of recomputation would have caught.

**A conflict surfaced by doing the calculation.** The device is specified to operate at 4 °C, but the vascular flow rates every velocity limit rests on are published targets for normothermic perfusion at 37 °C. Flow and viscosity both differ. Every velocity-dependent limit is marked provisional until the operating temperature is settled.

**One derivation, one place.** The calculation chain lives in the design input specification; the protocol cites it rather than repeating it. Two copies of the same arithmetic in two documents will diverge at the first change.

**A requirement that existed only to satisfy a test.** The protocol's AC-5 checks that the detector does not halt perfusion on noise — a sound ISO 14971 concern, since a control that introduces a new hazard is not a control. But it traced to no requirement; nothing in the specification prohibited false triggering. REQ-014e was added so the acceptance criterion tests something that was actually specified.

**A traceability matrix that found what the documents could not show on their own.** Running the chain forward — hazard, failure mode, risk control, requirement, verification, evidence — showed that only one of six hazards reaches a verification protocol, and that four break at the same link: they have DFMEA entries with recommended actions and no risk controls. Running it backward showed zero orphan tests. The most useful finding was structural: the `HAZ-` and `RC-` identifier series are used throughout all three documents and defined in none of them, because the risk management file does not yet exist. A reference that resolves nowhere looks correct inside the document that makes it, and only fails when something tries to follow it.

**What the numbers do not establish.** The design input specification ends with what the arithmetic rests on and cannot support: an assumed organ mass, the unresolved operating temperature, an unvalidated bubble transport model, a detection threshold set by what a sensor can detect rather than by what an organ can tolerate, an unstated tubing bore tolerance, a chosen rather than derived response-time budget, and a safety factor named as covering three error sources none of which is quantified. Correct arithmetic on unestablished inputs produces a precise answer, not a right one.

---

## Standards referenced

ISO 13485:2016 · ISO 14971:2019 · EU MDR 2017/745 · 21 CFR 820.30 / QMSR · IEC 62304

---

## About

**Raj Harsh** — engineer working in safety-critical rail systems, moving into medical device quality and verification and validation.

[LinkedIn](https://www.linkedin.com/in/raj-harsh-73905615a)
