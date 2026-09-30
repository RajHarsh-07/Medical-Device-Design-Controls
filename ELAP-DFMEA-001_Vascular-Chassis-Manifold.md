# Design FMEA — Vascular Chassis Isolation Manifold

| | |
|---|---|
| Document number | ELAP-DFMEA-001 |
| Revision | 1.1 |
| Prepared by | Raj Harsh |

> Self-directed exercise on an independent design project. Not industry work. Not a controlled document under any quality system.

---

## 1. Scope and assumptions

| Field | Entry |
|---|---|
| **Item analysed** | Vascular Chassis — precision isolation manifold forming the core cartridge of the External Liver Assistance Platform (ELAP). Analysed at component level as a fluidic distribution and isolation device. |
| **Configuration / revision** | V_3.1_Assembly 1.2, comprising Flow region, Cradle, Chassis_Base and Chassis_Lid. CFD reference: SimScale project Project_L_V_3.1_Extreme, Run 7 (22 May 2026; 234 min, 748.58 core hours), Mesh 6 (21,767,268 nodes; approximately 89.0 million volume cells). Boundary conditions: velocity inlet 0.15 m/s at 4 °C; pressure outlet 0 Pa gauge at 4 °C. Fluid modelled as water; solids modelled as steel. |
| **Boundary of analysis (what is in)** | Manifold body and internal flow channels; inlet and outlet ports; port isolation features; sealing interfaces and connectors at the manifold boundary; Cradle, Chassis_Base and Chassis_Lid as modelled in V_3.1_Assembly 1.2. |
| **Boundary of analysis (what is out)** | Pump, tubing set, oxygenator, temperature control equipment, sensors, control software and user interface — none of these form part of this analysis. The organ scaffold itself, and biological variability in it. |
| **Assumptions** | Assumed single-use and supplied sterile; not formally specified at this stage. Perfusate modelled as water; real perfusate properties not characterised. Solids modelled as steel; the intended manufacturing material is not yet specified. Operating condition taken as 0.15 m/s inlet velocity at 4 °C. Wall shear criterion of 1.5 Pa adopted for extracellular-matrix protection, set on engineering judgement and not derived from a cited source. No physical units have been built or tested. All occurrence ratings are engineering judgement based on analogous fluidic components, not on test or field data.                                                                                      This analysis covers selected principal functions of the manifold and chamber and is not exhaustive. It is a self-directed learning exercise, not a production deliverable. |
| **Not covered, and why** | Manufacturing and assembly process failure modes are outside the scope of a design FMEA. Software behaviour and use-related errors are likewise outside the scope of this analysis. Thermal performance is not addressed: the referenced CFD run was isothermal at 4 °C with no thermal load applied, so it provides no evidence of thermal behaviour under ambient heat ingress. None of these areas has been analysed elsewhere for this project at present. |
| **Team / reviewers** | Raj Harsh — sole analyst. Limitation: a design FMEA is normally conducted cross-functionally, across design, manufacturing, quality and clinical input. A single-analyst analysis is more exposed to blind spots, and this is recorded as a limitation of the exercise. |
| **Action threshold rule applied** | Any failure mode with S ≥ 8 is actioned regardless of RPN. Any failure mode with RPN ≥ 100 is actioned. Any failure mode with S ≥ 7 and D ≥ 7 is actioned regardless of RPN. |
| **Justification for that rule** | RPN alone is unsuitable as a sole decision rule. S, O and D are ordinal scales, so their product is not mathematically meaningful — an RPN of 100 arising from 10 × 10 × 1 describes a different problem from 5 × 5 × 4. High-severity modes are therefore actioned on severity, consistent with ISO 14971, which directs that risk be evaluated on the basis of severity where the probability of occurrence of harm cannot be reliably estimated. That is the situation here, since no physical units have been built or tested. AIAG-VDA's replacement of RPN with Action Priority reflects the same criticism in an automotive context; it is cited as supporting rationale only and is not a medical device requirement. |

---

## 2. Method

A DFMEA is **bottom-up**: it starts from a function and asks what happens when that function fails. ISO 14971 is **top-down**: it starts from a hazard and works back. The two are complementary, not substitutes. Every failure effect here that constitutes harm is traced to the risk management file in section 5.

Functions were listed before any failure mode was written. Failure mode, effect and cause are kept distinct throughout: the cause is a mechanism that could be changed, not a restatement of the failure.

---

## 3. Rating scales

