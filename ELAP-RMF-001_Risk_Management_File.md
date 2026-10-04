# ELAP-RMF-001 — Risk Management File

**External Liver Assistance Platform**

| Field | Entry |
|---|---|
| Document number | ELAP-RMF-001 |
| Revision | 1.2 |
| Effective date | 04 October 2026 |
| Prepared by | Raj Harsh |
| Governing plan | ELAP-RMP-001 Rev 1.3 |
| Standard | ISO 14971:2019, Clauses 5, 6, 7 |
| Phase covered | **Decellularization at 4 °C only.** See section 1.4. |

*Self-directed exercise on an independent design project. Not industry work. Not a controlled document under any quality management system.*

---

## 1. Intended use and scope

### 1.1 Intended use (clause 5.2)

The External Liver Assistance Platform is a perfusion system for the **ex vivo decellularization and subsequent recellularization of a whole human liver**. Perfusate is driven into the organ's vasculature through cannulated vessels, passes through the organ, drains into the chamber as a bath and returns to the circuit. Bile ducts are cannulated to a separate drainage path.

The device is a **processing platform, not a therapy**. It never contacts a patient. Harm reaches a patient only through the product it produces — a bioengineered scaffold intended for implantation.

**Three operating phases, at two temperatures.** This matters because the harm from a given failure is different in each.

| Phase | Temperature | Perfusate | What is in the chamber |
|---|---|---|---|
| **1. Decellularization, detergent** | **4 °C** | Chelating and detergent solutions — EDTA, sodium deoxycholate, Triton X-100, protease inhibitor | A liver losing its cells. No living tissue by the end. |
| **2. Decellularization, enzymatic and wash** | **37 °C**, then ambient | DNase, then distilled water | An acellular extracellular matrix scaffold |
| **3. Recellularization** | **37 °C**, 5 % CO₂ | Cell culture medium | A scaffold being seeded with living cells, cultured for days |

Cold perfusion at 4 °C for phase 1 follows the approach in Napierala et al., *Scientific Reports* (2017), which uses 4 °C throughout the detergent stages with a protease inhibitor, to limit endogenous protease activity degrading the matrix. Phase 3 necessarily runs at 37 °C because cells cannot be cultured cold.

### 1.2 Reasonably foreseeable misuse (clause 5.2)

Misuse is not failure. In each of these the device works correctly and harm still follows.

| # | Foreseeable misuse | Why it is foreseeable | Harm |
|---|---|---|---|
| M-1 | Cleaning and reusing a chassis intended for single use | Chassis cost, and the chamber looks cleanable | Residual detergent, residual DNA and cellular material from a previous donor; cross-contamination between donors |
| M-2 | Running the detergent phase beyond its specified duration, to be sure cells are gone | More appears safer | Over-decellularization; ECM protein loss and loss of mechanical integrity of the scaffold |
| M-3 | Substituting a different detergent or concentration | Local availability, or an operator's familiarity with another protocol | Too aggressive destroys the ECM; too mild leaves immunogenic cellular remnants in a scaffold intended for implantation |
| M-4 | Shortening or omitting the post-detergent wash | Wash stages are long and appear inactive | Residual detergent retained in the scaffold, cytotoxic to the cells seeded in phase 3 and to any recipient |
| M-5 | Connecting the arterial line to the portal vein, or vice versa | Two similar lines, two similar cannulae, and the ports may not be keyed | Perfusion at a pressure the vessel is not designed for; vascular rupture or ECM damage |
| M-6 | Running with the lid unsealed or opened mid-run | To reposition the organ, inspect it, or save setup time | Loss of the sterile barrier during a run lasting days — see HAZ-003 |
| M-7 | Restarting perfusion after an interruption without re-priming | The circuit appears still full | Gas drawn into the inlet line — see HAZ-001 |
| M-8 | Processing an organ outside the size range the chamber was dimensioned for | A donor organ is available and discarding it is costly | Organ contacts the chamber wall; compression and flow disturbance — see HAZ-004 |
| M-9 | Reading absence of bile output during phase 1 or 2 as organ failure | Bile output is treated as a viability indicator elsewhere in liver perfusion | A sound scaffold discarded. **Absence of bile output in phases 1 and 2 is expected** — there are no hepatocytes to produce it |

**None of M-1 to M-9 has a risk control, and none is planned.** Use-related risk requires IEC 62366-1 usability engineering, which is outside the scope of this file and of ELAP-DFMEA-001. Design changes to address these cases are not being made at this stage of the project.

**The consequence is stated rather than softened.** M-5, connecting the arterial line to the portal vein, and M-1, reusing a single-use chassis, both reach harms assessed at S4 or S5 elsewhere in this file. ELAP-RMP-001 section 4.3 holds that risk at those severities is not acceptable without a control. **Declining to control them does not make them acceptable** — it means this file cannot conclude that use-related risk is acceptable, and does not attempt to. Two of the nine are controllable by inherently safe design without new mechanisms, by keying the vascular ports asymmetrically and by not presenting bile output as a viability indicator in phases where no bile can exist; both are recorded here as available and not taken.

### 1.3 Characteristics related to safety (clause 5.3)

| Characteristic | Present | Consequence |
|---|---|---|
| Contacts human tissue intended for implantation | Yes | Anything the device leaves behind reaches a patient |
| Delivers a cytotoxic chemical to that tissue | Yes — detergents in phase 1 | Residue is itself a hazard; the wash phases are a risk control, not a formality |
| Requires a sterile fluid path | Yes, over a run of days | HAZ-003. Phase 3 is an incubator at 37 °C — contamination multiplies rather than merely persisting |
| Operates across a temperature range | Yes, 4 °C to 37 °C | Thermal control is a range requirement, not a setpoint |
| Pressure-driven fluid circuit with cannulated connections | Yes | HAZ-001, HAZ-008 |
| Single-use, supplied sterile | **Assumed, not specified** | M-1 is uncontrolled while this is an assumption rather than a requirement |
| Produces an output used in a decision about the product | Yes | HAZ-005 |
| Delivers energy to a patient | No | The device never contacts a patient |
| Software or programmable control | Yes — pump control, interlock, monitoring | IEC 62304 applies. Not analysed in this file. |

### 1.4 Scope of this revision

**This revision analyses phase 1 only — decellularization at 4 °C.**

Phase 2 at 37 °C and phase 3 at 37 °C with cell culture are **not analysed**. The hazards below must not be read as covering them. Several would change materially:

- **HAZ-003** worsens in phase 3. A seven-day culture at 37 °C is a growth environment, so a barrier breach multiplies rather than persists.
- **HAZ-007** inverts. At 4 °C the harm from a temperature excursion is protease activity degrading the matrix. At 37 °C in phase 3 the harm from an excursion is cell death.
- **HAZ-005** has no meaning in phases 1 and 2 and may become meaningful late in phase 3.
- Detergent residue, cell seeding uniformity, CO₂ control and medium sterility are phase 2 and 3 hazards with no entry here at all.

Scoping to one phase is a deliberate limitation, recorded so that the file is not read as more complete than it is.

---

## 2. Method

### 2.1 Basis

**Severity** uses the five-level scale in ELAP-RMP-001 section 4.1. **Probability is not estimated** — no unit has been built, there is no test data and no predecessor device, so risk is evaluated on severity alone per clause 4.4 d). **Acceptability** follows RMP-001 section 4.3, including the amendment that a tier 1 or tier 2 control must be used where practicable irrespective of severity.

**Identifiers** follow ELAP-RMP-001 section 8.1. `HAZ-` and `RC-` are defined here and nowhere else; `RC-` is assigned sequentially in order of definition.

### 2.2 Hazard register

