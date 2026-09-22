# AI Use Case Discovery Survey – Draft Submissions (Process Engineering)

*Prepared in accordance with the "Guidance for Completing the AI Use Case Discovery Survey". One primary use case per submission; each follows the three-part description model (current situation, pain point, proposed AI support) and the Q1–Q10 structure. All hour and cost figures are order-of-magnitude estimates with stated assumptions, to be confirmed on a pilot project. AI output requires engineer verification in every case.*

## Overview of submissions

| # | Use case title | Complexity | Primary benefit | Est. annual saving |
| --- | --- | --- | --- | --- |
| A | Automated Drafting of Pump Process Datasheets from Line List and Hydraulics | Low–Medium | Productivity | ~1,800 h |
| B | AI-Assisted Relief Scenario Identification and PSV Sizing | High | Quality | ~2,400 h |
| C | Automated Consistency Check of P&IDs Against Line List and Datasheets | Medium | Reduced rework | ~9,000 h |
| D | Automated Generation of Pre-Commissioning Check Sheets and Test Packs from P&IDs | Medium | Productivity | ~7,500 h |

**Suggested prioritisation:** Submission A first (lowest complexity, structured inputs, quick pilot); Submission C second (largest hour saving, reusable on every project); Submissions B and D require governance for safety-critical outputs and are recommended once A and C have demonstrated the verification workflow.

---

# Submission A: Automated Drafting of Pump Process Datasheets from Line List and Hydraulics

*Working-step focus: Rotating equipment process design – pump hydraulic calculation and PDS preparation*

## Q1–Q4 Identification

**1. Name:** [Optional – enter name if you wish to participate in implementation]

**2. Process Technology team:** [Select team – e.g. Process Engineering / Process Design]

**3. Title of proposed AI use case:** Automated Drafting of Pump Process Datasheets from Line List and Hydraulics

**4. Working step(s) addressed:**

- Pump hydraulic calculation (suction/discharge pressure drop, NPSHa, differential head, power)
- Preparation and revision of pump Process Datasheets (PDS)
- Update of PDS after HMB, line-list or plot-plan revisions

## Q5 Describe the proposed AI solution

**Current situation:** The process engineer collects flow, fluid properties, line sizes, lengths and elevations from the HMB, line list, P&ID and plot plan; performs the hydraulic calculation in an individual Excel sheet; transcribes results into the PDS template; the checker re-verifies inputs and arithmetic. Each HMB or routing revision repeats most of the cycle.

**Pain point:** Highly repetitive data transfer between four to five documents; transcription and unit errors are common and only found at checking; calculation sheets differ between engineers, making checking slow; every revision of flow, line size or elevation triggers a full manual re-run. Typical effort is 8–10 h per pump service including revisions.

**Proposed AI support:** An AI assistant reads the line list, equipment list and HMB export, extracts the required inputs per pump, runs a validated deterministic hydraulic script (Darcy-Weisbach with Churchill friction factor, NPSHa, API 610 motor margin), populates the standard PDS template, and appends a calculation note plus a flag list (velocity limits, low NPSHa, missing data). The engineer reviews the flagged items, selects pump type and margins, and approves the datasheet.

**Inputs → AI task → Output → Engineer role:**

- Inputs: line list (CSV/database export), equipment list, HMB, project design criteria (velocity limits, margins)
- AI task: extract → calculate (deterministic script) → populate PDS → flag deviations
- Output: draft PDS (Excel/PDF), hydraulic calculation note, deviation list
- Engineer: verifies inputs and flags, confirms pump type/margins, signs as originator; checker signs as normal

## Q6 How complicated is the implementation?

| Assessment factor | Yes/No | Rationale |
| --- | --- | --- |
| Do results need to be checked? | Yes | Output is a deliverable (PDS). Originator and checker review remain mandatory. |
| Multiple rules and standards? | Yes | API 610, company hydraulic design criteria, client specifications, IEC motor frames. |
| Large / complex data analysis? | No | Small structured data set per project (line list, equipment list, HMB). |
| Safety-critical decisions? | No | Max. discharge pressure feeds design pressure, but final setting remains an engineer decision. |
| Regulatory / legal requirements? | No | No direct external compliance effect. |
| Significant engineering judgement from AI? | No | Extraction, calculation and formatting only; pump type, margins and acceptance stay with the engineer. |

**Overall complexity:** Low to medium. Structured inputs, deterministic calculation, human review already embedded in the workflow.