Fixed before scoring. An RPN is meaningless without a stated scale.

**Severity (S)**

| Rank | Criterion |
|---|---|
| 10 | Death, or regulatory non-compliance without warning |
| 8–9 | Loss of primary function; potential serious injury |
| 6–7 | Degraded primary function; potential minor injury |
| 4–5 | Loss or degradation of secondary function |
| 2–3 | Appearance or nuisance effect |
| 1 | No discernible effect |

**Occurrence (O)**

| Rank | Criterion |
|---|---|
| 10 | Almost inevitable; no prevention control |
| 7–9 | Frequent; new design, unproven |
| 4–6 | Occasional; similar design with some history |
| 2–3 | Rare; proven design in similar application |
| 1 | Eliminated by design |

**Detection (D)** — note the inversion: 1 is certain detection, 10 is none.

| Rank | Criterion |
|---|---|
| 10 | No detection possible |
| 7–9 | Detection unlikely; indirect or by chance |
| 4–6 | Detection likely; post-design testing |
| 2–3 | Very likely; established analysis or test |
| 1 | Cannot occur, or detected with certainty |

---

## 4. Analysis

### DF-001 — Maintain a sealed barrier between the fluid path and the external environment (lid seal)

| | |
|---|---|
| **Failure mode** | O-ring gland fails to seal the lid |
| **Effect** | Air and bacteria enter the enclosure; perfusate contaminated; infection risk to the organ and recipient |
| **Severity (S)** | 8 |
| **Cause** | Gland dimensions do not guarantee sufficient O-ring compression across the tolerance range; incorrect O-ring size or material |
| **Occurrence (O)** | 3 |
| **Prevention control** | Gland dimensioned per O-ring supplier compression guidance; tolerance stack analysis to confirm minimum squeeze at worst case |
| **Detection control** | Post-assembly seal verification by pressure decay test; visual check that the lid is fully closed |
| **Detection (D)** | 3 |
| **RPN** | **72** |
| **Action** | Tolerance stack analysis on the gland to confirm minimum compression at worst-case tolerances; define a post-assembly leak test with a documented acceptance criterion |
| **Owner** | R. Harsh |

### DF-002 — Allow pressure equalisation across the lid while preventing ingress of airborne contamination

| | |
|---|---|
| **Failure mode** | Vent filter fails to retain airborne contamination |
| **Effect** | Air and bacteria enter the enclosure; perfusate contaminated; infection risk to the organ and recipient |
| **Severity (S)** | 8 |
| **Cause** | Filter pore size not specified for bacterial retention; filter media wetted by condensation and blocked; retention method fails and filter detaches |
| **Occurrence (O)** | 5 |
| **Prevention control** | 0.2 µm hydrophobic sterilising-grade vent filter specified in design inputs; vent area sized for required flow; retention method defined on the drawing |
| **Detection control** | Incoming inspection of filter specification against the drawing; bacterial challenge test on the filter as fitted |
| **Detection (D)** | 4 |
| **RPN** | **160** |
| **Action** | Define the filter specification (pore size, hydrophobicity, retention rating, fixing method) as a design input; qualify the fitted filter by bacterial challenge test with a documented acceptance criterion |
| **Owner** | R. Harsh |

### DF-003 — Locate and retain the scaffold cradle in a defined, repeatable position within the chamber

| | |
|---|---|
| **Failure mode** | Cradle seats in an incorrect or unrepeatable position |
| **Effect** | Cradle shifts during perfusion; tension or kinking on the vascular connections; occlusion or detachment of a connection; loss of perfusion to the scaffold and mechanical damage to the organ |
| **Severity (S)** | 7 |
| **Cause** | Pin-to-hole clearance and tolerance stack allow the cradle to seat in more than one position; hole pattern is symmetric, so the cradle can be fitted in the wrong orientation; no positive locating feature |
| **Occurrence (O)** | 4 |
| **Prevention control** | Asymmetric pin pattern so the cradle physically cannot seat in the wrong orientation; one close-fit round hole for location and one slotted hole to absorb tolerance without over-constraining; tolerance stack analysis on pin-to-hole fit |
| **Detection control** | Visual and tactile confirmation of full seating at setup; lid cannot close unless the cradle is correctly seated |
| **Detection (D)** | 4 |
| **RPN** | **112** |
| **Action** | Add an asymmetric keying feature to make incorrect orientation physically impossible; tolerance stack analysis on the pin-and-hole fit; define a seating verification step with a pass/fail criterion |
| **Owner** | R. Harsh |