| ID | Hazard | Severity | Source |
|---|---|---|---|
| HAZ-001 | Gas present in the perfusion inlet circuit | S4 | ELAP-DFMEA-001 DF-010 |
| HAZ-002 | Cold external surfaces at the operating temperature | S2 | **This file** — no DFMEA entry |
| HAZ-003 | Loss of the sterile barrier at the enclosure boundary | S5 | ELAP-DFMEA-001 DF-001, DF-002 |
| HAZ-004 | Mechanical loading of the organ and its vascular connections | S4 | ELAP-DFMEA-001 DF-003, DF-005, DF-009 |
| HAZ-005 | Viability measurement that does not reflect the organ's state | S5 | ELAP-DFMEA-001 DF-007, partial. **Out of scope for phase 1** — no hepatocytes, no bile. |
| HAZ-006 | Fluid outside the intended biliary drainage path | S5 | ELAP-DFMEA-001 DF-007 — **identified by the DFMEA's traceability check** |
| HAZ-007 | Loss of thermal control of the perfusate at 4 °C | S4 | **This file** — thermal out of DFMEA scope |
| HAZ-008 | Non-physiological perfusion pressure or flow distribution | S4 | ELAP-DFMEA-001 DF-004, DF-006, DF-008, DF-011 |
| HAZ-009 | Perfusate cooled below the process temperature toward freezing | S4 | **This file** — introduced by RC-023, per clause 7.5 |

**Four of nine hazards were not found by the design FMEA.** HAZ-002 and HAZ-007 fall outside its scope — a design FMEA starts from component functions, and neither an operator's hands nor ambient heat ingress is a component. HAZ-006 was found by tracing DFMEA effects against the risk file and discovering that no hazard covered them. HAZ-009 was introduced by a risk control measure rather than existing in the design at all, which is the case clause 7.5 exists to catch. That asymmetry is the argument for running both analyses rather than either alone.

### 2.3 Why HAZ-004 and HAZ-008 are separate

ELAP-DFMEA-001 section 5 mapped seven failure modes to a single hazard. On review that hazard was doing too much work: a hazard is a potential **source** of harm, and these are two sources.

| | Source | DFMEA items |
|---|---|---|
| **HAZ-004** | Mechanical — the organ or its connections are loaded, displaced or compressed | DF-003 cradle seating · DF-005 support deflection · DF-009 chamber envelope |
| **HAZ-008** | Hydraulic — pressure or flow in the perfusate is outside the physiological range | DF-004 maldistribution · DF-006 inlet jetting · DF-008 outlet restriction · DF-011 vent occlusion |

Both end in damage to the organ. They need different controls, which is the practical test for whether a split is real.

---

## 3. HAZ-001 — Gas present in the perfusion inlet circuit

| Field | Entry |
|---|---|
| **Hazard** | Gas present in the perfusion inlet circuit |
| **Foreseeable sequence of events** | Gas is retained in the inlet circuit after priming, or is drawn in at a connector or loose fitting during operation, or evolves out of the perfusate on warming or a pressure change → it is carried along the inlet line by pump-driven flow → it reaches the portal vein or hepatic artery cannula → it passes the cannula into the organ vasculature |
| **Hazardous situation** | Gas is present in the organ's vascular bed while perfusion is running — the organ is exposed to the gas |
| **Harm** | Gas occludes vascular channels of the scaffold; detergent cannot reach the occluded region, leaving cellular material and DNA behind in a scaffold intended for implantation; gas expansion and interfacial stress damage the extracellular matrix. **Note the phase.** In phase 1 there is no living tissue to infarct, so the harm is incomplete decellularization and matrix damage, not ischaemia. In phase 3 the same hazard would kill seeded cells; that phase is out of scope. |
| **Severity** | **S4 — Critical.** Loss of the scaffold, and if an incompletely decellularized scaffold is implanted, an immune response in the recipient. Maps to 8–9 on the ten-point scale in ELAP-DFMEA-001, which scored DF-010 at 9. |
| **P1 / P2** | Not estimated — RMP-001 section 4.2 |
| **Initial risk evaluation** | Not acceptable without risk control, per RMP-001 section 4.3 for S4 |
| **Risk control** | **RC-001** — gas detection on each perfusion inlet line, with an interlock that halts the pump on detection |
| **Tier, and why not higher** | **Tier 2, protective measure.** Tier 1 is not available: gas cannot be excluded from a fluid circuit by geometry alone, since it enters through priming, connectors and dissolution out of the perfusate. A passive bubble trap was considered as a closer-to-tier-1 option and **rejected** — see the option analysis below. |
| **Rejected control option** | **Passive bubble trap upstream of the cannula.** A trap removes gas rather than reacting to it, which would rank above detection in the hierarchy. Rejected on three grounds. **(a)** A trap is an additional interface in the fluid path, degrading the sterile barrier of HAZ-003 — the dominant control interaction in this file. **(b)** A trap is a deliberate gas reservoir held in the circuit; a flow or pressure transient can release an accumulated volume downstream, converting a slow accumulation into a single bolus. **(c)** A trap requires its own priming and purge procedure, adding a use step and therefore a use-related failure mode, in a device whose use-related risk is already uncontrolled. Detection with a pump interlock arrests flow before the bolus reaches the cannula, which is the harm pathway. Gas remaining upstream is then cleared before flow resumes. **This is a judgement, not a demonstration** — see residual risk. |
| **Requirements** | REQ-014a, REQ-014b, REQ-014c, REQ-014e (ELAP-DIS-001 Rev 1.4) |
| **Verification — implementation** | ELAP-VP-001 Rev 3.3, steps 1, 2, 2a; AC-3 |
| **Verification — effectiveness** | ELAP-VP-001 Rev 3.3, steps 6–11; AC-1, AC-2, AC-5 |
| **New risks introduced (clause 7.5)** | **(a)** False trigger halting perfusion unnecessarily — controlled by REQ-014e, verified by AC-5. **(b)** The sensor housing adds a fluid-path interface, a potential leak and contamination site — carried to HAZ-003. |
| **Severity after control** | **S4 — unchanged.** A detector does not reduce the harm an embolism causes; it reduces how often one occurs. |
| **Residual risk** | **Not acceptable, for two separate reasons.** First, ELAP-VP-001 is written and not executed, so the control is verified neither as implemented nor as effective. Second, RMP-001 section 4.3 requires S4 risk reduced as far as possible. Detection arrests flow; it does not remove gas. The rejection of the bubble trap above rests on a reasoned trade against HAZ-003 and against use-related risk, **but that trade has not been quantified** — no analysis compares the interface risk a trap adds against the gas-removal benefit it provides. Reduction as far as possible is therefore argued, not demonstrated, and the residual risk cannot be declared acceptable on this basis. |
| **Traceability** | DF-010 · REQ-014a/b/c/e · ELAP-VP-001 AC-1/2/3/5 · ELAP-TRM-001 section 3 |

---

## 4. HAZ-002 — Cold external surfaces at the operating temperature

