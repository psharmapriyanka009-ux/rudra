# RudraEdge RE-T1 (Spectra) — System Requirements Specification (SRS) Starter Template
## Requirements Decomposition Framework & Bidirectional Mapping Matrix Design

---

## 1. Document Control

### 1.1 Document Metadata
| Field | Value / Record |
| :--- | :--- |
| **Document Title** | System Requirements Specification (SRS) Starter Template & Requirements Decomposition Framework |
| **Project Identity** | Project Rudra-Tactical / Platform: RudraEdge RE-T1 (Spectra) |
| **Project Proposal Reference** | `RE-iDEX-PROPOSAL-2026-R1` (Target Framework: iDEX / DIO / MoD Evaluation Standard) |
| **Assigned Engineer** | **Priyanka Sharma** |
| **Engineering Role** | Systems Requirements & Configuration Engineer |
| **Task Order Directive** | `REA/2026/RE-T1/TRAIN-001/ADD-03` (Dated: 09 October 2026) |
| **Document Identifier** | `REA-T1-SRS-DAY2-2026-V1.0` |
| **Preparation Date** | 11 October 2026 (Day 2 Milestone Activity) |
| **Document Version** | Version 1.0 (Pre-Implementation Technical Readiness Starter Baseline) |
| **Security Classification** | Commercial-in-Confidence / Technical Specification |
| **Document Status** | **DRAFT — UNDER REVIEW** |
| **Authorizing Project Lead** | Sarvesh Sharma, Founder & Technical Lead, RudraEdge Aerospace |

### 1.2 Document Revision History
| Revision | Date | Author / Cadre | Description of Change / Scope | Approval Status |
| :--- | :--- | :--- | :--- | :--- |
| **Rev 0.1** | 10-Oct-2026 | Priyanka Sharma | Day 1 Initial SRS Baseline setup (`REA-T1-SRS-2026-V1.0`) establishing 25 system requirements and architecture mapping. | Baseline Draft |
| **Rev 1.0** | 11-Oct-2026 | Priyanka Sharma | Day 2 Task 3 & Task 4 implementation: 4-level requirements decomposition framework, 17-field tracking node structure, and 16-column bidirectional traceability wireframe. | Under Review |

### 1.3 Review and Approval Gate
| Role | Designated Reviewer | Review Date | Disposition / Signature |
| :--- | :--- | :--- | :--- |
| **Systems Requirements Engineer** | Priyanka Sharma | 11-Oct-2026 | Prepared & Submitted for Cadre Review |
| **Lead Aerospace Architect** | TBD (Nominated Senior Specialist) | PENDING | Awaiting Formal Review Gate |
| **Founder & Technical Lead** | Sarvesh Sharma | PENDING | Awaiting Milestone 1 Freeze Sign-off |

---

## 2. Purpose

This **System Requirements Specification (SRS) Starter Template** establishes the formalized engineering framework for decomposing high-level tactical system goals into verifiable subsystem, functional, and derived requirements for the **RudraEdge RE-T1 (Spectra)** autonomous tactical Unmanned Aerial Vehicle (UAV).

Commissioned under Task Order Directive `REA/2026/RE-T1/TRAIN-001/ADD-03` on Day 2 of the Pre-Implementation Technical Readiness lifecycle, this document:
1. **Fulfills Task 3 (Requirements Decomposition Framework)**: Establishes a rigorous 4-level requirements hierarchy (System $\rightarrow$ Subsystem $\rightarrow$ Functional $\rightarrow$ Derived/Detailed), defines a 17-field requirement node schema, enforces verifiability criteria, and establishes unambiguous parent-child traceability relationships.
2. **Fulfills Task 4 (Bidirectional Mapping Matrix Design)**: Constructs an end-to-end 16-column Bidirectional Traceability Wireframe linking source goals, requirements, allocated subsystems, implementation artifacts, verification methods, and test case evidence in both forward and backward directions.
3. **Guarantees Engineering Integrity**: Explicitly distinguishes between source-supported specifications and proposed items, marks missing technical data as `TBD` or `NOT YET DEFINED`, flags orphan requirements for review, and strictly enforces zero-cost, local-only engineering compliance.

---



### 2.1 Engineering Task Deliverable Quick Reference Map
| Engineering Task | Focus & Content | SRS Document Section | Implementation Status |
| :--- | :--- | :--- | :--- |
| **TASK 3: Requirements Decomposition** | • 4-Level Requirement Hierarchy (L1 System, L2 Subsystem, L3 Functional, L4 Derived)<br/>• Standardized 17-Field Requirement Tracking Node Schema<br/>• Structured Requirement Statements (*shall*) with Rationale & Verification<br/>• Parent-Child Decomposition Links & Orphan Management | **Part I (Sections 6, 7, 8)** | **FULLY IMPLEMENTED** |
| **TASK 4: Bidirectional Mapping Matrix** | • 16-Column Bidirectional Traceability Wireframe connecting Source $\rightarrow$ Parent $\rightarrow$ Req $\rightarrow$ Subsystem $\rightarrow$ Impl $\rightarrow$ Verification $\rightarrow$ Evidence<br/>• Forward & Backward Traceability Verification Procedures<br/>• Anomaly Detection Rules (Orphans, Gaps, Missing Links, Rogue Code) | **Part II (Sections 9, 10, 11, 12, 13)** | **FULLY IMPLEMENTED** |

---

## 3. Scope

### 3.1 System Boundary & Addressed Subsystems
The scope of this starter template encompasses the airborne elements, physical interfaces, compute substrates, and line-of-sight communications defining the RE-T1 platform:
* **Tactical Navigation & Pose Estimation**: Visual-Inertial Odometry (VIO), high-rate IMU integration, and Digital Elevation Model (DEM) terrain correlation (`MOD-01`).
* **Multi-Spectral Perception & Gimbal Avionics**: Stabilized daylight optical CMOS and Long-Wave Infrared (LWIR) bolometer streams (`MOD-02`).
* **Heterogeneous Edge AI Compute**: Zero-cloud onboard CPU/GPU/NPU/DSP processing fabric executing TensorRT INT8 semantic segmentation, temporal change detection, and super-resolution (`MOD-03`).
* **Electromagnetic Awareness & Acoustic Tracking**: Wideband SDR RF spectrum monitoring (400 MHz to 6 GHz) and 4-channel microphone acoustic Time-Difference-of-Arrival (TDoA) direction finding (`MOD-04`).
* **Secure Directional Communications**: Free-Space Optical (FSO) laser communications transceivers with coarse-fine pointing, acquisition, and tracking (PAT), backed by frequency-hopping encrypted SDR RF (`MOD-05`).
* **Mission Effectors & Payloads**: Wind-compensated ballistic precision cargo drop pod and authorized defense payload interlocks (`MOD-06`).
* **Flight Avionics & Autopilot Core**: Bare-metal 32-bit microcontroller (STM32 running PX4) attitude control loops, motor timers, and aerodynamic actuators.
* **Cybersecurity & Data Sovereignty**: Hardware Root of Trust (RoT), secure bootloader, cryptographic key vaults, and automated zero-trace flash memory sanitization.

### 3.2 Known Boundaries and Explicit Exclusions
* **Excluded from Current Scope**: Heavy ground transport carriers, fixed optical ground base stations, long-term depot maintenance tooling, and off-board cloud infrastructure (strictly prohibited under the zero-cloud architecture).
* **Provisional & TBD Data**: In accordance with project instructions, unverified vendor part numbers, uncalibrated optical zoom focal lengths, absolute aerodynamic lift coefficients, and unmeasured RF noise figures are explicitly designated as `TBD — To Be Determined` and tracked in Section 14.

---

## 4. Applicable Source Documents and References

All requirements, architectural allocations, and verification criteria in this document are strictly grounded in verified project documentation:

| Document Identifier | Document Title | Author / Origin | Project Relevance & Baseline Status |
| :--- | :--- | :--- | :--- |
| `REA-T1-OVERVIEW-2026-V1.0` | RudraEdge RE-T1 (Spectra) Project Introduction & Technical Overview | Sarvesh Sharma (Founder & Project Lead) | Primary source of truth for the 8-Layer PECLF architecture, 6 modular subsystems, 10-Tier Validation Ladder, and 18-month roadmap. |
| `REA/2026/RE-T1/TRAIN-001/ADD-03` | Pre-Implementation Technical Readiness & Training Task Order | Sarvesh Sharma (Project Lead) | Direct engineering directive governing Day 2 Tasks 3 and 4 deliverables, cadre roles, and zero-cost constraints. |
| `REA-T1-SRS-2026-V1.0` | System Requirements Specification (SRS) — Baseline Foundation (Day 1) | Priyanka Sharma (Systems Engineer) | Day 1 requirements baseline establishing initial 25 system requirements (`REQ-SYS-0001` through `REQ-SYS-0025`). |
| `REA-T1-ARCH-STUDY-2026-V1.0` | RE-T1 Cross-Domain Architecture Study | Priyanka Sharma (Systems Engineer) | Technical node register (22 nodes), inter-subsystem data flow topologies, and bus protocol definitions. |
| `RE-iDEX-PROPOSAL-2026-R1` | Master iDEX Proposal: Autonomous Tactical UAV Platform | RudraEdge Aerospace / MoD | Authoritative framework defining the 20 frozen advanced capabilities and deliverables D1 through D20. |

---

## 5. System Overview

### 5.1 Tactical Context & High-Altitude Operations
The **RudraEdge RE-T1 (Spectra)** is an autonomous, tactical-class Unmanned Aerial Vehicle engineered specifically for operation in contested, high-altitude border frontiers such as Ladakh and the Siachen Glacier. The operational theater is characterized by:
1. **Severe GNSS Denial**: Pervasive adversary jamming and spoofing rendering conventional GPS/GLONASS navigation non-functional.
2. **Extreme Atmospheric Stress**: Sub-zero temperatures down to $-20^\circ\text{C}$, thin mountain air drastically reducing aerodynamic lift, and severe high-altitude wind turbulence.
3. **Electronic Warfare (EW) Contestation**: Hostile RF monitoring, radio jamming, and radar cross-section surveillance requiring RF discipline and low physical/electromagnetic signatures.
4. **Supply Chain Vulnerability**: Foreign flight controllers and proprietary silicon presenting supply-chain choke points and backdoor vulnerabilities.

### 5.2 The 8-Layer PECLF Architectural Concept
To resolve these operational bottlenecks, RE-T1 implements an integrated **Physical-Electromagnetic-Cyber Layer Fusion (PECLF)** framework:
* **Layer A (Physical Perception)**: Gyro-stabilized daylight EO + LWIR thermal gimbals, micro-LiDAR altimeter, micro-GPR, 4-element acoustic array, and CBRN sniffers.
* **Layer B (Navigation & Autonomy)**: VIO state estimation, DEM terrain elevation matching, and custom Swadeshi ROS 2 coupled with PX4 flight control.
* **Layer C (Heterogeneous Edge Compute)**: Dedicated zero-cloud onboard computing matrix (CPU/GPU/NPU/DSP) utilizing local POSIX shared memory (`shm`).
* **Layer D (Electromagnetic Awareness)**: Wideband SDR RF spectrum monitoring (400 MHz to 6 GHz) and acoustic Time-Difference-of-Arrival (TDoA) gunfire localization.
* **Layer E (Secure Communications)**: Directional Free-Space Optical (FSO) narrow-beam laser data link with automated fallback to encrypted frequency-hopping SDR RF.
* **Layer F (Mission Intelligence & AI)**: Pixel-level semantic segmentation, temporal visual change detection, neural super-resolution, and SAR path planning.
* **Layer G (Authorized Effectors & Payloads)**: Wind-compensated ballistic cargo drop pod and authorized payload interface with hardware safety interlocks.
* **Layer H (Cybersecurity & Data Sovereignty)**: Hardware Root of Trust, secure bootloader, encrypted local partitions, and automated zero-trace memory wipe.

*Unavailable information (such as exact airframe wingspan, maximum takeoff weight, battery pack chemistries, and motor stator dimensions) is officially designated as `TBD` awaiting Milestone 2 benchtop and airframe fabrication data.*

---

---

# ==============================================================================
# PART I: TASK 3 — REQUIREMENTS DECOMPOSITION FRAMEWORK
# ==============================================================================

## 6. Requirements Organization & Hierarchy Architecture

### 6.1 Requirements Hierarchy
To ensure modular decomposition, readability, and deterministic traceability, all requirements in this framework are organized into four discrete levels:

```
+-----------------------------------------------------------------------------------+
| LEVEL 1: SYSTEM-LEVEL REQUIREMENTS (Operational Objectives & Mission Pillars)     |
| [OBJ-01 .. OBJ-07] / [REQ-SYS-0001 .. REQ-SYS-0025]                               |
+-----------------------------------------------------------------------------------+
                                         |
                                         v
+-----------------------------------------------------------------------------------+
| LEVEL 2: SUBSYSTEM-LEVEL REQUIREMENTS (Allocated Subsystem Boundaries & Modules)  |
| [REQ-SUB-VIO-xxx] [REQ-SUB-CAM-xxx] [REQ-SUB-AI-xxx] [REQ-SUB-EW-xxx]             |
| [REQ-SUB-FSO-xxx] [REQ-SUB-POD-xxx] [REQ-SUB-AVI-xxx] [REQ-SUB-SEC-xxx]           |
+-----------------------------------------------------------------------------------+
                                         |
                                         v
+-----------------------------------------------------------------------------------+
| LEVEL 3: FUNCTIONAL REQUIREMENTS (Algorithmic Processing & Subsystem Behaviors)   |
| [REQ-FNC-VIO-xxx] [REQ-FNC-AI-xxx]  [REQ-FNC-EW-xxx]  [REQ-FNC-FSO-xxx]           |
+-----------------------------------------------------------------------------------+
                                         |
                                         v
+-----------------------------------------------------------------------------------+
| LEVEL 4: DETAILED / DERIVED REQUIREMENTS (Interfaces, Timing, Fault Logic, Busses)|
| [REQ-DER-INT-xxx] [REQ-DER-TIM-xxx] [REQ-DER-FLT-xxx] [REQ-DER-ENV-xxx]           |
+-----------------------------------------------------------------------------------+
```