### DF-004 — Distribute perfusate uniformly across the scaffold vasculature through the hammock port array

| | |
|---|---|
| **Failure mode** | Non-uniform flow distribution between ports |
| **Effect** | Over-perfusion of some scaffold regions with wall shear exceeding the 1.5 Pa limit and extracellular matrix damage; under-perfusion of others causing ischaemia; loss of viable scaffold |
| **Severity (S)** | 7 |
| **Cause** | Port diameter and edge fillet vary within the manufacturing tolerance band, changing local flow resistance port to port; header not sized so that port restriction dominates distribution; hydraulic tolerances not derived from an allowable flow variation |
| **Occurrence (O)** | 5 |
| **Prevention control** | Port diameter and fillet radius toleranced from a defined allowable per-port flow variation; manifold header sized so port pressure drop dominates the distribution; CFD verification of distribution across the worst-case tolerance combination |
| **Detection control** | Dimensional inspection of port diameter and fillet on first article; bench flow-distribution test measuring per-port flow against an acceptance band |
| **Detection (D)** | 3 |
| **RPN** | **105** |
| **Action** | Derive port dimensional tolerances from an allowable per-port flow variation; run CFD or a bench flow test at the worst-case tolerance combination; define a per-port flow acceptance criterion |
| **Owner** | R. Harsh |

### DF-005 — Support the cradle and its load in a level, fixed position throughout the perfusion period

| | |
|---|---|
| **Failure mode** | Support bars deflect or creep under sustained load |
| **Effect** | Cradle tilts progressively during perfusion; scaffold orientation changes; tension develops on vascular connections; non-uniform perfusion and mechanical stress on the organ |
| **Severity (S)** | 7 |
| **Cause** | Bar section sized for strength but not for deflection; material creeps under sustained load at 4 °C over the full perfusion duration; span too long for the section |
| **Occurrence (O)** | 3 |
| **Prevention control** | Bars sized against a deflection limit, not only a strength limit; material selected for creep resistance at operating temperature over maximum perfusion duration; span reduced or section increased |
| **Detection control** | Deflection measurement under maximum load during design verification; visual check of cradle level during operation |
| **Detection (D)** | 4 |
| **RPN** | **84** |
| **Action** | No action required — residual risk acceptable against the stated threshold rule |
| **Owner** | R. Harsh |

### DF-006 — Deliver inlet perfusate into the scaffold through the cradle window without obstruction or maldistribution

| | |
|---|---|
| **Failure mode** | Chamber inlet port partially obstructed by, or offset from, the cradle window |
| **Effect** | Flow jets through the reduced opening; localised high velocity raises wall shear above the 1.5 Pa limit at the entry region; non-uniform perfusion across the scaffold; extracellular matrix damage locally and ischaemia elsewhere |
| **Severity (S)** | 7 |
| **Cause** | Tolerance stack between chamber inlet position and cradle window position permits partial overlap at worst case; cradle and inlet port not located from a common datum; window sized with insufficient margin over the port |
| **Occurrence (O)** | 4 |
| **Prevention control** | Cradle window sized to exceed the inlet port by more than the worst-case tolerance stack, so misalignment cannot reduce the flow area; cradle located from the same datum as the inlet port; tolerance stack analysis on port-to-window registration |
| **Detection control** | Dimensional check of port-to-window registration at assembly; inlet pressure drop measured against an expected range; CFD of the worst-case offset |
| **Detection (D)** | 4 |
| **RPN** | **112** |
| **Action** | Size the cradle window to exceed the inlet port diameter by more than the worst-case tolerance stack and confirm by tolerance analysis; run CFD at the maximum credible offset to confirm inlet velocity and wall shear remain within limits |
| **Owner** | R. Harsh |

### DF-007 — Collect and drain bile from the cannulated bile duct to the collection reservoir, without obstruction and without leakage into the perfusate

