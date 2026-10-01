# ELAP-VP-001 — Verification Protocol

**Inlet-Line Gas Detection and Pump Interlock — Response Time and Detection Threshold**

| **Field**              | **Entry**                                                                                                                               |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Document number        | ELAP-VP-001                                                                                                                             |
| Revision               | 3.2                                                                                                                                     |
| Supersedes             | ELAP-VP-007 Rev 1.0. Renumbered: no protocols VP-001 to VP-006 exist, so the original number implied documents that were never written. |
| Requirement verified   | REQ-014a, REQ-014b, REQ-014c, REQ-014d, REQ-014e (ELAP-DIS-001 Rev 1.3)                                                                 |
| Risk control verified  | RC-010                                                                                                                                  |
| Source of risk control | ELAP-DFMEA-001 Rev 1.3, item DF-010 (S=9, O=5, D=8, RPN 360) — recommended action                                                       |
| Related hazard         | HAZ-001 — gas in the perfusion circuit reaching the organ vasculature                                                                   |
| Prepared by            | Raj Harsh                                                                                                                               |
| Effective date         | 01 October 2026                                                                                                                         |

*Self-directed exercise on an independent design project. Not industry work. Not a controlled document under any quality management system.*

## Approval before execution

*This protocol, including its acceptance criteria, is approved before any test is run. Approval after execution only would allow the criteria to be written to fit the data.*

| **Role**         | **Name**  | **Signature** | **Date**    |
|------------------|-----------|---------------|-------------|
| Prepared by      | Raj Harsh | R.H.          | 01 Oct 2026 |
| Reviewed by      |           |               |             |
| Approved by (QA) |           |               |             |

## 1. Purpose

To verify that the inlet-line gas detection subsystem detects a gas bolus in a perfusion inlet line at or above the specified threshold volume, and halts the perfusion pump within the specified response time, so that the bolus is arrested upstream of the cannula connection while flow is stopped. Halting flow does not remove the gas; it remains in the line and must be cleared before flow resumes.

## 2. Scope and status of the control under test

### 2.1 Status of the control

RC-010 is SPECIFIED, NOT YET BUILT. It does not exist in the current ELAP design.

ELAP-DFMEA-001 Rev 1.3 records DF-010 — gas in the perfusion inlet circuit reaching the organ vasculature — as having no prevention control and no detection control, at RPN 360, the highest item in the analysis. The recommended action for DF-010 is to design a gas control into the inlet circuit. RC-010 is the adoption of that recommended action as a design decision: inlet-line gas detection with a pump interlock.

This protocol is therefore a blank protocol written against a specified control, ahead of the hardware. That is the normal sequence — a protocol is written and approved before execution, and it is written from the requirement, not from the built device. What this document must not do is imply the control exists or that results have been obtained. It contains no results. Section 11 is empty and remains empty until the subsystem is built and the protocol is executed.

### 2.2 In scope

- Detection of a discrete gas bolus in each perfusion inlet line (hepatic artery line and portal vein line), independently.

- Time from bolus entering the sensing volume to cessation of pump-driven flow.

- Minimum standoff distance between the sensing point and the cannula connection.

- Verification of RC-010 as implemented, and as effective (both are required — see section 12).

### 2.3 Out of scope

- Gas removal. A detector stops flow; it does not remove gas already in the line. Whether a bubble trap is also required is an open design decision recorded in ELAP-DFMEA-001 Rev 1.3 section 8.

- Chamber headspace gas and the chamber vent. That is DF-011 and a separate protocol.

- Dissolved gas and microbubbles below the sensor threshold. Not addressed by this control and not claimed to be.

- Software verification of the interlock logic (IEC 62304). Separate activity.

## 3. Requirements verified

*REQ-014 as first drafted combined three separable requirements in one statement and left both numeric values blank. It is replaced by three testable requirements. A requirement that cannot be passed or failed on its own is not a requirement.*

| **REQ ID** | **Requirement statement**                                                                                                                                                          | **Risk control?** | **Method** |
|------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------|------------|
| REQ-014a   | Gas detection shall be fitted on each perfusion inlet line and shall detect a discrete gas bolus of 0.113 mL or greater (equivalent to a 6 mm diameter sphere).                    | Yes — RC-010      | Test       |
| REQ-014b   | On detection of a gas bolus meeting REQ-014a, the system shall halt pump-driven flow within 200 ms, measured from entry of the bolus into the sensing volume to cessation of flow. | Yes — RC-010      | Test       |
| REQ-014c   | The sensing point on each inlet line shall be located not less than 450 mm upstream of the cannula connection, measured along the flow path.                                       | Yes — RC-010      | Inspection |
| REQ-014d   | Perfusion inlet tubing bore shall be selected such that bulk flow velocity at maximum specified flow does not exceed 0.45 m/s in any line carrying gas detection.                  | Derived — see 4.5 | Analysis   |

