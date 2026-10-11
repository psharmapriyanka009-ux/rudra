# Engineering Training Guide & Conceptual Notes: Day 2
## Task 3: Requirements Decomposition Framework & Task 4: Bidirectional Traceability Matrix

**Project Context:** RudraEdge Aerospace — RE-T1 (Spectra) / Rudra-Tactical  
**Assigned Engineer:** Priyanka Sharma (Systems Requirements & Configuration Engineer)  
**Milestone Date:** 11 October 2026 — Day 2  
**Applicable Task Order:** `REA/2026/RE-T1/TRAIN-001/ADD-03`  

---

## 1. Executive Summary & Core Objectives

In mission-critical aerospace and defense systems, software and hardware cannot be built from vague top-level concepts. Every flight function, sensor driver, communications protocol, and test procedure must be methodically decomposed and bidirectionally tracked.

This guide provides the complete **theoretical framework, practical workflows, architectural flowcharts, and technical notes** for:
1. **Task 3 (Requirements Decomposition Framework)**: Systematically breaking down high-level tactical mission goals into verifiable subsystem, functional, and derived engineering requirements.
2. **Task 4 (Bidirectional Mapping Matrix Design)**: Designing and operating a 16-column matrix that links source objectives down to code and test evidence (**Forward Traceability**), and verifies that every line of code and test case is contractually justified (**Backward Traceability**).

---

## 2. Master Architectural Flowcharts

### 2.1 Flowchart 1: 4-Level Requirements Decomposition Hierarchy
This flowchart illustrates how high-level tactical mission goals flow downward into discrete, verifiable engineering nodes across four distinct hierarchical levels:

```mermaid
flowchart TD
    subgraph LEVEL_1 ["LEVEL 1: System-Level Requirements (Operational Pillars)"]
        direction TB
        OBJ["Contractual Tactical Objectives (OBJ-01 to OBJ-07)<br/>Source: Master Proposal / Overview"]
        SYS_REQ["REQ-SYS-xxxx<br/>Platform-wide functional, environmental & safety capabilities<br/>Example: REQ-SYS-0001 (GNSS-Denied 6-DOF Localization)"]
        OBJ --> SYS_REQ
    end

    subgraph LEVEL_2 ["LEVEL 2: Subsystem-Level Requirements (Module Boundaries)"]
        direction TB
        SUB_ALLOC["Allocation to Primary Subsystem Boundaries<br/>MOD-01 to MOD-06, AVIONICS-CORE, CRYPTO-ROOT, AIRFRAME"]
        SUB_REQ["REQ-SUB-<SUB>-xxx [PROPOSED]<br/>Example: REQ-SUB-VIO-001 (Odometry Fusion Engine Allocation)"]
        SYS_REQ --> SUB_ALLOC --> SUB_REQ
    end

    subgraph LEVEL_3 ["LEVEL 3: Functional Requirements (Algorithmic Behaviors)"]
        direction TB
        FNC_LOGIC["Subsystem Functional Logic, Math Models & Rates"]
        FNC_REQ["REQ-FNC-<SUB>-xxx [PROPOSED]<br/>Example: REQ-FNC-VIO-001 (Visual Feature Point Tracking >= 30 Hz)"]
        SUB_REQ --> FNC_LOGIC --> FNC_REQ
    end

    subgraph LEVEL_4 ["LEVEL 4: Detailed / Derived Requirements (Leaf Interfaces)"]
        direction TB
        DER_SPECS["Physical Pinning, Bus Protocols, Timing Deadlines, Memory Buffers"]
        DER_REQ["REQ-DER-<TYPE>-xxx [PROPOSED]<br/>Example: REQ-DER-INT-001 (Micro-XRCE-DDS Odometry Topic at 50 Hz)<br/>Example: REQ-DER-TIM-003 (Inner Attitude Loop Latency < 1.0 ms)"]
        FNC_REQ --> DER_SPECS --> DER_REQ
    end

    classDef l1 fill:#1e293b,stroke:#38bdf8,stroke-width:2px,color:#fff;
    classDef l2 fill:#0f172a,stroke:#818cf8,stroke-width:2px,color:#fff;
    classDef l3 fill:#1e1e38,stroke:#a78bfa,stroke-width:2px,color:#fff;
    classDef l4 fill:#172554,stroke:#38bdf8,stroke-width:2px,color:#fff;

    class OBJ,SYS_REQ l1;
    class SUB_ALLOC,SUB_REQ l2;
    class FNC_LOGIC,FNC_REQ l3;
    class DER_SPECS,DER_REQ l4;
```

