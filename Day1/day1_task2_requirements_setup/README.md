# Day 1, Task 2: System Requirements Structure Setup
## Project RE-T1 (Spectra) / Rudra-Tactical
**Organization:** RudraEdge Aerospace (Incubated at TIDES, IIT Roorkee)  
**Cadre:** Priyanka Sharma, Systems Requirements & Configuration Engineer  
**Date:** 10 October 2026  
**Status:** DRAFT FOR REVIEW  
**Task Order Reference:** `REA/2026/RE-T1/TRAIN-001/ADD-03`  

---

## 1. Directory Purpose & Overview

This directory (`day1_task2_requirements_setup/`) contains the formal System Requirements Specification (SRS) engineering foundation established for the **RudraEdge RE-T1 (Spectra)** autonomous tactical UAV platform. 

The deliverables herein translate high-level operational concepts, architectural layers, and defense capability commitments from authoritative project documents (`REA-T1-OVERVIEW-2026-V1.0` and `REA-T1-ARCH-STUDY-2026-V1.0`) into discrete, structured, traceable, and review-ready engineering requirements. All deliverables adhere to the strict zero-cost compliance mandate (INR 0 personal expenditure) using standard, local open-format Markdown and CSV schemas.

---

## 2. Directory Contents & File Purpose

The directory contains five core engineering artifacts and this orientation file:

| Filename | Format | Engineering Purpose | Current Status |
| :--- | :---: | :--- | :--- |
| **`RE_T1_SYSTEM_REQUIREMENTS_SPECIFICATION.md`** | Markdown | Primary System Requirements Specification document organized into 14 formal sections. Establishes the functional, interface, performance, environmental, safety, security, and configuration requirements for Milestone 1. Defines systems engineering distinctions and proposed CCB workflows. | **DRAFT FOR REVIEW** |
| **`RE_T1_REQUIREMENTS_REGISTER.csv`** | CSV | Consolidated engineering database capturing 25 verified requirements across 16 standardized attribute columns (`Requirement_ID`, `Requirement_Title`, `Statement`, `Type`, `Source`, `Node`, `Rationale`, `Verification_Method`, `Criteria`, `Priority`, `Status`, etc.). | **PROVISIONAL (DRAFT)** |
| **`RE_T1_REQUIREMENTS_TRACEABILITY.csv`** | CSV | Bidirectional Traceability Matrix linking requirements to source documents, source pages/sections, parent features, architectural nodes, interface vectors, verification techniques, and open issues. | **INITIAL BASELINE** |
| **`RE_T1_REQUIREMENT_VERIFICATION_TEMPLATE.csv`** | CSV | Standardized verification test case schema containing 14 operational fields (`Test_Case_ID`, `Objective`, `Method`, `Preconditions`, `Inputs`, `Procedure`, `Expected_Result`, `Actual_Result`, `Evidence_Location`, etc.) populated with 5 illustrative sample records. | **TEMPLATE (WITH SAMPLE RECORDS)** |
| **`RE_T1_REQUIREMENTS_ISSUES.csv`** | CSV | Quality audit register cataloging 15 identified requirement defects, unquantified thresholds, missing numerical boundaries, and critical safety hazards discovered during analysis. | **OPEN DEFECT LEDGER** |
| **`README.md`** | Markdown | Directory documentation explaining file roles, inter-relationships, configuration status, and outstanding engineering tasks. | **ACTIVE REFERENCE** |

---

## 3. Inter-Relationship Between Deliverables

The deliverables in this package form an integrated, traceable engineering ecosystem:

```
[REA-T1-OVERVIEW-2026-V1.0] ──> Source Document of Truth
         │
         ▼
[RE_T1_SYSTEM_REQUIREMENTS_SPECIFICATION.md] ◄── Formal Narrative Specification
         │
         ├───► [RE_T1_REQUIREMENTS_REGISTER.csv] ◄── Tabular Requirements Master
         │             │
         │             ├───► [RE_T1_REQUIREMENTS_TRACEABILITY.csv] ◄── Node & Source Matrix
         │             │               │
         │             │               └───► [day1_task1_architecture_study/
         │             │                      TECHNICAL_NODE_REGISTER.csv]
         │             │
         │             └───► [RE_T1_REQUIREMENT_VERIFICATION_TEMPLATE.csv] ◄── Test Execution
         │
         └───► [RE_T1_REQUIREMENTS_ISSUES.csv] ◄── Gaps & Clarification Register
                       │
                       └───► [day1_task1_architecture_study/
                              RE_T1_ARCHITECTURE_OPEN_QUESTIONS.csv]
```

1. **SRS Document (`.md`)** provides the narrative context, governance framework, and formal requirement statements.
2. **Requirements Register (`.csv`)** stores the machine-readable database of the 25 provisional requirements.
3. **Traceability Matrix (`.csv`)** maps every requirement back to the source pages and forward to the architectural nodes established in Task 1 (`TECHNICAL_NODE_REGISTER.csv`).
4. **Verification Template (`.csv`)** establishes the standard test protocol structure and aligns verification methods with the 10-Tier Validation Ladder.
5. **Requirements Issues Register (`.csv`)** flags vague, incomplete, or unquantified parameters, directly correlating with the open questions logged in Task 1.

---

## 4. What Has Been Completed

- **100% Extraction of Verified Requirements**: Formulated 25 discrete requirements directly from the source literature without inventing unsupported technical facts or arbitrary numerical values.
- **Traceability Established**: Bidirectionally linked all 25 requirements to parent iDEX features (Features 1, 5, 6, 7, 8, 9, 10, 11, 13, 15, 17, 19), architecture nodes (`MOD-01` to `MOD-06`, `STUDY-NODE-07` to `STUDY-NODE-20`), and interface protocols.
- **Verification Mapping**: Assigned formal verification methods (Test, Demonstration, Analysis, Inspection) aligned to the exit criteria of the 10-Tier Validation Ladder.
- **Verification Template Formulated**: Created the standardized 14-column test case template and populated it with 5 clearly marked illustrative sample cases (`SAMPLE — NOT A VERIFIED PROJECT TEST`).
- **Quality Audit Performed**: Scrutinized every requirement for verifiability and clarity, logging 15 specific issues in `RE_T1_REQUIREMENTS_ISSUES.csv`.
- **Systems Engineering Principles Documented**: Fully articulated the distinctions between functional vs. non-functional requirements, requirements vs. design decisions, verification vs. validation, draft vs. baseline, and verified vs. unverified states.

---

## 5. What Remains to Be Completed (Next Engineering Steps)

1. **Configuration Control Board (CCB) Review**: Submit this draft baseline to Project Lead Sarvesh Sharma for formal engineering review and promotional approval from `PROVISIONAL (DRAFT)` to `APPROVED BASELINE`.
2. **Clarification of Identified Gaps**: Resolve the 15 open issues in `RE_T1_REQUIREMENTS_ISSUES.csv` (specifically DEM spatial resolution, optical zoom ratios, interim compute System-on-Module model, cargo pod mass ratings, and false-positive tamper wipe prevention logic).
3. **Release of Master iDEX Capability Definitions**: Obtain itemized definitions for the remaining 8 unindexed capabilities within the frozen set of 20 to achieve complete 100% requirements coverage.
4. **Transition to Milestone 1 Testbench Setup**: Utilize these requirements to define Software-in-the-Loop (SIL) simulation scenario test cases in Gazebo and PX4.