## 4. Basis for the acceptance limits

*Every numeric limit in section 3 is derived below. A limit without a derivation is an assumption presented as a specification.*

### 4.1 Perfusion flow rate (design input, not a measurement)

Targeted vascular flows for ex vivo normothermic machine perfusion of the human liver, from Brüggenwirth et al., Communications Medicine (2024), "A reproducible extended ex-vivo normothermic machine liver perfusion protocol utilising improved nutrition and targeted vascular flows": portal vein 75–80 mL/100 g/min, hepatic artery 25–30 mL/100 g/min, combined 100–110 mL/100 g/min.

| **Parameter**                | **Value**   | **Basis**                                                      |
|------------------------------|-------------|----------------------------------------------------------------|
| Nominal donor liver mass     | 1500 g      | ASSUMPTION — requires citation before approval. See section 8. |
| Portal vein flow, maximum    | 1200 mL/min | 80 mL/100 g/min x 15                                           |
| Hepatic artery flow, maximum | 450 mL/min  | 30 mL/100 g/min x 15                                           |
| Combined flow, maximum       | 1650 mL/min | 110 mL/100 g/min x 15                                          |

This is a design input the designer specifies, on published physiological targets. It is not blocked on pump selection or on bench measurement.

### 4.2 Detection threshold

Set by commercially available sensor capability, not chosen arbitrarily. SONOTEC SONOFLOW CO.56 Pro V2.0 technical data sheet gives factory-default bubble thresholds as the diameter of an equivalent sphere, by tube size:

| **Tube (OD x wall)** | **Internal bore** | **Default threshold (sphere dia.)** | **Equivalent volume** |
|----------------------|-------------------|-------------------------------------|-----------------------|
| 1/4" x 1/16"         | 3.1750 mm         | 4 mm                                | 0.0335 mL             |
| 1/4" x 3/32"         | 1.5875 mm         | 5 mm                                | 0.0654 mL             |
| 3/8" x 3/32"         | 4.7625 mm         | 6 mm                                | 0.1131 mL             |
| 1/2" x 1/16"         | 9.5250 mm         | 6 mm                                | 0.1131 mL             |

Both bores in use carry the same 6 mm default, so 0.113 mL is met on either line without an optional non-standard threshold. The datasheet states bubble sensitivity depends on tube properties and mounting position, so the threshold is verified on the actual build in this protocol rather than taken from the datasheet.

LIMITATION, stated rather than hidden: 0.113 mL is what the sensor can detect. It is not known to be the volume the organ can tolerate. No organ-level gas tolerance figure has been established for this device. The threshold is therefore precautionary and capability-led, and the tolerance question is recorded as an open input in section 8.

### 4.3 Flow velocity, flow regime and bubble transport velocity

Worst case is the highest velocity at which a gas bolus can travel, because that gives the shortest time for the interlock to act before the bolus reaches the cannula. Bulk mean velocity is NOT that worst case, and Revision 2.0 of this protocol wrongly used it.

| **Line**                      | **Max flow** | **Tube (OD x wall)** | **Bore** | **Area**  | **Mean velocity** | **Reynolds number** |
|-------------------------------|--------------|----------------------|----------|-----------|-------------------|---------------------|
| Portal vein                   | 1200 mL/min  | 1/2" x 1/16"         | 9.525 mm | 71.26 mm2 | 0.281 m/s         | 1706 — laminar      |
| Hepatic artery                | 450 mL/min   | 3/8" x 3/32"         | 4.762 mm | 17.81 mm2 | 0.421 m/s         | 1280 — laminar      |
| Portal vein — rejected option | 1200 mL/min  | 3/8" x 3/32"         | 4.762 mm | 17.81 mm2 | 1.123 m/s         | 3412 — transitional |

Both selected lines run laminar (Re below 2300), so the velocity profile is parabolic and the centreline velocity is twice the mean. Which case bounds a line depends on whether a bolus at the detection threshold fits inside that bore. The derivation is in ELAP-DIS-001 Annex A.6; the result is summarised here because it determines the acceptance limits.