## Q7 Benefits of the proposed solution

| Benefit category | Applies | Measurable statement |
| --- | --- | --- |
| Cost reduction | No | Consequence of hours saved, not the primary target. |
| Increased productivity | Yes | Primary: reduce effort per pump service from ~9 h to ~3 h (review-focused). |
| Reduced engineering rework | Yes | Eliminate transcription errors between line list, calculation and PDS; revisions re-run in minutes. |
| Improved quality | Yes | Uniform calculation method and datasheet format across all engineers; 100% check coverage of velocity/NPSH criteria. |
| Improved customer satisfaction | No | Indirect only (fewer client comments on datasheets). |

## Q8 Project types / phases that benefit

| Phase | Applies | Rationale |
| --- | --- | --- |
| Bidding | Partly | Preliminary power estimates for cost estimating; full PDS not needed. |
| PDP | Yes | Preliminary hydraulics and PDS for equipment list and cost estimate. |
| BEP | Yes | Main application – first issue of pump PDS. |
| FEED | Yes | Main application – PDS for enquiry. |
| Detail Engineering | Yes | PDS updates after vendor data, line routing and HMB revisions. |

## Q9 Number of projects where the solution can be used

- Applicable to all projects with rotating equipment – approx. 10–12 projects per year across the team
- Typical 20–60 pump services per project (basis: recent BEP/FEED projects); assume 30 for the calculation
- Each service is revised 2–3 times through the project

## Q10 Typical saving per project / annual cost saving

**Calculation:**

- Current: ~9 h per pump service (calculation 4 h + PDS 2 h + revisions 3 h)
- Future: ~3 h per pump service (input check, flag review, approval)
- Saving: 6 h × 30 services × 10 projects/year = approx. 1,800 engineering hours per year
- Monetary: 1,800 h × €80/h (placeholder – replace with internal blended engineering rate) ≈ €145,000 per year; approx. €14,500 per project

**Assumptions:**

- Line list and equipment list are available as structured exports (not scanned PDFs)
- Hydraulic script is validated once against three completed projects before use
- Hours are order-of-magnitude estimates from engineers' experience; to be confirmed by time recording on a pilot project

---

# Submission B: AI-Assisted Relief Scenario Identification and PSV Sizing

*Working-step focus: Pressure relief and flare system design – scenario identification, relief load and PSV sizing*

## Q1–Q4 Identification

**1. Name:** [Optional – enter name if you wish to participate in implementation]

**2. Process Technology team:** [Select team – e.g. Process Engineering / Process Design]

**3. Title of proposed AI use case:** AI-Assisted Relief Scenario Identification and PSV Sizing

**4. Working step(s) addressed:**

- Identification of credible overpressure scenarios per protected system (API 521)
- Relief load calculation and PSV orifice sizing (API 520 / API 526)
- Preparation of PSV process datasheets and relief load summary

## Q5 Describe the proposed AI solution

**Current situation:** The engineer reviews each P&ID, identifies protected systems and lists overpressure scenarios from experience and checklists; relief loads and orifice sizes are calculated in Excel or vendor tools; results are transcribed into the PSV datasheet and relief load summary. A senior engineer checks the scenario list and calculations. Scenarios are frequently added or changed after HAZOP.

**Pain point:** Scenario lists vary between engineers, and missed credible cases are found late (HAZOP or client review) causing re-sizing, datasheet re-issue and sometimes flare re-evaluation. API 520 arithmetic is repetitive and error-prone. Typical effort is 12–16 h per PSV across scenario identification, sizing, datasheet and revisions.

**Proposed AI support:** An AI assistant reads P&ID topology data (upstream pressure sources, block valves, heat sources, exchangers, control valves) and proposes a systematic scenario checklist per protected system with a short justification for each case, referenced to API 521 clauses. A validated deterministic sizing script calculates relief loads, required area, orifice letter and governing case per API 520/526 and drafts the PSV datasheet and relief summary. The engineer confirms scenario credibility, verifies inputs and approves; the checker reviews as today.

**Inputs → AI task → Output → Engineer role:**

- Inputs: P&ID tag/topology export, HMB, equipment design pressures, fluid properties, project relief philosophy
- AI task: propose scenarios (LLM with API 521 checklist) → calculate (deterministic API 520 script) → draft datasheet and summary
- Output: scenario register with justification, sizing calculation sheet, draft PSV datasheet, relief load summary
- Engineer: accepts/rejects each scenario, confirms inputs, approves sizing; senior engineer checks as normal