1. **Level 1 (System-Level Requirements)**: High-level operational objectives and tactical flight capabilities defining platform mission success (e.g., continuous drift-bounded navigation in GPS-denied airspace).
2. **Level 2 (Subsystem-Level Requirements)**: Technical requirements allocated to specific subsystem boundaries (e.g., Module 01 VIO-NAV subsystem requirements, Module 03 Edge AI subsystem requirements).
3. **Level 3 (Functional Requirements)**: Precise functional behavior, algorithmic transformations, data ingestion, and control laws executed by a subsystem.
4. **Level 4 (Detailed / Derived Requirements)**: Fine-grained specifications covering bus protocols, latency thresholds, electrical interlocks, memory buffers, and fail-safe recovery logic derived from higher-level requirements.

### 6.2 Requirement Identifier Conventions
To avoid ambiguity, identifiers follow a standardized taxonomy:
* `OBJ-XX`: Official Level 1 Project Objectives (frozen in `REA-T1-OVERVIEW-2026-V1.0`).
* `REQ-SYS-XXXX`: Approved Baseline Level 1 System Requirements (established in Day 1 SRS `REA-T1-SRS-2026-V1.0`).
* `REQ-SUB-<SUB>-XXX`: Level 2 Subsystem Requirements (e.g., `REQ-SUB-VIO-001`, `REQ-SUB-AI-001`).
* `REQ-FNC-<SUB>-XXX`: Level 3 Functional Requirements (e.g., `REQ-FNC-VIO-001`, `REQ-FNC-AI-001`).
* `REQ-DER-<TYPE>-XXX`: Level 4 Detailed or Derived Requirements (e.g., `REQ-DER-INT-001`, `REQ-DER-TIM-001`).

*Identification Rule: All newly proposed Level 2, 3, and 4 requirements are explicitly tagged with `[PROPOSED]` in their tracking records to distinguish them from approved baselined requirements.*

### 6.3 Requirement Classification Types
* **Functional**: Defines a specific operational task, algorithmic computation, or transformation.
* **Performance**: Specifies a quantitative metric, timing deadline, accuracy tolerance, or bandwidth.
* **Interface**: Defines an electrical bus, software protocol, data format, or physical pinning.
* **Safety / Reliability**: Specifies isolation mechanisms, failsafes, interlocks, or watchdog triggers.
* **Security / Cryptography**: Defines cryptographic authentication, encryption, or memory sanitization.
* **Physical / Structural**: Specifies airframe geometry, material properties, or thermal insulation.
* **Environmental**: Specifies operating temperature, pressure altitude, or weather tolerance.

### 6.4 Requirement Tracking Node Schema (17 Mandatory Fields)
Each requirement tracking record in this SRS template includes the following seventeen explicit fields:
1. **Requirement ID**: Unique, permanent alphanumeric identifier.
2. **Requirement Title**: Short, descriptive summary phrase.
3. **Requirement Statement**: Formal, normative engineering statement using *shall*.
4. **Requirement Level**: Explicit classification (Level 1, Level 2, Level 3, or Level 4).
5. **Parent Requirement ID**: Direct upstream parent identifier (or `N/A - Top Level Objective`).
6. **Source / Origin**: Document, section, page, or stakeholder origin.
7. **Requirement Type**: Functional, Performance, Interface, Safety, Security, Physical, or Environmental.
8. **Allocated Subsystem**: Physical or logical module responsible for implementation.
9. **Rationale**: Technical engineering justification for why the requirement exists.
10. **Verification Method**: Method of verification (Inspection, Analysis, Demonstration, Test).
11. **Verification Status**: Current execution status (Unexecuted, Awaiting Testbench, Pending HIL, etc.).
12. **Child Requirement IDs**: Downstream derived requirement identifiers (or `TBD / Pending Decomposition`).
13. **Upstream Traceability**: Path tracing back to high-level iDEX operational pillars.
14. **Downstream Traceability**: Path tracing to implementation modules, interfaces, and testbench tiers.
15. **Configuration / Baseline Status**: Draft, Proposed, Under Review, Approved, or Baselined.
16. **Assumptions or Constraints**: Operating conditions, architectural boundaries, or environmental limits.
17. **Open Issues / TBD Items**: Unresolved numerical values, missing part numbers, or open queries.

---

## 7. Initial Requirements Tracking Nodes

Below are the initial structured requirement tracking nodes demonstrating the complete 4-level decomposition for representative mission domains of the RE-T1 platform.

---

### Node 7.1: GNSS-Denied Navigation & Odometry Decomposition Chain

#### 7.1.1 Level 1 System Requirement Node: REQ-SYS-0001
| Field Name | Value / Engineering Content |
| :--- | :--- |
| **Requirement ID** | `REQ-SYS-0001` |
| **Requirement Title** | GNSS-Denied 6-DOF Vehicle Localization & Navigation |
| **Requirement Statement** | The system shall calculate continuous, drift-bounded 6-DOF vehicle pose estimations in GPS-denied and satellite-jammed environments by fusing high-rate IMU angular rates, visual tracking streams, onboard Digital Elevation Models (DEM), and micro-LiDAR altimetry. |
| **Requirement Level** | **Level 1: System-Level Requirement** |
| **Parent Requirement ID** | `OBJ-01` (GNSS-Denied Flight Pillar) |
| **Source / Origin** | `REA-T1-OVERVIEW-2026-V1.0`, Section 2 (p. 3); Section 7 (p. 8); Section 10 (p. 11) |
| **Requirement Type** | Functional / Performance |
| **Allocated Subsystem** | `MOD-01` (`VIO-NAV`) — GNSS-Denied Localization & Navigation Subsystem |
| **Rationale** | Satellite GPS/GNSS signals are actively jammed, spoofed, or blocked across contested Himalayan operational theaters, causing unhardened commercial and legacy military drones to suffer catastrophic positional loss and mission failure. |
| **Verification Method** | Test / Demonstration (Tier 8 Exit Criteria) |
| **Verification Status** | UNEXECUTED — Awaiting Tier 8 GNSS-Denied Flight Trials |
| **Child Requirement IDs** | `REQ-SUB-VIO-001` [PROPOSED], `REQ-SUB-VIO-002` [PROPOSED] |
| **Upstream Traceability** | `RE-iDEX-PROPOSAL-2026-R1` $\rightarrow$ `OBJ-01` $\rightarrow$ `REQ-SYS-0001` |
| **Downstream Traceability** | `REQ-SUB-VIO-001` $\rightarrow$ `REQ-FNC-VIO-001` $\rightarrow$ `REQ-DER-INT-001` $\rightarrow$ Tier 8 Testing |
| **Configuration / Baseline Status** | **PROVISIONAL (DRAFT)** — Established in Day 1 SRS Baseline |
| **Assumptions or Constraints** | Requires terrain feature contrast in daylight/thermal spectrum and pre-loaded digital elevation maps of the operational sector. |
| **Open Issues / TBD Items** | `ISSUE-REQ-001`: DEM grid spatial resolution (e.g., 5m vs 30m) and offline map storage footprint are unstated. |

---

#### 7.1.2 Level 2 Subsystem Requirement Node: REQ-SUB-VIO-001 [PROPOSED]
| Field Name | Value / Engineering Content |
| :--- | :--- |
| **Requirement ID** | `REQ-SUB-VIO-001` `[PROPOSED]` |
| **Requirement Title** | Multi-Sensor Odometry Fusion Engine Allocation |
| **Requirement Statement** | The VIO-NAV subsystem (`MOD-01`) shall host a real-time sensor fusion filter that ingests high-rate tactical IMU acceleration/angular velocity, optical feature tracking frames, and micro-LiDAR range updates to generate kinematic velocity vectors and 6-DOF spatial state estimates. |
| **Requirement Level** | **Level 2: Subsystem-Level Requirement** |
| **Parent Requirement ID** | `REQ-SYS-0001` |
| **Source / Origin** | `REA-T1-OVERVIEW-2026-V1.0`, Section 7 (p. 8: Module 01 functional definition) |
| **Requirement Type** | Functional / Architecture |
| **Allocated Subsystem** | `MOD-01` (`VIO-NAV`) |
| **Rationale** | High-rate inertial integration drifts unbounded over time without continuous visual feature updates and LiDAR altitude clamping. |
| **Verification Method** | Demonstration / Test (Tier 2 SIL & Tier 3 HIL Criteria) |
| **Verification Status** | UNEXECUTED — Awaiting Gazebo Digital Twin & HIL Testbench |
| **Child Requirement IDs** | `REQ-FNC-VIO-001` `[PROPOSED]`, `REQ-FNC-VIO-002` `[PROPOSED]` |
| **Upstream Traceability** | `OBJ-01` $\rightarrow$ `REQ-SYS-0001` $\rightarrow$ `REQ-SUB-VIO-001` |
| **Downstream Traceability** | `REQ-FNC-VIO-001` $\rightarrow$ `REQ-DER-INT-001` $\rightarrow$ Gazebo SITL Simulation |
| **Configuration / Baseline Status** | **PROPOSED (UNDER REVIEW)** |
| **Assumptions or Constraints** | Micro-LiDAR operational range bounded between 0.5m and 100m AGL. |
| **Open Issues / TBD Items** | TBD — Micro-LiDAR optical wavelength and update frequency (Hz). |

---

#### 7.1.3 Level 3 Functional Requirement Node: REQ-FNC-VIO-001 [PROPOSED]
| Field Name | Value / Engineering Content |
| :--- | :--- |
| **Requirement ID** | `REQ-FNC-VIO-001` `[PROPOSED]` |
| **Requirement Title** | Visual Feature Point Tracking and Odometry Estimation |
| **Requirement Statement** | The VIO-NAV algorithmic pipeline shall extract and track visual feature points across consecutive camera frames at a rate of not less than 30 Hz to compute relative translation and rotation deltas. |
| **Requirement Level** | **Level 3: Functional Requirement** |
| **Parent Requirement ID** | `REQ-SUB-VIO-001` |
| **Source / Origin** | `REA-T1-OVERVIEW-2026-V1.0`, Section 4 (p. 5); Section 7 (p. 8) |
| **Requirement Type** | Functional / Algorithmic |
| **Allocated Subsystem** | `MOD-01` (`VIO-NAV`) / Edge Compute Fabric (`Layer C`) |
| **Rationale** | Feature tracking at lower frequencies degrades pose estimation accuracy during aggressive maneuvers or turbulent wind shear. |
| **Verification Method** | Analysis / Simulation (Tier 1 Algorithm Simulation) |
| **Verification Status** | UNEXECUTED — Awaiting PyTorch / OpenCV Algorithmic Benchmark |
| **Child Requirement IDs** | `REQ-DER-INT-001` `[PROPOSED]`, `REQ-DER-TIM-001` `[PROPOSED]` |
| **Upstream Traceability** | `OBJ-01` $\rightarrow$ `REQ-SYS-0001` $\rightarrow$ `REQ-SUB-VIO-001` $\rightarrow$ `REQ-FNC-VIO-001` |
| **Downstream Traceability** | `REQ-DER-INT-001` $\rightarrow$ `REQ-DER-TIM-001` $\rightarrow$ Tier 1 VIO Model Benchmark |
| **Configuration / Baseline Status** | **PROPOSED (UNDER REVIEW)** |
| **Assumptions or Constraints** | Assumes tracking lens field of view contains minimum 50 trackable optical feature points per frame. |
| **Open Issues / TBD Items** | `ISSUE-REQ-002`: Minimum illumination threshold for optical feature tracking before automated infrared handoff is unstated. |

---

#### 7.1.4 Level 4 Detailed / Derived Requirement Node: REQ-DER-INT-001 [PROPOSED]
| Field Name | Value / Engineering Content |
| :--- | :--- |
| **Requirement ID** | `REQ-DER-INT-001` `[PROPOSED]` |
| **Requirement Title** | VIO-to-PX4 ROS 2 Odometry Topic Publishing Interface |
| **Requirement Statement** | The VIO navigation node shall publish estimated 6-DOF kinematic pose and velocity covariance matrices to the PX4 Autopilot flight controller via ROS 2 topic `/re_t1/nav/odometry` utilizing Micro-XRCE-DDS over high-speed UART/Ethernet with a publication rate of at least 50 Hz. |
| **Requirement Level** | **Level 4: Detailed / Derived Requirement** |
| **Parent Requirement ID** | `REQ-FNC-VIO-001` |
| **Source / Origin** | `REA-T1-OVERVIEW-2026-V1.0`, Section 7 (p. 8: Module 01 outputs); Section 8 (p. 9: Autopilot to Compute interface) |
| **Requirement Type** | Interface / Performance |
| **Allocated Subsystem** | `MOD-01` (`VIO-NAV`) $\leftrightarrow$ `AVIONICS-CORE` (`STUDY-NODE-07`) |
| **Rationale** | Deterministic pose transmission over Micro-XRCE-DDS allows PX4 extended Kalman filter (EKF2) to substitute missing satellite GPS coordinates without software divergence. |
| **Verification Method** | Test / Inspection (Tier 2 SIL & Tier 4 Benchtop Integration) |
| **Verification Status** | UNEXECUTED — Awaiting ROS 2-PX4 Micro-XRCE-DDS Bus Test |
| **Child Requirement IDs** | None (Leaf Node in Decomposition Hierarchy) |
| **Upstream Traceability** | `OBJ-01` $\rightarrow$ `REQ-SYS-0001` $\rightarrow$ `REQ-SUB-VIO-001` $\rightarrow$ `REQ-FNC-VIO-001` $\rightarrow$ `REQ-DER-INT-001` |
| **Downstream Traceability** | `STUDY-NODE-07` / `STUDY-NODE-08` $\rightarrow$ Micro-XRCE-DDS Interface $\rightarrow$ Tier 2 / Tier 4 Tests |
| **Configuration / Baseline Status** | **PROPOSED (UNDER REVIEW)** |
| **Assumptions or Constraints** | UART baud rate configured to 3,000,000 baud or Gigabit Ethernet link active. |
| **Open Issues / TBD Items** | NOT YET DEFINED — Exact ROS 2 message definition standard (standard `nav_msgs/Odometry` vs custom MAVLink extension). |