| **Line**       | **Bore**  | **Largest sphere the bore holds** | **Regime at the 0.113 mL threshold**                    | **Bounding transport velocity**   | **Transit over 450 mm** |
|----------------|-----------|-----------------------------------|---------------------------------------------------------|-----------------------------------|-------------------------|
| Portal vein    | 9.5250 mm | 0.4525 mL                         | Bubble — threshold is sub-bore, centreline case applies | 0.561 m/s                         | 802 ms                  |
| Hepatic artery | 4.7625 mm | 0.0566 mL                         | Slug — threshold is 2.0x the largest sub-bore sphere    | 0.421 m/s plus unquantified drift | 1069 ms                 |

The binding case is the PORTAL VEIN line at 0.561 m/s. Revision 2.0 and 3.0 of this protocol named the hepatic artery line, having applied the centreline case to a line where no detectable bolus can ride the centreline.

### 4.4 Response time budget and margin

| **Contribution**                     | **Allocation**    | **Basis**                                                                                                                  |
|--------------------------------------|-------------------|----------------------------------------------------------------------------------------------------------------------------|
| Sensor detection and evaluation      | \< 10 ms          | SONOTEC SONOFLOW CO.56 Pro data sheet: internal evaluation interval max 1.6 ms, response \< 10 ms                          |
| Interlock signal and pump command    | Not yet allocated | Depends on control architecture — see section 8                                                                            |
| Pump deceleration to zero flow       | Not yet allocated | REQUIREMENT IMPOSED ON THE PUMP, not a measurement awaited from it                                                         |
| Total, specified (REQ-014b)          | 200 ms            | Set by the designer, then allocated across the three contributions above                                                   |
| Minimum acceptable margin            | 2.5x              | Design decision. Covers bore tolerance, flow overshoot above nominal, and the approximation in the bubble transport model. |
| Minimum standoff at the binding case | 281 mm            | 2.5 x 200 ms x 0.561 m/s = 280.7 mm                                                                                        |
| Specified standoff (REQ-014c)        | 450 mm            | 281 mm increased, to cover the unquantified slug drift on the artery line and to avoid relaxing a previously issued limit  |
| Calculated transit, binding case     | 802 ms            | 450 mm / 0.561 m/s — calculated, not measured; nothing has been built                                                      |
| Calculated margin                    | 4.01x             | 802 / 200                                                                                                                  |

The direction of this reasoning matters. The response time is not discovered by measuring a pump that has already been bought; it is specified first, and it then constrains which pump may be selected. A pump that cannot stop flow inside the allocation left after sensor and signal delays does not meet the design input and is not selectable.

### 4.5 Constraints the requirement imposes back on the design

REQ-014c and REQ-014d are not specified from outside. They fall out of REQ-014b and the flow figures, and they constrain the design rather than describing it.

| **Option**                  | **Bounding transport velocity** | **Transit over 450 mm** | **Margin** | **Verdict**                                                                                                                                                                                                    |
|-----------------------------|---------------------------------|-------------------------|------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Portal line on 1/2" x 1/16" | 0.561 m/s                       | 802 ms                  | 4.01x      | Accepted — the binding case                                                                                                                                                                                    |
| Artery line on 3/8" x 3/32" | 0.421 m/s (slug)                | 1069 ms                 | 5.34x      | Accepted, excluding unquantified drift                                                                                                                                                                         |
| Portal line on 3/8" x 3/32" | 2.245 m/s                       | 200 ms                  | 1.00x      | REJECTED. The governing reason is Re 3412, which leaves the laminar regime the transport model assumes; the margin figure shown is itself computed from that invalid model and is not the basis for rejection. |

REQ-014d sets the ceiling at 0.45 m/s mean, which is exactly the velocity giving 2.5x margin at 450 mm under the 2 x mean transport assumption. Any line exceeding it fails REQ-014b however fast the sensor and pump are.

### 4.6 Number of trials

| **Parameter**                     | **Value** | **Basis**                                                                                                                                                         |
|-----------------------------------|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Trials per line, per bolus volume | 29        | Zero-failure attribute sampling: n = ln(1 - C) / ln(R) = ln(0.05) / ln(0.90) = 28.43, rounded up to 29. 95% confidence at 90% reliability. Confirmed 01 Oct 2026. |
| Bolus volumes tested              | 3         | At threshold (0.113 mL), and two above it, to show the response is not volume-marginal                                                                            |
| Lines tested                      | 2         | Hepatic artery and portal vein, independently                                                                                                                     |

## 5. Equipment and configuration

