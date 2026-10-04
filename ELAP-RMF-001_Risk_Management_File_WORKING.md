# ELAP-RMF-001 — Risk Management File

**External Liver Assistance Platform**

| Field | Entry |
|---|---|
| Document number | ELAP-RMF-001 |
| Revision | 0.3 — WORKING DRAFT, not for publication |
| Prepared by | Raj Harsh |
| Governing plan | ELAP-RMP-001 Rev 1.1 |
| Standard | ISO 14971:2019, Clauses 5, 6, 7 |

*Self-directed exercise on an independent design project. Not industry work. Not a controlled document under any quality management system.*

---

## 1. How to fill this in

**HAZ-001 below is worked completely. It is the model.** HAZ-002 to HAZ-006 have the same fields, empty. Fill them in your own words; I will correct the classifications rather than write them for you.

### The three that get confused, every time

| Field | What it is | Test |
|---|---|---|
| **Hazard** | A potential **source** of harm | Can it sit there harming nobody? Then it's a hazard. |
| **Hazardous situation** | Circumstances in which something is **exposed** to the hazard | Does the word *exposure* apply? Then it's a hazardous situation. |
| **Harm** | Injury or damage to health | Has something actually been damaged? Then it's harm. |

What takes you from hazard to hazardous situation is the **foreseeable sequence of events**. That field is where most of the thinking lives, and it is the field people leave blank.

Common error, worth naming: "air embolism" is **not** a hazard. It is harm. The hazard is gas in the circuit.

### Rules from ELAP-RMP-001

- **Severity** uses the five-level scale in RMP-001 section 4.1. S5 death, S4 critical or loss of the graft, S3 serious, S2 minor, S1 negligible.
- **Probability is not estimated.** No unit exists. Write "Not estimated — RMP-001 section 4.2" and do not invent a figure.
- **Acceptability** follows RMP-001 section 4.3. S4 and S5 are not acceptable without a control, and information for safety alone is never enough.
- **Risk controls follow the hierarchy** in order: inherently safe design, then protective measures, then information for safety. If you choose tier 2 or 3, **state why tier 1 was not available.** That justification is required, not optional.
- **Controls reduce probability, not severity.** A detector does not make an embolism less harmful. Severity after control is the same number as before. If you find yourself lowering severity because you added a control, that is the error.

---

## 2. HAZ-001 — WORKED MODEL

| Field | Entry |
|---|---|
| **Hazard ID** | HAZ-001 |
| **Hazard** | Gas present in the perfusion inlet circuit |
| **Foreseeable sequence of events** | Gas is retained in the inlet circuit after priming, or is drawn in at a connector or loose fitting during operation, or evolves out of the perfusate on warming or on a pressure change → the gas is carried along the inlet line by pump-driven flow → it reaches the portal vein or hepatic artery cannula → it passes the cannula into the organ vasculature |
| **Hazardous situation** | Gas is present in the organ's vascular bed while perfusion is running — the organ is exposed to the gas |
| **Harm** | Gas embolism occluding the microvasculature; ischaemic damage to the perfused tissue; loss of the graft, rendering it untransplantable |
| **Severity** | **S4 — Critical.** Loss of the graft. Maps to 8–9 on the ten-point scale in ELAP-DFMEA-001, which scored DF-010 at 9. Consistent. |
| **P1 — probability of the hazardous situation** | Not estimated — RMP-001 section 4.2. No unit built, no test data, no predecessor device. |
| **P2 — probability the hazardous situation leads to harm** | Not estimated — RMP-001 section 4.2. |
| **Initial risk evaluation** | **Not acceptable without risk control**, per RMP-001 section 4.3 for S4. |
| **Risk control measure** | **RC-001** — gas detection on each perfusion inlet line, with an interlock that halts the pump on detection. |
| **Control hierarchy tier, and why not higher** | **Tier 2, protective measure.** Tier 1 inherently safe design was considered and is not available: gas cannot be eliminated from a fluid circuit by geometry alone, since it enters through priming, connectors and dissolution out of the perfusate. A passive bubble trap would arguably sit closer to tier 1, removing gas rather than reacting to it, and **that option remains open** — see residual risk below. |
| **Requirements generated** | REQ-014a, REQ-014b, REQ-014c, REQ-014e in ELAP-DIS-001 Rev 1.3. REQ-014d is a derived constraint rather than a control requirement. |
| **Verification — implementation** | ELAP-VP-001 Rev 3.2, steps 1, 2, 2a; AC-3. Confirms sensors fitted on both lines, interlock wired, standoff as drawn. |
| **Verification — effectiveness** | ELAP-VP-001 Rev 3.2, steps 6–11; AC-1, AC-2, AC-5. Confirms gas at or above threshold is detected and flow stops before the bolus reaches the cannula. |
| **New or increased risks introduced by the control (clause 7.5)** | **(a)** False trigger halting perfusion unnecessarily, interrupting organ perfusion. Controlled by REQ-014e, verified by AC-5. **(b)** The sensor housing adds a further interface to the fluid path, which is a potential leak and contamination site. **Not yet analysed** — belongs to HAZ-003 and is recorded there as an open item. |
| **Severity after control** | **S4 — unchanged.** A detector does not reduce the harm an embolism causes; it reduces how often one occurs. Severity is a property of the harm, not of the controls. |
| **Residual risk** | **Cannot be determined, and is not acceptable as things stand.** Two reasons. First, ELAP-VP-001 is written and not executed, so the control is not verified as implemented or effective — RMP-001 section 6 requires both. Second, RMP-001 section 4.3 requires S4 risk to be reduced **as far as possible**, and that cannot be claimed while the bubble trap option is still open: detection halts flow but does not remove gas already in the line, and a trap would. Until that design decision is taken and justified, reduction as far as possible is not demonstrated. |
| **Traceability** | ELAP-DFMEA-001 DF-010 · ELAP-DIS-001 REQ-014a/b/c/e · ELAP-VP-001 AC-1/2/3/5 · ELAP-TRM-001 section 3 |