| | |
|---|---|
| **Failure mode** | Bile drainage path misaligned — cannula offset from the chamber port, causing kinking, obstruction or disconnection |
| **Effect** | Bile cannot drain, producing biliary back-pressure and cholestatic injury to the graft; or bile escapes into the perfusate, where bile salts are cytotoxic and damage the scaffold; and bile output, used as a viability indicator, is lost or misread, risking a wrong assessment of graft suitability |
| **Severity (S)** | 8 |
| **Cause** | Tolerance stack between bile port position and cradle/cannula position; no strain relief on the bile line, so cannula position is coupled to port position; port position not designed for the anatomical range of bile duct positions across donor organs |
| **Occurrence (O)** | 5 |
| **Prevention control** | Flexible, strain-relieved bile line decoupling cannula position from port position; port located and sized to accommodate the anatomical range of duct positions, specified as a design input; bile path physically separated and sealed from the perfusate path so a leak cannot reach the circuit |
| **Detection control** | Visual check of bile line routing at setup; bile output monitored during perfusion, with absence of expected output flagging obstruction; perfusate checked for bile salts |
| **Detection (D)** | 3 |
| **RPN** | **120** |
| **Action** | Decouple the cannula from the port with a flexible strain-relieved line; define the anatomical range of bile duct positions as a design input; physically separate bile and perfusate paths; define an expected bile output range and flag absence |
| **Owner** | R. Harsh |

### DF-008 — Return processed perfusate from the scaffold outflow to the circuit at the design flow rate, without developing back-pressure

| | |
|---|---|
| **Failure mode** | Outlet path restricted or obstructed |
| **Effect** | Outflow resistance rises; intravascular pressure within the scaffold exceeds design; vascular distension and extracellular matrix damage; oedema; net perfusion falls; in the limit, fluid accumulates in the chamber and overflows the enclosure |
| **Severity (S)** | 7 |
| **Cause** | Outlet port cross-section undersized for design flow; outlet positioned where the cradle or scaffold can occlude it; particulate or clot accumulation at the port over a long run; outlet line kinking at the port |
| **Occurrence (O)** | 4 |
| **Prevention control** | Outlet port sized with margin over design flow; outlet located where neither cradle nor scaffold can occlude it at worst-case position; strain relief at the port; sump geometry or screen keeping debris away from the port mouth |
| **Detection control** | Outlet or differential pressure monitored against an expected range; chamber fluid level monitored; inlet and outlet flow compared for imbalance |
| **Detection (D)** | 3 |
| **RPN** | **84** |
| **Action** | No action required — residual risk acceptable against the stated threshold rule |
| **Owner** | R. Harsh |

### DF-009 — Enclose the scaffold with sufficient clearance across the full range of donor organ sizes, at the specified bath volume

| | |
|---|---|
| **Failure mode** | Chamber internal envelope does not accommodate the intended range of scaffold sizes; scaffold contacts the chamber wall |
| **Effect** | Localised compression of the organ at the contact point; regional ischaemia and tissue damage; disturbed flow around the scaffold; at the extreme, the scaffold cannot be positioned correctly at all and the run cannot proceed |
| **Severity (S)** | 7 |
| **Cause** | Chamber internal dimensions derived from a single nominal organ geometry rather than the anatomical range; clearance envelope never defined as a design input; volume occupied by the cradle not subtracted when sizing |
| **Occurrence (O)** | 5 |
| **Prevention control** | Chamber internal envelope defined from the documented anatomical range of donor organ sizes plus a stated clearance margin, specified as a design input; cradle envelope subtracted from available volume during sizing |
| **Detection control** | Dimensional inspection of the chamber internal envelope against drawing; fit check using a maximum-size organ phantom |
| **Detection (D)** | 3 |
| **RPN** | **105** |
| **Action** | Define the chamber internal envelope from the anatomical range of donor organ sizes with a stated clearance margin, as a design input; verify by fit check with a maximum-size phantom |
| **Owner** | R. Harsh |

### DF-010 — Prime the fluid path without trapping air

| | |
|---|---|
| **Failure mode** | Air remains trapped in the manifold after priming |
| **Effect** | Gas carried downstream into the perfusion circuit; air embolism; ischaemic damage to the organ |
| **Severity (S)** | 9 |
| **Cause** | Flow path geometry contains high points or dead volumes not swept clear at the priming flow rate |
| **Occurrence (O)** | 5 |
| **Prevention control** | Vent port located at the highest point of the chamber in the operating orientation, allowing buoyant gas to escape; flow path shaped without high points or dead volumes where gas could be retained; priming performed with the vent open |
| **Detection control** | Visual confirmation of gas clearance through the chamber during priming; vent patency checked before each run |
| **Detection (D)** | 4 |
| **RPN** | **180** |
| **Action** | Priming study to confirm complete gas clearance through the vent at the specified priming flow rate and chamber orientation; define a priming procedure with a documented acceptance criterion; assess gas clearance under credible off-axis orientations |
| **Owner** | R. Harsh |
---

