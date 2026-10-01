# ELAP-DIS-001 — Design Input Specification

**External Liver Assistance Platform**

| **Field**       | **Entry**       |
|-----------------|-----------------|
| Document number | ELAP-DIS-001    |
| Revision        | 1.3             |
| Effective date  | 01 October 2026 |
| Prepared by     | Raj Harsh       |

*Self-directed exercise on an independent design project. Not industry work. Not a controlled document under any quality management system.*

*ISO 13485:2016 - 7.3.3 / 21 CFR 820.30(c). Inputs must be verifiable — if you cannot write a test that passes or fails against it, it is not a requirement yet.*

## 1. Purpose and scope

This specification records design input requirements for the External Liver Assistance Platform under ISO 13485:2016 - 7.3.3 and 21 CFR 820.30(c).

**This revision is partial.** It covers only the requirements arising from risk control measure RC-010 and the constraints derived from them, which was adopted as the recommended action against DF-010 in ELAP-DFMEA-001 Rev 1.3. Requirements covering the remaining functions of the device are not yet written. The specification is issued in this partial state so that ELAP-VP-001 has a requirement baseline to verify against.

## 2. Requirement sources

| **Source**                         | **Reference**                                                                                                                                                                                                                                                                                                |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Risk control measures              | ELAP-DFMEA-001 Rev 1.3, DF-010 → RC-010                                                                                                                                                                                                                                                                      |
| Similar devices / state of the art | Brüggenwirth I.M.A. et al., "A reproducible extended ex-vivo normothermic machine liver perfusion protocol utilising improved nutrition and targeted vascular flows", Communications Medicine (2024). doi:10.1038/s43856-024-00636-2 — targeted vascular flow rates for ex vivo normothermic liver perfusion |
| Component capability               | SONOTEC SONOFLOW CO.56 Pro V2.0 ultrasonic flow-bubble sensor, technical data sheet — bubble detection threshold by tube size, sensor response time                                                                                                                                                          |
| User needs                         | Not yet documented. ELAP-RMP-001 is not complete, so intended use and user needs are not yet a formal input to this specification.                                                                                                                                                                           |
| Applicable standards               | ISO 14971:2019 (risk control derivation); ISO 13485:2016 - 7.3.3; 21 CFR 820.30(c)                                                                                                                                                                                                                           |
| Applicable regulatory requirements | Not yet determined. Device classification under EU MDR 2017/745 and the US pathway have not been established for this design.                                                                                                                                                                                |

## 3. Requirements

**Rules for this table:** *one requirement per row; no "and"; no "shall be user-friendly"; every row must be testable. Requirements derived from risk controls are marked, because those need verification of effectiveness as well as implementation.*

**REQ-014a — Gas detection shall be fitted on each perfusion inlet line and shall detect a discrete gas bolus of 0.113 mL or greater, equivalent to a 6 mm diameter sphere.**

| **Field**            | **Entry**                                                                                                                                                                                                                              |
|----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Category             | Safety                                                                                                                                                                                                                                 |
| Source               | DF-010 → RC-010                                                                                                                                                                                                                        |
| Risk control?        | Yes — verification of implementation and of effectiveness both required                                                                                                                                                                |
| Acceptance criterion | 29 of 29 trials detected per line, per bolus volume, zero misses. Sample size from n = ln(1 - C) / ln(R) for zero-failure attribute sampling: ln(0.05) / ln(0.90) = 28.43, rounded up to 29, giving 95% confidence at 90% reliability. |
| Verification method  | Test                                                                                                                                                                                                                                   |
| Basis for the limit  | Threshold set by commercially available sensor capability (SONOFLOW CO.56 Pro default threshold for the bores in use). Derived in Annex A.8.                                                                                           |

**REQ-014b — On detection of a gas bolus meeting REQ-014a, the system shall halt pump-driven flow within 200 ms, measured from entry of the bolus into the sensing volume to cessation of flow.**