---

### Node 7.2: Heterogeneous Edge AI & Vision Intelligence Decomposition Chain

#### 7.2.1 Level 1 System Requirement Node: REQ-SYS-0003
| Field Name | Value / Engineering Content |
| :--- | :--- |
| **Requirement ID** | `REQ-SYS-0003` |
| **Requirement Title** | Zero-Cloud Heterogeneous Neural Inferencing |
| **Requirement Statement** | The system shall execute real-time pixel-level semantic segmentation and object detection entirely onboard utilizing INT8 quantized neural models hosted on dedicated heterogeneous CPU/GPU/NPU/DSP hardware without external cloud or ground station connectivity. |
| **Requirement Level** | **Level 1: System-Level Requirement** |
| **Parent Requirement ID** | `OBJ-02` (Heterogeneous Edge AI Pillar) |
| **Source / Origin** | `REA-T1-OVERVIEW-2026-V1.0`, Section 2 (p. 3); Section 6 (p. 7); Section 7 (p. 8) |
| **Requirement Type** | Functional / Performance |
| **Allocated Subsystem** | `MOD-03` (`EDGE-AI`) / `STUDY-NODE-09` (Heterogeneous Edge Compute) |
| **Rationale** | Congested tactical RF links and enemy electronic sniffing prevent offloading uncompressed raw high-definition video feeds to remote cloud or ground-station servers. |
| **Verification Method** | Demonstration / Analysis (Tier 1 & Tier 9 Criteria) |
| **Verification Status** | UNEXECUTED — Awaiting INT8 Quantized Model Benchmarking |
| **Child Requirement IDs** | `REQ-SUB-AI-001` `[PROPOSED]`, `REQ-SUB-AI-002` `[PROPOSED]` |
| **Upstream Traceability** | `RE-iDEX-PROPOSAL-2026-R1` $\rightarrow$ `OBJ-02` $\rightarrow$ `REQ-SYS-0003` |
| **Downstream Traceability** | `REQ-SUB-AI-001` $\rightarrow$ `REQ-FNC-AI-001` $\rightarrow$ `REQ-DER-INT-002` $\rightarrow$ Tier 1 / Tier 9 Testing |
| **Configuration / Baseline Status** | **PROVISIONAL (DRAFT)** — Established in Day 1 SRS Baseline |
| **Assumptions or Constraints** | Board-level thermal dissipation must sustain maximum neural engine throttle without throttling below nominal clock speeds in ambient temperatures up to $+45^\circ\text{C}$. |
| **Open Issues / TBD Items** | `ISSUE-REQ-003`: Interim COTS System-on-Module model part number (prior to indigenous VEGA/SHAKTI migration) is unstated. |

---

#### 7.2.2 Level 2 Subsystem Requirement Node: REQ-SUB-AI-001 [PROPOSED]
| Field Name | Value / Engineering Content |
| :--- | :--- |
| **Requirement ID** | `REQ-SUB-AI-001` `[PROPOSED]` |
| **Requirement Title** | Edge Intelligence Engine Model Execution Environment |
| **Requirement Statement** | The Edge Intelligence Engine (`MOD-03`) shall host an air-gapped containerized Linux runtime supporting NVIDIA TensorRT INT8 compiled execution engines with zero public network socket dependencies. |
| **Requirement Level** | **Level 2: Subsystem-Level Requirement** |
| **Parent Requirement ID** | `REQ-SYS-0003` |
| **Source / Origin** | `REA-T1-OVERVIEW-2026-V1.0`, Section 6 (p. 7: Software Layer Specifications) |
| **Requirement Type** | Functional / Software |
| **Allocated Subsystem** | `MOD-03` (`EDGE-AI`) |
| **Rationale** | Containerized microservices prevent dependency collisions between disparate deep learning frameworks and maintain deterministic software execution. |
| **Verification Method** | Inspection / Demonstration (Tier 1 Simulation & Tier 4 Benchtop) |
| **Verification Status** | UNEXECUTED — Awaiting Container Image Build & Bench Test |
| **Child Requirement IDs** | `REQ-FNC-AI-001` `[PROPOSED]`, `REQ-FNC-AI-002` `[PROPOSED]` |
| **Upstream Traceability** | `OBJ-02` $\rightarrow$ `REQ-SYS-0003` $\rightarrow$ `REQ-SUB-AI-001` |
| **Downstream Traceability** | `REQ-FNC-AI-001` $\rightarrow$ `REQ-DER-INT-002` $\rightarrow$ Container Audit Logs |
| **Configuration / Baseline Status** | **PROPOSED (UNDER REVIEW)** |
| **Assumptions or Constraints** | Model files must be pre-compiled and cryptographically signed prior to loading. |
| **Open Issues / TBD Items** | TBD — Root filesystem storage allocation for frozen model binaries. |

---

#### 7.2.3 Level 3 Functional Requirement Node: REQ-FNC-AI-001 [PROPOSED]
| Field Name | Value / Engineering Content |
| :--- | :--- |
| **Requirement ID** | `REQ-FNC-AI-001` `[PROPOSED]` |
| **Requirement Title** | Real-Time INT8 Semantic Segmentation Inference |
| **Requirement Statement** | The neural execution engine shall perform pixel-level semantic segmentation on 1080p synchronized EO/IR video frames at an inferencing throughput of not less than 15 frames per second with INT8 precision. |
| **Requirement Level** | **Level 3: Functional Requirement** |
| **Parent Requirement ID** | `REQ-SUB-AI-001` |
| **Source / Origin** | `REA-T1-OVERVIEW-2026-V1.0`, Section 2 (p. 3); Section 7 (p. 8) |
| **Requirement Type** | Performance / Functional |
| **Allocated Subsystem** | `MOD-03` (`EDGE-AI`) |
| **Rationale** | High inference throughput is mandatory to maintain track retention on dynamic tactical ground targets during high-speed airframe transit. |
| **Verification Method** | Demonstration / Test (Tier 1 Simulation & Tier 3 HIL Bench) |
| **Verification Status** | UNEXECUTED — Awaiting Model Benchmark Profiler Execution |
| **Child Requirement IDs** | `REQ-DER-INT-002` `[PROPOSED]`, `REQ-DER-TIM-002` `[PROPOSED]` |
| **Upstream Traceability** | `OBJ-02` $\rightarrow$ `REQ-SYS-0003` $\rightarrow$ `REQ-SUB-AI-001` $\rightarrow$ `REQ-FNC-AI-001` |
| **Downstream Traceability** | `REQ-DER-INT-002` $\rightarrow$ `REQ-DER-TIM-002` $\rightarrow$ Tier 1 Profiler Reports |
| **Configuration / Baseline Status** | **PROPOSED (UNDER REVIEW)** |
| **Assumptions or Constraints** | Input camera streams conditioned and calibrated by OpenCV pre-processing threads. |
| **Open Issues / TBD Items** | `ISSUE-REQ-004`: Quantitative mean Intersection-over-Union (mIoU) target threshold for tactical segmentation classes is unstated. |

---

#### 7.2.4 Level 4 Detailed / Derived Requirement Node: REQ-DER-INT-002 [PROPOSED]
| Field Name | Value / Engineering Content |
| :--- | :--- |
| **Requirement ID** | `REQ-DER-INT-002` `[PROPOSED]` |
| **Requirement Title** | Zero-Copy POSIX Shared Memory Ingress Interface |
| **Requirement Statement** | The edge AI engine shall ingest raw video frame buffers directly from MIPI-CSI Gen3 DMA memory using POSIX shared memory (`/dev/shm`) zero-copy ring buffers, bypassing host CPU cache overhead and achieving zero frame drop buffering. |
| **Requirement Level** | **Level 4: Detailed / Derived Requirement** |
| **Parent Requirement ID** | `REQ-FNC-AI-001` |
| **Source / Origin** | `REA-T1-OVERVIEW-2026-V1.0`, Section 8 (p. 9: Hardware & Software Interface Architecture) |
| **Requirement Type** | Interface / Performance |
| **Allocated Subsystem** | `MOD-03` (`EDGE-AI`) $\leftrightarrow$ `MOD-02` (`EO-IR-GIMBAL`) |
| **Rationale** | Copying uncompressed 1080p YUV/RGB frames across CPU memory buffers causes host memory bus contention, frame drops, and excessive power consumption. |
| **Verification Method** | Test / Analysis (Tier 4 Benchtop Integration) |
| **Verification Status** | UNEXECUTED — Awaiting DMA Memory Buffer Stress Testing |
| **Child Requirement IDs** | None (Leaf Node in Decomposition Hierarchy) |
| **Upstream Traceability** | `OBJ-02` $\rightarrow$ `REQ-SYS-0003` $\rightarrow$ `REQ-SUB-AI-001` $\rightarrow$ `REQ-FNC-AI-001` $\rightarrow$ `REQ-DER-INT-002` |
| **Downstream Traceability** | POSIX shm driver $\rightarrow$ MIPI CSI DMA Controller $\rightarrow$ Tier 4 Bench Logs |
| **Configuration / Baseline Status** | **PROPOSED (UNDER REVIEW)** |
| **Assumptions or Constraints** | Linux kernel configured with real-time PREEMPT_RT patches and continuous hugepage memory pools. |
| **Open Issues / TBD Items** | NOT YET DEFINED — Ring buffer depth and allocation size (MB). |

---

### Node 7.3: Electronic Warfare & RF Awareness Decomposition Chain

#### 7.3.1 Level 1 System Requirement Node: REQ-SYS-0007
| Field Name | Value / Engineering Content |
| :--- | :--- |
| **Requirement ID** | `REQ-SYS-0007` |
| **Requirement Title** | Wideband RF Spectrum Sensing & Electronic Awareness |
| **Requirement Statement** | The system shall monitor the ambient RF electromagnetic spectrum across 400 MHz to 6 GHz to detect hostile radio emissions, characterize radar signatures, and generate RF spectrum occupancy grids. |
| **Requirement Level** | **Level 1: System-Level Requirement** |
| **Parent Requirement ID** | `OBJ-05` (Multi-Modal Perception Pillar) |
| **Source / Origin** | `REA-T1-OVERVIEW-2026-V1.0`, Section 7 (p. 8); Section 8 (p. 9) |
| **Requirement Type** | Functional / Performance |
| **Allocated Subsystem** | `MOD-04` (`EW-DSP`) / `STUDY-NODE-15` (SDR RF Front-End) |
| **Rationale** | Tactical airframes operating along contested borders require autonomous electronic surveillance to detect hostile air-defense radar emissions and pinpoint electronic jammer sites. |
| **Verification Method** | Test / Analysis (Tier 4 Integration Criteria) |
| **Verification Status** | UNEXECUTED — Awaiting RF Testbed Bench Integration |
| **Child Requirement IDs** | `REQ-SUB-EW-001` `[PROPOSED]` |
| **Upstream Traceability** | `RE-iDEX-PROPOSAL-2026-R1` $\rightarrow$ `OBJ-05` $\rightarrow$ `REQ-SYS-0007` |
| **Downstream Traceability** | `REQ-SUB-EW-001` $\rightarrow$ `REQ-FNC-EW-001` $\rightarrow$ `REQ-DER-INT-003` $\rightarrow$ Tier 4 / Tier 9 Testing |
| **Configuration / Baseline Status** | **PROVISIONAL (DRAFT)** — Established in Day 1 SRS Baseline |
| **Assumptions or Constraints** | Hostile emitters radiate within 400 MHz to 6 GHz frequency band. |
| **Open Issues / TBD Items** | `ISSUE-REQ-006`: Receiver minimum detectable signal (MDS in dBm), instantaneous RF bandwidth, and sweep rates are unstated. |

---

#### 7.3.2 Level 2 Subsystem Requirement Node: REQ-SUB-EW-001 [PROPOSED]
| Field Name | Value / Engineering Content |
| :--- | :--- |
| **Requirement ID** | `REQ-SUB-EW-001` `[PROPOSED]` |
| **Requirement Title** | Wideband SDR Receiver and DSP Slicing Allocation |
| **Requirement Statement** | The EW-DSP subsystem (`MOD-04`) shall ingest digitized wideband RF intermediate frequency (IF) samples from the SDR front-end, execute digital FIR/IIR filtering, and extract spectral occupancy grids. |
| **Requirement Level** | **Level 2: Subsystem-Level Requirement** |
| **Parent Requirement ID** | `REQ-SYS-0007` |
| **Source / Origin** | `REA-T1-OVERVIEW-2026-V1.0`, Section 7 (p. 8: Module 04 definition) |
| **Requirement Type** | Functional / Architecture |
| **Allocated Subsystem** | `MOD-04` (`EW-DSP`) |
| **Rationale** | Digitized RF streaming requires dedicated DSP acceleration to compute fast Fourier transforms (FFT) without saturating host CPU cores. |
| **Verification Method** | Demonstration / Test (Tier 4 Benchtop Integration) |
| **Verification Status** | UNEXECUTED — Awaiting SDR Hardware Bench Rig |
| **Child Requirement IDs** | `REQ-FNC-EW-001` `[PROPOSED]` |
| **Upstream Traceability** | `OBJ-05` $\rightarrow$ `REQ-SYS-0007` $\rightarrow$ `REQ-SUB-EW-001` |
| **Downstream Traceability** | `REQ-FNC-EW-001` $\rightarrow$ `REQ-DER-INT-003` $\rightarrow$ Tier 4 Test Logs |
| **Configuration / Baseline Status** | **PROPOSED (UNDER REVIEW)** |
| **Assumptions or Constraints** | Front-end antenna array matched to 50-ohm characteristic impedance across band. |
| **Open Issues / TBD Items** | TBD — ADC sampling rate and dynamic range in bits. |