---

## 3. HAZ-002 — Cold external surfaces (operator)

**Status: COMPLETE.** Drafted by Raj Harsh; classifications corrected on review. Severity, control tier and the open material decision are recorded below.

| Field | Entry |
|---|---|
| **Hazard ID** | HAZ-002 |
| **Hazard** | Cold external surfaces of the chamber at the 4 °C operating temperature |
| **Foreseeable sequence of events** | Perfusion is started → the chamber is filled with perfusate at 4 °C → the chamber wall temperature falls toward the perfusate temperature by conduction → the operator needs to handle the chamber, to reposition it or to change its contents → the operator makes contact with the external surface bare-handed |
| **Hazardous situation** | An operator's unprotected skin is in contact with the cold external surface of the chamber |
| **Harm** | Localised cold injury to the skin: pain and transient numbness, resolving without intervention |
| **Severity** | **S2 — Minor.** Assumes sustained bare-skin contact of the order of a minute against a high-conductivity exterior. ELAP-DFMEA-001 Rev 1.3 models the solids as steel and records that the manufacturing material is **not yet selected**. If a low-conductivity exterior is specified, this falls to **S1 — Negligible**. The severity therefore depends on a design decision that remains open. |
| **P1 — probability of the hazardous situation** | Not estimated — RMP-001 section 4.2 |
| **P2 — probability it leads to harm** | Not estimated — RMP-001 section 4.2 |
| **Initial risk evaluation** | S2 is acceptable with risk control, per RMP-001 section 4.3. Note that acceptability does not by itself authorise a low control tier — see the control tier field. |
| **Risk control measure** | **RC-002** — thermal isolation of the operator-contact surfaces, by one of: an insulating layer or sleeve over the cold surfaces; handles or grip points in a low-conductivity material held near ambient; or specification of a low-conductivity exterior material in place of steel. Selection is open; all three are tier 1. |
| **Control hierarchy tier, and why not higher** | **Tier 1, inherently safe design.** An earlier draft of this record proposed protective gloves and justified skipping tier 1 on the grounds of design complexity. That justification was rejected on review for two reasons. First, gloves worn by the operator on instruction are **tier 3, information for safety** — not tier 2; tier 2 is confined to measures in the device itself or in the manufacturing process. Second, tier 1 **is** practicable here: insulation, a sleeve, low-conductivity grip points and exterior material selection are all available, and the exterior material has not yet been chosen. ISO 14971 clause 7.1 permits moving down the hierarchy only where the higher option is not practicable, and complexity or cost is not such a ground — see RMP-001 section 4.4. Gloves may be added as a tier 3 supplement but are not the control. |
| **Requirements generated** | **None yet.** This control will generate two requirements in ELAP-DIS-001: a limit on the maximum temperature of any intended operator-contact surface at thermal steady state, and a specification of the exterior material or insulation that achieves it. |
| **Verification — implementation** | Inspection that the specified insulation, sleeve or grip material is present as drawn, at every intended contact point. |
| **Verification — effectiveness** | Surface temperature measured at each intended contact point at thermal steady state, with the chamber filled at 4 °C and at the lowest specified ambient, against the limit set by the requirement above. |
| **New or increased risks introduced by the control (clause 7.5)** | **(a)** An insulating layer or sleeve adds an external surface that must be cleaned or disinfected, and a crevice where contamination can lodge. Feeds HAZ-003. **(b)** If gloves are added as a tier 3 supplement, reduced tactile feedback and grip raise the risk of dropping the chamber or mishandling a vascular or bile connection. Feeds HAZ-004. Neither is yet analysed. |
| **Severity after control** | **S2 — unchanged.** Insulating the surface does not change how a cold injury presents; it changes how often skin reaches a cold surface. Severity is a property of the harm, not of the controls. |
| **Residual risk** | **Not acceptable as things stand.** No control is specified, selected or verified: the exterior material is undecided, no requirement exists in ELAP-DIS-001, and no verification protocol has been written. Once a tier 1 control is specified and verified as implemented and effective, residual risk at S2 is acceptable per RMP-001 section 4.3. |
| **Traceability** | **No DFMEA entry.** Thermal performance is outside the scope of ELAP-DFMEA-001 Rev 1.3. **This hazard was identified by this risk management file, not by the DFMEA** — the second such hazard after HAZ-006. |