---

### 2.2 Flowchart 2: End-to-End Bidirectional Traceability Loop
This flowchart maps the complete bidirectional loop: Forward Traceability ensuring objective fulfillment, and Backward Traceability ensuring contractual justification:

```mermaid
flowchart LR
    subgraph FORWARD_CHAIN ["FORWARD TRACEABILITY (Objective Fulfillment)"]
        direction LR
        S["Source Goal / Contract<br/>(OBJ-xx)"] --> L1["System Requirement<br/>(REQ-SYS-xxxx)"]
        L1 --> L2["Subsystem Allocation<br/>(REQ-SUB-xxxx)"]
        L2 --> L3["Functional Requirement<br/>(REQ-FNC-xxxx)"]
        L3 --> L4["Interface / Leaf Req<br/>(REQ-DER-xxxx)"]
        L4 --> IMP["Implementation Artifact<br/>(src/ , firmware/ , hardware/)"]
        IMP --> VM["Verification Method<br/>(Inspection / Analysis / Test)"]
        VM --> TC["Test Case ID<br/>(TC-xxxx)"]
        TC --> EV["Verification Evidence<br/>(Test Logs / Reports)"]
    end

    subgraph BACKWARD_CHAIN ["BACKWARD TRACEABILITY (Contractual Justification)"]
        direction RL
        REV["Verified Test Logs<br/>(Audit Sign-Off)"] --> RTC["Test Case Procedure<br/>(Test Justification)"]
        RTC --> RVM["Verification Method<br/>(Method Audit)"]
        RVM --> RIMP["Source Code / Schematics<br/>(Code Justification)"]
        RIMP --> RREQ["Functional / Derived Req<br/>(Refinement Anchor)"]
        RREQ --> RPAR["Parent Requirement<br/>(Hierarchy Ascent)"]
        RPAR --> RSRC["Contractual Objective<br/>(Authorized Scope)"]
    end

    EV -.->|"Verified by Logs"| REV
    RSRC -.->|"Originates"| S

    classDef fwd fill:#064e3b,stroke:#34d399,stroke-width:2px,color:#fff;
    classDef bwd fill:#451a03,stroke:#fb923c,stroke-width:2px,color:#fff;

    class S,L1,L2,L3,L4,IMP,VM,TC,EV fwd;
    class REV,RTC,RVM,RIMP,RREQ,RPAR,RSRC bwd;
```

---

### 2.3 Flowchart 3: Traceability Gap & Anomaly Detection Logic
This flowchart illustrates the decision rules used by a Configuration Engineer to detect orphans, unallocated requirements, rogue code, and unverified links:

```mermaid
flowchart TD
    START(["Audit Requirement / Artifact"]) --> Q1{"Is Requirement Level 1?"}
    
    Q1 -- Yes --> Q2{"Does it link to an<br/>authorized Source / OBJ?"}
    Q2 -- No --> ANOM_NO_SRC["ANOMALY: Requirement Without Source<br/>Flag as Ungrounded Scope Addition"]
    Q2 -- Yes --> Q3{"Is Subsystem Allocated?"}
    
    Q1 -- No --> Q4{"Does Parent Req ID exist<br/>and link to valid Parent?"}
    Q4 -- No --> ANOM_ORPHAN["ANOMALY: Orphan Requirement<br/>Flag: Missing Upstream Authority"]
    Q4 -- Self --> ANOM_CIRC["ANOMALY: Circular Self-Parenting<br/>Flag: Parent ID == Requirement ID"]
    Q4 -- Yes --> Q3
    
    Q3 -- No --> ANOM_UNALLOC["ANOMALY: Unallocated Requirement<br/>Flag: No Engineering Module Owner"]
    Q3 -- Yes --> Q5{"Does Implementation<br/>Artifact path exist?"}
    
    Q5 -- No --> GAP_FWD_IMPL["FORWARD GAP: Unimplemented<br/>Status: PARTIAL / TBD"]
    Q5 -- Yes --> Q6{"Is Verification Method<br/>& Test Case assigned?"}
    
    Q6 -- No --> GAP_FWD_VER["FORWARD GAP: Unverified Requirement<br/>Status: PARTIAL / TBD"]
    Q6 -- Yes --> Q7{"Has Physical / Simulation<br/>Test been executed?"}
    
    Q7 -- No --> VALID_STARTER["VALID STARTER BASELINE<br/>Traceability Status: PARTIAL<br/>Evidence: NOT ESTABLISHED"]
    Q7 -- Yes --> FULLY_VERIFIED["MILESTONE COMPLETE<br/>Traceability Status: COMPLETE<br/>Evidence: Log File Linked"]

    classDef anom fill:#7f1d1d,stroke:#f87171,stroke-width:2px,color:#fff;
    classDef gap fill:#78350f,stroke:#fbbf24,stroke-width:2px,color:#fff;
    classDef ok fill:#064e3b,stroke:#34d399,stroke-width:2px,color:#fff;

    class ANOM_NO_SRC,ANOM_ORPHAN,ANOM_CIRC,ANOM_UNALLOC anom;
    class GAP_FWD_IMPL,GAP_FWD_VER gap;
    class VALID_STARTER,FULLY_VERIFIED ok;
```