---

#### 7.3.3 Level 3 Functional Requirement Node: REQ-FNC-EW-001 [PROPOSED]
| Field Name | Value / Engineering Content |
| :--- | :--- |
| **Requirement ID** | `REQ-FNC-EW-001` `[PROPOSED]` |
| **Requirement Title** | Real-Time RF Spectral Peak Detection and Emitter Profiling |
| **Requirement Statement** | The DSP pipeline shall process incoming digitized RF frames to detect spectral power peaks exceeding a dynamic threshold of 10 dB above ambient noise floor within 50 milliseconds. |
| **Requirement Level** | **Level 3: Functional Requirement** |
| **Parent Requirement ID** | `REQ-SUB-EW-001` |
| **Source / Origin** | `REA-T1-OVERVIEW-2026-V1.0`, Section 5 (p. 6); Section 7 (p. 8) |
| **Requirement Type** | Functional / Performance |
| **Allocated Subsystem** | `MOD-04` (`EW-DSP`) |
| **Rationale** | Rapid emitter peak detection allows immediate tactical identification of radar lock-on or pulsed jamming attacks. |
| **Verification Method** | Test / Simulation (Tier 1 Algorithm Simulation & Tier 4 Bench) |
| **Verification Status** | UNEXECUTED — Awaiting DSP Simulated RF Ingress Verification |
| **Child Requirement IDs** | `REQ-DER-INT-003` `[PROPOSED]` |
| **Upstream Traceability** | `OBJ-05` $\rightarrow$ `REQ-SYS-0007` $\rightarrow$ `REQ-SUB-EW-001` $\rightarrow$ `REQ-FNC-EW-001` |
| **Downstream Traceability** | `REQ-DER-INT-003` $\rightarrow$ Tier 1 / Tier 4 RF Signal Generator Tests |
| **Configuration / Baseline Status** | **PROPOSED (UNDER REVIEW)** |
| **Assumptions or Constraints** | Dynamic threshold adapts to background thermal and co-site noise. |
| **Open Issues / TBD Items** | TBD — Hostile radar pulse repetition frequency (PRF) de-interleaving capabilities. |

---

#### 7.3.4 Level 4 Detailed / Derived Requirement Node: REQ-DER-INT-003 [PROPOSED]
| Field Name | Value / Engineering Content |
| :--- | :--- |
| **Requirement ID** | `REQ-DER-INT-003` `[PROPOSED]` |
| **Requirement Title** | VITA 49 Radio Transport Protocol over Gigabit Ethernet / PCIe |
| **Requirement Statement** | The SDR receiver front-end shall encapsulate digitized RF intermediate frequency I/Q samples into ANSI/VITA 49.0 Radio Transport (VRT) packets and stream them over Gigabit Ethernet or PCIe to the DSP processing engine. |
| **Requirement Level** | **Level 4: Detailed / Derived Requirement** |
| **Parent Requirement ID** | `REQ-FNC-EW-001` |
| **Source / Origin** | `REA-T1-OVERVIEW-2026-V1.0`, Section 8 (p. 9: SDR RF Ingress interface) |
| **Requirement Type** | Interface / Protocol |
| **Allocated Subsystem** | `STUDY-NODE-15` $\leftrightarrow$ `MOD-04` (`EW-DSP`) |
| **Rationale** | Adhering to the open VITA 49 standard ensures interoperability and deterministic packet framing between RF tuners and downstream DSP processors. |
| **Verification Method** | Inspection / Test (Tier 4 Benchtop Integration) |
| **Verification Status** | UNEXECUTED — Awaiting Network Packet Sniffer Bus Capture |
| **Child Requirement IDs** | None (Leaf Node in Decomposition Hierarchy) |
| **Upstream Traceability** | `OBJ-05` $\rightarrow$ `REQ-SYS-0007` $\rightarrow$ `REQ-SUB-EW-001` $\rightarrow$ `REQ-FNC-EW-001` $\rightarrow$ `REQ-DER-INT-003` |
| **Downstream Traceability** | VITA 49 Packet Decoder $\rightarrow$ PCIe / GbE Interface $\rightarrow$ Tier 4 Bench Logs |
| **Configuration / Baseline Status** | **PROPOSED (UNDER REVIEW)** |
| **Assumptions or Constraints** | Maximum packet jitter must remain under 100 microseconds to prevent DSP buffer underruns. |
| **Open Issues / TBD Items** | NOT YET DEFINED — Maximum VITA 49 packet payload byte size (MTU configuration). |

---

### Node 7.4: Secure Communications Decomposition Chain

#### 7.4.1 Level 1 System Requirement Node: REQ-SYS-0009
| Field Name | Value / Engineering Content |
| :--- | :--- |
| **Requirement ID** | `REQ-SYS-0009` |
| **Requirement Title** | Directional Free-Space Optical (FSO) Communications Link |
| **Requirement Statement** | The system shall transmit high-bandwidth mission intelligence and video streams over a directional narrow-beam Free-Space Optical laser link using closed-loop coarse-fine pointing, acquisition, and tracking (PAT). |
| **Requirement Level** | **Level 1: System-Level Requirement** |
| **Parent Requirement ID** | `OBJ-06` (Jam-Resistant Optical Link Pillar) |
| **Source / Origin** | `REA-T1-OVERVIEW-2026-V1.0`, Section 2 (p. 3); Section 7 (p. 8); Section 8 (p. 9) |
| **Requirement Type** | Functional / Performance |
| **Allocated Subsystem** | `MOD-05` (`FSO-COMM`) / Optical Transceiver Assembly |
| **Rationale** | Optical laser beams provide narrow line-of-sight spatial transmission that is physically immune to RF jamming and hostile electronic eavesdropping. |
| **Verification Method** | Demonstration / Test (Tier 9 Criteria) |
| **Verification Status** | UNEXECUTED — Awaiting Tier 9 Integrated Payload Flight Trials |
| **Child Requirement IDs** | `REQ-SUB-FSO-001` `[PROPOSED]` |
| **Upstream Traceability** | `RE-iDEX-PROPOSAL-2026-R1` $\rightarrow$ `OBJ-06` $\rightarrow$ `REQ-SYS-0009` |
| **Downstream Traceability** | `REQ-SUB-FSO-001` $\rightarrow$ `REQ-FNC-FSO-001` $\rightarrow$ `REQ-DER-INT-004` $\rightarrow$ Tier 9 Flight Trials |
| **Configuration / Baseline Status** | **PROVISIONAL (DRAFT)** — Established in Day 1 SRS Baseline |
| **Assumptions or Constraints** | Clear line-of-sight path between aircraft optical gimbal and friendly Optical Ground Terminal (OGT). |
| **Open Issues / TBD Items** | `ISSUE-REQ-008`: Laser transmitter optical wavelength (e.g., 850nm vs 1550nm) and maximum operational link range are unstated. |

---

#### 7.4.2 Level 2 Subsystem Requirement Node: REQ-SUB-FSO-001 [PROPOSED]
| Field Name | Value / Engineering Content |
| :--- | :--- |
| **Requirement ID** | `REQ-SUB-FSO-001` `[PROPOSED]` |
| **Requirement Title** | Coarse-Fine Pointing, Acquisition, and Tracking (PAT) Subsystem Allocation |
| **Requirement Statement** | The FSO-COMM subsystem (`MOD-05`) shall integrate a 2-axis motorized optical gimbal and fine fast-steering mirror (FSM) driven by closed-loop tracking algorithms to maintain optical beam alignment with ground terminal beacons under airframe angular perturbations. |
| **Requirement Level** | **Level 2: Subsystem-Level Requirement** |
| **Parent Requirement ID** | `REQ-SYS-0009` |
| **Source / Origin** | `REA-T1-OVERVIEW-2026-V1.0`, Section 7 (p. 8); Section 8 (p. 9) |
| **Requirement Type** | Functional / Mechatronics |
| **Allocated Subsystem** | `MOD-05` (`FSO-COMM`) |
| **Rationale** | High-frequency airframe vibrations and mountain wind gusts misalign narrow optical beams unless compensated by rapid closed-loop steering. |
| **Verification Method** | Test / Demonstration (Tier 3 HIL & Tier 9 Integrated Payload) |
| **Verification Status** | UNEXECUTED — Awaiting HIL Motion Platform PAT Calibration |
| **Child Requirement IDs** | `REQ-FNC-FSO-001` `[PROPOSED]` |
| **Upstream Traceability** | `OBJ-06` $\rightarrow$ `REQ-SYS-0009` $\rightarrow$ `REQ-SUB-FSO-001` |
| **Downstream Traceability** | `REQ-FNC-FSO-001` $\rightarrow$ `REQ-DER-INT-004` $\rightarrow$ Tier 3 / Tier 9 PAT Logs |
| **Configuration / Baseline Status** | **PROPOSED (UNDER REVIEW)** |
| **Assumptions or Constraints** | Requires RS-422 gyro coordinate offset telemetry from central IMU. |
| **Open Issues / TBD Items** | TBD — Coarse gimbal slew rate and fast-steering mirror angular bandwidth (Hz). |

---

#### 7.4.3 Level 3 Functional Requirement Node: REQ-FNC-FSO-001 [PROPOSED]
| Field Name | Value / Engineering Content |
| :--- | :--- |
| **Requirement ID** | `REQ-FNC-FSO-001` `[PROPOSED]` |
| **Requirement Title** | Closed-Loop Beam Tracking and Optical Uplink Acquisition |
| **Requirement Statement** | The PAT control loop shall acquire the optical ground beacon within 10 seconds of entering designated line-of-sight coordinates and maintain beam tracking error within $\pm 50$ microradians under flight vibration. |
| **Requirement Level** | **Level 3: Functional Requirement** |
| **Parent Requirement ID** | `REQ-SUB-FSO-001` |
| **Source / Origin** | `REA-T1-OVERVIEW-2026-V1.0`, Section 8 (p. 9: Optical FSO Gimbal interface) |
| **Requirement Type** | Functional / Performance |
| **Allocated Subsystem** | `MOD-05` (`FSO-COMM`) |
| **Rationale** | Beam pointing jitter exceeding the optical beam divergence angle results in total optical link loss and packet corruption. |
| **Verification Method** | Test / Analysis (Tier 3 HIL Simulation) |
| **Verification Status** | UNEXECUTED — Awaiting HIL Optical Motion Simulator Runs |
| **Child Requirement IDs** | `REQ-DER-INT-004` `[PROPOSED]` |
| **Upstream Traceability** | `OBJ-06` $\rightarrow$ `REQ-SYS-0009` $\rightarrow$ `REQ-SUB-FSO-001` $\rightarrow$ `REQ-FNC-FSO-001` |
| **Downstream Traceability** | `REQ-DER-INT-004` $\rightarrow$ PAT Simulation Data Logs |
| **Configuration / Baseline Status** | **PROPOSED (UNDER REVIEW)** |
| **Assumptions or Constraints** | Atmospheric scintillation within moderate limits (clear sky or light haze). |
| **Open Issues / TBD Items** | TBD — Uplink optical beacon detector matrix type (quadrant photodiode vs CMOS tracker). |

---

#### 7.4.4 Level 4 Detailed / Derived Requirement Node: REQ-DER-INT-004 [PROPOSED]
| Field Name | Value / Engineering Content |
| :--- | :--- |
| **Requirement ID** | `REQ-DER-INT-004` `[PROPOSED]` |
| **Requirement Title** | RS-422 Serial High-Rate Gyro Coordinate Offset Telemetry |
| **Requirement Statement** | The central IMU / autopilot interface shall stream high-rate body angular rate offsets to the FSO gimbal controller over dedicated full-duplex RS-422 serial lines at a baud rate of not less than 921,600 baud and update rate of 500 Hz. |
| **Requirement Level** | **Level 4: Detailed / Derived Requirement** |
| **Parent Requirement ID** | `REQ-FNC-FSO-001` |
| **Source / Origin** | `REA-T1-OVERVIEW-2026-V1.0`, Section 8 (p. 9: Optical FSO Gimbal interface) |
| **Requirement Type** | Interface / Performance |
| **Allocated Subsystem** | `AVIONICS-CORE` (`STUDY-NODE-16`) $\leftrightarrow$ `MOD-05` (`FSO-COMM`) |
| **Rationale** | Inertial feedforward stabilization is required to isolate the optical payload from high-rate airframe body oscillations before feedback loops react. |
| **Verification Method** | Test / Inspection (Tier 4 Benchtop Integration) |
| **Verification Status** | UNEXECUTED — Awaiting Benchtop Serial Ingress Latency Check |
| **Child Requirement IDs** | None (Leaf Node in Decomposition Hierarchy) |
| **Upstream Traceability** | `OBJ-06` $\rightarrow$ `REQ-SYS-0009` $\rightarrow$ `REQ-SUB-FSO-001` $\rightarrow$ `REQ-FNC-FSO-001` $\rightarrow$ `REQ-DER-INT-004` |
| **Downstream Traceability** | RS-422 Transceiver $\rightarrow$ Gimbal Motor Driver $\rightarrow$ Tier 4 Integration Logs |
| **Configuration / Baseline Status** | **PROPOSED (UNDER REVIEW)** |
| **Assumptions or Constraints** | Twisted-pair shielded cabling used to prevent motor PWM induction spikes. |
| **Open Issues / TBD Items** | NOT YET DEFINED — Binary packet checksum algorithm (CRC-16 vs CRC-32). |