| Field | Entry |
|---|---|
| **Hazard** | Cold external surfaces of the chamber at the 4 °C operating temperature |
| **Foreseeable sequence of events** | Perfusion is started → the chamber is filled with perfusate at 4 °C → the chamber wall temperature falls toward the perfusate temperature by conduction → the operator handles the chamber to reposition it or change its contents → contact is made bare-handed |
| **Hazardous situation** | An operator's unprotected skin is in contact with the cold external surface of the chamber |
| **Harm** | Localised cold injury to the skin: pain and transient numbness, resolving without intervention |
| **Severity** | **S2 — Minor.** Assumes sustained bare-skin contact of the order of a minute against a high-conductivity exterior. ELAP-DFMEA-001 models the solids as steel and records that the material is **not yet selected**; with a low-conductivity exterior this falls to S1. The severity depends on an open design decision. |
| **P1 / P2** | Not estimated — RMP-001 section 4.2 |
| **Initial risk evaluation** | S2 is acceptable with risk control. Note that acceptability does not authorise a low control tier — RMP-001 section 4.3 as amended. |
| **Risk control** | **RC-002** — thermal isolation of operator-contact surfaces, by one of: an insulating layer or sleeve; grip points in a low-conductivity material held near ambient; or a low-conductivity exterior material in place of steel. Selection open; all three are tier 1. |
| **Tier, and why not higher** | **Tier 1, inherently safe design.** An earlier draft proposed protective gloves, justified on design complexity. Rejected on review: gloves worn on instruction are **tier 3**, not tier 2, and tier 1 is practicable here since the exterior material is unselected. Clause 7.1 permits moving down only where the higher tier is not practicable, and complexity is not such a ground. Gloves may supplement but are not the control. |
| **Requirements** | **None yet.** Will generate a limit on maximum operator-contact surface temperature at thermal steady state, and a specification of the exterior material or insulation achieving it. |
| **Verification — implementation** | Inspection that the specified insulation, sleeve or grip material is present as drawn at every intended contact point |
| **Verification — effectiveness** | Surface temperature measured at each intended contact point at thermal steady state, chamber filled at 4 °C, at the lowest specified ambient, against the requirement limit |
| **New risks introduced (clause 7.5)** | **(a)** An insulating layer adds an external surface to clean and a crevice where contamination can lodge — carried to HAZ-003. **(b)** If gloves are added, reduced tactile feedback and grip raise the risk of dropping the chamber or mishandling a connection — carried to HAZ-004. |
| **Severity after control** | **S2 — unchanged** |
| **Residual risk** | **Not acceptable.** No control selected, specified or verified; the exterior material is undecided and no requirement exists. |
| **Traceability** | No DFMEA entry. **Identified by this file.** |

---

## 5. HAZ-003 — Loss of the sterile barrier at the enclosure boundary

| Field | Entry |
|---|---|
| **Hazard** | Non-sterile ambient air, airborne microorganisms and particulate at the enclosure boundary |
| **Foreseeable sequence of events** | The enclosure boundary has several interfaces: the lid O-ring gland, the vent filter, the port fittings, the RC-001 sensor housing and the RC-002 insulation surface → one interface fails to maintain the barrier, through insufficient O-ring compression across the tolerance range, a filter not rated for bacterial retention, a filter wetted by condensation, a filter that detaches, or a leaking fitting → ambient air and airborne microorganisms enter the chamber → organisms reach the perfusate in the chamber bath → the perfusate is recirculated through the organ vasculature → organisms are distributed throughout the organ |
| **Hazardous situation** | The organ's vasculature and tissue are exposed to contaminated perfusate while perfusion is running |
| **Harm** | Microbial colonisation and infection of the graft; loss of the graft. If the graft is transplanted, infection is transmitted to the recipient, who is immunosuppressed — sepsis, graft loss requiring re-transplantation, or death |
| **Severity** | **S5 — Catastrophic.** Harm is scoped to the recipient, per the basis note below. Transmitted infection in an immunosuppressed transplant recipient is credibly fatal. ELAP-DFMEA-001 DF-001 and DF-002 record the effect as "infection risk to the organ and recipient", consistent with this scoping. |
| **P1 / P2** | Not estimated — RMP-001 section 4.2 |
| **Initial risk evaluation** | Not acceptable without risk control, per RMP-001 section 4.3 for S5. Information for safety is never sufficient at this severity. |
| **Risk control** | **RC-003** — lid O-ring gland dimensioned per the O-ring supplier's compression guidance, with minimum squeeze guaranteed across the worst-case tolerance stack. **RC-004** — 0.2 µm hydrophobic sterilising-grade vent filter, with pore size, hydrophobicity, bacterial retention rating and fixing method specified on the drawing. **RC-005** — 100 % post-assembly pressure decay leak test on every unit, against a documented acceptance criterion. **RC-006** — per-lot incoming inspection of filter specification against the drawing. |
| **Tier, and why not higher** | **RC-003 and RC-004 are tier 1** — the barrier is a property of the design, present in every unit by selection and dimensioning. **RC-005 and RC-006 are tier 2**, protective measures in the manufacturing process: a barrier that depends on correct assembly and on correct incoming material needs a per-unit and per-lot check, because tier 1 guarantees the design and not the build. No tier 3 control is relied on, as RMP-001 section 4.3 forbids it at this severity. |
| **Requirements** | **None yet.** Will generate: minimum O-ring squeeze across the tolerance stack; filter pore size, retention rating, hydrophobicity and fixing method; leak test limit and method; incoming inspection criteria. Sterility assurance level and the single-use, supplied-sterile assumption also need to become stated requirements — ELAP-DFMEA-001 records them as assumed but not formally specified. |
| **Verification — implementation** | Dimensional inspection of the gland against drawing; incoming inspection record for the filter; confirmation that the leak test is in the assembly route sheet |
| **Verification — effectiveness** | Tolerance stack analysis confirming minimum compression at worst case; bacterial challenge test on the filter as fitted, not as supplied; leak test method validated against a seeded leak of known rate |
| **New risks introduced (clause 7.5)** | **(a)** The pressure decay test needs a test port or sealing fixture, which is itself another interface. **(b)** A leak test at assembly does not detect degradation during a long perfusion run — the barrier is verified once and then relied on for hours. **(c)** Neither is analysed; both are open. |
| **Severity after control** | **S5 — unchanged.** A better seal does not make transmitted sepsis less severe. |
| **Residual risk** | **Not acceptable.** No requirement exists, no protocol is written, sterilisation method and sterility assurance level are unspecified, and the single-use assumption is not a stated requirement. The time-dependent barrier degradation noted above is also uncontrolled. |
| **Traceability** | DF-001, DF-002 · carries the RC-001 sensor housing interface and the RC-002 insulation surface |

> **Basis for scoping harm to the recipient.** The device is ex vivo and never contacts a patient, so the question is whether harm transmitted through the product it produces falls inside the analysis. It does. The scaffold is intended for implantation, and a contaminated or incompletely decellularized scaffold carries its defect into a recipient who is immunosuppressed. Severity is therefore assessed on the worst credible outcome in the recipient, not on loss of the scaffold alone. This applies to HAZ-003, HAZ-005 and HAZ-006. ELAP-DFMEA-001 DF-001 and DF-002 already record the effect as reaching the recipient, so the two documents are consistent.

---

## 6. HAZ-004 — Mechanical loading of the organ and its vascular connections