> **Scope note.** This record covers cold injury to the **operator**. It does not cover failure to hold the perfusate at temperature, which harms the **organ** and is a separate hazard with materially higher severity. That is recorded as HAZ-007.

---

## 4. HAZ-003 — Contamination of the perfusate

| Field | Entry |
|---|---|
| **Hazard ID** | HAZ-003 |
| **Hazard** | |
| **Foreseeable sequence of events** | |
| **Hazardous situation** | |
| **Harm** | |
| **Severity** | |
| **P1 / P2** | Not estimated — RMP-001 section 4.2 |
| **Initial risk evaluation** | |
| **Risk control measure** | |
| **Control hierarchy tier, and why not higher** | |
| **Requirements generated** | |
| **Verification — implementation** | |
| **Verification — effectiveness** | |
| **New risks introduced by the control** | |
| **Severity after control** | |
| **Residual risk** | |
| **Traceability** | ELAP-DFMEA-001 DF-001 (lid O-ring seal), DF-002 (vent filter retention). Also the sensor housing interface carried over from HAZ-001. |

---

## 5. HAZ-004 — Loss of perfusion and mechanical damage to the organ

| Field | Entry |
|---|---|
| **Hazard ID** | HAZ-004 |
| **Hazard** | |
| **Foreseeable sequence of events** | |
| **Hazardous situation** | |
| **Harm** | |
| **Severity** | |
| **P1 / P2** | Not estimated — RMP-001 section 4.2 |
| **Initial risk evaluation** | |
| **Risk control measure** | |
| **Control hierarchy tier, and why not higher** | |
| **Requirements generated** | |
| **Verification — implementation** | |
| **Verification — effectiveness** | |
| **New risks introduced by the control** | |
| **Severity after control** | |
| **Residual risk** | |
| **Traceability** | ELAP-DFMEA-001 DF-003, DF-004, DF-005, DF-006, DF-008, DF-009, DF-011 — seven failure modes. |

> **Note.** This one carries seven DFMEA items reaching the same harm by different routes. Consider whether it is genuinely one hazard or whether it should split — cradle misplacement, flow maldistribution and outlet obstruction are different sources even though the damage looks similar. A hazard that absorbs seven failure modes may be doing too much work.

---

## 6. HAZ-005 — Erroneous measurement

| Field | Entry |
|---|---|
| **Hazard ID** | HAZ-005 |
| **Hazard** | |
| **Foreseeable sequence of events** | |
| **Hazardous situation** | |
| **Harm** | |
| **Severity** | |
| **P1 / P2** | Not estimated — RMP-001 section 4.2 |
| **Initial risk evaluation** | |
| **Risk control measure** | |
| **Control hierarchy tier, and why not higher** | |
| **Requirements generated** | |
| **Verification — implementation** | |
| **Verification — effectiveness** | |
| **New risks introduced by the control** | |
| **Severity after control** | |
| **Residual risk** | |
| **Traceability** | ELAP-DFMEA-001 DF-007, partial. |

> **Note.** The harm here is indirect: a wrong measurement leads a clinician to a wrong decision about whether the graft is usable. Think about who is harmed and how — the sequence of events runs through a human decision, which makes it different in kind from the others.

---

## 7. HAZ-006 — Biliary obstruction and bile contamination of the perfusate