---

### 2.4 Flowchart 4: Engineering Change Impact Assessment Flow
This flowchart shows the workflow when a requirement modification or deletion is requested:

```mermaid
flowchart TD
    CR(["Engineering Change Request (ECR) Initiated"]) --> IDENT["Identify Target Requirement ID (Col 4)"]
    IDENT --> UPSTREAM["Traverse Upstream via Parent Req ID (Col 3)<br/>Evaluate Impact on High-Level Objectives"]
    IDENT --> DOWNSTREAM["Traverse Downstream (Search Col 3 for this Req ID)<br/>Identify all Child Functional & Interface Reqs"]
    
    DOWNSTREAM --> IMPACT_CODE["Audit Implementation Artifacts (Col 9)<br/>Identify Source Files, Firmware, CAD to Modify"]
    DOWNSTREAM --> IMPACT_TEST["Audit Test Cases & Verification Evidence (Col 11 & 12)<br/>Flag impacted Test Procedures for Re-execution"]
    
    UPSTREAM & IMPACT_CODE & IMPACT_TEST --> SAFETY_CHECK{"Does change affect<br/>Bare-Metal Flight Safety<br/>or Security Boundaries?"}
    
    SAFETY_CHECK -- Yes --> HIGH_RISK["HIGH RISK DESIGNATION<br/>Mandatory Airworthiness Review Gate"]
    SAFETY_CHECK -- No --> STD_REVIEW["STANDARD DESIGNATION<br/>Configuration Control Board (CCB) Review"]
    
    HIGH_RISK & STD_REVIEW --> CCB_DECISION{"CCB Decision"}
    CCB_DECISION -- Approved --> UPDATE_MATRIX["Increment Revision (Rev A -> Rev B)<br/>Update Traceability Matrix<br/>Re-baseline Rows"]
    CCB_DECISION -- Rejected --> ARCHIVE["Archive ECR with Justification"]

    classDef proc fill:#1e293b,stroke:#38bdf8,stroke-width:2px,color:#fff;
    classDef decision fill:#0f172a,stroke:#a855f7,stroke-width:2px,color:#fff;
    classDef crit fill:#7f1d1d,stroke:#ef4444,stroke-width:2px,color:#fff;
    classDef app fill:#064e3b,stroke:#22c55e,stroke-width:2px,color:#fff;

    class CR,IDENT,UPSTREAM,DOWNSTREAM,IMPACT_CODE,IMPACT_TEST,UPDATE_MATRIX,ARCHIVE proc;
    class SAFETY_CHECK,CCB_DECISION decision;
    class HIGH_RISK crit;
    class STD_REVIEW,UPDATE_MATRIX app;
```

---

## 3. Deep-Dive Notes: Task 3 (Requirements Decomposition Framework)

### 3.1 Why Requirements Decomposition is Mandatory
In advanced tactical aerospace projects, high-level mission goals like *"Achieve continuous drift-bounded flight in satellite-jammed airspace"* cannot be directly coded or tested on a benchtop. 
* A flight software engineer cannot write C++ code for *"GNSS-Denied Flight"*.
* An embedded systems engineer cannot solder a bus harness for *"Indian IP Sovereignty"*.