| Field | Entry |
|---|---|
| **Hazard** | Mechanical force transmitted to the organ or to its cannulated vascular connections |
| **Foreseeable sequence of events** | The cradle seats in an incorrect or unrepeatable position because the locating pattern is symmetric and pin-to-hole clearance permits more than one seated position, **or** the support bars deflect or creep under sustained load so the cradle tilts progressively through the run, **or** the chamber internal envelope is too small for the donor organ because it was dimensioned from a single specimen rather than the anatomical range → the organ shifts, tilts or contacts the chamber wall → tension, kinking or compression is applied to the organ or to a cannula → a vascular connection is occluded or detaches, or the organ is locally compressed |
| **Hazardous situation** | The organ is mechanically loaded, displaced or compressed while perfused, or a vascular connection is under tension |
| **Harm** | Localised compression injury and regional ischaemia; loss of perfusion to part or all of the organ on occlusion or detachment; mechanical tissue damage; loss of the graft |
| **Severity** | **S4 — Critical.** Loss of the graft. Consistent with ELAP-DFMEA-001, which scores DF-003, DF-005 and DF-009 at 7, mapping to S3. **Raised to S4 here**, because the DFMEA scored each failure mode's own effect while the hazard carries the worst credible outcome — complete occlusion or detachment of a vascular connection loses the graft, not merely degrades it. |
| **P1 / P2** | Not estimated — RMP-001 section 4.2 |
| **Initial risk evaluation** | Not acceptable without risk control, per RMP-001 section 4.3 for S4 |
| **Risk control** | **RC-007** — asymmetric cradle locating pattern, so an incorrect orientation is physically impossible. **RC-008** — pin-and-slot location: one close-fit round hole to locate, one slotted hole to absorb tolerance without over-constraining. **RC-009** — support bars sized against a deflection limit rather than a strength limit, in a material selected for creep resistance at operating temperature over the maximum perfusion duration. **RC-010** — chamber internal envelope defined from the documented anatomical range of donor organ sizes plus a stated clearance margin, with the cradle envelope subtracted. |
| **Tier, and why not higher** | **All four are tier 1, inherently safe design.** RC-007 makes a wrong orientation impossible rather than detectable. RC-008 removes the ambiguity in seating rather than instructing the operator to check it. RC-009 and RC-010 are dimensioning decisions. No tier 2 or 3 control is required, which is the strongest position available — these are the clearest tier 1 controls in the file. |
| **Requirements** | **None yet.** Will generate: the asymmetric pattern on the drawing; pin-to-hole fit tolerances; a cradle deflection limit under maximum load over maximum duration; the anatomical range of donor organ sizes and the clearance margin, which is currently an open input in ELAP-DFMEA-001 section 8. |
| **Verification — implementation** | Dimensional inspection of the locating pattern and pin-to-hole fit; confirmation of bar section and material against drawing |
| **Verification — effectiveness** | Demonstration that the cradle physically cannot seat in a wrong orientation; tolerance stack analysis on the pin-and-slot fit; deflection measurement under maximum load held for the maximum perfusion duration; fit check with a maximum-size organ phantom |
| **New risks introduced (clause 7.5)** | **(a)** A close-fit locating pin raises the force needed to seat and unseat the cradle, which could itself jar the organ during setup. **(b)** An asymmetric pattern that is not visually obvious may still be force-fitted. Neither is analysed. |
| **Severity after control** | **S4 — unchanged** |
| **Residual risk** | **Not acceptable.** No control is specified as a requirement, the anatomical range is an open input, and nothing is verified. The anatomical range is the blocking item: RC-010 cannot be dimensioned without it. |
| **Traceability** | DF-003, DF-005, DF-009 · carries the glove-related grip risk from RC-002 |

---

## 7. HAZ-005 — Viability measurement that does not reflect the organ's state

> **OUT OF SCOPE FOR THIS REVISION.** Bile output indicates hepatocyte function. **In phase 1 there are no hepatocytes**, so no bile is produced and the indicator has no meaning — this hazard cannot arise during decellularization. It is retained unchanged below because it becomes live late in phase 3, and because misuse case **M-9** — reading the expected absence of bile as organ failure — is a real phase 1 risk arising from the same confusion. The record below describes phase 3 and is not part of this revision's analysis.

| Field | Entry |
|---|---|
| **Hazard** | A displayed viability indicator that may not correspond to the organ's actual condition |
| **Foreseeable sequence of events** | Bile output is used as an indicator of hepatocyte function → the bile drainage path is obstructed, kinked or disconnected, or bile leaks out of the path before reaching the collection reservoir → measured bile output is lower than the organ is actually producing, or is absent → a clinician reads the output and forms a judgement on graft suitability → the judgement is made on a measurement that does not reflect the organ |
| **Hazardous situation** | A clinical decision on whether to transplant is taken on the basis of a measurement that misrepresents the organ's condition |
| **Harm** | **Two directions, both harmful.** False negative: a viable graft is judged non-viable and discarded, and the intended recipient does not receive a transplant they needed. False positive: a non-viable graft is judged acceptable and transplanted, causing primary graft non-function, re-transplantation, or death. |
| **Severity** | **S5 — Catastrophic.** The false-positive direction transplants a failed graft into a patient. The false-negative direction denies a transplant to a patient who needed one. Both are credibly fatal outcomes, which is why this is the highest-severity hazard in the file alongside HAZ-003. |
| **P1 / P2** | Not estimated — RMP-001 section 4.2 |
| **Initial risk evaluation** | Not acceptable without risk control, per RMP-001 section 4.3 for S5 |
| **Risk control** | **RC-019** — an expected bile output range defined as a design input, with absence or out-of-range output flagged to the operator rather than displayed as a bare number. **RC-020** — the perfusate monitored for bile salts, so leakage out of the bile path is detected rather than silently reducing the measured output. **RC-021** — instructions for use stating that bile output must not be the sole criterion for a transplant decision, and naming the corroborating indicators required. |
| **Tier, and why not higher** | **RC-019 and RC-020 are tier 2**, protective measures in the device. **RC-021 is tier 3**, information for safety, and is a supplement only — RMP-001 section 4.3 forbids relying on information for safety at S5. Tier 1 is partially available and is handled under HAZ-006: physically separating the bile path (RC-017) removes the leakage route that corrupts the measurement in the first place. That is the stronger control and it is counted there, not here, to avoid double-counting. |
| **Requirements** | **None yet.** Will generate: the expected bile output range and flagging behaviour; a bile salt detection method and threshold in the perfusate; the corroborating viability indicators named in the IFU. |
| **Verification — implementation** | Inspection that the flagging behaviour is present; confirmation that the IFU statement is in the released document |
| **Verification — effectiveness** | Demonstration that a simulated absence of bile output raises the flag within a defined time; bile salt detection challenged with a known concentration in the perfusate |
| **New risks introduced (clause 7.5)** | **(a)** A flag on low bile output could cause a **viable** graft to be rejected on a false alarm — the control introduces the false-negative harm it is partly intended to prevent. This needs a defined false-alarm rate and is unanalysed. **(b)** Naming corroborating indicators in the IFU creates a dependency on indicators the device may not measure. |
| **Severity after control** | **S5 — unchanged** |
| **Residual risk** | **Not acceptable.** No requirement exists, nothing is verified, and the false-alarm behaviour of RC-019 is itself an uncontrolled route to the false-negative harm. |
| **Traceability** | DF-007, partial · depends on RC-017 under HAZ-006 |

> **This hazard runs through a human decision.** The harm is not caused by the device acting on the organ; it is caused by a person acting on what the device displayed. That places it in the territory of **IEC 62366-1 usability engineering**, which ELAP-DFMEA-001 section 1 records as out of scope and not analysed elsewhere. The risk controls above address measurement integrity. They do not address how the information is presented, which is the other half of the problem and remains unanalysed.

---

## 8. HAZ-006 — Bile outside its intended drainage path