| **Item**                                                   | **Purpose**                                     | **ID / serial** | **Calibration due** |
|------------------------------------------------------------|-------------------------------------------------|-----------------|---------------------|
| Inlet-line gas sensor, artery line                         | Unit under test                                 |                 |                     |
| Inlet-line gas sensor, portal line                         | Unit under test                                 |                 |                     |
| Perfusion pump and controller                              | Unit under test                                 |                 |                     |
| Calibrated gas-tight syringe                               | Introduce known bolus volume                    |                 |                     |
| Flow switch or high-speed camera at cannula                | Independent confirmation that flow ceased       |                 |                     |
| Second gas sensor, or optical gate, at the injection point | Independent timestamp for bolus entry — see A.5 |                 |                     |
| Data logger, \>= 1 kHz                                     | Timestamp detection signal and pump command     |                 |                     |
| Flow meter                                                 | Confirm flow rate at test condition             |                 |                     |
| Steel rule / calipers                                      | Verify standoff distance (REQ-014c)             |                 |                     |

*The timing measurement must not rely on the subsystem under test to report its own response time. A device reporting that it stopped in time is not evidence that it stopped in time.*

## 6. Acceptance criteria

*Approved before execution. Not to be altered after any test has been run; an alteration after execution is a change to this protocol and requires re-approval and re-execution.*

| **\#** | **Criterion**                                                                                                                                                                            | **Requirement** |
|--------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
| AC-1   | Every introduced bolus of 0.113 mL or greater is detected. 29 of 29 trials per line, per volume, zero misses.                                                                            | REQ-014a        |
| AC-2   | Time from bolus entry into the sensing volume to cessation of flow at the cannula is \<= 200 ms in every trial. The maximum observed value, not the mean, is compared against the limit. | REQ-014b        |
| AC-3   | Measured standoff from sensing point to cannula connection is \>= 450 mm on both lines.                                                                                                  | REQ-014c        |
| AC-4   | Calculated bulk velocity at maximum specified flow is \<= 0.45 m/s in both lines, from measured bore and measured flow.                                                                  | REQ-014d        |
| AC-5   | No false trigger occurs during 30 minutes of continuous gas-free circulation at maximum flow on each line.                                                                               | REQ-014e        |

AC-5 exists because a detector that halts the pump on noise is a new hazard, not a control. ISO 14971:2019 requires risk control measures to be analysed for the new risks they introduce.

## 7. Procedure

*Record every result at the moment of observation, in this document, in ink. Do not transcribe from notes made elsewhere. A record reconstructed afterwards cannot be shown to reflect what happened, and is treated as unreliable regardless of whether the numbers are correct.*

| **Step** | **Action**                                                                                                                                                                                                                       | **Expected result**                                           | **Actual** | **P/F** | **Init / Date** |
|----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------|------------|---------|-----------------|
| 1        | Record sensor, pump and instrument identifiers and calibration status in section 5.                                                                                                                                              | All instruments in calibration.                               |            |         |                 |
| 2        | Measure and record internal bore of each inlet line. Measure and record standoff from sensing point to cannula connection on each line.                                                                                          | Standoff \>= 450 mm both lines.                               |            |         |                 |
| 2a       | Inspect and record: a gas sensor is fitted on each inlet line; the interlock output of each sensor is wired to the pump controller; actuate each sensor by test input and confirm the pump controller receives the halt command. | Sensor on both lines; interlock wired and responding on both. |            |         |                 |
| 3        | Prime both lines. Confirm gas-free by visual inspection and by absence of sensor trigger.                                                                                                                                        | No trigger; no visible gas.                                   |            |         |                 |
| 4        | Set artery line to 450 mL/min and portal line to 1200 mL/min. Record measured flow.                                                                                                                                              | Flow within +/- 5% of setpoint.                               |            |         |                 |
| 5        | Calculate bulk velocity from measured bore and measured flow. Record.                                                                                                                                                            | \<= 0.45 m/s both lines.                                      |            |         |                 |
| 6        | Circulate gas-free at maximum flow for 30 minutes on each line, logging sensor output.                                                                                                                                           | No trigger in 30 min.                                         |            |         |                 |
| 7        | Inject a 0.113 mL bolus into the artery line upstream of the sensing point. Log detection signal, pump command and flow cessation.                                                                                               | Detected; flow ceases \<= 200 ms.                             |            |         |                 |
| 8        | Repeat step 7 for 29 trials. Record every trial individually, including any miss.                                                                                                                                                | 29 of 29 detected.                                            |            |         |                 |
| 9        | Repeat steps 7 and 8 at two bolus volumes above threshold.                                                                                                                                                                       | All detected within 200 ms.                                   |            |         |                 |
| 10       | Repeat steps 7 to 9 on the portal vein line.                                                                                                                                                                                     | As above.                                                     |            |         |                 |
| 11       | Inspect the cannula-side line for gas past the cannula connection after each detection event.                                                                                                                                    | No gas past the connection.                                   |            |         |                 |
| 11a      | Record every individual trial on the trial log sheet appended to this protocol: trial number, line, bolus volume, detected yes/no, response time. 174 rows in total. Section 11 records only the summary.                        | Trial log complete, 174 rows.                                 |            |         |                 |
| 12       | Record maximum observed response time per line and per volume in section 11.                                                                                                                                                     | —                                                             |            |         |                 |
| 13       | Record all deviations in section 9 and all failures in section 10 before leaving the bench.                                                                                                                                      | —                                                             |            |         |                 |