## Q6 How complicated is the implementation?

| Assessment factor | Yes/No | Rationale |
| --- | --- | --- |
| Do results need to be checked? | Yes | Safety deliverable – full originator and checker review required; AI proposal is a starting point only. |
| Multiple rules and standards? | Yes | API 520, API 521, API 526, ASME VIII, client relief philosophy, local statutory codes. |
| Large / complex data analysis? | No | Moderate – P&ID topology and HMB data; structured if intelligent P&ID export is available. |
| Safety-critical decisions? | Yes | Relief design is safety-critical. Strict validation of the sizing script and accountable engineering review are mandatory. |
| Regulatory / legal requirements? | Yes | Pressure equipment regulations (e.g. PED) and local statutory approvals may apply depending on jurisdiction. |
| Significant engineering judgement from AI? | Yes | Scenario credibility involves judgement. AI proposes; the engineer decides. Sizing itself is rule-based. |

**Overall complexity:** High. Suitable as an assistant with strong governance; sizing script requires formal validation and version control.

## Q7 Benefits of the proposed solution

| Benefit category | Applies | Measurable statement |
| --- | --- | --- |
| Cost reduction | No | Secondary; avoided late changes are real but hard to quantify. |
| Increased productivity | Yes | Reduce effort per PSV from ~14 h to ~8 h. |
| Reduced engineering rework | Yes | Fewer scenarios discovered late in HAZOP; target 50% reduction in post-HAZOP PSV re-sizing. |
| Improved quality | Yes | Primary: systematic and traceable scenario coverage for every protected system; consistent method across engineers. |
| Improved customer satisfaction | No | Indirect via fewer client review comments. |

## Q8 Project types / phases that benefit

| Phase | Applies | Rationale |
| --- | --- | --- |
| Bidding | No | Relief design not performed at bidding. |
| PDP | No | Only preliminary flare load estimates; scenario-level work not yet done. |
| BEP | Yes | Preliminary scenario identification and flare load estimate. |
| FEED | Yes | Main application – scenario register and preliminary sizing. |
| Detail Engineering | Yes | Main application – final sizing, datasheets, post-HAZOP updates. |

## Q9 Number of projects where the solution can be used

- Applicable to all FEED and Detail Engineering projects – approx. 8–10 per year
- Typical 30–100 PSVs per project (basis: recent projects); assume 50 for the calculation

## Q10 Typical saving per project / annual cost saving

**Calculation:**

- Current: ~14 h per PSV (scenarios 4 h + sizing 4 h + datasheet 2 h + revisions 4 h)
- Future: ~8 h per PSV (scenario confirmation, input verification, review)
- Saving: 6 h × 50 PSVs × 8 projects/year = approx. 2,400 engineering hours per year
- Monetary: 2,400 h × €80/h (placeholder – replace with internal blended engineering rate) ≈ €190,000 per year; approx. €24,000 per project
- Not quantified: avoided late HAZOP-driven re-work and flare system re-evaluation

**Assumptions:**

- Sizing script validated against hand calculations and vendor sizing software before use; two-phase cases remain manual
- Intelligent P&ID data or equivalent tag/topology export available; otherwise scenario proposal is limited to checklist support
- Hours based on engineer estimates; confirm on pilot project

---

# Submission C: Automated Consistency Check of P&IDs Against Line List and Datasheets

*Working-step focus: P&ID development – inter-discipline and process check of P&IDs before IFD/IFC*

## Q1–Q4 Identification

**1. Name:** [Optional – enter name if you wish to participate in implementation]

**2. Process Technology team:** [Select team – e.g. Process Engineering / Process Design]

**3. Title of proposed AI use case:** Automated Consistency Check of P&IDs Against Line List and Datasheets

**4. Working step(s) addressed:**

- Process check of P&IDs at each issue (IFR, IFD, IFC)
- Cross-check of P&ID tags/attributes against line list, equipment list, PDS and IPDS
- Check of P&ID content against company legend and P&ID development rules (vents, drains, isolation, spec breaks)

## Q5 Describe the proposed AI solution

**Current situation:** Engineers manually compare each P&ID with the line list, equipment list, process and instrument datasheets, checking line numbers, sizes, spec breaks, insulation codes, tag numbers and design conditions. Legend-rule compliance (drains, vents, isolation, PSV arrangements) is checked from experience. Comments are red-lined and returned to CAD.