| Field | Entry |
|---|---|
| **Hazard** | Fluid outside its intended drainage path in the biliary conduit. **In phase 1 this is perfusate and detergent, not bile** — the biliary tree is extracellular matrix and survives decellularization as a conduit, but nothing produces bile. Bile proper becomes the fluid of concern only in phase 3. |
| **Foreseeable sequence of events** | **Sequence A — retention.** Tolerance stack between the bile port position and the cradle or cannula position misaligns the drainage path, or there is no strain relief so cannula position is coupled to port position, or the port position does not accommodate the anatomical range of bile duct positions across donor organs → the bile line kinks, is obstructed, or disconnects → bile cannot leave the biliary tree → biliary back-pressure rises.<br>**Sequence B — escape.** The same misalignment, or a failure of the seal between the bile path and the perfusate path → bile escapes the drainage path into the chamber bath → bile enters the recirculating perfusate. |
| **Hazardous situation** | **A.** The biliary tree is exposed to raised back-pressure while the organ is perfused. **B.** The organ's vasculature and tissue are exposed to bile salts in the recirculating perfusate. |
| **Harm** | **Phase 1, A — retention.** Detergent-bearing perfusate retained in an obstructed biliary conduit is not cleared by the wash phases; residual detergent remains in a scaffold intended for implantation, cytotoxic to the cells seeded in phase 3 and to a recipient. Local over-pressure may also damage the biliary ECM. **Phase 1, B — escape.** Perfusate crossing into the chamber bath disturbs the residue budget, though the fluid is the detergent already in circulation so the contamination harm is lower than in phase 3. **Phase 3, out of scope.** Bile retention causes cholestatic injury; bile salts are cytotoxic to seeded hepatocytes. |
| **Severity** | **S5 — Catastrophic.** The recipient is in scope, confirmed. Retained detergent in an implanted scaffold is cytotoxic to the recipient and to any seeded cells, by a retention route the wash phases are not designed to clear. ELAP-DFMEA-001 scores DF-007 at 8, mapping to S4, but that score was assigned for bile, not for retained detergent reaching a patient. **Raised in Rev 1.1.** |
| **P1 / P2** | Not estimated — RMP-001 section 4.2 |
| **Initial risk evaluation** | Not acceptable without risk control, per RMP-001 section 4.3 for S4 |
| **Risk control** | **RC-016** — a flexible, strain-relieved bile line, decoupling cannula position from port position so that tolerance in one does not load the other. **RC-017** — the bile path physically separated from and sealed against the perfusate path, so that a bile leak cannot reach the circuit. **RC-018** — the bile port located and sized for the documented anatomical range of bile duct positions, specified as a design input. |
| **Tier, and why not higher** | **All three are tier 1, inherently safe design.** RC-017 is the important one: it makes sequence B impossible by construction rather than detectable after the fact, which is why the bile-salt monitoring under HAZ-005 is a backstop rather than the primary control. |
| **Requirements** | **None yet.** Will generate: bile line flexibility and strain relief specification; the separation and sealing requirement between bile and perfusate paths; the anatomical range of bile duct positions, currently an open input in ELAP-DFMEA-001 section 8. |
| **Verification — implementation** | Inspection that strain relief is fitted and that the bile and perfusate paths are separated as drawn |
| **Verification — effectiveness** | Demonstration that cannula displacement across the anatomical range does not load or kink the line; pressurised leak test across the bile-to-perfusate seal with a tracer, confirming no transfer |
| **New risks introduced (clause 7.5)** | **(a)** A flexible line can be routed incorrectly by the operator, kinking it in a way a rigid line could not — this reintroduces sequence A by a different route and is a tier 3 instruction problem. **(b)** Separating the two paths adds a seal, which adds an interface to HAZ-003. Neither is analysed. |
| **Severity after control** | **S4 — unchanged** |
| **Residual risk** | **Not acceptable.** No requirement exists, the anatomical range of duct positions is an open input, and nothing is verified. |
| **Traceability** | DF-007 · **this hazard was identified by the traceability check in ELAP-DFMEA-001 section 5**, which found that HAZ-005 covered only the measurement loss and not the cholestatic injury or the bile contamination · supports RC-019 and RC-020 under HAZ-005 |

> **One hazard, two sequences — and why not two hazards.** Obstruction and leakage produce different harms by different routes, which is an argument for splitting. They are kept as one hazard because a hazard is defined by its **source**, and the source in both cases is the same: bile outside the path intended for it. The two sequences are recorded separately so that neither is lost, and RC-017 addresses only sequence B while RC-016 and RC-018 address both. If a later revision finds that the two need different acceptability judgements, the split should be made then.

---

## 9. HAZ-007 — Loss of thermal control of the perfusate

| Field | Entry |
|---|---|
| **Hazard** | Heat ingress into the perfusate circuit from the ambient environment, raising the organ above the 4 °C process temperature of phase 1 |
| **Foreseeable sequence of events** | The device operates with the perfusate at 4 °C while the ambient is at room temperature → heat conducts and convects inward through chamber walls, lid, port fittings and external tubing → the perfusate temperature rises above 4 °C → **endogenous protease activity increases with temperature** → proteases released as cells lyse under detergent exposure digest the extracellular matrix they are released into |
| **Hazardous situation** | The organ is held above the 4 °C process temperature while detergent perfusion is lysing its cells |
| **Harm** | Enzymatic degradation of the extracellular matrix: loss of collagen and laminin structure, loss of mechanical integrity, loss of the vascular basement membrane that phase 3 reseeding depends on. The scaffold is structurally compromised and cannot support recellularization. **This is not ischaemic injury** — by the point of detergent exposure there is no viable tissue to starve. The source protocol runs cold and adds a protease inhibitor for precisely this reason. |
| **Severity** | **S4 — Critical.** Loss of the graft. |
| **P1 / P2** | Not estimated — RMP-001 section 4.2 |
| **Initial risk evaluation** | Not acceptable without risk control, per RMP-001 section 4.3 for S4 |
| **Risk control** | **RC-022** — insulation of the chamber and circuit, with thermal mass sized to limit the rate of temperature rise on loss of active cooling. **RC-023** — active cooling under closed-loop control of perfusate temperature. **RC-024** — perfusate temperature monitored with high and low alarm limits. |
| **Tier, and why not higher** | **RC-022 is tier 1**, inherently safe design — passive, and it works when nothing else does. It is **not sufficient alone**: insulation slows heat ingress but cannot hold a temperature indefinitely against a thermal gradient over a perfusion lasting hours, so tier 1 cannot close this risk and tier 2 is required rather than merely preferred. **RC-023 and RC-024 are tier 2**, protective measures in the device. This is the one hazard in the file where the justification for moving down the hierarchy is a physical limit rather than a practicability judgement. |
| **Requirements** | **None yet.** Will generate: the perfusate temperature setpoint and tolerance band; the maximum rate of temperature rise on cooling failure; alarm limits and response time; insulation performance expressed as a maximum heat ingress rate at a stated ambient. |
| **Verification — implementation** | Inspection that insulation, cooling and sensing are present as drawn; confirmation of alarm limit configuration |
| **Verification — effectiveness** | Temperature held within the tolerance band over the maximum perfusion duration at the highest specified ambient, with the organ thermal load simulated; rate of rise measured with active cooling deliberately disabled; alarm demonstrated to raise within its specified response time |
| **New risks introduced (clause 7.5)** | **(a)** Active cooling can **over-cool**: perfusate below 0 °C risks ice crystal formation and direct cell damage. This is a new hazard introduced by the control and is the reason RC-024 specifies a **low** alarm as well as a high one. Not yet analysed as its own hazard. **(b)** Insulation adds a cleanable external surface — carried to HAZ-003, and the same interface RC-002 introduces. **(c)** A cooling system adds electrical and mechanical failure modes not covered by this file. |
| **Severity after control** | **S4 — unchanged** |
| **Residual risk** | **Not acceptable, and unsupported by any analysis.** No requirement exists and nothing is verified. ELAP-DFMEA-001 records that the referenced CFD run was **isothermal at 4 °C with no thermal load applied**, so it provides no evidence of thermal behaviour under heat ingress. There is currently no analysis of any kind supporting a thermal claim about this device. |
| **Traceability** | No DFMEA entry — thermal is outside the scope of ELAP-DFMEA-001 Rev 1.4. **Identified by this file.** |

