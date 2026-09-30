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
| [ELAP-DFMEA-001 — Design FMEA, Vascular Chassis Isolation Manifold](ELAP-DFMEA-001_Vascular-Chassis-Manifold.md) | Complete, Rev 1.2 |
| ELAP-RMF-001 — Risk management file (ISO 14971) | In progress |
| ELAP-RMP-001 — Risk management plan | In progress |
| ELAP-SRS-001 — Design inputs specification | In progress |
| ELAP-VP-007 — Verification protocol | In progress |
| ELAP-TRM-001 — Bidirectional traceability matrix | In progress |
| ELAP-GAP-001 — Design control gap assessment, ISO 13485 §7.3 | In progress |

---

## What the DFMEA demonstrates

**Functions before failures.** Functions were listed before any failure mode was written. A DFMEA that starts from parts rather than functions misses failure modes.

**Mode, effect and cause kept distinct.** The cause in each row is a mechanism that could actually be changed, not a restatement of the failure.

**A severity-weighted action threshold, not RPN alone.** S, O and D are ordinal scales, so their product is not mathematically meaningful. The threshold actions high severity on severity, consistent with ISO 14971 where occurrence cannot be reliably estimated. It caught a failure mode at RPN 72 that a product-only rule would have passed over.

**The threshold applied in both directions.** Eight of ten modes are actioned; two are recorded as acceptable with the reasoning stated. A sheet where everything triggers action is a sheet where the threshold is doing nothing.

**Controls at the top of the hierarchy.** Four failure modes are controlled by inherent safety in the design — asymmetric keying so incorrect assembly is physically impossible, an oversized window so misalignment cannot obstruct flow, header sizing so distribution is insensitive to tolerance, and a passive vent rather than an active pressure-relief mechanism. Under the ISO 14971 hierarchy these rank above protective measures and information for safety.

**An uncontrolled failure mode, found by correcting an assumption.** The highest-severity item in the analysis — gas in the perfusion inlet circuit reaching the organ vasculature — was originally credited to a control that cannot work. The chamber vent sits downstream of the organ, so it cannot intercept gas travelling up the inlet line. Detection was re-scored from 4 to 8 and the RPN went from 180 to 360, making it the only item to fire all three action criteria. The design currently has no control for it, and the document says so.

**A hazard the risk file had missed.** Tracing each failure effect to the risk management file showed that biliary obstruction and bile contamination of the perfusate were not represented by any existing hazard. That is the reason to run a bottom-up analysis alongside a top-down one, and it is recorded in section 5.

**Open inputs recorded, not assumed.** Section 8 lists what the analysis needs and does not have — maximum fill rate, tolerable chamber pressure, the gas control method for the inlet circuit, material selection, and the anatomical range of donor organs. Each is named rather than filled with a plausible number.

**Limitations stated rather than hidden.** Single analyst, no test data behind the occurrence ratings, selected functions only, and a CFD run that does not evidence thermal performance because it was isothermal with no thermal load applied.

---

## Standards referenced

ISO 13485:2016 · ISO 14971:2019 · EU MDR 2017/745 · 21 CFR 820.30 / QMSR · IEC 62304

---

## About

**Raj Harsh** — engineer working in safety-critical rail systems, moving into medical device quality and verification and validation.

[LinkedIn](https://www.linkedin.com/in/raj-harsh-73905615a)