| Field | Entry |
|---|---|
| **Hazard ID** | HAZ-006 |
| **Hazard** | |
| **Foreseeable sequence of events** | |
| **Hazardous situation** | |
| **Harm** | |
| **Severity** | |
| **P1 / P2** | Not estimated — RMP-001 section 4.2 |
| **Initial risk evaluation** | |
| **Risk control measure** | |
| **Control hierarchy tier, and why not higher** | |
| **Requirements generated** | |
| **Verification — implementation** | |
| **Verification — effectiveness** | |
| **New risks introduced by the control** | |
| **Severity after control** | |
| **Residual risk** | |
| **Traceability** | ELAP-DFMEA-001 DF-007. **Identified by the DFMEA**, not present in any earlier risk analysis. |

> **Note.** This is the hazard your own DFMEA found. There may be two distinct harms here rather than one — obstruction causing cholestatic injury, and leakage putting cytotoxic bile salts into the perfusate. Decide whether that is one hazard or two.

---

## 7a. HAZ-007 — Loss of thermal control of the perfusate

| Field | Entry |
|---|---|
| **Hazard ID** | HAZ-007 |
| **Hazard** | |
| **Foreseeable sequence of events** | |
| **Hazardous situation** | |
| **Harm** | |
| **Severity** | |
| **P1 / P2** | Not estimated — RMP-001 section 4.2 |
| **Initial risk evaluation** | |
| **Risk control measure** | |
| **Control hierarchy tier, and why not higher** | |
| **Requirements generated** | |
| **Verification — implementation** | |
| **Verification — effectiveness** | |
| **New risks introduced by the control** | |
| **Severity after control** | |
| **Residual risk** | |
| **Traceability** | No DFMEA entry. Thermal performance is outside the scope of ELAP-DFMEA-001 Rev 1.3. |

> **Note.** This is the thermal hazard that matters. The harm is to the organ, not the operator. Two things to settle first: whether the device is hypothermic (holding 4 °C) or normothermic (holding 37 °C), since ELAP-DIS-001 records that conflict as unresolved; and whether the harm is gradual degradation or loss of the graft, because that decides S3 against S4.
>
> Also relevant: ELAP-DFMEA-001 records that the referenced CFD run was **isothermal at 4 °C with no thermal load applied**, so it provides no evidence of thermal behaviour under ambient heat ingress. There is currently no analysis supporting any thermal claim about this device.

---

## 8. Corrections raised from this file — status

| Raised while working | Issue | Status |
|---|---|---|
| HAZ-002 | RMP-001 section 4.3 permitted a tier 3 control for an S2 hazard even where tier 1 was practicable, contradicting section 4.4. | **Applied** in ELAP-RMP-001 Rev 1.1. Acceptability and hierarchy are now separate requirements. |
| HAZ-002 | Risk control identifiers followed two different rules: RC-010 mirrored DFMEA item DF-010, RC-002 mirrored HAZ-002. RC-010 also implied nine earlier controls that never existed. | **Applied.** Renumbered RC-010 → RC-001. Convention recorded in ELAP-RMP-001 section 8.1: sequential in order of definition. Propagated to ELAP-DFMEA-001 Rev 1.4, ELAP-DIS-001 Rev 1.4, ELAP-VP-001 Rev 3.3, ELAP-TRM-001 Rev 1.1. |
| HAZ-002 | Thermal was treated as a single hazard. Operator cold contact and loss of organ thermal control are distinct hazards with materially different severity. | **Applied.** Split into HAZ-002 and HAZ-007. |
| HAZ-002 | ELAP-RMP-001 section 8 document list omitted HAZ-007. | Open — add when HAZ-007 is written. |

---

## 8.1 Risk controls defined by this file

Assigned sequentially in order of definition, per ELAP-RMP-001 section 8.1.

| RC ID | Control | Tier | Hazards served | Defined for |
|---|---|---|---|---|
| RC-001 | Inlet-line gas detection with pump interlock | 2 — protective measure | HAZ-001 | HAZ-001. Previously numbered RC-010. |
| RC-002 | Thermal isolation of operator-contact surfaces: insulating layer or sleeve, low-conductivity grip points, or low-conductivity exterior material | 1 — inherently safe design | HAZ-002, and feeds HAZ-003 via the cleanable surface it introduces | HAZ-002 |

---

## 9. Overall residual risk — to be completed last

Per ELAP-RMP-001 section 5, this is evaluated only after every individual residual risk is acceptable, and against four considerations: interaction between controls, cumulative severity, burden of information for safety, and completeness.

Leave this blank. RMP-001 already records that the conclusion cannot be reached, because no control in the file is verified.

---

## 10. Review and approval

| Role | Name | Signature | Date |
|---|---|---|---|
| Prepared by | Raj Harsh | | |
| Reviewed by | | | |
| Approved by | | | |

Independent review and approval cannot be performed in a single-person exercise. Both roles are left unsigned deliberately.