| **Field**            | **Entry**                                                                                                                                                                                                                                    |
|----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Category             | Safety                                                                                                                                                                                                                                       |
| Source               | DF-010 → RC-010                                                                                                                                                                                                                              |
| Risk control?        | Yes — verification of implementation and of effectiveness both required                                                                                                                                                                      |
| Acceptance criterion | Maximum observed response time ≤ 200 ms in every trial. The maximum, not the mean, is compared against the limit.                                                                                                                            |
| Verification method  | Test                                                                                                                                                                                                                                         |
| Basis for the limit  | Budget specified by the designer and then allocated across sensor detection, interlock signal and pump deceleration. It constrains which pump may be selected; it is not a figure measured from a pump already chosen. Derived in Annex A.7. |

**REQ-014c — The sensing point on each inlet line shall be located not less than 450 mm upstream of the cannula connection, measured along the flow path.**

| **Field**            | **Entry**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Category             | Safety                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Source               | DF-010 → RC-010                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Risk control?        | Yes — verification of implementation and of effectiveness both required                                                                                                                                                                                                                                                                                                                                                                                                                        |
| Acceptance criterion | Measured standoff ≥ 450 mm on both inlet lines                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Verification method  | Inspection                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Basis for the limit  | Both inlet lines run laminar. Whether a bolus travels at the mean velocity or at twice it depends on whether it fits inside the bore — see Annex A.6. The binding case is the portal vein line at a bounding bubble velocity of 0.561 m/s, which requires 281 mm for a 2.5x margin. 450 mm is specified, giving 4.01x on that line and 5.34x on the hepatic artery line. The additional margin covers the buoyant drift on slug-regime boluses, which is not quantified. Derived in Annex A.7. |

**REQ-014e — Gas detection shall not halt pump-driven flow in the absence of a gas bolus. No false trigger shall occur during 30 minutes of continuous gas-free circulation at maximum specified flow on each inlet line.**

| **Field**            | **Entry**                                                                                                                                                                                                                                |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Category             | Safety                                                                                                                                                                                                                                   |
| Source               | ISO 14971:2019 clause 7.5 — risks arising from risk control measures                                                                                                                                                                     |
| Risk control?        | Yes — RC-010 is itself analysed for the new risks it introduces                                                                                                                                                                          |
| Acceptance criterion | Zero triggers in 30 minutes of gas-free circulation at maximum flow, each line                                                                                                                                                           |
| Verification method  | Test                                                                                                                                                                                                                                     |
| Basis for the limit  | A detector that halts perfusion on noise is a new hazard, not a control: an unnecessary stop interrupts organ perfusion. The 30 minute duration is a design decision and is not derived from a target false-alarm rate; recorded in A.9. |

**REQ-014d — Perfusion inlet tubing bore shall be selected such that bulk flow velocity at maximum specified flow does not exceed 0.45 m/s in any line carrying gas detection.**

| **Field**            | **Entry**                                                                                                                                                                                                                                                                                             |
|----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Category             | Performance                                                                                                                                                                                                                                                                                           |
| Source               | Derived from REQ-014b and REQ-014c                                                                                                                                                                                                                                                                    |
| Risk control?        | No — derived design constraint                                                                                                                                                                                                                                                                        |
| Acceptance criterion | Calculated velocity ≤ 0.45 m/s in both lines, from measured bore and measured flow                                                                                                                                                                                                                    |
| Verification method  | Analysis                                                                                                                                                                                                                                                                                              |
| Basis for the limit  | Derived, not specified from outside. Running the portal line on 3/8" x 3/32" instead would raise its mean velocity to 1.123 m/s and push Reynolds to 3412, outside the laminar regime the transport model of Annex A.6 assumes, so the bore itself must be constrained. Full derivation in Annex A.8. |

*T = Test · I = Inspection · A = Analysis · D = Demonstration*