> **Phase basis and its limits.** This record covers operating phase 1, cold detergent decellularization at 4 °C, per ELAP-RMF-001 section 1.1. Cold perfusion at this stage follows Napierala et al., *Scientific Reports* (2017), which maintains 4 °C through the detergent stages together with a protease inhibitor, specifically to suppress the matrix degradation described above.
>
> The hazard behaves differently in the other two phases and neither is analysed here. In the 37 °C enzymatic stage and in the 37 °C recellularization culture, a temperature excursion downward rather than upward is the concern, and the harm becomes loss of enzyme activity or death of seeded cells rather than protease digestion of the matrix. The control would be active heating rather than active cooling, and the new risk introduced by that control would be protein denaturation rather than ice formation.
>
> **No thermal analysis of any kind supports this record.** The CFD run referenced by ELAP-DFMEA-001 was isothermal at 4 °C with no thermal load applied, so it provides no evidence of heat ingress behaviour. Closing this requires either a transient thermal model with the organ's thermal mass and a stated ambient, or measurement on a built chamber. Neither exists.

---

## 10. HAZ-008 — Non-physiological perfusion pressure or flow distribution

| Field | Entry |
|---|---|
| **Hazard** | Perfusate pressure or flow distribution outside the physiological range for the organ |
| **Foreseeable sequence of events** | **Maldistribution.** Port diameter and edge fillet vary within the manufacturing tolerance band, changing local flow resistance port to port, and the manifold header is not sized so that port restriction dominates distribution → flow divides unevenly between ports.<br>**Inlet jetting.** Tolerance stack between the chamber inlet position and the cradle window permits partial overlap at worst case → flow jets through a reduced opening at locally elevated velocity.<br>**Outflow obstruction.** The outlet port is undersized, occluded by the cradle or organ, kinked, or fouled by particulate over a long run → outflow resistance rises.<br>**Headspace pressurisation.** The chamber vent is occluded or its filter blocked by condensation or fouling → headspace pressure rises during filling and opposes hepatic venous drainage.<br>Each route ends in the same place: the pressure or flow the organ experiences is not the pressure or flow it was designed for. |
| **Hazardous situation** | The organ's vascular bed is exposed to perfusate at a pressure or flow distribution outside its physiological tolerance while perfused |
| **Harm** | Over-perfusion with wall shear above the 1.5 Pa limit, damaging the extracellular matrix; under-perfusion of other regions causing ischaemia; raised intravascular pressure causing vascular distension and oedema; venous outflow obstruction; loss of viable scaffold or of the whole graft |
| **Severity** | **S4 — Critical.** Loss of the graft. ELAP-DFMEA-001 scores DF-004, DF-006, DF-008 and DF-011 at 7, mapping to S3. **Raised to S4 here** for the same reason as HAZ-004: the DFMEA scored each mode's own effect, while the hazard carries the worst credible outcome, which is loss of the graft rather than regional damage. |
| **P1 / P2** | Not estimated — RMP-001 section 4.2 |
| **Initial risk evaluation** | Not acceptable without risk control, per RMP-001 section 4.3 for S4 |
| **Risk control** | **RC-011** — manifold header sized so that port pressure drop dominates the distribution, making flow division insensitive to port-to-port tolerance variation. **RC-012** — cradle window sized to exceed the inlet port by more than the worst-case tolerance stack, so misalignment cannot reduce the flow area. **RC-013** — outlet port sized with margin over design flow and located where neither cradle nor organ can occlude it at worst-case position, with strain relief and a sump or screen keeping debris from the port mouth. **RC-014** — vent bore and filter sized for the gas displacement rate at maximum fill rate with margin, hydrophobic media, positioned away from the splash zone. **RC-015** — inlet and outlet pressure monitored against an expected range, with inlet and outlet flow compared for imbalance. |
| **Tier, and why not higher** | **RC-011 to RC-014 are tier 1, inherently safe design.** Each makes the failure insensitive to a tolerance or a position rather than detecting it afterwards — RC-011 in particular is the strongest kind of tier 1 control, since it removes the sensitivity rather than tightening the tolerance. **RC-015 is tier 2**, added because fouling and particulate accumulation are time-dependent and no dimensioning decision prevents them over a long run. |
| **Requirements** | **None yet.** Will generate: allowable per-port flow variation, from which port dimensional tolerances are derived; header-to-port pressure drop ratio; cradle window margin over the worst-case tolerance stack; outlet port area margin; vent bore and filter flow capacity; a tolerable chamber headspace pressure derived from hepatic venous back-pressure; pressure and flow monitoring ranges. |
| **Verification — implementation** | Dimensional inspection of port diameters and fillets on first article; inspection of window-to-port registration at assembly; confirmation of outlet position and sump geometry against drawing |
| **Verification — effectiveness** | CFD or bench flow-distribution test at the worst-case tolerance combination, measuring per-port flow against the acceptance band; CFD at the maximum credible inlet offset confirming velocity and wall shear remain within limits; outlet pressure drop measured at maximum flow; vent flow capacity measured against the gas displacement rate at maximum fill rate |
| **New risks introduced (clause 7.5)** | **(a)** A sump or screen at the outlet is itself a fouling site and may obstruct in the way it was fitted to prevent. **(b)** Pressure monitoring adds two more fluid-path interfaces — carried to HAZ-003. **(c)** Sizing the header so port drop dominates raises total system pressure drop, which raises the pump duty required and may push inlet pressure up. None is analysed. |
| **Severity after control** | **S4 — unchanged** |
| **Residual risk** | **Not acceptable.** No requirement exists and nothing is verified. Two open inputs block the controls directly: the **maximum credible chamber fill rate**, which RC-014 cannot be sized without, and the **tolerable chamber headspace pressure**, which has no derived value. Both are recorded in ELAP-DFMEA-001 section 8. |
| **Traceability** | DF-004, DF-006, DF-008, DF-011 · ELAP-VP-002 (chamber vent protocol, not written) will verify RC-014 |

> **Two recommended actions here are executable now** against the existing CFD model, and are the only actions in the whole file that do not need hardware: the worst-case tolerance study for RC-011 and the maximum-offset study for RC-012. ELAP-DFMEA-001 section 7 already records this.

---

## 11. HAZ-009 — Perfusate cooled below the process temperature toward freezing

**Introduced by a risk control measure.** RC-023, active cooling under closed-loop control, was adopted to control HAZ-007. ISO 14971 clause 7.5 requires any new risk a control introduces to go through the full cycle of estimation, evaluation and control. This record is that cycle.