**Requirements Decomposition** is the systematic process of breaking down high-level, multi-disciplinary operational goals into discrete, single-discipline, verifiable engineering specifications.

### 3.2 The 4-Level Requirement Hierarchy Explained

| Level | Formal Name | Scope and Engineering Definition | Typical Owner | Example Identifier |
| :---: | :--- | :--- | :--- | :--- |
| **Level 1** | **System-Level Requirements** | Defines platform-wide operational capabilities, environmental tolerances, airworthiness firewalls, and defense mission objectives. Direct children of contractual objectives (`OBJ-01` to `OBJ-07`). | Chief Systems Engineer / Aerospace Architect | `REQ-SYS-0001`<br/>`REQ-SYS-0013` |
| **Level 2** | **Subsystem-Level Requirements** | Allocates functional boundaries to a single physical module (`MOD-01` to `MOD-06`, `AVIONICS-CORE`, `CRYPTO-ROOT`, etc.). Specifies subsystem responsibilities without dictating internal algorithms. | Subsystem Lead / Hardware Architect | `REQ-SUB-VIO-001`<br/>`REQ-SUB-AVI-001` |
| **Level 3** | **Functional Requirements** | Specifies discrete internal behaviors, algorithmic models, sampling frequencies, mathematical filters, and data transformations executed by a subsystem. | Algorithm Lead / Firmware Engineer | `REQ-FNC-VIO-001`<br/>`REQ-FNC-AVI-001` |
| **Level 4** | **Detailed / Derived Requirements** | Leaf requirements detailing electrical interfaces, software transport protocols, memory sharing structures, timing deadlines, and hardware safety interlocks. | Driver Developer / Mechatronics Engineer | `REQ-DER-INT-001`<br/>`REQ-DER-TIM-003` |

### 3.3 The 17-Field Requirement Node Anatomy
Each requirement node in the SRS must contain 17 explicit fields to prevent ambiguity and ensure auditability:
1. **Requirement ID**: Permanent unique string (e.g., `REQ-SYS-0001`).
2. **Requirement Title**: Short descriptive title.
3. **Requirement Statement**: Strict normative engineering language using *shall* (never *should*, *could*, or *may*).
4. **Requirement Level**: Explicit tag (`Level 1`, `Level 2`, `Level 3`, `Level 4`).
5. **Parent Requirement ID**: Direct parent node ID. Prohibited from being empty (unless L1) or self-referencing.
6. **Source / Origin**: Formal document identifier, section, and page number.
7. **Requirement Type**: Classification (Functional, Performance, Interface, Safety, Security, etc.).
8. **Allocated Subsystem**: Physical module ownership (`MOD-01`, `MOD-02`, etc.).
9. **Rationale**: Technical explanation of *why* the requirement exists.
10. **Verification Method**: One of four formal engineering methods:
    * **Inspection (I)**: Visual audit of drawings, wiring, or code.
    * **Analysis (A)**: Calculations, simulation, link budgets.
    * **Demonstration (D)**: Qualitative verification without calibrated instruments.
    * **Test (T)**: Quantitative evaluation against measurable tolerances using calibrated instruments.
11. **Verification Status**: `UNEXECUTED`, `AWAITING TESTBENCH`, `PASSED`, `FAILED`. (Never claim passed without data).
12. **Child Requirement IDs**: List of immediate child IDs or `None (Leaf Node)`.
13. **Upstream Traceability**: Path ascending to the top-level mission objective.
14. **Downstream Traceability**: Path descending to leaf interfaces and validation tiers.
15. **Configuration / Baseline Status**: `DRAFT`, `PROPOSED`, `UNDER REVIEW`, `APPROVED`, `BASELINED`.
16. **Assumptions or Constraints**: Operating boundaries, sensor limits, environmental boundaries.
17. **Open Issues / TBD Items**: Tracking unconfirmed parameters (e.g., `ISSUE-REQ-001`).

### 3.4 Decomposition Integrity & Orphan Handling Rules
* **Rule 1: No Unlinked Children**: Every Level 2, 3, and 4 requirement must possess an explicit parent link.
* **Rule 2: Orphan Detection**: Any requirement lacking a confirmed parent is flagged `ORPHAN REQUIREMENT`. Orphans indicate unauthorized scope expansion ("gold-plating") or missing higher-level requirements.
* **Rule 3: Childless Parent Detection**: High-level requirements without decomposed children are flagged `CHILDLESS PARENT`. In Milestone 1, they must either be decomposed or justified as `ATOMIC / DIRECT VERIFICATION`.
* **Rule 4: Scope Preservation**: Decomposed children must never add unapproved capabilities that exceed the parent requirement's scope.