*Requirements covering the remaining device functions — chamber envelope, bile drainage, lid seal, vent, outlet path, thermal control, materials, sterility, labelling — are not yet written. The DFMEA recommended actions for DF-001 to DF-004, DF-006, DF-007, DF-009 and DF-011 are the input to those requirements and remain to be converted. DF-005 and DF-008 carry no action, having been assessed as acceptable.*

## 4. Incomplete, ambiguous or conflicting requirements

*ISO 13485:2016 - 7.3.3 requires these to be identified and resolved. Recorded here with their resolution.*

| **REQ ID**         | **Issue**                                                                                                                                                                                                                                                                                                                                                                                       | **Resolution**                                                                                                                                                                                                                                                                                                                                                                                                                                    | **Date**    |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| REQ-014 (original) | Combined a detection threshold and a response time in a single statement, and left both numeric values blank. Not independently testable as written: a single pass/fail could not be assigned, and no limit existed to test against.                                                                                                                                                            | Split into REQ-014a, REQ-014b and REQ-014c, each independently testable. All numeric limits derived in ELAP-VP-001 section 4 against cited sources. REQ-014d added as a design input derived from the response-time requirement — the standoff of REQ-014c is only satisfiable within a bore constraint.                                                                                                                                          | 01 Oct 2026 |
| REQ-014a           | The 0.113 mL threshold is set by sensor capability, not by established organ tolerance to gas volume. No figure for tolerable gas volume in hepatic microvasculature has been established for this device.                                                                                                                                                                                      | Not resolved. Recorded as an open input in Annex A.9 of this document and in ELAP-VP-001 section 8. The threshold is precautionary and capability-led, and is stated as such rather than presented as clinically derived.                                                                                                                                                                                                                         | 01 Oct 2026 |
| REQ-014c           | Rev 1.0 specified a standoff of 250 mm. The transit time behind it had been computed from bulk MEAN velocity. Both inlet lines are laminar, so a small gas bolus on the centreline travels at up to twice the mean, halving the available transit time. The stated margin of 2.97x was in fact 1.48x.                                                                                           | Corrected in Rev 1.1. Standoff increased to 450 mm. The 2.67x margin claimed at the time was itself computed from a transport model since found to be wrong for that line — see the next row. Current derivation in Annex A.5 to A.7.                                                                                                                                                                                                             | 01 Oct 2026 |
| REQ-014c, REQ-014d | The 2 x mean centreline transport model was applied to both inlet lines. It cannot apply to the hepatic artery line: the REQ-014a detection threshold of 0.113 mL is twice the largest sphere its 4.7625 mm bore will hold, so every detectable bolus there is a slug, not a centreline bubble. The limits were therefore derived from a transport case the control is specified not to detect. | Corrected in Rev 1.3. Regime determined per line in Annex A.6. The binding case is the portal vein line at 0.561 m/s, requiring 281 mm for a 2.5x margin. The 450 mm standoff is retained, now justified as margin over the unquantified slug drift rather than as a calculated minimum. The error direction was conservative — the standoff was over-specified, not under-specified — but the derivation did not support the figure it produced. | 01 Oct 2026 |
| REQ-014a to 014d   | The flow rates these limits derive from are published targets for NORMOTHERMIC perfusion at 37 degC. ELAP-DFMEA-001 Rev 1.3 states operation at 4 degC. Hypothermic perfusion runs at lower flow, and water viscosity at 4 degC is roughly twice that at 37 degC, changing both velocity and Reynolds number.                                                                                   | Not resolved. The operating temperature of the device is not settled. Recorded as an open input in Annex A.9 of this document and in ELAP-VP-001 section 8. Every velocity-dependent limit in this specification is provisional until it is.                                                                                                                                                                                                      | 01 Oct 2026 |

## Annex A — Derivation of the numeric limits

*This annex is the authoritative derivation for every number in section 3. ELAP-VP-001 cites it rather than repeating it, so that a change to a limit is made in one place only. Every value was recomputed from its formula on 01 Oct 2026 and agrees with the figure stated. That is an arithmetic check by the same person who wrote it, not an independent review; section 5 records that independent review is not available in a single-person exercise.*