---

### Node 7.5: Flight Avionics & Safety Isolation Decomposition Chain

#### 7.5.1 Level 1 System Requirement Node: REQ-SYS-0013
| Field Name | Value / Engineering Content |
| :--- | :--- |
| **Requirement ID** | `REQ-SYS-0013` |
| **Requirement Title** | Asynchronous Bare-Metal Flight Control Isolation |
| **Requirement Statement** | The system shall execute inner-loop attitude stabilization and rate control loops on a dedicated bare-metal 32-bit automotive/aerospace microcontroller (STM32 running PX4) completely decoupled from the Linux edge compute operating system. |
| **Requirement Level** | **Level 1: System-Level Requirement** |
| **Parent Requirement ID** | `OBJ-07` (Indian IP Sovereignty Pillar & Airworthiness Mandate) |
| **Source / Origin** | `REA-T1-OVERVIEW-2026-V1.0`, Section 6 (p. 7); Section 8 (p. 9); Section 10 (p. 11) |
| **Requirement Type** | Safety / Architecture |
| **Allocated Subsystem** | `AVIONICS-CORE` (`STUDY-NODE-07`) |
| **Rationale** | Complex, non-deterministic high-level software processes (neural networks, computer vision, ROS 2 nodes) running on Linux must never compromise flight-critical vehicle stabilization loops. |
| **Verification Method** | Inspection / Test (Tier 3 HIL Latency Testbench) |
| **Verification Status** | UNEXECUTED — Awaiting Tier 3 HIL Avionics Bench Rig |
| **Child Requirement IDs** | `REQ-SUB-AVI-001` `[PROPOSED]` |
| **Upstream Traceability** | `RE-iDEX-PROPOSAL-2026-R1` $\rightarrow$ `OBJ-07` $\rightarrow$ `REQ-SYS-0013` |
| **Downstream Traceability** | `REQ-SUB-AVI-001` $\rightarrow$ `REQ-FNC-AVI-001` $\rightarrow$ `REQ-DER-TIM-003` $\rightarrow$ Tier 3 HIL Verification |
| **Configuration / Baseline Status** | **PROVISIONAL (DRAFT)** — Established in Day 1 SRS Baseline |
| **Assumptions or Constraints** | Microcontroller hardware architecture based on STM32 Cortex-M series running PX4 Autopilot firmware. |
| **Open Issues / TBD Items** | TBD — Exact microcontroller part number (e.g., STM32H7 series vs C-DAC VEGA roadmap chip). |

---

#### 7.5.2 Level 2 Subsystem Requirement Node: REQ-SUB-AVI-001 [PROPOSED]
| Field Name | Value / Engineering Content |
| :--- | :--- |
| **Requirement ID** | `REQ-SUB-AVI-001` `[PROPOSED]` |
| **Requirement Title** | Real-Time Attitude Control Loop Partitioning |
| **Requirement Statement** | The real-time avionics subsystem (`AVIONICS-CORE`) shall execute inner attitude rate and angle stabilization loops on bare-metal firmware without an underlying multi-user operating system. |
| **Requirement Level** | **Level 2: Subsystem-Level Requirement** |
| **Parent Requirement ID** | `REQ-SYS-0013` |
| **Source / Origin** | `REA-T1-OVERVIEW-2026-V1.0`, Section 6 (p. 7); Section 8 (p. 9) |
| **Requirement Type** | Safety / Software |
| **Allocated Subsystem** | `AVIONICS-CORE` (`STUDY-NODE-07`) |
| **Rationale** | Eliminates thread preemption jitter, memory leaks, and operating system panics from affecting flight control surfaces. |
| **Verification Method** | Inspection / Test (Tier 2 SIL & Tier 3 HIL) |
| **Verification Status** | UNEXECUTED — Awaiting Bare-Metal Firmware Build Audit |
| **Child Requirement IDs** | `REQ-FNC-AVI-001` `[PROPOSED]` |
| **Upstream Traceability** | `OBJ-07` $\rightarrow$ `REQ-SYS-0013` $\rightarrow$ `REQ-SUB-AVI-001` |
| **Downstream Traceability** | `REQ-FNC-AVI-001` $\rightarrow$ `REQ-DER-TIM-003` $\rightarrow$ Tier 3 Timing Reports |
| **Configuration / Baseline Status** | **PROPOSED (UNDER REVIEW)** |
| **Assumptions or Constraints** | PX4 flight stack compiled in bare-metal configuration. |
| **Open Issues / TBD Items** | None identified. |

---

#### 7.5.3 Level 3 Functional Requirement Node: REQ-FNC-AVI-001 [PROPOSED]
| Field Name | Value / Engineering Content |
| :--- | :--- |
| **Requirement ID** | `REQ-FNC-AVI-001` `[PROPOSED]` |
| **Requirement Title** | Deterministic 1 kHz Attitude Rate Loop Execution |
| **Requirement Statement** | The flight control firmware shall sample IMU rate gyros and compute actuator PWM motor updates at a deterministic loop frequency of 1,000 Hz ($\pm 2\%$). |
| **Requirement Level** | **Level 3: Functional Requirement** |
| **Parent Requirement ID** | `REQ-SUB-AVI-001` |
| **Source / Origin** | `REA-T1-OVERVIEW-2026-V1.0`, Section 8 (p. 9); Section 10 (p. 11) |
| **Requirement Type** | Functional / Performance |
| **Allocated Subsystem** | `AVIONICS-CORE` (`STUDY-NODE-07`) |
| **Rationale** | 1 kHz loop rates are essential to counteract sudden aerodynamic shears and microbursts in high-altitude mountain valleys. |
| **Verification Method** | Test (Tier 3 HIL Latency Testbench) |
| **Verification Status** | UNEXECUTED — Awaiting Oscilloscope Profiling on HIL Rig |
| **Child Requirement IDs** | `REQ-DER-TIM-003` `[PROPOSED]` |
| **Upstream Traceability** | `OBJ-07` $\rightarrow$ `REQ-SYS-0013` $\rightarrow$ `REQ-SUB-AVI-001` $\rightarrow$ `REQ-FNC-AVI-001` |
| **Downstream Traceability** | `REQ-DER-TIM-003` $\rightarrow$ Tier 3 Oscilloscope Latency Logs |
| **Configuration / Baseline Status** | **PROPOSED (UNDER REVIEW)** |
| **Assumptions or Constraints** | SPI bus between IMU and microcontroller running at 10 MHz or higher. |
| **Open Issues / TBD Items** | None identified. |

---

#### 7.5.4 Level 4 Detailed / Derived Requirement Node: REQ-DER-TIM-003 [PROPOSED]
| Field Name | Value / Engineering Content |
| :--- | :--- |
| **Requirement ID** | `REQ-DER-TIM-003` `[PROPOSED]` |
| **Requirement Title** | Sub-Millisecond Inner-Loop Execution Latency Limit |
| **Requirement Statement** | The total inner attitude loop execution time—measured from sensor interrupt assertion to PWM duty cycle update—shall remain strictly under 1.0 millisecond across 100% of nominal and worst-case operating cycles per Tier 3 exit criteria. |
| **Requirement Level** | **Level 4: Detailed / Derived Requirement** |
| **Parent Requirement ID** | `REQ-FNC-AVI-001` / `REQ-SYS-0023` |
| **Source / Origin** | `REA-T1-OVERVIEW-2026-V1.0`, Section 10 (p. 11: Tier 3 Exit Criteria) |
| **Requirement Type** | Performance / Safety |
| **Allocated Subsystem** | `AVIONICS-CORE` (`STUDY-NODE-07`) |
| **Rationale** | Exceeding 1.0 millisecond latency risks phase lag and fatal pilot-induced oscillations during gust recovery. |
| **Verification Method** | Test (Tier 3 Hardware-in-the-Loop Latency Testing) |
| **Verification Status** | UNEXECUTED — Awaiting Tier 3 Bench Test Logs |
| **Child Requirement IDs** | None (Leaf Node in Decomposition Hierarchy) |
| **Upstream Traceability** | `OBJ-07` $\rightarrow$ `REQ-SYS-0013` $\rightarrow$ `REQ-SUB-AVI-001` $\rightarrow$ `REQ-FNC-AVI-001` $\rightarrow$ `REQ-DER-TIM-003` |
| **Downstream Traceability** | Bare-metal PX4 inner loop $\rightarrow$ GPIO debug pulse $\rightarrow$ Tier 3 HIL Testbench |
| **Configuration / Baseline Status** | **PROPOSED (UNDER REVIEW)** |
| **Assumptions or Constraints** | Measured on dedicated benchtop HIL rig with real-time sensor simulators. |
| **Open Issues / TBD Items** | None identified. Verified against Tier 3 success criteria. |

---

## 8. Requirements Decomposition Framework

### 8.1 Parent-Child Relationships & Derivation Rules
Requirements decomposition on the RudraEdge RE-T1 platform obeys strict systems engineering rules:
1. **Rule of Derivation**: Every Level 2, 3, and 4 requirement must possess an explicit parent link to a higher-level requirement or operational objective.
2. **Rule of Traceability Continuity**: No derived requirement may exist without an unbroken upward path terminating at an authorized Project Objective (`OBJ-01` through `OBJ-07`).
3. **Rule of Subsystem Allocation**: Every Level 2 requirement must be allocated to exactly one primary subsystem module (`MOD-01` through `MOD-06`, `AVIONICS-CORE`, `CRYPTO-ROOT`, or `AIRFRAME-MECH`). Inter-subsystem relationships must be expressed via Level 4 Interface Requirements (`REQ-DER-INT-xxx`).
4. **Rule of Scope Non-Expansion**: Derived child requirements must refine, quantify, or implement the parent requirement; they must never silently expand project operational scope beyond authorized documents.



### 8.2 Comprehensive Parent-Child Decomposition Register
The following table provides the complete hierarchical mapping connecting parent nodes to derived child requirements across all evaluated subsystems:

| Parent Requirement ID | Requirement ID | Requirement Title | Level | Allocated Subsystem | Child Requirement IDs | Decomposition Rationale & Derivation Scope |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| OBJ-01 (GNSS-Denied Flight) | REQ-SYS-0001 | GNSS-Denied 6-DOF Localization | Level 1 | MOD-01 (VIO-NAV) | REQ-SUB-VIO-001 | System-level requirement addressing satellite GPS jamming in mountain theaters. |
| REQ-SYS-0001 | REQ-SUB-VIO-001 | Multi-Sensor Odometry Allocation | Level 2 | MOD-01 (VIO-NAV) | REQ-FNC-VIO-001 | Subsystem allocation of multi-sensor fusion (IMU + VIO + LiDAR) on MOD-01. |
| REQ-SUB-VIO-001 | REQ-FNC-VIO-001 | Visual Feature Point Tracking | Level 3 | MOD-01 (VIO-NAV) | REQ-DER-INT-001 | Functional visual tracking pipeline maintaining $\\ge 30\\text{ Hz}$ update rate. |
| REQ-FNC-VIO-001 | REQ-DER-INT-001 | VIO-to-PX4 ROS 2 Interface | Level 4 | MOD-01 $\\leftrightarrow$ AVIONICS-CORE | None (Leaf) | Detailed Micro-XRCE-DDS /re_t1/nav/odometry topic publication at 50 Hz. |
| OBJ-05 (Multi-Modal Perception)| REQ-SYS-0002 | Stabilized Multi-Spectral Imaging | Level 1 | MOD-02 (EO-IR-GIMBAL)| TBD (Milestone 2) | Dual daylight CMOS + LWIR thermal gimbal routed over MIPI-CSI Gen3 DMA. |
| OBJ-02 (Heterogeneous Edge AI) | REQ-SYS-0003 | Zero-Cloud Neural Inferencing | Level 1 | MOD-03 (EDGE-AI) | REQ-SUB-AI-001 | Onboard INT8 neural inferencing eliminating dependency on cloud or RF datalinks. |
| REQ-SYS-0003 | REQ-SUB-AI-001 | Edge AI Runtime Environment | Level 2 | MOD-03 (EDGE-AI) | REQ-FNC-AI-001 | Subsystem allocation of air-gapped containerized TensorRT runtime. |
| REQ-SUB-AI-001 | REQ-FNC-AI-001 | Real-Time INT8 Segmentation | Level 3 | MOD-03 (EDGE-AI) | REQ-DER-INT-002 | Functional semantic segmentation at $\\ge 15\\text{ FPS}$ on 1080p synchronized video. |
| REQ-FNC-AI-001 | REQ-DER-INT-002 | Zero-Copy POSIX Shared Memory | Level 4 | MOD-03 $\\leftrightarrow$ MOD-02 | None (Leaf) | Detailed DMA ingress directly into POSIX /dev/shm zero-copy frame buffers. |
| OBJ-02 (Heterogeneous Edge AI) | REQ-SYS-0004 | Onboard Change Detection | Level 1 | MOD-03 (EDGE-AI) | TBD (Milestone 2) | Temporal visual comparison against historical terrain embeddings. |
| OBJ-02 (Heterogeneous Edge AI) | REQ-SYS-0005 | Neural Super-Resolution | Level 1 | MOD-03 (EDGE-AI) | TBD (Milestone 2) | Onboard neural image upscaling to enhance degraded atmospheric imagery. |
| OBJ-02 (Heterogeneous Edge AI) | REQ-SYS-0006 | Autonomous SAR Path Planning | Level 1 | MOD-03 / SWADESHI-ROS| TBD (Milestone 2) | Autonomous search and rescue waypoint calculation under ROS 2 mission coordination. |
| OBJ-05 (Multi-Modal Perception)| REQ-SYS-0007 | Wideband RF Spectrum Sensing | Level 1 | MOD-04 (EW-DSP) | REQ-SUB-EW-001 | Broad spectrum monitoring across 400 MHz to 6 GHz to detect hostile radar & jammers. |
| REQ-SYS-0007 | REQ-SUB-EW-001 | Wideband SDR & DSP Slicing | Level 2 | MOD-04 (EW-DSP) | REQ-FNC-EW-001 | Subsystem allocation of wideband SDR tuner and dedicated FIR/IIR DSP filtering. |
| REQ-SUB-EW-001 | REQ-FNC-EW-001 | Real-Time RF Peak Detection | Level 3 | MOD-04 (EW-DSP) | REQ-DER-INT-003 | Functional spectral peak detection $>10\\text{ dB}$ above noise within 50 ms. |
| REQ-FNC-EW-001 | REQ-DER-INT-003 | VITA 49 Radio Transport Bus | Level 4 | STUDY-NODE-15 $\\leftrightarrow$ MOD-04 | None (Leaf) | Detailed protocol encapsulation of I/Q samples into ANSI/VITA 49 packets over GbE. |
| OBJ-05 (Multi-Modal Perception)| REQ-SYS-0008 | Acoustic Impulse TDoA Bearing | Level 1 | MOD-04 (EW-DSP) | TBD (Milestone 2) | 4-channel microphone array TDoA localization of gunfire and artillery blasts. |
| OBJ-06 (Jam-Resistant Link) | REQ-SYS-0009 | Directional FSO Optical Link | Level 1 | MOD-05 (FSO-COMM) | REQ-SUB-FSO-001 | High-bandwidth laser data link impervious to RF jamming. |
| REQ-SYS-0009 | REQ-SUB-FSO-001 | Coarse-Fine PAT Allocation | Level 2 | MOD-05 (FSO-COMM) | REQ-FNC-FSO-001 | Subsystem allocation of 2-axis coarse gimbal and fast-steering mirror. |
| REQ-SUB-FSO-001 | REQ-FNC-FSO-001 | Closed-Loop Beam Tracking | Level 3 | MOD-05 (FSO-COMM) | REQ-DER-INT-004 | Functional acquisition within 10s and tracking jitter $\\le \\pm 50\\ \\mu\\text{rad}$. |
| REQ-FNC-FSO-001 | REQ-DER-INT-004 | RS-422 Serial High-Rate Gyro | Level 4 | AVIONICS-CORE $\\leftrightarrow$ MOD-05 | None (Leaf) | Detailed high-speed RS-422 serial interface streaming gyro deltas at 500 Hz. |
| OBJ-06 (Jam-Resistant Link) | REQ-SYS-0010 | Resilient SDR RF Backup Link | Level 1 | MOD-05 / STUDY-NODE-15 | TBD (Milestone 2) | Encrypted frequency-hopping RF channel acting as automated fallback link. |
| OBJ-03 (High-Altitude Cap) | REQ-SYS-0011 | Precision Cargo Delivery | Level 1 | MOD-06 (PAYLOAD-POD)| TBD (Milestone 3) | Wind-compensated ballistic delivery of emergency logistic supplies. |
| OBJ-03 (High-Altitude Cap) | REQ-SYS-0012 | Dual-Redundant Safety Interlock| Level 1 | MOD-06 / AVIONICS-CORE | TBD (Milestone 2) | Hardware opto-isolated interlock preventing accidental uncommanded unlatching. |
| OBJ-07 (Indian IP Sovereignty) | REQ-SYS-0013 | Bare-Metal Flight Control Iso | Level 1 | AVIONICS-CORE | REQ-SUB-AVI-001 | Decouples inner-loop flight stabilization from Linux compute operating system. |
| REQ-SYS-0013 | REQ-SUB-AVI-001 | Attitude Loop Partitioning | Level 2 | AVIONICS-CORE | REQ-FNC-AVI-001 | Subsystem allocation of bare-metal PX4 firmware loops on STM32 MCU. |
| REQ-SUB-AVI-001 | REQ-FNC-AVI-001 | Deterministic 1 kHz Attitude | Level 3 | AVIONICS-CORE | REQ-DER-TIM-003 | Functional attitude rate sampling and PWM update at strict 1,000 Hz ($\\pm 2\\%$). |
| REQ-FNC-AVI-001 | REQ-DER-TIM-003 | Sub-Millisecond Inner Latency | Level 4 | AVIONICS-CORE | None (Leaf) | Detailed loop execution latency $< 1.0\\text{ ms}$ satisfying Tier 3 exit criteria. |
| OBJ-07 (Indian IP Sovereignty) | REQ-SYS-0014 | Autopilot Watchdog Failsafe | Level 1 | AVIONICS-CORE / SWADESHI | TBD (Milestone 2) | Uninterrupted flight stabilization and RTH upon AI compute freeze or crash. |
| OBJ-03 (High-Altitude Cap) | REQ-SYS-0015 | High-Altitude Cold Resilience | Level 1 | AIRFRAME-MECH / AVIONICS | TBD (Milestone 2) | Uninterrupted electronics and propulsion operation at $-20^\\circ\\text{C}$ cold soak. |
| OBJ-04 (Stealth & Low Sig) | REQ-SYS-0016 | Faceted Low-RCS Stealth Airframe| Level 1 | AIRFRAME-MECH (NODE-18)| TBD (Milestone 3) | Faceted composite geometry and RAM to minimize radar and visual detection. |
| OBJ-07 (Indian IP Sovereignty) | REQ-SYS-0017 | Hardware Root of Trust & Boot | Level 1 | CRYPTO-ROOT (NODE-10)| TBD (Milestone 2) | Hardware-enforced cryptographic validation of signed bootloader and OS keys. |
| OBJ-07 (Indian IP Sovereignty) | REQ-SYS-0018 | Zero-Trace Memory Sanitization | Level 1 | CRYPTO-ROOT (NODE-10)| TBD (Milestone 2) | Automated zero-trace memory erasure upon physical breach, tamper, or capture. |
| OBJ-07 (Indian IP Sovereignty) | REQ-SYS-0019 | Swadeshi ROS 2 & Micro-XRCE | Level 1 | SWADESHI-ROS / AVIONICS| TBD (Milestone 2) | 100% sovereign robotics middleware stack eliminating foreign IP dependencies. |
| OBJ-07 (Indian IP Sovereignty) | REQ-SYS-0020 | Air-Gapped Local Networking | Level 1 | EDGE-COMPUTE-FABRIC | TBD (Milestone 2) | Inter-process communication restricted strictly to local POSIX shared memory. |
| OBJ-05 (Multi-Modal Perception)| REQ-SYS-0021 | Micro-GPR Ingress & DSP Slicing| Level 1 | MOD-04 / STUDY-NODE-12 | TBD (Milestone 4) | 16-bit IQ radar stream ingestion into dedicated DSP thread via SPI/USB 3.0. |
| OBJ-05 (Multi-Modal Perception)| REQ-SYS-0022 | Airborne CBRN Hazard Sniffing | Level 1 | STUDY-NODE-14 (CBRN) | TBD (Milestone 4) | Digital atmospheric sampling and coordinate logging of toxic airborne agents. |
| OBJ-07 (Indian IP Sovereignty) | REQ-SYS-0023 | Inner Flight Control Latency | Level 4 | AVIONICS-CORE (NODE-07)| None (Leaf) | Sub-millisecond inner attitude loop latency requirement (traceable to REQ-SYS-0013).|
| OBJ-05 (Multi-Modal Perception)| REQ-SYS-0024 | Electromagnetic Shielding (EMI)| Level 4 | MOD-04 / AVIONICS-CORE | None (Leaf) | Physical EMI gasket shielding isolating wideband SDR receiver from motor lines. |
| OBJ-07 (Indian IP Sovereignty) | REQ-SYS-0025 | Indigenous Silicon Roadmap | Level 1 | EDGE-COMPUTE-FABRIC | TBD (Milestone 5) | Portability roadmap ensuring code compilation on C-DAC VEGA & IIT SHAKTI CPUs. |


### 8.3 Orphan Requirement Handling Protocol
An **orphan requirement** is any requirement that lacks an upstream parent requirement.
* **Detection Mechanism**: Automated query of the Traceability Matrix checking column `Parent Requirement ID` for empty or invalid entries.
* **Review Protocol**: If an orphan requirement is detected:
  1. It is flagged with status `ORPHAN — AWAITING PARENT ALLOCATION`.
  2. The Systems Requirements Engineer determines whether an implicit operational requirement was omitted from the higher level or if the requirement represents unauthorized scope creep ("gold plating").
  3. If legitimate, a parent requirement change request (CR) is submitted for review. If illegitimate, the orphan requirement is rejected.
  4. **Baseline Prohibition**: No orphan requirement may be baselined or approved.

### 8.4 Childless Parent Requirement Handling Protocol
A **childless parent** is a high-level requirement that has not yet been decomposed into subsystem or functional requirements.
* **Detection Mechanism**: Inspection of column `Child Requirement IDs` in the parent tracking record.
* **Handling Protocol**:
  1. In the starter baseline (Milestone 1), high-level requirements without completed decomposition are flagged with `DECOMPOSITION PENDING`.
  2. If a requirement is an atomic system constraint (e.g., an overall platform weight limit) that requires no functional breakdown, it is explicitly classified as `ATOMIC / DIRECT VERIFICATION`.
  3. All other childless requirements must be scheduled for decomposition prior to the Milestone 1 SRS freeze.

---

---

# ==============================================================================
# PART II: TASK 4 — BIDIRECTIONAL MAPPING MATRIX DESIGN
# ==============================================================================

## 9. Bidirectional Traceability Wireframe (16-Column Master Matrix)

Below is the complete 16-column **Bidirectional Traceability Wireframe** specified in Task 4. It links source documents, requirements across all four hierarchy levels, allocated subsystems, implementation artifacts, verification methods, and test case evidence.