## 8. Open inputs — to be closed before approval

*Recorded rather than filled with a plausible number. Each entry names what is missing and what would close it.*

| **Input**                                      | **Status**                       | **What closes it**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|------------------------------------------------|----------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Nominal and worst-case donor liver mass        | Assumed 1500 g                   | A cited reference range for adult liver mass. Worst-case mass sets worst-case flow and therefore worst-case velocity; if the upper bound is materially above 1500 g, section 4.3 and REQ-014d are recalculated.                                                                                                                                                                                                                                                                                                        |
| Organ tolerance to gas volume                  | Not established                  | Literature or experiment on gas volume tolerated by hepatic microvasculature without occlusion. Until then, 0.113 mL is capability-led and precautionary, not tolerance-led. This is the single largest unknown behind AC-1.                                                                                                                                                                                                                                                                                           |
| Allocation of the 200 ms budget                | Not allocated                    | Control architecture decision, then a pump specification derived from what remains after sensor and signal delays.                                                                                                                                                                                                                                                                                                                                                                                                     |
| Whether a bubble trap is also required         | Open                             | DF-010 recommends detection and/or a bubble trap. Detection stops flow; it does not remove gas. If a trap is added it is a separate control needing its own requirement and protocol.                                                                                                                                                                                                                                                                                                                                  |
| Cannula and tubing connection geometry         | Not defined                      | Needed to fix the measurement datum for the 450 mm standoff.                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Operating temperature of the perfusion circuit | CONFLICT                         | ELAP-DFMEA-001 Rev 1.3 states operation at 4 degC and its CFD run is isothermal at 4 degC. The flow rates in section 4.1 are published targets for NORMOTHERMIC perfusion at 37 degC. Hypothermic machine perfusion runs at substantially lower flow, and fluid viscosity at 4 degC is roughly twice that at 37 degC, which changes both velocity and Reynolds number. Either the operating temperature or the flow basis is wrong for this device. This must be resolved before the limits in section 4 are approved. |
| Inlet tubing bore tolerance                    | Not stated                       | The hepatic artery line runs at 94 percent of the REQ-014d velocity ceiling. AC-4 is checked on measured bore, so a tube at the low end of an unstated commercial tolerance could fail AC-4 while conforming to the drawing. A bore tolerance is required as a design input.                                                                                                                                                                                                                                           |
| Independent timestamp for bolus entry          | Equipment added, method unproven | A.5 requires both timestamps from an instrument independent of the unit under test, but the sensor trigger is the only thing that knows when a bolus entered its own sensing volume. A second sensor or optical gate at the injection point is listed in section 5; the transit correction between injection point and sensing volume has not been established.                                                                                                                                                        |
| Bubble transport model                         | Approximate                      | The 2 x mean centreline assumption bounds a small bubble in laminar flow. It is not validated for this geometry, and real bubble transport depends on bubble size relative to bore, tube orientation and buoyancy. The assumption is conservative for a slug and is intended to be so, but it has not been tested.                                                                                                                                                                                                     |

## 9. Deviations

*A deviation is a departure from THIS PROTOCOL — wrong equipment, altered step, different sample size, steps out of order. The protocol was not followed. A deviation may or may not invalidate the result; that requires assessment and written justification. It is not the same thing as a failure.*

| **DEV ID** | **Step** | **Description of departure** | **Assessment of impact on validity** | **Raised by / Date** |
|------------|----------|------------------------------|--------------------------------------|----------------------|
|            |          |                              |                                      |                      |
|            |          |                              |                                      |                      |
|            |          |                              |                                      |                      |

## 10. Failures

*A failure is the device not meeting an acceptance criterion, with the protocol correctly followed. A failure is a result and is recorded as one. Do not repeat a test to obtain a better number; an undocumented retest after a failure is the most common finding in this area.*