### A.1 Perfusion flow rate

Formula: Q = q_specific x (m / 100 g)

| **Quantity**            | **Inputs**                           | **Result**        |
|-------------------------|--------------------------------------|-------------------|
| Donor liver mass, m     | 1500 g assumed — open input, see A.9 | 15 units of 100 g |
| Portal vein, maximum    | 80 mL/100 g/min x 15                 | 1200 mL/min       |
| Hepatic artery, maximum | 30 mL/100 g/min x 15                 | 450 mL/min        |
| Combined, maximum       | 110 mL/100 g/min x 15                | 1650 mL/min       |
| Arithmetic cross-check  | 1200 + 450                           | 1650 — consistent |

Specific flows from Brüggenwirth et al., Communications Medicine (2024): portal vein 75-80 mL/100 g/min, hepatic artery 25-30 mL/100 g/min. The upper bound of each range is taken, since worst case for this analysis is maximum velocity.

### A.2 Tube internal bore

Tubing is specified as outside diameter x wall thickness, both in inches. The bore is the remaining hole through which fluid flows. 1 inch = 25.4 mm.

Formula: d = (OD - 2w) x 25.4

| **Tube (OD x wall)** | **Working**             | **Bore d** |
|----------------------|-------------------------|------------|
| 1/4" x 1/16"         | (0.250 - 0.125) x 25.4  | 3.1750 mm  |
| 1/4" x 3/32"         | (0.250 - 0.1875) x 25.4 | 1.5875 mm  |
| 3/8" x 3/32"         | (0.375 - 0.1875) x 25.4 | 4.7625 mm  |
| 1/2" x 1/16"         | (0.500 - 0.125) x 25.4  | 9.5250 mm  |

### A.3 Cross-sectional area

Formula: A = pi d^2 / 4

| **Bore d** | **Working**       | **Area A**  |
|------------|-------------------|-------------|
| 4.7625 mm  | pi x 4.7625^2 / 4 | 17.8139 mm2 |
| 9.5250 mm  | pi x 9.5250^2 / 4 | 71.2557 mm2 |

### A.4 Bulk mean velocity

Formula: v_mean = Q / A, with 1 mL/min = 1000 mm3 / 60 s = 16.6667 mm3/s

| **Line and tube**                    | **Working**                                    | **v_mean**               |
|--------------------------------------|------------------------------------------------|--------------------------|
| Hepatic artery, 3/8" x 3/32"         | (450 x 16.6667) / 17.8139 = 7500.0 / 17.8139   | 421.02 mm/s = 0.421 m/s  |
| Portal vein, 1/2" x 1/16"            | (1200 x 16.6667) / 71.2557 = 20000.0 / 71.2557 | 280.68 mm/s = 0.281 m/s  |
| Portal vein, 3/8" x 3/32" — rejected | 20000.0 / 17.8139                              | 1122.72 mm/s = 1.123 m/s |

### A.5 Flow regime — and why it matters

Formula: Re = rho v d / mu. Water at 4 degC: rho = 1000 kg/m3, mu = 1.567 x 10^-3 Pa s. Flow is laminar below Re of approximately 2300.

| **Line**                     | **Working**                          | **Re** | **Regime**                   |
|------------------------------|--------------------------------------|--------|------------------------------|
| Hepatic artery               | 1000 x 0.4210 x 0.0047625 / 1.567e-3 | 1280   | Laminar                      |
| Portal vein                  | 1000 x 0.2807 x 0.0095250 / 1.567e-3 | 1706   | Laminar                      |
| Portal vein, 3/8" — rejected | 1000 x 1.1227 x 0.0047625 / 1.567e-3 | 3412   | Transitional — model invalid |

This step is not decorative. The flow regime determines the velocity profile, and the velocity profile determines how fast a gas bolus can travel relative to the bulk flow.

### A.6 Bubble transport velocity

In fully developed laminar pipe flow the velocity profile is parabolic and the centreline velocity is twice the cross-sectional mean. Which case applies depends on whether the bolus fits inside the bore:

- A bolus SMALLER than the bore can ride the centreline and travels at up to 2 x v_mean.

- A bolus LARGER than the bore spans the full cross-section as a slug. It travels at approximately v_mean plus a buoyant drift that is not quantified here.

Whether the detection threshold of REQ-014a falls above or below the bore therefore decides which case bounds each line. Formula for the largest sphere a bore will contain: V = pi d_bore^3 / 6

| **Line**       | **Bore**  | **Largest sphere the bore contains** | **REQ-014a threshold** | **Regime at threshold**                                                                                                |
|----------------|-----------|--------------------------------------|------------------------|------------------------------------------------------------------------------------------------------------------------|
| Hepatic artery | 4.7625 mm | 56.56 mm3 = 0.0566 mL                | 0.113 mL               | SLUG — threshold is 2.0x the largest sub-bore sphere. A 0.113 mL bolus forms a slug 6.35 mm long, 1.33 bore diameters. |
| Portal vein    | 9.5250 mm | 452.47 mm3 = 0.4525 mL               | 0.113 mL               | BUBBLE — threshold is well under the sub-bore limit, so the centreline case applies.                                   |

This is a correction to the reasoning carried in Rev 1.1 and Rev 1.2, which applied the 2 x mean case to both lines. It cannot apply to the hepatic artery line: no bolus the control is specified to detect is small enough to ride the centreline there. Any bolus that is small enough is below the detection threshold and is explicitly out of scope.

| **Line**                       | **Regime at and above threshold** | **v_mean** | **Bounding transport velocity**                                              |
|--------------------------------|-----------------------------------|------------|------------------------------------------------------------------------------|
| Hepatic artery                 | Slug                              | 0.421 m/s  | 0.421 m/s + unquantified buoyant drift                                       |
| Portal vein                    | Bubble, centreline                | 0.281 m/s  | 0.561 m/s                                                                    |
| Portal vein on 3/8" — rejected | Bubble, centreline                | 1.123 m/s  | 2.245 m/s, but Re 3412 puts it outside the laminar regime this model assumes |

The binding case is therefore the PORTAL VEIN line at 0.561 m/s, not the hepatic artery line. The direction of the Rev 1.2 error was conservative — it over-specified the standoff rather than under-specifying it — but the derivation did not support the number it produced.

### A.7 Standoff distance (REQ-014c)

Formulas:

t_transit = L / v_bubble

margin = t_transit / t_budget

L_min = k x t_budget x v_bubble

| **Quantity**                 | **Working**                                                                                                                                                                                                                                                          | **Result** |
|------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|
| Minimum acceptable margin, k | Design decision, not derived. Intended to cover bore manufacturing tolerance, flow overshoot above nominal, and the approximation in the transport model of A.6. None of those three is quantified, so k is a judgement, not a calculation. Recorded as such in A.9. | 2.5        |
| Binding line                 | Portal vein — highest bounding transport velocity at and above the detection threshold, per A.6                                                                                                                                                                      | 0.561 m/s  |
| L_min                        | 2.5 x 0.200 s x 561.4 mm/s                                                                                                                                                                                                                                           | 280.7 mm   |
| Specified in REQ-014c        | 280.7 mm, increased to 450 mm                                                                                                                                                                                                                                        | 450 mm     |

450 mm is specified rather than the calculated 281 mm. The additional distance covers the buoyant drift on slug-regime boluses in the hepatic artery line, which A.6 records as unquantified, and it retains the figure carried in Rev 1.1 and Rev 1.2 so that no previously issued limit is relaxed on the strength of a model correction.