---

## 4. Deep-Dive Notes: Task 4 (Bidirectional Mapping Matrix Design)

### 4.1 Forward vs. Backward Traceability
Bidirectional traceability requires traversing the engineering data model in both directions:

```
[FORWARD TRACEABILITY: Objective-Driven]
Contract Objective  -->  System Req  -->  Subsystem  -->  Functional  -->  Interface  -->  Code/HW  -->  Test Case  -->  Evidence Log
"Did we build EVERYTHING that the tactical customer paid for?"

[BACKWARD TRACEABILITY: Justification-Driven]
Evidence Log  -->  Test Case  -->  Method  -->  Code/HW  -->  Interface  -->  Functional  -->  Subsystem  -->  System Req  -->  Contract Objective
"Is EVERY line of code and test case CONTRACTUALLY JUSTIFIED, or did someone introduce rogue features?"
```

### 4.2 The 16-Column Matrix Schema Explained

| Col # | Column Name | Engineering Function & Audit Question | Standard Permitted Values |
| :---: | :--- | :--- | :--- |
| **1** | **Source Reference** | What document authorizes this requirement? | Document ID + Section + Page (e.g., `REA-T1-OVERVIEW-2026-V1.0, Sec 2`) |
| **2** | **Source Requirement ID** | What top-level tactical goal originated this? | `OBJ-01` to `OBJ-07` or Proposal ID |
| **3** | **Parent Requirement ID** | What is the immediate upstream parent node? | `N/A — Top-Level Requirement` (L1) or Parent Req ID |
| **4** | **Requirement ID** | What is this requirement's unique identity? | `REQ-SYS-xxxx`, `REQ-SUB-xxxx`, `REQ-FNC-xxxx`, `REQ-DER-xxxx` |
| **5** | **Requirement Title** | What is the concise name of this requirement? | Standard Title String |
| **6** | **Requirement Level** | Where does this node sit in the hierarchy? | `Level 1`, `Level 2`, `Level 3`, `Level 4` |
| **7** | **Requirement Type** | What engineering discipline governs this? | `Functional`, `Performance`, `Interface`, `Safety`, `Security`, etc. |
| **8** | **Allocated Subsystem** | Which physical team or module owns this? | `MOD-01` to `MOD-06`, `AVIONICS-CORE`, `CRYPTO-ROOT`, etc. |
| **9** | **Implementation Reference** | Where does this requirement exist in physical files? | File path (`src/`, `firmware/`, `cad/`) or `TBD (Pre-Implementation)` |
| **10** | **Verification Method** | How will compliance be formally proven? | `Inspection`, `Analysis`, `Demonstration`, `Test` |
| **11** | **Test Case ID** | Which test procedure validates this requirement? | Formal Test ID (e.g., `TC-NAV-001`) or `TBD (Awaiting Testbench)` |
| **12** | **Verification Evidence** | Where are the signed, executed test logs stored? | File link / URI or `NOT ESTABLISHED (Unexecuted)` |
| **13** | **Forward Traceability Status** | Are all forward links down to test logs complete? | `COMPLETE`, `PARTIAL`, `GAP`, `NOT ASSESSED` |
| **14** | **Backward Traceability Status** | Does this link cleanly back to contractual source? | `COMPLETE`, `PARTIAL`, `GAP`, `NOT ASSESSED` |
| **15** | **Configuration / Baseline Status** | What is the change-control baseline state? | `DRAFT`, `PROPOSED`, `UNDER REVIEW`, `APPROVED`, `BASELINED` |
| **16** | **Open Issues / Remarks** | What parameters are unstated or under investigation?| Reference to Open Issues Register (`ISSUE-REQ-xxx`) |

### 4.3 Standard Status Dictionary
* **`COMPLETE`**: Every link in the chain is established and supported by empirical evidence.
* **`PARTIAL`**: Upstream and architectural links exist, but downstream implementation or verification evidence is pending execution (`TBD`).
* **`GAP`**: A required relationship is missing, broken, or unallocated.
* **`NOT ASSESSED`**: The row has not yet undergone formal configuration engineering review.