| **FAIL ID** | **AC** | **Observed** | **Investigation reference** | **Disposition** |
|-------------|--------|--------------|-----------------------------|-----------------|
|             |        |              |                             |                 |
|             |        |              |                             |                 |
|             |        |              |                             |                 |

On any failure, in order: stop and record the observed result; document it here; investigate root cause across device, test method, equipment, operator and the acceptance criterion itself; assess impact on the design, on the risk file, on other tests and on any units already built; route through the change process; re-test only under an approved protocol with the retest and its justification documented.

## 11. Result

*Empty until executed. No results are claimed. This section records the summary only; individual trial records go on the trial log sheet appended to this protocol, per step 11a.*

| **Criterion** | **Met?** | **Evidence reference** | **Max observed value** |
|---------------|----------|------------------------|------------------------|
| AC-1          |          |                        |                        |
| AC-2          |          |                        |                        |
| AC-3          |          |                        |                        |
| AC-4          |          |                        |                        |
| AC-5          |          |                        |                        |

**Overall verdict:** \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

## 12. Verification of risk control RC-010

*ISO 14971:2019 requires two distinct verifications of every risk control. One is not sufficient for the other. A control can be correctly fitted and still not work — an alarm that is installed but inaudible in the real use environment is implemented and ineffective.*

|                | **What is verified**                                                                                                                                      | **Evidence in this protocol** |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------|
| Implementation | RC-010 is present in the build as specified — sensors fitted on both inlet lines, interlock wired to the pump, standoff as drawn.                         | Steps 1, 2 and 2a; AC-3       |
| Effectiveness  | RC-010 actually reduces the risk it was introduced to reduce — gas at or above threshold is detected and flow stops before the bolus reaches the cannula. | Steps 6–11; AC-1, AC-2, AC-5  |

### 12.1 Feedback to the risk management file

On acceptance, ELAP-DFMEA-001 DF-010 is re-scored and ELAP-RMF-001 HAZ-001 residual risk is re-evaluated. DF-010 currently carries D=8 on the basis that there is no detection control. If RC-010 is verified, a re-score of detection becomes justified and the RPN would fall from 360. The magnitude is not predicted here; it follows from the evidence, not from the decision to fit a control. The re-score is recorded in the DFMEA revision history with this protocol as its evidence, and is not applied before the protocol has been executed and approved.

Per ISO 14971:2019 clause 7.5, RC-010 must itself be analysed for new or increased risks it introduces. Two are already identified: a false trigger halting perfusion unnecessarily (addressed by AC-5), and the sensor housing as an additional fluid-path interface. Both are carried back into the DFMEA.

## Approval after execution

*The executed record, including all results, deviations, failures and the verdict, is reviewed and approved as a separate event from the approval of the blank protocol above.*

| **Role**         | **Name** | **Signature** | **Date** |
|------------------|----------|---------------|----------|
| Executed by      |          |               |          |
| Reviewed by      |          |               |          |
| Approved by (QA) |          |               |          |

## Annex A — Test-specific calculations

*The derivation of the requirement limits themselves — flow rates, bore, area, velocity, flow regime, bubble transport, standoff and velocity ceiling — is held in ELAP-DIS-001 Annex A and is NOT repeated here. Carrying the same calculation chain in two documents guarantees the two will diverge at the next change. This annex covers only what is specific to executing this protocol.*

### A.1 Values imported from ELAP-DIS-001 Annex A

Used in sections 4 to 7 of this protocol. Any change to these is made in ELAP-DIS-001 and flows through to this document; it is not edited here.

| **Quantity**                                               | **Value**                                 | **Source**                       |
|------------------------------------------------------------|-------------------------------------------|----------------------------------|
| Portal vein flow, maximum                                  | 1200 mL/min                               | ELAP-DIS-001 Annex A.1           |
| Hepatic artery flow, maximum                               | 450 mL/min                                | ELAP-DIS-001 Annex A.1           |
| Bore, 3/8" x 3/32" tube                                    | 4.7625 mm                                 | ELAP-DIS-001 Annex A.2           |
| Bore, 1/2" x 1/16" tube                                    | 9.5250 mm                                 | ELAP-DIS-001 Annex A.2           |
| Mean velocity, hepatic artery line                         | 0.421 m/s                                 | ELAP-DIS-001 Annex A.4           |
| Mean velocity, portal vein line                            | 0.281 m/s                                 | ELAP-DIS-001 Annex A.4           |
| Reynolds number, both lines                                | 1280 (artery) and 1706 (portal) — laminar | ELAP-DIS-001 Annex A.5           |
| Largest sphere the artery bore holds                       | 0.0566 mL                                 | ELAP-DIS-001 Annex A.6           |
| Largest sphere the portal bore holds                       | 0.4525 mL                                 | ELAP-DIS-001 Annex A.6           |
| Bounding transport velocity, binding case (portal, bubble) | 0.561 m/s                                 | ELAP-DIS-001 Annex A.6           |
| Transport velocity, artery line (slug)                     | 0.421 m/s + unquantified drift            | ELAP-DIS-001 Annex A.6           |
| Standoff, specified                                        | 450 mm                                    | ELAP-DIS-001 Annex A.7, REQ-014c |
| Calculated transit, binding case                           | 802 ms                                    | ELAP-DIS-001 Annex A.7           |
| Calculated margin, binding case                            | 4.01x                                     | ELAP-DIS-001 Annex A.7           |
| Detection threshold                                        | 0.1131 mL (6 mm equivalent sphere)        | ELAP-DIS-001 Annex A.8, REQ-014a |