| **Standoff L** | **Line**              | **v_bubble** | **t_transit** | **Margin vs 200 ms** | **Verdict**                                                                                                                                       |
|----------------|-----------------------|--------------|---------------|----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| 450 mm         | Portal vein           | 0.561 m/s    | 801.6 ms      | 4.01x                | Accepted — binding case                                                                                                                           |
| 450 mm         | Hepatic artery (slug) | 0.421 m/s    | 1069 ms       | 5.34x                | Accepted, excluding unquantified drift                                                                                                            |
| 281 mm         | Portal vein           | 0.561 m/s    | 500.0 ms      | 2.50x                | Minimum that would satisfy k                                                                                                                      |
| 450 mm         | Portal vein on 3/8"   | 2.245 m/s    | 200.4 ms      | 1.00x                | Rejected — no margin; also outside the laminar regime, so this margin figure is itself unreliable and the Reynolds result is the governing reason |

### A.8 Velocity ceiling (REQ-014d) and gas bolus volume (REQ-014a)

Formula: v_mean,max = L / (2 k t_budget). The factor 2 converts mean velocity to bounding bubble velocity per A.6.

| **Quantity**                                    | **Working**                                                      | **Result**                                                |
|-------------------------------------------------|------------------------------------------------------------------|-----------------------------------------------------------|
| v_mean,max                                      | 450 mm / (2 x 2.5 x 200 ms)                                      | 0.450 m/s                                                 |
| Check                                           | v_bubble = 0.900 m/s; t = 450 / 900 = 500 ms; margin = 500 / 200 | 2.50x — exactly at the limit                              |
| Headroom on the portal line as designed         | 0.281 / 0.450                                                    | 62% of the ceiling                                        |
| Headroom on the hepatic artery line as designed | 0.421 / 0.450                                                    | 94% of the ceiling — see A.9, no bore tolerance is stated |

The ceiling applies the 2 x factor, so it is written for the bubble case. It is conservative for the hepatic artery line, where the slug case applies. The artery line nonetheless sits at 94 percent of the ceiling, and because AC-4 is checked on MEASURED bore, a tube at the low end of an unstated commercial tolerance could exceed the ceiling while conforming to the drawing. A bore tolerance is required and is recorded in A.9.

Formula: V = pi d^3 / 6. The sensor datasheet states detection thresholds as the diameter of an equivalent sphere; the requirement is written as a volume.

| **Sphere diameter** | **Tube it applies to**        | **Working**  | **Volume**              |
|---------------------|-------------------------------|--------------|-------------------------|
| 4 mm                | 1/4" x 1/16"                  | pi x 64 / 6  | 33.510 mm3 = 0.0335 mL  |
| 5 mm                | 1/4" x 3/32"                  | pi x 125 / 6 | 65.450 mm3 = 0.0654 mL  |
| 6 mm                | 3/8" x 3/32" and 1/2" x 1/16" | pi x 216 / 6 | 113.097 mm3 = 0.1131 mL |

Both bores actually in use carry the same 6 mm factory default, so 0.113 mL is satisfied on either line without ordering a non-standard threshold. The 1/4" rows are shown for completeness; no 1/4" tube appears in this design. 113.097 mm3 is stated in REQ-014a as 0.113 mL, a downward rounding that makes the requirement marginally stricter than the 6.00 mm equivalence it quotes.

### A.9 What this annex does not establish

The arithmetic above is reproducible and has been re-checked by its author. It rests on four inputs that are not established, and correct arithmetic on unestablished inputs produces a precise answer rather than a right one.