### 4.4 The 10 Traceability Anomalies Every Systems Engineer Must Detect

```
+-----------------------------------+-----------------------------------+-----------------------------------+
| ANOMALY TYPE                      | DETECTION SIGNATURE IN MATRIX     | ENGINEERING SEVERITY & REMEDY     |
+-----------------------------------+-----------------------------------+-----------------------------------+
| 1. Requirement Without Source     | Col 1 or Col 2 is empty / TBD     | CRITICAL: Unsubstantiated scope.  |
|                                   |                                   | Action: Solicit customer CR or drop.|
+-----------------------------------+-----------------------------------+-----------------------------------+
| 2. Orphan Requirement             | Col 3 is empty on Level 2/3/4     | CRITICAL: Disconnected child node.|
|                                   |                                   | Action: Trace to parent or reject.|
+-----------------------------------+-----------------------------------+-----------------------------------+
| 3. Circular Self-Parenting        | Col 3 == Col 4 (Parent == Req ID) | HIGH: Breaks decomposition tree.  |
|                                   |                                   | Action: Point to true upstream ID.|
+-----------------------------------+-----------------------------------+-----------------------------------+
| 4. Unallocated Requirement        | Col 8 (Allocated Subsystem) empty | HIGH: No engineering module owner.|
|                                   |                                   | Action: Assign physical subsystem.|
+-----------------------------------+-----------------------------------+-----------------------------------+
| 5. Unimplemented Requirement      | Col 9 (Implementation Ref) empty  | MEDIUM: Code omission risk.       |
|                                   |                                   | Action: Assign src/firmware path. |
+-----------------------------------+-----------------------------------+-----------------------------------+
| 6. Unverified Requirement         | Col 10 (Verification Method) empty| HIGH: Cannot certify for flight.  |
|                                   |                                   | Action: Define method & criteria. |
+-----------------------------------+-----------------------------------+-----------------------------------+
| 7. Missing Test Case              | Col 11 empty where Method is Test | MEDIUM: Testbench cannot execute. |
|                                   |                                   | Action: Author formal test script.|
+-----------------------------------+-----------------------------------+-----------------------------------+
| 8. Rogue Implementation           | Source code exists with no Req ID | CRITICAL: Gold-plating / defects. |
|                                   |                                   | Action: Delete code or draft ECR. |
+-----------------------------------+-----------------------------------+-----------------------------------+
| 9. Orphan Test Case               | Test script exists with no Req ID | MEDIUM: Wasted testbench runtime. |
|                                   |                                   | Action: Map to req or retire test.|
+-----------------------------------+-----------------------------------+-----------------------------------+
| 10. Broken Traceability Chain     | Forward or Backward marked GAP    | HIGH: Audit failure / blind spot. |
|                                   |                                   | Action: Re-link missing hierarchy.|
+-----------------------------------+-----------------------------------+-----------------------------------+
```

---

## 5. Summary of Deliverable Files in Day 2 Workspace

| File Name | Location | Primary Contents |
| :--- | :--- | :--- |
| **`Day2_Task3_Task4_Training_Notes_and_Flowcharts.md`** *(This File)* | `C:\Users\Admin\OneDrive\Desktop\Day2\` | Master engineering notes, 4 architectural flowcharts (Mermaid), 10 anomaly rules, and theoretical guides. |
| **`SRS_Starter_Template_Day2_2026-10-11.md`** | `C:\Users\Admin\OneDrive\Desktop\Day2\` and `docs/` | Complete 17-section SRS Starter Template with 17-field tracking nodes, 40-row parent-child register, and embedded 16-column matrix. |
| **`Bidirectional_Traceability_Wireframe_Day2_2026-10-11.md`** | `C:\Users\Admin\OneDrive\Desktop\Day2\` and `docs/` | Standalone 16-column Bidirectional Traceability Wireframe with 40 starter rows, traversal walkthroughs, and gap rules. |
| **`README.md`** | `C:\Users\Admin\OneDrive\Desktop\Day2\` | Workspace index and directory navigation summary. |

---

## 6. Engineering Integrity Statement
All flowcharts, notes, and schemas in this document reflect verified systems engineering methodologies and project records from `REA-T1-OVERVIEW-2026-V1.0`. All placeholder implementation references and test cases remain marked `TBD` / `NOT ESTABLISHED` in strict compliance with the zero-fabrication and local-only engineering mandate.