**Pain point:** 100–200 P&IDs per project with 3 or more review cycles; manual checking is tedious and coverage is incomplete under schedule pressure. Inconsistencies found after IFC lead to field changes, vendor re-issues and client comments. Typical effort is 4–5 h per P&ID per review cycle.

**Proposed AI support:** An AI tool extracts tags and attributes from the intelligent P&ID export (or OCR of PDF drawings), cross-references them to the line list, equipment list and datasheets, applies configurable legend rules, and produces a discrepancy report per drawing (missing or duplicate tags, size/spec mismatches, missing vents/drains/isolation, design-condition conflicts). The engineer reviews the report, decides on each item and red-lines accordingly.

**Inputs → AI task → Output → Engineer role:**

- Inputs: P&ID data export (or PDF), line list, equipment list, PDS/IPDS, company legend and P&ID rules
- AI task: extract → compare → apply rule checks → classify discrepancies
- Output: discrepancy report per P&ID with severity and source references
- Engineer: reviews items, confirms or rejects, red-lines drawing; final check responsibility unchanged

## Q6 How complicated is the implementation?

| Assessment factor | Yes/No | Rationale |
| --- | --- | --- |
| Do results need to be checked? | Yes | Report supports a deliverable review; false positives must be filtered by the engineer. |
| Multiple rules and standards? | Yes | Company P&ID legend and development rules, ISA 5.1, client specifications. |
| Large / complex data analysis? | Yes | Many drawings in mixed formats; OCR of non-intelligent PDFs is the main technical challenge. |
| Safety-critical decisions? | No | Supports safety review but does not make safety decisions. |
| Regulatory / legal requirements? | No | No direct external compliance effect. |
| Significant engineering judgement from AI? | No | Comparison and rule-checking; judgement stays with the engineer. |

**Overall complexity:** Medium. Low complexity with intelligent P&IDs; higher with scanned/PDF drawings.

## Q7 Benefits of the proposed solution

| Benefit category | Applies | Measurable statement |
| --- | --- | --- |
| Cost reduction | No | Consequence of reduced rework. |
| Increased productivity | Yes | Reduce check effort from ~4.5 h to ~2 h per P&ID per cycle. |
| Reduced engineering rework | Yes | Primary: inconsistencies found before IFC instead of at site; target 50% fewer post-IFC P&ID revisions. |
| Improved quality | Yes | 100% tag-level check coverage every cycle instead of sampling. |
| Improved customer satisfaction | Yes | Fewer client review comments on P&ID consistency. |

## Q8 Project types / phases that benefit

| Phase | Applies | Rationale |
| --- | --- | --- |
| Bidding | No | P&IDs not developed in detail. |
| PDP | Partly | Preliminary P&IDs – limited value. |
| BEP | Yes | First formal P&ID issue and check. |
| FEED | Yes | IFD check cycles. |
| Detail Engineering | Yes | Main application – IFD/IFC cycles and vendor P&ID integration. |

## Q9 Number of projects where the solution can be used

- Used on all engineering projects – approx. 12–15 per year
- Typical 100 P&IDs per project with 3 process check cycles (basis: recent projects)

## Q10 Typical saving per project / annual cost saving

**Calculation:**

- Current: ~4.5 h per P&ID per cycle; Future: ~2 h
- Saving: 2.5 h × 100 P&IDs × 3 cycles × 12 projects/year = approx. 9,000 engineering hours per year
- Monetary: 9,000 h × €80/h (placeholder – replace with internal blended engineering rate) ≈ €720,000 per year; approx. €60,000 per project
- Not quantified: avoided field change orders from post-IFC inconsistencies

**Assumptions:**

- Majority of projects use an intelligent P&ID tool with database export; PDF-only projects yield lower savings
- Legend rules encoded once and maintained by the P&ID focal point
- Hours are order-of-magnitude estimates; confirm on pilot project

---

# Submission D: Automated Generation of Pre-Commissioning Check Sheets and Test Packs from P&IDs

*Working-step focus: Systems completion – system definition, test pack and ITR preparation*

## Q1–Q4 Identification

**1. Name:** [Optional – enter name if you wish to participate in implementation]

**2. Process Technology team:** [Select team – e.g. Process Engineering / Process Design]

**3. Title of proposed AI use case:** Automated Generation of Pre-Commissioning Check Sheets and Test Packs from P&IDs

**4. Working step(s) addressed:**