| Field | Entry |
|---|---|
| **Hazard** | Cooling capacity capable of driving the perfusate below the 4 °C process temperature |
| **Foreseeable sequence of events** | Active cooling runs under closed-loop control to a 4 °C setpoint → the control loop faults, the temperature sensor drifts low, or the setpoint is entered incorrectly → cooling continues past the setpoint → perfusate temperature falls toward 0 °C → ice nucleates in the perfusate and in the interstitial water of the organ |
| **Hazardous situation** | The organ is exposed to perfusate at or below the freezing point of the perfusate |
| **Harm** | Ice crystal formation ruptures cell membranes and disrupts the extracellular matrix architecture; loss of the vascular basement membrane that phase 3 reseeding depends on; the scaffold is structurally compromised and cannot support recellularization |
| **Severity** | **S4 — Critical.** Loss of the scaffold. Equal to HAZ-007, which is expected: both are a failure to hold the process temperature, in opposite directions, with the same consequence for the matrix. |
| **P1 / P2** | Not estimated — RMP-001 section 4.2 |
| **Initial risk evaluation** | Not acceptable without risk control, per RMP-001 section 4.3 for S4 |
| **Risk control** | **RC-025** — cooling capacity sized so that the lowest perfusate temperature achievable at the lowest specified ambient is above a stated floor, making sub-zero operation physically impossible regardless of control or sensor fault. **RC-024** — the low alarm limit already specified under HAZ-007 provides a second, independent indication. |
| **Tier, and why not higher** | **RC-025 is tier 1, inherently safe design.** It does not detect the fault or warn about it; it removes the capability. A chiller that cannot reach 0 °C in this configuration cannot freeze the organ however the control loop behaves, which is a stronger position than any alarm. **RC-024 is tier 2** and is retained as a second layer, not as the control. The cooling plant is not yet selected, so capacity sizing is a design input rather than a design change. |
| **Requirements** | **None yet.** Will generate: a minimum perfusate temperature floor; a cooling capacity limit expressed as the lowest achievable equilibrium temperature at the lowest specified ambient; a low alarm limit set above that floor. |
| **Verification — implementation** | Confirmation of the selected chiller's rated minimum output temperature against the capacity requirement; inspection of the configured low alarm limit |
| **Verification — effectiveness** | Cooling driven to maximum with the control loop deliberately defeated and the setpoint forced to minimum, at the lowest specified ambient, confirming the perfusate equilibrates above the stated floor; low alarm demonstrated to raise above that floor |
| **New or increased risks introduced (clause 7.5)** | **Limiting cooling capacity trades directly against HAZ-007.** A plant sized so it cannot reach 0 °C may also be unable to hold 4 °C at high ambient or against a large thermal load. The two hazards are controlled by opposing adjustments of the same parameter, and the acceptable band between them has not been established. This is the clearest control conflict in the file. |
| **Severity after control** | **S4 — unchanged** |
| **Residual risk** | **Not acceptable.** No requirement exists, the cooling plant is not selected, and the capacity band that satisfies both HAZ-007 and HAZ-009 has not been determined. Establishing it requires a transient thermal model with the organ's thermal mass and a stated ambient range, which does not exist — the referenced CFD run was isothermal with no thermal load. |
| **Traceability** | No DFMEA entry. **Introduced by RC-023 and identified by this file under clause 7.5.** Interacts with HAZ-007. |

---

## 12. Risk controls defined by this file

Assigned sequentially in order of definition, per ELAP-RMP-001 section 8.1.

| RC | Control | Tier | Hazard | Requirement written? | Verified? |
|---|---|---|---|---|---|
| RC-001 | Inlet-line gas detection with pump interlock | 2 | HAZ-001 | Yes — REQ-014a/b/c/e | No |
| RC-002 | Thermal isolation of operator-contact surfaces | 1 | HAZ-002 | No | No |
| RC-003 | O-ring gland dimensioned for guaranteed minimum squeeze | 1 | HAZ-003 | No | No |
| RC-004 | 0.2 µm sterilising-grade hydrophobic vent filter, retention specified | 1 | HAZ-003 | No | No |
| RC-005 | 100 % post-assembly pressure decay leak test | 2 | HAZ-003 | No | No |
| RC-006 | Per-lot incoming inspection of filter specification | 2 | HAZ-003 | No | No |
| RC-007 | Asymmetric cradle locating pattern | 1 | HAZ-004 | No | No |
| RC-008 | Pin-and-slot location, one round and one slotted | 1 | HAZ-004 | No | No |
| RC-009 | Support bars sized to a deflection and creep limit | 1 | HAZ-004 | No | No |
| RC-010 | Chamber envelope from anatomical range plus clearance margin | 1 | HAZ-004 | No | No |
| RC-011 | Header sized so port pressure drop dominates distribution | 1 | HAZ-008 | No | No |
| RC-012 | Cradle window oversized beyond worst-case tolerance stack | 1 | HAZ-008 | No | No |
| RC-013 | Outlet port sized with margin, located clear of occlusion, with sump | 1 | HAZ-008 | No | No |
| RC-014 | Vent bore and filter sized for gas displacement at maximum fill rate | 1 | HAZ-008 | No | No |
| RC-015 | Inlet and outlet pressure and flow monitoring | 2 | HAZ-008 | No | No |
| RC-016 | Flexible strain-relieved bile line decoupling cannula from port | 1 | HAZ-006 | No | No |
| RC-017 | Bile path physically separated from and sealed against the perfusate path | 1 | HAZ-006 | No | No |
| RC-018 | Bile port located for the anatomical range of duct positions | 1 | HAZ-006 | No | No |
| RC-019 | Expected bile output range with absence flagged | 2 | HAZ-005 | No | No |
| RC-020 | Perfusate monitored for bile salts | 2 | HAZ-005 | No | No |
| RC-021 | IFU: bile output not to be the sole viability criterion | 3 | HAZ-005 | No | No |
| RC-022 | Insulation and thermal mass | 1 | HAZ-007 | No | No |
| RC-023 | Active cooling under closed-loop temperature control | 2 | HAZ-007 | No | No |
| RC-024 | Perfusate temperature monitoring with high and low alarms | 2 | HAZ-007, HAZ-009 | No | No |
| RC-025 | Cooling capacity sized so sub-zero perfusate is physically unachievable | 1 | HAZ-009 | No | No |

**Tier distribution: 16 tier 1, 8 tier 2, 1 tier 3.** The single tier 3 control is a supplement at S5 and is not relied on, as RMP-001 section 4.3 requires.

**One of twenty-five controls has a written requirement. None is verified.** That is the state of this design file, stated plainly rather than implied by a column of blanks.

---

## 13. Overall residual risk (clause 8)

**Not evaluated, and cannot be.**

ELAP-RMP-001 section 5 permits evaluation of overall residual risk only once every individual residual risk is acceptable. **No individual residual risk in this file is acceptable** — twenty-four of twenty-five controls have no requirement written, and none of the twenty-five is verified as implemented or effective. HAZ-001 is additionally unacceptable on a second, independent ground: reduction as far as possible is argued rather than demonstrated, the bubble trap trade being unquantified.

The method in RMP-001 section 5 is therefore defined and inapplicable. Four considerations it names, recorded now so they are not lost:

| Consideration | What this file already shows |
|---|---|
| Interaction between controls | Real and already visible. RC-002 insulation, RC-015 pressure monitoring, RC-017 bile separation and the RC-001 sensor housing each add an interface to HAZ-003 — every control that adds a boundary crossing degrades the sterile barrier. |
| Cumulative severity | Two hazards at S5 and six at S4, none controlled to an acceptable residual. Nine foreseeable misuse cases, none controlled. |
| Burden of information for safety | Only one tier 3 control exists, so this is currently low — but only because use-related risk is uncontrolled rather than controlled by instruction. |
| Opposing controls | **HAZ-007 and HAZ-009 are controlled by opposing adjustments of cooling capacity.** The band satisfying both has not been established. Any overall residual risk evaluation would have to resolve this first. |
| Completeness | Four of nine hazards were found outside the DFMEA, which suggests the set is not complete. One of the four, HAZ-009, was introduced by a control measure rather than existing in the design — which implies further controls may introduce further hazards not yet seen. |

---

## 14. Open items

