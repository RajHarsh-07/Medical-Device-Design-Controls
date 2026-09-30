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
| [ELAP-DFMEA-001 — Design FMEA, Vascular Chassis Isolation Manifold](ELAP-DFMEA-001_Vascular-Chassis-Manifold.md) | Complete |
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

**Controls at the top of the hierarchy.** Three failure modes are controlled by inherent safety in the design — asymmetric keying so incorrect assembly is physically impossible, an oversized window so misalignment cannot obstruct flow, and header sizing so distribution is insensitive to tolerance — rather than by inspection or warnings.

**A hazard found that the risk file had missed.** Tracing each failure effect to the risk management file showed that biliary obstruction and bile contamination of the perfusate were not represented by any existing hazard. That is the reason to run a bottom-up analysis alongside a top-down one, and it is recorded in section 5.

**Limitations stated rather than hidden.** Single analyst, no test data behind the occurrence ratings, selected functions only, and a CFD run that does not evidence thermal performance because it was isothermal with no thermal load applied.

---

## Standards referenced

ISO 13485:2016 · ISO 14971:2019 · EU MDR 2017/745 · 21 CFR 820.30 / QMSR · IEC 62304

---

## About

**Raj Harsh** — engineer working in safety-critical rail systems, moving into medical device quality and verification and validation.

[LinkedIn](https://www.linkedin.com/in/raj-harsh-73905615a)