| **Unestablished input**                                                                                                                                        | **Consequence if wrong**                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Donor liver mass of 1500 g                                                                                                                                     | Scales every flow figure, and therefore every velocity, transit time and margin in A.4 to A.8.                                                                                                                                                                                                                 |
| The 200 ms response budget of REQ-014b                                                                                                                         | Chosen, not derived. It is the denominator of every margin in A.7 and A.8. No analysis establishes that 200 ms is the right figure rather than 100 ms or 400 ms, and the allocation across sensor, signal and pump is not yet made.                                                                            |
| The minimum margin k = 2.5                                                                                                                                     | Chosen, not derived. It is named as covering bore tolerance, flow overshoot and transport-model error, none of which is quantified.                                                                                                                                                                            |
| Inlet tubing bore tolerance                                                                                                                                    | Not stated anywhere. The hepatic artery line runs at 94 percent of the REQ-014d ceiling, so an ordinary commercial bore tolerance could take a conforming tube over the limit. Required before REQ-014d can be verified meaningfully.                                                                          |
| The measurement datum for REQ-014c                                                                                                                             | Cannula and tubing connection geometry is not defined, so "450 mm measured along the flow path to the cannula connection" has no fixed endpoint and cannot be inspected repeatably.                                                                                                                            |
| Operating temperature. The flow figures of A.1 are published targets for NORMOTHERMIC perfusion at 37 degC; ELAP-DFMEA-001 Rev 1.3 states operation at 4 degC. | Hypothermic perfusion runs at lower flow, and water viscosity at 4 degC is roughly twice that at 37 degC. Both velocity and Reynolds number change. Every velocity-dependent limit in this specification is provisional until the operating temperature is settled.                                            |
| The 2 x mean bubble transport model of A.6                                                                                                                     | A.6 establishes which case applies to each line, but neither case is validated for this geometry. The slug drift velocity on the hepatic artery line is not quantified at all, and tube orientation and buoyancy are not modelled. The 450 mm standoff is believed conservative; it is not demonstrated to be. |
| Organ tolerance to gas volume                                                                                                                                  | The 0.113 mL threshold of REQ-014a is what the sensor can detect, not what the organ can withstand. No tolerance figure has been established. The threshold is precautionary, not clinically derived.                                                                                                          |

## 5. Review and approval

| **Role**    | **Name**  | **Signature** | **Date**    |
|-------------|-----------|---------------|-------------|
| Prepared by | Raj Harsh | R.H.          | 01 Oct 2026 |
| Reviewed by |           |               |             |
| Approved by |           |               |             |

*Independent review and QA approval cannot be performed in a single-person exercise. Both roles are left unsigned deliberately.*

## Revision history

| **Rev** | **Date**    | **Change**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | **By**    |
|---------|-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| 1.3     | 01 Oct 2026 | TRANSPORT MODEL CORRECTED following review. Rev 1.1 and 1.2 applied the 2 x mean centreline case to both inlet lines. It cannot apply to the hepatic artery line: the REQ-014a detection threshold of 0.113 mL is twice the largest sphere that fits its 4.7625 mm bore, so every detectable bolus there is a slug travelling at approximately the mean. The binding case is the portal vein line at 0.561 m/s, requiring 281 mm. The 450 mm standoff of REQ-014c is retained, now justified as margin over the unquantified slug drift rather than as a calculated minimum. REQ-014e added so that AC-5 in ELAP-VP-001 traces to a requirement. REQ-014d source corrected to name REQ-014c. Stale REQ-014d basis text carrying the superseded 250 mm figure removed. Sample size of 29 closed with its formula. Four further unestablished inputs recorded in A.9: the 200 ms budget, the k = 2.5 margin, inlet bore tolerance, and the REQ-014c measurement datum. All references to ELAP-DFMEA-001 updated from Rev 1.2 to Rev 1.3, which is the revision that adopts RC-010. | Raj Harsh |
| 1.2     | 01 Oct 2026 | Annex A added, giving the derivation of every numeric limit with its formula, inputs and result, independently re-checked. Header reduced to the fields in use. Section symbols replaced with plain text.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Raj Harsh |
| 1.1     | 01 Oct 2026 | REQ-014c standoff corrected from 250 mm to 450 mm. The transit time behind the original figure used bulk mean velocity; laminar centreline velocity is twice the mean, so the margin was 1.48x rather than the 2.97x claimed. Two unresolved entries added to section 4: the normothermic/hypothermic temperature conflict, and the sensor-led basis of the detection threshold.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Raj Harsh |
| 1.0     | 01 Oct 2026 | Initial issue, partial. Covers the four requirements derived from risk control RC-010 only. Issued in partial state to give ELAP-VP-001 a requirement baseline.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | Raj Harsh |