### A.2 Response time budget allocation

REQ-014b specifies 200 ms total. That total is allocated across three contributions. Two are not yet allocated, and the allocation is what constrains component selection.

| **Contribution**                  | **Allocation**    | **Basis**                                                                                         |
|-----------------------------------|-------------------|---------------------------------------------------------------------------------------------------|
| Sensor detection and evaluation   | \< 10 ms          | SONOTEC SONOFLOW CO.56 Pro data sheet: internal evaluation interval max 1.6 ms, response \< 10 ms |
| Interlock signal and pump command | Not yet allocated | Depends on control architecture — open input, section 8                                           |
| Pump deceleration to zero flow    | Not yet allocated | A requirement imposed on the pump, not a measurement awaited from it                              |
| Remaining after sensor            | \> 190 ms         | 200 - 10, to be divided between the two unallocated contributions                                 |

A pump that cannot stop flow inside whatever remains after the signal allocation does not meet REQ-014b and is not selectable. This is the practical output of the protocol for procurement.

### A.3 Bolus volumes to be injected

Three volumes per line: one at the REQ-014a threshold and two above it, to show the response is not marginal at the threshold.

| **Volume** | **Equivalent sphere diameter** | **Purpose**                                                                 |
|------------|--------------------------------|-----------------------------------------------------------------------------|
| 0.113 mL   | 6.00 mm (5.998 exactly)        | At the specified threshold — the pass/fail case for REQ-014a                |
| 0.250 mL   | 7.82 mm                        | Above threshold — confirms the response does not degrade with larger volume |
| 0.500 mL   | 9.85 mm                        | Well above threshold — slug regime in the 4.76 mm bore                      |

Equivalent diameters from d = (6V / pi)^(1/3). All three volumes exceed the 4.7625 mm bore of the hepatic artery line and travel there as slugs of 6.35 mm, 14.03 mm and 28.07 mm length. All three are below the 9.5250 mm bore of the portal vein line and travel there as discrete boluses. The protocol therefore exercises the slug regime on one line and the bubble regime on the other, which is the distinction drawn in ELAP-DIS-001 Annex A.6.

### A.4 Number of trials

| **Parameter**                     | **Value** | **Basis**                                                                                                                                                               |
|-----------------------------------|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Trials per line, per bolus volume | 29        | Zero-failure attribute sampling: n = ln(1 - C) / ln(R). ln(0.05) / ln(0.90) = 28.43, rounded up to 29, giving 95% confidence at 90% reliability. Confirmed 01 Oct 2026. |
| Bolus volumes                     | 3         | A.3                                                                                                                                                                     |
| Lines                             | 2         | Hepatic artery and portal vein, tested independently                                                                                                                    |
| Total trials                      | 174       | 29 x 3 x 2                                                                                                                                                              |

### A.5 Timing measurement

Formula: t_response = t_flow_ceased - t_bolus_entered_sensing_volume

Both timestamps are taken from the independent data logger, not from the subsystem under test. A device reporting that it stopped in time is not evidence that it stopped in time. Logger resolution must be at least 1 kHz so that a 200 ms interval is resolved to 0.5 percent.

| **Quantity**                     | **Requirement**                    | **Reason**                                                       |
|----------------------------------|------------------------------------|------------------------------------------------------------------|
| Logger sample rate               | \>= 1 kHz                          | 1 ms resolution on a 200 ms limit                                |
| Flow cessation detection         | Independent of the pump controller | The pump reporting zero command is not evidence that flow ceased |
| Value compared against the limit | Maximum observed, not mean         | A mean within limit conceals individual trials outside it        |