## 5. Link to the risk management file

Every failure effect constituting harm must appear in the risk management file (ELAP-RMF-001).

| DFMEA ID | Failure effect | Hazard | Carried across |
|---|---|---|---|
| DF-010 | Air embolism; ischaemic organ damage | HAZ-001 | Yes |
| DF-001 | Contamination of perfusate; infection risk | HAZ-003 | Yes |
| DF-002 | Contamination of perfusate; infection risk | HAZ-003 | Yes |
| DF-003 | Loss of perfusion; mechanical damage to organ | HAZ-004 | Yes |
| DF-004 | ECM damage and regional ischaemia | HAZ-004 | Yes |
| DF-005 | Non-uniform perfusion; mechanical stress on organ | HAZ-004 | Yes |
| DF-006 | ECM damage from elevated wall shear | HAZ-004 | Yes |
| DF-007 | Cholestatic injury; wrong viability assessment | HAZ-005 | Partial — see note |
| DF-008 | Vascular distension; oedema; loss of perfusion | HAZ-004 | Yes |
| DF-009 | Localised compression; regional ischaemia | HAZ-004 | Yes |

**Note on DF-007.** HAZ-005 (erroneous measurement) covers the loss of bile output as a viability indicator. It does not cover biliary back-pressure causing cholestatic injury, nor bile leakage into the perfusate where bile salts are cytotoxic. These effects are not represented by any existing hazard in ELAP-RMF-001. A new hazard, HAZ-006 — biliary obstruction and bile contamination of the perfusate — is required. **Identified by this DFMEA.**

**Note on HAZ-002.** HAZ-002 (thermal) has no corresponding DFMEA entry. Thermal performance is outside the scope of this analysis, as recorded in section 1.

---

## 6. Action threshold and rationale

A failure mode is actioned if **any** of the following is true:

1. S ≥ 8, regardless of RPN
2. RPN ≥ 100
3. S ≥ 7 **and** D ≥ 7, regardless of RPN

**Why not RPN alone.** S, O and D are ordinal scales, so their product is not mathematically meaningful — an RPN of 100 arising from 10 × 10 × 1 describes a different problem from 5 × 5 × 4. High-severity modes are therefore actioned on severity, consistent with ISO 14971, which directs that risk be evaluated on the basis of severity where the probability of occurrence of harm cannot be reliably estimated. That is the situation here, since no physical units have been built or tested. AIAG-VDA's replacement of RPN with Action Priority reflects the same criticism in an automotive context; it is cited as supporting rationale only and is not a medical device requirement.

Applying the rule: **eight of ten** failure modes are actioned. **DF-005 and DF-008** fall below all three thresholds and are recorded as acceptable with the reasoning stated, rather than actioned by default.

---

## 7. Observations

**Anatomical variability is an unstated design input.** Three failure modes — DF-007 (bile duct position), DF-009 (chamber envelope) and, indirectly, DF-003 — arise from the design being dimensioned around a single specimen geometry rather than the range of donor organs. This should be captured explicitly as a design input.

**Four controls use inherent safety by design** rather than inspection or warning: the asymmetric keying feature in DF-003, header sizing so distribution is insensitive to tolerance in DF-004, the oversized cradle window in DF-006, and in DF-010 a vent at the highest point of the chamber so entrapped gas escapes by buoyancy rather than requiring detection and intervention. Under the ISO 14971 control hierarchy these rank above protective measures and information for safety.

**The vent control carries an orientation dependency.** Because it relies on buoyancy, the DF-010 control is effective only in the intended operating orientation. Gas clearance under credible off-axis orientations is identified as an open verification item.

**Two recommended actions are executable now** against the existing CFD model: the worst-case tolerance study in DF-004 and the maximum-offset study in DF-006.

---

## 8. Limitations

- Single analyst. A design FMEA is normally cross-functional, across design, manufacturing, quality and clinical input.
- No physical units built or tested; all occurrence ratings are engineering judgement.
- Selected principal functions only; not exhaustive.
- Process failure modes, software behaviour and use-related errors are out of scope and are not analysed elsewhere for this project at present.

---

## Revision history

| Rev | Description |
|---|---|
| 1.0 | Initial issue |
| 1.1 | DF-010 prevention and detection controls corrected to reflect the vent-based design actually implemented, replacing a bubble-detector control carried over in error from a template. Section 7 updated accordingly, and the orientation dependency of the vent control recorded. |