| Source Reference | Source Req ID | Parent Req ID | Requirement ID | Requirement Title | Requirement Level | Requirement Type | Allocated Subsystem | Implementation Reference | Verification Method | Test Case ID | Verification Evidence | Forward Traceability Status | Backward Traceability Status | Configuration / Baseline Status | Open Issues / Remarks |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 2 | `OBJ-01` | N/A — Top-Level Requirement | `REQ-SYS-0001` | GNSS-Denied 6-DOF Localization | Level 1 | Functional / Performance | `MOD-01` (`VIO-NAV`) | `src/modules/vio_nav/` (TBD) | Test / Demonstration | `TC-NAV-001` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | DRAFT | `ISSUE-REQ-001`: DEM grid resolution unstated. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 7 | `OBJ-01` | `REQ-SYS-0001` | `REQ-SUB-VIO-001` | Multi-Sensor Odometry Allocation | Level 2 | Functional / Architecture | `MOD-01` (`VIO-NAV`) | `src/modules/vio_nav/fusion/` (TBD) | Demonstration / Test | `TC-NAV-002` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | PROPOSED | Derived from REQ-SYS-0001. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 4 | `OBJ-01` | `REQ-SUB-VIO-001` | `REQ-FNC-VIO-001` | Visual Feature Point Tracking | Level 3 | Functional / Algorithmic | `MOD-01` (`VIO-NAV`) | `src/modules/vio_nav/features/` (TBD) | Analysis / Simulation | `TC-NAV-003` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | PROPOSED | Target tracking rate $\ge 30\text{ Hz}$. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 8 | `OBJ-01` | `REQ-FNC-VIO-001` | `REQ-DER-INT-001` | VIO-to-PX4 ROS 2 Interface | Level 4 | Interface / Performance | `MOD-01` $\leftrightarrow$ `AVIONICS-CORE` | `src/bridge/micro_xrce/` (TBD) | Test / Inspection | `TC-INT-001` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | PROPOSED | Micro-XRCE-DDS odometry topic (50 Hz). |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 7 | `OBJ-05` | N/A — Top-Level Requirement | `REQ-SYS-0002` | Stabilized Multi-Spectral Imaging | Level 1 | Functional / Interface | `MOD-02` (`EO-IR-GIMBAL`) | `src/drivers/camera_gimbal/` (TBD)| Demonstration / Test | `TC-CAM-001` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | DRAFT | `ISSUE-REQ-002`: Optical zoom ratio unstated. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 2 | `OBJ-02` | N/A — Top-Level Requirement | `REQ-SYS-0003` | Zero-Cloud Neural Inferencing | Level 1 | Functional / Performance | `MOD-03` (`EDGE-AI`) | `src/modules/edge_ai/` (TBD) | Demonstration / Analysis | `TC-AI-001` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | DRAFT | `ISSUE-REQ-003`: Interim COTS SoC unstated. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 6 | `OBJ-02` | `REQ-SYS-0003` | `REQ-SUB-AI-001` | Edge AI Runtime Environment | Level 2 | Functional / Software | `MOD-03` (`EDGE-AI`) | `docker/edge_runtime/` (TBD) | Inspection / Demonstration | `TC-AI-002` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | PROPOSED | Air-gapped containerized runtime. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 7 | `OBJ-02` | `REQ-SUB-AI-001` | `REQ-FNC-AI-001` | Real-Time INT8 Segmentation | Level 3 | Performance / Functional | `MOD-03` (`EDGE-AI`) | `models/segmentation_int8/` (TBD) | Demonstration / Test | `TC-AI-003` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | PROPOSED | Target throughput $\ge 15\text{ FPS}$ at 1080p. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 8 | `OBJ-02` | `REQ-FNC-AI-001` | `REQ-DER-INT-002` | Zero-Copy POSIX Shared Memory | Level 4 | Interface / Performance | `MOD-03` $\leftrightarrow$ `MOD-02` | `src/drivers/mipi_dma_shm/` (TBD) | Test / Analysis | `TC-INT-002` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | PROPOSED | Direct Memory Access DMA to shm buffer. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 5 | `OBJ-02` | N/A — Top-Level Requirement | `REQ-SYS-0004` | Onboard Change Detection | Level 1 | Functional | `MOD-03` (`EDGE-AI`) | `src/modules/edge_ai/change/` (TBD) | Demonstration | `TC-AI-004` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | DRAFT | `ISSUE-REQ-004`: Detection threshold unstated. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 2 | `OBJ-02` | N/A — Top-Level Requirement | `REQ-SYS-0005` | Neural Super-Resolution | Level 1 | Functional | `MOD-03` (`EDGE-AI`) | `src/modules/edge_ai/sr/` (TBD) | Demonstration | `TC-AI-005` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | DRAFT | `ISSUE-REQ-005`: Upscaling factor unstated. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 6 | `OBJ-02` | N/A — Top-Level Requirement | `REQ-SYS-0006` | Autonomous SAR Path Planning | Level 1 | Functional | `MOD-03` / `SWADESHI-ROS`| `src/modules/sar_planner/` (TBD) | Demonstration / Test | `TC-AI-006` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | DRAFT | Dynamic search waypoint generation. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 7 | `OBJ-05` | N/A — Top-Level Requirement | `REQ-SYS-0007` | Wideband RF Spectrum Sensing | Level 1 | Functional / Performance | `MOD-04` (`EW-DSP`) | `src/modules/ew_dsp/` (TBD) | Test / Analysis | `TC-EW-001` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | DRAFT | `ISSUE-REQ-006`: RF sensitivity unstated. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 7 | `OBJ-05` | `REQ-SYS-0007` | `REQ-SUB-EW-001` | Wideband SDR & DSP Slicing | Level 2 | Functional / Architecture | `MOD-04` (`EW-DSP`) | `src/modules/ew_dsp/fft_pipe/` (TBD)| Demonstration / Test | `TC-EW-002` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | PROPOSED | 400 MHz to 6 GHz spectral coverage. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 5 | `OBJ-05` | `REQ-SUB-EW-001` | `REQ-FNC-EW-001` | Real-Time RF Peak Detection | Level 3 | Functional / Performance | `MOD-04` (`EW-DSP`) | `src/modules/ew_dsp/peak_det/` (TBD) | Test / Simulation | `TC-EW-003` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | PROPOSED | 10 dB above noise floor within 50 ms. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 8 | `OBJ-05` | `REQ-FNC-EW-001` | `REQ-DER-INT-003` | VITA 49 Radio Transport Bus | Level 4 | Interface / Protocol | `STUDY-NODE-15` $\leftrightarrow$ `MOD-04` | `src/drivers/vita49_rx/` (TBD) | Inspection / Test | `TC-INT-003` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | PROPOSED | VITA 49 packets over GbE / PCIe. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 7 | `OBJ-05` | N/A — Top-Level Requirement | `REQ-SYS-0008` | Acoustic Impulse TDoA Bearing | Level 1 | Functional | `MOD-04` (`EW-DSP`) | `src/modules/ew_dsp/acoustic/` (TBD)| Demonstration / Test | `TC-EW-004` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | DRAFT | `ISSUE-REQ-007`: Angular accuracy unstated. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 2 | `OBJ-06` | N/A — Top-Level Requirement | `REQ-SYS-0009` | Directional FSO Optical Link | Level 1 | Functional / Performance | `MOD-05` (`FSO-COMM`) | `src/modules/fso_comm/` (TBD) | Demonstration / Test | `TC-FSO-001` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | DRAFT | `ISSUE-REQ-008`: Laser wavelength unstated. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 7 | `OBJ-06` | `REQ-SYS-0009` | `REQ-SUB-FSO-001` | Coarse-Fine PAT Allocation | Level 2 | Functional / Mechatronics | `MOD-05` (`FSO-COMM`) | `src/modules/fso_comm/pat/` (TBD) | Test / Demonstration | `TC-FSO-002` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | PROPOSED | 2-axis gimbal + fast-steering mirror. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 8 | `OBJ-06` | `REQ-SUB-FSO-001` | `REQ-FNC-FSO-001` | Closed-Loop Beam Tracking | Level 3 | Functional / Performance | `MOD-05` (`FSO-COMM`) | `src/modules/fso_comm/tracking/` (TBD)| Test / Analysis | `TC-FSO-003` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | PROPOSED | Acquisition within 10s; $\pm 50\ \mu\text{rad}$. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 8 | `OBJ-06` | `REQ-FNC-FSO-001` | `REQ-DER-INT-004` | RS-422 Serial High-Rate Gyro | Level 4 | Interface / Performance | `AVIONICS-CORE` $\leftrightarrow$ `MOD-05` | `src/drivers/serial_rs422/` (TBD) | Test / Inspection | `TC-INT-004` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | PROPOSED | 921,600 baud, 500 Hz gyro streaming. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 2 | `OBJ-06` | N/A — Top-Level Requirement | `REQ-SYS-0010` | Resilient SDR RF Backup Link | Level 1 | Functional / Interface | `MOD-05` / `STUDY-NODE-15` | `src/drivers/sdr_link/` (TBD) | Test | `TC-COMM-001` (TBD)| NOT ESTABLISHED | PARTIAL | PARTIAL | DRAFT | `ISSUE-REQ-009`: Failover timeout unstated. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 7 | `OBJ-03` | N/A — Top-Level Requirement | `REQ-SYS-0011` | Precision Cargo Delivery | Level 1 | Functional | `MOD-06` (`PAYLOAD-POD`) | `src/modules/cargo_ballistics/` (TBD)| Demonstration / Test | `TC-POD-001` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | DRAFT | Wind-compensated release calculations. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 4 | `OBJ-03` | N/A — Top-Level Requirement | `REQ-SYS-0012` | Dual-Redundant Safety Interlock| Level 1 | Safety / Interface | `MOD-06` / `AVIONICS-CORE` | `hardware/interlock_circuit/` (TBD) | Test / Inspection | `TC-POD-002` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | DRAFT | Prevents uncommanded release during boot. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 6 | `OBJ-07` | N/A — Top-Level Requirement | `REQ-SYS-0013` | Bare-Metal Flight Control Iso | Level 1 | Safety / Architecture | `AVIONICS-CORE` | `firmware/px4_stm32/` (TBD) | Inspection / Test | `TC-AVI-001` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | DRAFT | Core airworthiness isolation pillar. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 6 | `OBJ-07` | `REQ-SYS-0013` | `REQ-SUB-AVI-001` | Attitude Loop Partitioning | Level 2 | Safety / Software | `AVIONICS-CORE` | `firmware/px4_stm32/attitude/` (TBD)| Inspection / Test | `TC-AVI-002` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | PROPOSED | Bare-metal execution without Linux OS. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 8 | `OBJ-07` | `REQ-SUB-AVI-001` | `REQ-FNC-AVI-001` | Deterministic 1 kHz Attitude | Level 3 | Functional / Performance | `AVIONICS-CORE` | `firmware/px4_stm32/rate_loop/` (TBD)| Test | `TC-AVI-003` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | PROPOSED | 1,000 Hz ($\pm 2\%$) loop iteration. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 10 | `OBJ-07` | `REQ-FNC-AVI-001` | `REQ-DER-TIM-003` | Sub-Millisecond Inner Latency | Level 4 | Performance / Safety | `AVIONICS-CORE` | `firmware/px4_stm32/irq_handler/` (TBD)| Test | `TC-AVI-004` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | PROPOSED | Loop latency $< 1.0\text{ ms}$ per Tier 3. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 8 | `OBJ-07` | N/A — Top-Level Requirement | `REQ-SYS-0014` | Autopilot Watchdog Failsafe | Level 1 | Safety / Reliability | `AVIONICS-CORE` / `SWADESHI-ROS`| `firmware/failsafe_watchdog/` (TBD) | Test | `TC-AVI-005` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | DRAFT | Uninterrupted flight upon compute crash. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 2 | `OBJ-03` | N/A — Top-Level Requirement | `REQ-SYS-0015` | High-Altitude Cold Resilience | Level 1 | Environmental / Thermal | `AIRFRAME-MECH` / `AVIONICS-CORE`| `hardware/thermal_enclosure/` (TBD) | Test | `TC-ENV-001` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | DRAFT | $-20^\circ\text{C}$ environmental cold soak. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 2 | `OBJ-04` | N/A — Top-Level Requirement | `REQ-SYS-0016` | Faceted Low-RCS Stealth Airframe| Level 1 | Structural / Stealth | `AIRFRAME-MECH` (`STUDY-NODE-18`)| `cad/airframe_stealth/` (TBD) | Analysis / Inspection | `TC-STR-001` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | DRAFT | `ISSUE-REQ-010`: Airframe OML CAD unstated. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 1 | `OBJ-07` | N/A — Top-Level Requirement | `REQ-SYS-0017` | Hardware Root of Trust & Boot | Level 1 | Security / Cryptography | `CRYPTO-ROOT` (`STUDY-NODE-10`)| `hardware/rot_vault/` (TBD) | Inspection / Test | `TC-SEC-001` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | DRAFT | Cryptographic verification of boot keys. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 1 | `OBJ-07` | N/A — Top-Level Requirement | `REQ-SYS-0018` | Zero-Trace Memory Sanitization | Level 1 | Security / Cryptography | `CRYPTO-ROOT` (`STUDY-NODE-10`)| `firmware/zero_trace_purge/` (TBD) | Test / Demonstration | `TC-SEC-002` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | DRAFT | Instant flash memory wipe upon tamper. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 6 | `OBJ-07` | N/A — Top-Level Requirement | `REQ-SYS-0019` | Swadeshi ROS 2 & Micro-XRCE | Level 1 | Software / Interface | `SWADESHI-ROS` / `AVIONICS-CORE`| `src/middleware/swadeshi_ros2/` (TBD)| Inspection / Test | `TC-SW-001` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | DRAFT | 100% sovereign robotics middleware stack.|
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 8 | `OBJ-07` | N/A — Top-Level Requirement | `REQ-SYS-0020` | Air-Gapped Local Networking | Level 1 | Security / Interface | `EDGE-COMPUTE-FABRIC` | `system/networking_config/` (TBD) | Inspection / Analysis | `TC-SEC-003` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | DRAFT | Zero external IP network listening ports.|
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 7 | `OBJ-05` | N/A — Top-Level Requirement | `REQ-SYS-0021` | Micro-GPR Ingress & DSP Slicing| Level 1 | Functional / Interface | `MOD-04` / `STUDY-NODE-12` | `src/drivers/micro_gpr/` (TBD) | Demonstration / Test | `TC-PAY-001` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | DRAFT | 16-bit IQ sample ingress via SPI/USB 3.0.|
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 3 | `OBJ-05` | N/A — Top-Level Requirement | `REQ-SYS-0022` | Airborne CBRN Hazard Sniffing | Level 1 | Functional / Sensor | `STUDY-NODE-14` (CBRN) | `src/drivers/cbrn_sniffer/` (TBD) | Demonstration | `TC-PAY-002` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | DRAFT | Digital hazard concentration logging. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 10 | `OBJ-07` | `REQ-SYS-0013` | `REQ-SYS-0023` | Inner Flight Control Latency | Level 4 | Performance / Safety | `AVIONICS-CORE` (`STUDY-NODE-07`)| `firmware/px4_stm32/latency/` (TBD) | Test | `TC-AVI-004` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | DRAFT | Sub-millisecond inner loop latency. |
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 8 | `OBJ-05` | `REQ-SYS-0007` | `REQ-SYS-0024` | Electromagnetic Shielding (EMI)| Level 4 | Interface / EMC | `MOD-04` / `AVIONICS-CORE` | `hardware/emi_shielding/` (TBD) | Test / Inspection | `TC-EMC-001` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | DRAFT | Gasket isolation of SDR from motor noise.|
| `REA-T1-OVERVIEW-2026-V1.0`, Sec 1 | `OBJ-07` | N/A — Top-Level Requirement | `REQ-SYS-0025` | Indigenous Silicon Roadmap | Level 1 | Architecture / Portability | `EDGE-COMPUTE-FABRIC` | `toolchains/riscv_vega_shakti/` (TBD)| Analysis / Inspection | `TC-SW-002` (TBD) | NOT ESTABLISHED | PARTIAL | PARTIAL | DRAFT | Roadmap to C-DAC VEGA & SHAKTI processors.|

*Note: In accordance with task order rules, implementation paths marked `(TBD)` and test cases marked `(TBD)` are placeholder allocations awaiting code repo creation and formal test procedure authoring. No fake test results or falsified verification evidence have been introduced.*

---

## 10. Forward Traceability Procedure

### 10.1 Forward Traceability Flow
Forward traceability tracks the logical realization of an operational objective from left to right:
$$\text{Project Objective / Source} \longrightarrow \text{System Requirement} \longrightarrow \text{Subsystem Requirement} \longrightarrow \text{Functional/Derived Req} \longrightarrow \text{Implementation Artifact} \longrightarrow \text{Verification Method} \longrightarrow \text{Test Evidence}$$

### 10.2 Forward Verification Walkthrough
To verify forward traceability during design and reviews:
1. **Source Ingress**: Select an operational objective (e.g., `OBJ-01`) or source document reference.
2. **System Requirement Allocation**: Verify that at least one Level 1 requirement (`REQ-SYS-xxxx`) captures the operational objective.
3. **Subsystem Decomposition**: Trace the Level 1 requirement to its derived Level 2 subsystem requirement (`REQ-SUB-xxxx`). Verify that the allocated subsystem has clear architectural boundaries.
4. **Functional Specification**: Trace from Level 2 to Level 3 functional requirements (`REQ-FNC-xxxx`) and Level 4 detailed interface/timing requirements (`REQ-DER-xxxx`).
5. **Implementation Linking**: Verify that every leaf requirement points to an explicit implementation artifact (source code directory, firmware module, hardware schematic, or configuration file).
6. **Verification Closure**: Trace the requirement to an assigned verification method and test case identifier. When executed, confirm that verified test records provide empirical proof of compliance.