## Sources

| **Ref** | **Source**                                                                                                                                                                                                                           | **Used for**                                                                               |
|---------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
| S1      | Brüggenwirth I.M.A. et al., "A reproducible extended ex-vivo normothermic machine liver perfusion protocol utilising improved nutrition and targeted vascular flows", Communications Medicine (2024). doi:10.1038/s43856-024-00636-2 | Targeted vascular flow rates, section 4.1                                                  |
| S2      | SONOTEC SONOFLOW CO.56 Pro V2.0 Ultrasonic Flow-Bubble Sensor, technical data sheet                                                                                                                                                  | Bubble threshold by tube size and sensor response time, sections 4.2 and 4.4               |
| S3      | ISO 14971:2019, clauses 7.2 and 7.5                                                                                                                                                                                                  | Two-part verification of risk control; analysis of new risks introduced, sections 6 and 12 |
| S4      | ISO 13485:2016 - 7.3.6; 21 CFR 820.30(f)                                                                                                                                                                                             | Design verification requirements                                                           |
| S5      | ELAP-DFMEA-001 Rev 1.3, item DF-010 and section 8                                                                                                                                                                                    | Origin of RC-010 and the open inputs carried into section 8                                |

## Revision history

| **Rev** | **Date**    | **Change**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | **By**    |
|---------|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| 1.0     |             | Initial issue. Written against a bubble-detector control that was carried over from a worked template and is not present in the ELAP design. Numeric limits left blank.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | Raj Harsh |
| 2.0     | 01 Oct 2026 | Renumbered from ELAP-VP-007 to ELAP-VP-001. Rebased. Control identified as RC-010, the adopted recommended action from DF-010, and explicitly recorded as specified but not built. REQ-014 split into four testable requirements (014a–014d). All numeric limits derived from cited sources in section 4. REQ-014d added as a design input derived from the response-time requirement. Section 8 open inputs added. Deviations and failures separated into distinct sections. Section 12 added for two-part risk control verification and feedback to the risk file. Requirements relocated to ELAP-DIS-001, which this protocol now verifies against.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | Raj Harsh |
| 3.2     | 01 Oct 2026 | SECOND ERROR CORRECTED, found in review. Rev 3.0 applied the laminar centreline case (2 x mean) to both inlet lines. It cannot apply to the hepatic artery line: the REQ-014a detection threshold of 0.113 mL is twice the largest sphere its 4.7625 mm bore will hold, so every bolus the control can detect there is a slug travelling at approximately the mean. The binding case is the portal vein line at 0.561 m/s, requiring 281 mm; the 450 mm standoff is retained as margin over the unquantified slug drift. Four internal section cross-references corrected, including step 13, which directed deviations and failures into the wrong sections. AC-5 now traces to REQ-014e rather than to a section number. Step 2a added so that RC-010 implementation is actually inspected. Step 11a and a trial log sheet added, the previous document having mandated 174 individual trial records with nowhere to put them. An independent bolus-entry timestamp instrument added to section 5 and its unresolved transit correction recorded in section 8. Sample size of 29 confirmed by formula and closed as an open input. ISO 14971 clause for risks arising from risk controls corrected from 7.4 to 7.5. All citations of ELAP-DFMEA-001 updated from Rev 1.2 to Rev 1.3 and of ELAP-DIS-001 from Rev 1.0 to Rev 1.3. Calculated values relabelled as calculated rather than achieved. | Raj Harsh |
| 3.1     | 01 Oct 2026 | Risk control identifier changed from RC-003 to RC-010 for consistency with ELAP-DFMEA-001. Section symbols replaced with plain text. Annex A reduced to test-specific calculations, the requirement derivation being held in ELAP-DIS-001 Annex A.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | Raj Harsh |
| 3.0     | 01 Oct 2026 | ERROR CORRECTED. Rev 2.0 computed bubble transit time from bulk MEAN velocity. Both inlet lines run laminar (Re 1280 and 1706), so centreline velocity is twice the mean and a small bolus can travel at up to 2 x the mean. The margin at a 250 mm standoff was therefore 1.48x, not the 2.97x stated — roughly half the claimed safety margin. REQ-014c standoff increased from 250 mm to 450 mm, restoring 2.67x. Reynolds numbers and flow regime added to section 4.3. Annex A added giving every formula and worked value. Two further open inputs recorded: a conflict between the 4 degC operating temperature in the DFMEA and the 37 degC basis of the cited flow rates, and the unvalidated bubble transport model. Stale cross-reference corrected.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | Raj Harsh |