- Systemization of P&IDs into commissioning systems / subsystems
- Preparation of pressure test packs (line list per pack, test pressure, blind and isolation lists)
- Preparation of inspection and test records (ITRs / check sheets) per tag
- Drafting of flushing, blowing and leak test procedures

## Q5 Describe the proposed AI solution

**Current situation:** Commissioning and process engineers manually mark up P&IDs with system boundaries, list every line, equipment item and instrument within each test pack, determine test pressures from the piping class, and populate Excel or completions-database check sheets. Work is largely done at site under schedule pressure.

**Pain point:** Highly repetitive listing and form-filling; boundaries and instruments are missed, producing punch items and re-tests; test pressures are transcribed manually from piping classes. Typical effort is 7–9 h per test pack plus 15–30 min per ITR.

**Proposed AI support:** An AI tool takes the systemized P&ID tag data, line list and piping-class test rules and generates the test pack content (line list per pack, test medium and pressure per ASME B31.3 and project spec, blind and instrument isolation lists), pre-filled ITRs per tag type, and a draft flushing/leak test procedure from the standard template. The commissioning engineer verifies boundaries, test pressures and isolation points before issue.

**Inputs → AI task → Output → Engineer role:**

- Inputs: P&ID export with system codes, line list, piping class specification, ITR templates, project commissioning procedures
- AI task: group by system → derive test parameters → populate test packs and ITRs → draft procedures
- Output: test pack dossier (Excel/PDF), ITR set, draft procedure
- Engineer: verifies boundaries, test pressure, isolation/blind list; approves for issue

## Q6 How complicated is the implementation?

| Assessment factor | Yes/No | Rationale |
| --- | --- | --- |
| Do results need to be checked? | Yes | Test pressures and isolation lists affect site safety; verification before issue mandatory. |
| Multiple rules and standards? | Yes | ASME B31.3 / B31.1 test requirements, piping class specs, client completions procedures. |
| Large / complex data analysis? | No | Moderate – structured tag data; volume high but format uniform. |
| Safety-critical decisions? | Yes | Pressure test pressure and isolation are safety-relevant; AI derives from rules, engineer confirms. |
| Regulatory / legal requirements? | Partly | Statutory pressure test witnessing requirements in some jurisdictions. |
| Significant engineering judgement from AI? | No | Rule application and form population; system boundary decisions remain with the engineer. |

**Overall complexity:** Medium. Rule-based generation with mandatory verification; depends on quality of systemized tag data.

## Q7 Benefits of the proposed solution

| Benefit category | Applies | Measurable statement |
| --- | --- | --- |
| Cost reduction | Yes | Reduced site engineering hours and fewer re-tests; earlier mechanical completion. |
| Increased productivity | Yes | Primary: reduce effort per test pack from ~8 h to ~3 h; ITR pre-fill removes most manual entry. |
| Reduced engineering rework | Yes | Fewer missed items and re-tests; target 30% reduction in pre-commissioning punch items related to documentation. |
| Improved quality | Yes | Complete and consistent test pack content traceable to P&ID and line list. |
| Improved customer satisfaction | Yes | Faster hand-over documentation and shorter pre-commissioning schedule. |

## Q8 Project types / phases that benefit

| Phase | Applies | Rationale |
| --- | --- | --- |
| Bidding | No | Not applicable. |
| PDP | No | Not applicable. |
| BEP | No | Not applicable. |
| FEED | No | Not applicable. |
| Detail Engineering | Yes | Late Detail Engineering (systemization) through construction and pre-commissioning on EPC/EPCM projects. |

## Q9 Number of projects where the solution can be used

- Applicable to EPC / EPCM and commissioning-support projects – approx. 4–6 per year
- Typical 100–300 test packs and 2,000–5,000 ITRs per project; assume 150 packs and 3,000 ITRs

## Q10 Typical saving per project / annual cost saving

**Calculation:**

- Test packs: 5 h × 150 packs = 750 h per project
- ITRs: 15 min × 3,000 = 750 h per project
- Saving: 1,500 h × 5 projects/year = approx. 7,500 engineering hours per year
- Monetary: 7,500 h × €80/h (placeholder – replace with internal blended engineering rate) ≈ €600,000 per year; approx. €120,000 per project
- Not quantified: schedule gain from earlier mechanical completion and fewer re-tests

**Assumptions:**

- P&IDs are systemized with system/subsystem codes in the tag database
- Piping class test rules available in structured form
- Site hours may be charged at higher rates than the placeholder; savings are conservative