### 10.3 Identifying Forward Traceability Gaps
* **Unallocated Requirements**: A requirement with an unassigned subsystem is flagged `GAP: UNALLOCATED`.
* **Unimplemented Requirements**: A requirement without an implementation reference is flagged `FORWARD GAP: NO IMPLEMENTATION`.
* **Unverified Requirements**: A requirement without an associated test case or verification method is flagged `FORWARD GAP: UNVERIFIED`.

---

## 11. Backward Traceability Procedure

### 11.1 Backward Traceability Flow
Backward traceability traces physical artifacts, source code, and test evidence in reverse order back to the authorizing requirement and origin:
$$\text{Test Evidence / Results} \longrightarrow \text{Test Case ID} \longrightarrow \text{Verification Method} \longrightarrow \text{Implementation Artifact} \longrightarrow \text{Derived / Functional Req} \longrightarrow \text{Parent System Req} \longrightarrow \text{Source Document}$$

### 11.2 Backward Verification Walkthrough
To verify backward traceability during quality audits:
1. **Test Case Origin**: Select a test case or flight trial log (e.g., `TC-NAV-001`). Confirm that it evaluates a specific requirement.
2. **Implementation Justification**: Inspect a source code repository module or firmware routine. Verify that an associated requirement ID justifies its inclusion.
3. **Parent Hierarchy Ascent**: Trace the requirement identifier up to its immediate parent requirement.
4. **Source Anchor**: Trace the parent requirement up to the authorizing Level 1 operational objective and contractual source document (`RE-iDEX-PROPOSAL-2026-R1` or `REA-T1-OVERVIEW-2026-V1.0`).

### 11.3 Identifying Backward Traceability Gaps
* **Rogue / Gold-Plated Implementation**: Any source code, hardware circuit, or effector mechanism that cannot be traced backward to an approved requirement is flagged as `BACKWARD GAP: ROGUE IMPLEMENTATION` and marked for removal or formal change request.
* **Orphan Test Cases**: Any test script or laboratory fixture that does not verify an explicit requirement is flagged `BACKWARD GAP: ORPHAN TEST CASE`.
* **Missing Source Justification**: Any requirement without an upstream parent or source citation is flagged `BACKWARD GAP: UNJUSTIFIED REQUIREMENT`.

---

## 12. Requirement Verification and Validation

### 12.1 The 10-Tier Validation Ladder
Verification on RE-T1 is structured across the **10-Tier Validation Ladder** defined in Section 10 of `REA-T1-OVERVIEW-2026-V1.0`. No subsystem advances to subsequent tiers without satisfying formal exit criteria:

```
[ Tier 10: Field Demonstration ]                <-- High-altitude tactical mission scenarios
      ^
[ Tier 09: Integrated Payload Runs ]           <-- EO/IR + GPR + Acoustic + FSO concurrent
      ^
[ Tier 08: GNSS-Denied Testing ]               <-- Deliberate satellite jamming, VIO drift < 1m
      ^
[ Tier 07: Controlled Free Flight ]            <-- Nominal GNSS open-air baseline flights
      ^
[ Tier 06: Tethered Flight Trials ]            <-- Closed-loop hover under mechanical arrest
      ^
[ Tier 05: Environmental Chamber ]             <-- -20°C cold soak & low-pressure chamber
      ^
[ Tier 04: Benchtop Integration ]              <-- Zero bus collision, multi-sensor electrical
      ^
[ Tier 03: Hardware-in-the-Loop (HIL) ]        <-- Inner-loop latency < 1 ms on real MCUs
      ^
[ Tier 02: Software-in-the-Loop (SIL) ]        <-- ROS 2 + PX4 in Gazebo mountain digital twin
      ^
[ Tier 01: Algorithm Simulation ]              <-- Pure software VIO, CNN, path planning
```

### 12.2 Verification Methods
* **Inspection (I)**: Visual, physical, or dimensional audit of drawings, code architectures, wiring diagrams, and configuration files.
* **Analysis (A)**: Mathematical calculations, link budgets, structural finite element modeling (FEM), and computational fluid dynamics (CFD).
* **Demonstration (D)**: Qualitative operational verification of system capabilities without precision measurement equipment.
* **Test (T)**: Quantitative evaluation using calibrated instrumentation against specified pass/fail performance criteria.

### 12.3 Status Handling and Verification Gaps
* `UNEXECUTED`: Test case defined, but test execution has not occurred.
* `PENDING TESTBENCH`: Awaiting completion of physical benchtop, environmental chamber, or airframe hardware.
* `PASSED`: Verification executed with formal test logs demonstrating complete satisfaction of acceptance criteria.
* `FAILED`: Verification executed and failed to meet acceptance criteria; non-conformance report (NCR) generated.
* **Current Baseline State**: At Day 2 of the Pre-Implementation phase, **0% of hardware flight tests are executed**. All test statuses are correctly marked `UNEXECUTED` or `NOT ESTABLISHED`.

---

## 13. Configuration and Baseline Management

### 13.1 Requirements Revision Tracking
All requirements are subject to formal configuration control:
* **Initial Draft**: Tagged as `Rev 0.1` or `Rev A (Draft)`.
* **Baseline Freeze**: Following stakeholder review at Milestone 1 (M1–M4), approved requirements transition to `Rev 1.0 (Frozen Baseline)`.
* **Change Identifier**: Any modification requires a formal Engineering Change Proposal (ECP) with revision increments (`Rev 1.1`, `Rev 1.2`).

### 13.2 Change Impact Assessment Procedure
When a requirement change is proposed:
1. **Identify Upstream Impact**: Query the Bidirectional Traceability Matrix to assess whether parent requirements or project objectives are affected.
2. **Identify Downstream Impact**: Assess child functional requirements, bus interfaces, software modules, and scheduled test cases affected by the modification.
3. **Evaluate Physical / Safety Boundaries**: Check if change compromises the bare-metal flight safety isolation firewall.
4. **Review Board Action**: The Change Control Board (CCB) reviews the impact assessment before approving or rejecting the ECP.

---

## 14. Open Issues and TBD Register

The following unresolved items, unstated technical parameters, and missing source data are recorded for investigation during Milestone 1:

| Issue ID | Related Requirement | Category | Issue Description | Source Reference | Potential Impact | Recommended Engineering Action | Status |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `ISSUE-REQ-001` | `REQ-SYS-0001` | Missing Metric | DEM terrain matching spatial resolution and update frequency omitted. | `REA-T1-OVERVIEW-2026-V1.0`, p. 8 | Cannot size onboard flash storage or Kalman filter innovation limits. | Specify DEM grid resolution (e.g., 5m vs 30m grid) and coordinate projection. | **OPEN** |
| `ISSUE-REQ-002` | `REQ-SYS-0002` | Incomplete Data | Optical camera zoom focal length, sensor resolution, and LWIR NETD sensitivity unstated. | `REA-T1-OVERVIEW-2026-V1.0`, p. 8 | Inability to compute optical ground sampling distance (GSD) and detection range. | Publish optical and thermal sensor datasheets. | **OPEN** |
| `ISSUE-REQ-003` | `REQ-SYS-0003` | Undefined Hardware | Interim COTS System-on-Module model (prior to VEGA/SHAKTI silicon migration) unstated. | `REA-T1-OVERVIEW-2026-V1.0`, p. 7 | Blocks carrier board layout, power rail dimensioning, and cooling design. | Select and specify interim COTS heterogeneous compute SOM. | **OPEN** |
| `ISSUE-REQ-004` | `REQ-SYS-0004` | Missing Threshold | Temporal visual change detection lacks quantitative detection threshold and false alarm limits. | `REA-T1-OVERVIEW-2026-V1.0`, p. 8 | Inability to verify CNN performance objectively. | Define minimum detectable change area ($m^2$) and false alarm probability. | **OPEN** |
| `ISSUE-REQ-005` | `REQ-SYS-0005` | Missing Metric | Neural super-resolution lacks scaling factor (2x vs 4x) and image fidelity targets. | `REA-T1-OVERVIEW-2026-V1.0`, p. 3 | Cannot establish pass/fail criteria for neural upscaling weights. | Define upscaling multiplier and minimum PSNR / SSIM metrics. | **OPEN** |
| `ISSUE-REQ-006` | `REQ-SYS-0007` | Missing Metric | Wideband SDR RF monitoring lacks minimum detectable signal sensitivity (dBm) and sweep rate. | `REA-T1-OVERVIEW-2026-V1.0`, p. 8 | Intercept probability for low-probability-of-intercept (LPI) radars cannot be sized. | Specify receiver sensitivity, instantaneous bandwidth, and sweep rates. | **OPEN** |
| `ISSUE-REQ-007` | `REQ-SYS-0008` | Missing Metric | Acoustic impulse TDoA bearing localization lacks angular accuracy tolerance and range limits. | `REA-T1-OVERVIEW-2026-V1.0`, p. 8 | Risk of unacceptable bearing errors in mountain valleys. | Define angular tolerance (e.g., $\pm 5^\circ$) and operational range (m). | **OPEN** |
| `ISSUE-REQ-008` | `REQ-SYS-0009` | Incomplete Data | FSO optical laser transceiver lacks laser wavelength, optical power, and eye-safety classification. | `REA-T1-OVERVIEW-2026-V1.0`, p. 8 | Inability to calculate laser link margin or laser safety zone. | Publish laser transceiver optical parameters and link budget. | **OPEN** |
| `ISSUE-REQ-009` | `REQ-SYS-0010` | Undefined Logic | Failover hysteresis and packet loss threshold between FSO laser and SDR backup unstated. | `REA-T1-OVERVIEW-2026-V1.0`, p. 9 | Risk of link flapping or packet loss during high-bank maneuvers. | Define loss-of-signal timeout and RSSI hysteresis band. | **OPEN** |
| `ISSUE-REQ-010` | `REQ-SYS-0016` | Missing Specs | Low-RCS stealth airframe dimensions, wingspan, MTOW, and radar-absorbing material properties omitted. | `REA-T1-OVERVIEW-2026-V1.0`, p. 10 | Cannot construct aerodynamic CFD or radar cross-section simulation models. | Release outer mold line (OML) CAD geometry and mass property targets. | **OPEN** |

---

## 15. Review and Quality Checklist

This checklist confirms that the requirements decomposition framework and bidirectional traceability matrix adhere to rigorous systems engineering principles:

- [x] **Hierarchy Representation**: 4-level hierarchy (System, Subsystem, Functional, Derived) established and populated.
- [x] **Field Completeness**: All 17 mandatory requirement tracking fields present in every requirement node.
- [x] **Matrix Completeness**: All 16 mandatory traceability columns represented in the wireframe.
- [x] **Parent-Child Linkage**: Every derived requirement explicitly linked to a validated parent; all top-level requirements traced to operational objectives.
- [x] **Distinction of Proposed IDs**: All newly proposed Level 2, 3, and 4 requirements tagged with `[PROPOSED]` and configuration status `PROPOSED (UNDER REVIEW)`.
- [x] **Orphan & Gap Detection**: Rules and mechanisms established for flagging orphan requirements, childless parents, and missing links.
- [x] **Verifiability**: Requirement statements written using unambiguous normative language (*shall*) with identifiable verification methods.
- [x] **Integrity & Anti-Fabrication**: Unknown values explicitly marked as `TBD` or `NOT YET DEFINED`. Zero fabricated test cases or unverified test logs.
- [x] **Markdown Structural Validity**: All markdown headings, lists, and tables syntactically valid and previewable in VS Code and GitHub Markdown.
- [x] **Zero-Cost & Local Mandate**: All work conducted strictly locally without external paid software, cloud APIs, or unauthorized repository pushes.

---

## 16. Day 2 Completion Summary

* **Task 3 (Requirements Decomposition Framework)**: Fully completed. Established a 4-level decomposition structure and documented complete 17-field tracking nodes for critical flight systems (GNSS-denied navigation, edge AI, electronic warfare, optical communications, and bare-metal flight avionics).
* **Task 4 (Bidirectional Mapping Matrix Design)**: Fully completed. Constructed the complete 16-column Bidirectional Traceability Wireframe connecting source goals, system requirements, subsystem allocations, functional refinements, interfaces, verification methods, and test case tracking in both directions.
* **Deliverable Location**: Documented in primary deliverable `docs/SRS_Starter_Template_Day2_2026-10-11.md` and supported by dedicated matrix deliverable `docs/Bidirectional_Traceability_Wireframe_Day2_2026-10-11.md`.

---

## 17. References

1. RudraEdge Aerospace, *Project Introduction & Technical Overview: RudraEdge RE-T1 (Spectra)*, Document ID: `REA-T1-OVERVIEW-2026-V1.0`, Author: Sarvesh Sharma, October 2026.
2. RudraEdge Aerospace, *Pre-Implementation Technical Readiness & Training Task Order*, Directive: `REA/2026/RE-T1/TRAIN-001/ADD-03`, Author: Sarvesh Sharma, 09 October 2026.
3. RudraEdge Aerospace, *System Requirements Specification (SRS) — Baseline Foundation*, Document ID: `REA-T1-SRS-2026-V1.0`, Author: Priyanka Sharma, 10 October 2026.
4. RudraEdge Aerospace, *RE-T1 Cross-Domain Architecture Study*, Document ID: `REA-T1-ARCH-STUDY-2026-V1.0`, Author: Priyanka Sharma, 10 October 2026.
5. Ministry of Defence / DIO, *iDEX Master Proposal: Autonomous Tactical UAV Platform*, Reference: `RE-iDEX-PROPOSAL-2026-R1`, 2026.