| Item | Blocks | Status |
|---|---|---|
| Phase 1 temperature | — | **Resolved.** 4 °C for detergent decellularization, per Napierala et al. 2017. |
| Perfusion control variable | Every flow-derived limit in ELAP-DIS-001 and ELAP-VP-001 | **Resolved and the news is bad.** Whole human liver decellularization is **pressure-controlled at 120 mmHg**, not flow-controlled. Flow is an output and **rises during the run** as cells are removed and scaffold resistance falls. The flow figures in ELAP-DIS-001 Annex A are normothermic preservation targets and do not apply to this device. |
| Flow rate at human-liver scale under pressure control | RC-001 velocity limits | **Not available.** The human liver source states 120 mmHg and no flow. Published decellularization flow figures are 20 mL/min for porcine pancreas and 5 mL/min at rat scale — neither transfers. |
| Phases 2 and 3 | Everything | **Not analysed.** See section 1.4. |
| Use-related risk, M-1 to M-9 | All nine misuse cases | **No controls, and none planned.** Requires IEC 62366-1, outside the scope of this file and of ELAP-DFMEA-001. M-1 and M-5 reach harms assessed at S4 and S5, so this file cannot conclude that use-related risk is acceptable and does not attempt to. |
| Residual detergent clearance | HAZ-006, M-4 | No requirement exists for residual detergent limits in the scaffold, and no test method. |
| Is the recipient in scope for harm? | Severity of HAZ-003, HAZ-005, HAZ-006 | **Resolved — yes.** Confirmed 04 Oct 2026. The device produces a scaffold intended for implantation, so harm reaches a patient through the product. |
| Anatomical range of donor organ size | RC-010 | Open input, ELAP-DFMEA-001 section 8 |
| Anatomical range of bile duct position | RC-018 | Open input, ELAP-DFMEA-001 section 8 |
| Maximum credible chamber fill rate | RC-014 | Open input, ELAP-DFMEA-001 section 8 |
| Tolerable chamber headspace pressure | RC-014, RC-015 | Open input, ELAP-DFMEA-001 section 8 |
| Chamber and lid material | RC-002 severity, RC-022 | Open input, ELAP-DFMEA-001 section 8 |
| Organ tolerance to gas volume | RC-001 detection threshold | Open input, ELAP-VP-001 section 8 |
| Sterilisation method and sterility assurance level | RC-003 to RC-006 | Not specified. ELAP-DFMEA-001 records single-use and supplied-sterile as assumed, not required. |
| Cooling capacity band satisfying both HAZ-007 and HAZ-009 | RC-023, RC-025 | **Not determined.** The two hazards are controlled by opposing adjustments of the same parameter. Needs a transient thermal model with the organ's thermal mass and a stated ambient range; none exists. |
| Usability engineering, IEC 62366-1 | HAZ-005 presentation of information | Out of scope and not analysed elsewhere |
| Quantified trade between a bubble trap and the interface risk it adds | HAZ-001 reduction as far as possible | **Not performed.** The trap was rejected on reasoned grounds recorded in HAZ-001, but no analysis compares the HAZ-003 interface risk it adds against the gas-removal benefit. Reduction as far as possible is argued, not demonstrated. |

---

## 15. Limitations

- **Single analyst, no independent review.** Every severity, every tier judgement and every acceptability conclusion in this file is one person's, unreviewed. ELAP-RMP-001 section 2 records this as the most significant structural limitation of the exercise.
- **Probability not estimated anywhere.** Risk is evaluated on severity alone, which is permitted by clause 4.4 d) but weaker than severity and probability together.
- **No clinical input.** Severity assignments involving graft viability and recipient outcome are engineering judgement, not clinical judgement.
- **No benefit-risk analysis.** Clause 7.4 cannot be performed without clinical benefit data.
- **One phase of three.** This revision covers decellularization at 4 °C. Phases 2 and 3 are not analysed, and several hazards would change materially in them — see section 1.4.
- **Use-related risk is identified and uncontrolled, by decision rather than by oversight.** Nine foreseeable misuse cases are recorded in section 1.2, none has a risk control, and no design change to address them is planned. Two are controllable by inherently safe design without new mechanisms and are recorded as available and not taken.
- **One control is justified by argument rather than analysis.** The rejection of a bubble trap under HAZ-001 rests on an unquantified trade against sterile-barrier interface risk.
- **Two hazards are controlled by opposing adjustments of the same parameter.** HAZ-007 and HAZ-009 both concern cooling capacity, in opposite directions, and the band satisfying both is undetermined.
- **Eight hazards is not demonstrably complete.** Three were found outside the DFMEA, which is evidence that the identification method has gaps rather than that it is finished.
- **Severity raised above the DFMEA in two places.** HAZ-004 and HAZ-008 are S4 here against S3 implied by the DFMEA's scores of 7. The reasoning is stated in each record; it is a judgement and could be argued the other way.

---

## 16. Review and approval

| Role | Name | Signature | Date |
|---|---|---|---|
| Prepared by | Raj Harsh | R.H. | 04 Oct 2026 |
| Reviewed by | | | |
| Approved by | | | |

Independent review and approval cannot be performed in a single-person exercise. Both roles are left unsigned deliberately. See ELAP-RMP-001 section 2.

---

## Revision history

| Rev | Date | Description | By |
|---|---|---|---|
| 1.2 | 04 Oct 2026 | **HAZ-009 added** — perfusate cooled toward freezing by the active cooling of RC-023, the new-risk cycle required by clause 7.5. Controlled by **RC-025**, cooling capacity sized so sub-zero operation is physically unachievable; tier 1, since it removes the capability rather than detecting the fault. Records that RC-025 and RC-023 adjust the same parameter in opposite directions and that the band satisfying both HAZ-007 and HAZ-009 is undetermined. **Bubble trap recorded as a rejected control option** for HAZ-001, with the three grounds for rejection, and with the residual risk stating that reduction as far as possible is argued rather than demonstrated because the trade is unquantified. **Use-related risk formally recorded as uncontrolled by decision**, with the consequence stated: M-1 and M-5 reach S4 and S5 harms, so this file cannot conclude use-related risk is acceptable. Notes addressed to the reader removed throughout in favour of document-voice basis statements. | Raj Harsh |
| 1.1 | 04 Oct 2026 | **Intended use added (clause 5.2)**, which the Rev 1.0 analysis was built without — the omission ISO 14971 puts first for exactly this reason. The device is a three-phase processing platform: decellularization at 4 °C, an enzymatic and wash stage at 37 °C, and recellularization at 37 °C with cell culture. **Nine reasonably foreseeable misuse cases added (M-1 to M-9)**, none controlled. **Characteristics related to safety added (clause 5.3).** **Scoped to phase 1 only**, with the consequences for other phases stated. Hazards corrected for the phase: HAZ-001 harm is incomplete decellularization and matrix damage rather than ischaemia, there being no living tissue; HAZ-005 cannot arise in phase 1, no hepatocytes meaning no bile, and is marked out of scope; HAZ-006 concerns retained detergent rather than bile and is **raised from S4 to S5**, since retained detergent reaches a patient by a route the wash phases do not clear; HAZ-007 harm is enzymatic degradation of the matrix by endogenous proteases at raised temperature, not warm ischaemia. Recipient confirmed in scope for harm. Perfusion found to be **pressure-controlled at 120 mmHg** for whole human liver decellularization, not flow-controlled, which invalidates the flow basis of the limits in ELAP-DIS-001. | Raj Harsh |
| 1.0 | 04 Oct 2026 | Initial issue. Eight hazards identified and analysed; twenty-four risk controls defined. HAZ-001 and HAZ-002 drafted and reviewed line by line; HAZ-003 to HAZ-008 drafted from ELAP-DFMEA-001 Rev 1.4. Supersedes working drafts 0.1 to 0.3, which were not for publication. The seven failure modes that ELAP-DFMEA-001 section 5 mapped to a single hazard are split into HAZ-004 (mechanical) and HAZ-008 (hydraulic), on the basis that a hazard is defined by its source and these are two sources needing different controls. HAZ-002 and HAZ-007 are hazards the design FMEA could not find, being outside its component-function scope. HAZ-006 was found by the DFMEA's traceability check. Severity for HAZ-004 and HAZ-008 raised to S4 against the S3 implied by the DFMEA, because a hazard carries the worst credible outcome rather than each failure mode's own effect. Records that one of twenty-four controls has a written requirement, that none is verified, and that overall residual risk therefore cannot be evaluated. | Raj Harsh |
