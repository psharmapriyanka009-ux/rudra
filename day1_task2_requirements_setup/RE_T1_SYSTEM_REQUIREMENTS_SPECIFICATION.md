# SYSTEM REQUIREMENTS SPECIFICATION (SRS)
## RudraEdge RE-T1 (Spectra) Autonomous Tactical UAV Platform
### Project Rudra-Tactical (`RE-iDEX-PROPOSAL-2026-R1`)

---

## 1. Document Control

| Attribute | Baseline Information |
| :--- | :--- |
| **Project Identity** | Project Rudra-Tactical \| Platform: RudraEdge RE-T1 (Spectra) |
| **Proposal Reference** | `RE-iDEX-PROPOSAL-2026-R1` (Target: iDEX / DIO / MoD Evaluation Standard) |
| **Document Title** | System Requirements Specification (SRS) — Baseline Foundation |
| **Document Identifier** | `REA-T1-SRS-2026-V1.0` |
| **Task Assignment** | Day 1, Task 2: System Requirements Structure Setup |
| **Task Order Reference** | `REA/2026/RE-T1/TRAIN-001/ADD-03` (Dated: 09 October 2026) |
| **Author / Cadre** | **Priyanka Sharma** |
| **Cadre Designation** | Systems Requirements & Configuration Engineer |
| **Organization** | RudraEdge Aerospace (Incubated at TIDES, IIT Roorkee) |
| **Authorizing Lead** | Sarvesh Sharma, Founder & Project Lead |
| **Document Version** | Version 1.0 (Initial Draft Baseline) |
| **Preparation Date** | 10 October 2026 |
| **Security Classification** | Commercial-in-Confidence / Technical Specification |
| **Document Status** | **DRAFT FOR REVIEW** |
| **Lifecycle Phase** | Milestone 1 (M1–M4): Simulation Digital Twin & SRS Freeze |

---

## 2. Purpose

This **System Requirements Specification (SRS)** establishes the formal, structured, and verifiable requirements baseline for the **RudraEdge RE-T1 (Spectra)** tactical Unmanned Aerial Vehicle (UAV) platform. 

Commissioned under directive `REA/2026/RE-T1/TRAIN-001/ADD-03`, this document translates high-level operational concepts, defense mission goals, and technical architectural frameworks into discrete, traceable, and verifiable engineering requirements. It defines the functional, interface, performance, environmental, safety, and security constraints governing Milestone 1 (*Simulation Digital Twin & SRS Freeze*) of the 18-month phased engineering lifecycle.

This specification serves as the primary technical contract for:
- Developing the high-fidelity Gazebo digital twin simulation models and PX4 Software-in-the-Loop (SIL) environments.
- Establishing testbench criteria for Milestone 2 Hardware-in-the-Loop (HIL) avionics integration.
- Enforcing end-to-end bidirectional traceability across the **10-Tier Validation Ladder** and the **20 frozen iDEX deliverables (D1 through D20)**.

---

## 3. Scope

### 3.1 System Scope
The scope of this SRS encompasses all airborne subsystems and immediate ground interfaces constituting the RE-T1 (Spectra) Physical-Electromagnetic-Cyber Layer Fusion (PECLF) architecture:
- **Physical Sensing Substrates**: Multi-spectral daylight CMOS/LWIR infrared gimbals, micro-LiDAR, micro-Ground Penetrating Radar (GPR), 4-element microphone array, and CBRN sniffers.
- **Embedded Real-Time Avionics**: Bare-metal flight control microcontroller (STM32 running PX4), inner attitude and rate control loops, PWM motor timers, and aerodynamic servo fins.
- **Heterogeneous Edge Compute**: Zero-cloud onboard CPU/GPU/NPU/DSP processing host running hardened air-gapped Linux, neural inference engines (TensorRT INT8), and Swadeshi ROS 2 middleware.
- **Resilient Navigation**: Drift-bounded Visual-Inertial Odometry (VIO), high-rate IMU fusion, and onboard Digital Elevation Model (DEM) terrain matching.
- **Multi-Domain Communications**: Directional Free-Space Optical (FSO) laser communications and encrypted Software-Defined Radio (SDR) backup link (400 MHz to 6 GHz).
- **Effectors & Payloads**: Wind-compensated ballistic precision cargo drop pod and authorized defense payload interlocks.
- **Data Sovereignty & Cybersecurity**: Hardware Root of Trust, Secure Bootloader, and automated zero-trace memory wiping daemons.

### 3.2 Known Exclusions and Boundaries
- **Exclusions**: Ground transportation vehicles, permanent base station optical towers, mass production manufacturing tooling, and third-party cloud infrastructure (explicitly prohibited under the zero-cloud architecture).
- **Provisional Status**: Detailed numerical flight envelope limits, exact airframe dimensions, and component manufacturer part numbers not established in authorized overview documents are excluded from frozen requirements and recorded in the Open Questions and TBD Register.

---

## 4. Applicable and Reference Documents

The requirements documented herein are directly traceable to the following project records:

| Document ID | Title / Description | Author / Source | Relevance / Evidence Scope |
| :--- | :--- | :--- | :--- |
| `REA-T1-OVERVIEW-2026-V1.0` | RudraEdge RE-T1 (Spectra) Project Introduction & Technical Overview | Sarvesh Sharma (Founder & Project Lead) | Authoritative source of truth for PECLF layers, subsystem modules (01–06), interface protocols, lifecycle phases, and 10-tier validation ladder. |
| `REA/2026/RE-T1/TRAIN-001/ADD-03` | Pre-Implementation Technical Readiness & Training Task Order | Sarvesh Sharma (Project Lead) | Direct engineering assignment, cadre scope, zero-cost mandate, and deliverable specifications. |
| `REA-T1-ARCH-STUDY-2026-V1.0` | RE-T1 Cross-Domain Architecture Study | Priyanka Sharma (Systems Engineer) | Day 1 Task 1 baseline report establishing 22 technical nodes, interface vectors, and preliminary architecture diagram. |
| `RE-iDEX-PROPOSAL-2026-R1` | Master iDEX Proposal: Autonomous Tactical UAV Platform | RudraEdge Aerospace / MoD | Parent reference establishing the 20 frozen advanced capabilities and deliverables D1 through D20. |

---

## 5. System Overview

The **RudraEdge RE-T1 (Spectra)** is an autonomous, tactical-class Unmanned Aerial Vehicle (UAV) engineered by RudraEdge Aerospace specifically for persistent tactical reconnaissance, electronic warfare sensing, and precision logistic support in contested, high-altitude border frontiers such as Ladakh and the Siachen Glacier.

To overcome the catastrophic failure modes of commercial and legacy military drones (satellite jamming, severe cold-soak motor/battery degradation, RF link interception, and foreign silicon supply-chain vulnerabilities), RE-T1 is structured around an integrated **Physical-Electromagnetic-Cyber Layer Fusion (PECLF)** framework:
- **Layer A (Physical Perception)**: Captures multi-spectral visual, thermal, acoustic, RF, and subsurface data.
- **Layer B (Navigation & Autonomy)**: Executes drift-bounded VIO and DEM terrain correlation under Swadeshi ROS 2.
- **Layer C (Heterogeneous Compute)**: Zero-cloud computing substrate executing real-time computer vision and DSP.
- **Layer D (Electromagnetic Awareness)**: Wideband RF monitoring (400 MHz–6 GHz) and acoustic gunfire direction finding.
- **Layer E (Secure Communications)**: High-bandwidth directional Free-Space Optical (FSO) laser link with SDR RF fallback.
- **Layer F (Mission Intelligence & AI)**: Pixel-level semantic segmentation, change detection, and super-resolution.
- **Layer G (Authorized Effectors)**: Wind-compensated ballistic cargo drop pod with dual-redundant safety interlocks.
- **Layer H (Cybersecurity Root)**: Hardware Root of Trust and automated zero-trace flash memory sanitization.

Flight-critical stabilization is decoupled from non-real-time mission computing, ensuring that software anomalies in experimental perception or neural network routines cannot corrupt basic flight airworthiness.

---

## 6. System Context and Boundaries

### 6.1 External System Entities
The RE-T1 airborne platform operates within a defined tactical operations context interfacing with two external entities:
1. **Optical Ground Terminal (OGT) (`STUDY-EXT-01`)**: Friendly line-of-sight optical tracking telescope receiving modulated high-speed laser transmissions and providing coarse-fine optical uplink beacons.
2. **Ground Control Station (GCS) SDR RF Terminal (`STUDY-EXT-02`)**: Mobile or outpost command station maintaining encrypted, frequency-hopping RF telemetry and emergency command abort capabilities.

### 6.2 Environmental & Operational Boundaries
- **Climatic Boundaries**: Low-density mountain atmosphere, sub-zero ambient temperatures down to -20°C, and severe high-altitude mountain wind shear.
- **Electromagnetic Boundaries**: Active adversary electronic warfare (wideband GNSS jamming, unhardened RF link blocking, and surveillance radar illumination).
- **Physical Boundaries**: Lightweight carbon-composite low-RCS monocoque containing all internal avionics, computing, sensors, battery heating jackets, and cargo release mechanics.

```
┌────────────────────────────────────────────────────────────────────────┐
│                   EXTERNAL OPERATIONAL BOUNDARY                        │
│                                                                        │
│   [OPTICAL GROUND TERMINAL]                [GCS SDR RF BACKUP]         │
│         (STUDY-EXT-01)                        (STUDY-EXT-02)           │
└─────────────────▲───────────────────────────────────▲──────────────────┘
                  │ Directional Laser                 │ Encrypted RF
                  │ (FSO Line-of-Sight)               │ (400 MHz - 6 GHz)
┌─────────────────▼───────────────────────────────────▼──────────────────┐
│                   AIRBORNE PLATFORM BOUNDARY                           │
│                                                                        │
│   ┌────────────────────────────────────────────────────────────────┐   │
│   │              Faceted Low-RCS Composite Airframe                │   │
│   │                                                                │   │
│   │   [Layer H: Security Root]      [Layer C: Heterogeneous Edge]  │   │
│   │    - Hardware Root of Trust      - Hardened Linux OS           │   │
│   │    - Zero-Trace Wipe Engine      - TensorRT INT8 Neural Models │   │
│   │                                  - Swadeshi ROS 2 Core         │   │
│   │                                                ▲               │   │
│   │                                 Micro-XRCE-DDS │ Watchdogs     │   │
│   │                                                ▼               │   │
│   │   [Layer G: Effectors]          [Layer B / 2: Flight Control]  │   │
│   │    - Wind-Compensated Pod        - Bare-Metal STM32 MCU        │   │
│   │    - Dual Logic Interlocks       - PX4 Autopilot Firmware      │   │
│   │                                                │               │   │
│   │                                 Microsecond    ▼               │   │
│   │                                 PWM Timers     [Propulsion]    │   │
│   │                                                                │   │
│   │   [Layer A: Perception]                                        │   │
│   │    - EO/IR Gimbal   - Micro-LiDAR   - 4-Ch Mic Array           │   │
│   │    - Micro-GPR      - SDR Rx Front  - CBRN Sniffer             │   │
│   └────────────────────────────────────────────────────────────────┘   │
└────────────────────────────────────────────────────────────────────────┘
```

---

## 7. System Requirements

The following requirements represent the initial technical baseline compiled from `REA-T1-OVERVIEW-2026-V1.0`. Every requirement is assigned a provisional study-level identifier (`REQ-SYS-XXXX`) pending formal project baseline approval.

### 7.1 Autonomous Navigation & Sensor Fusion

#### REQ-SYS-0001: GNSS-Denied 6-DOF Localization
- **Statement**: The system shall calculate continuous, drift-bounded 6-DOF vehicle pose estimations in GPS-denied and satellite-jammed environments by fusing high-rate IMU angular rates, visual tracking streams, onboard Digital Elevation Models (DEM), and micro-LiDAR altimetry.
- **Type**: Functional / Performance
- **Parent Traceability**: Feature 1 / D1–D20
- **Implementing Node**: `MOD-01` (`VIO-NAV`)
- **Source Reference**: `REA-T1-OVERVIEW-2026-V1.0`, Section 2 (p. 3), Section 7 (p. 8), Section 10 (p. 11)
- **Rationale**: Tactical military operations in Ladakh and Siachen operate under continuous hostile electronic warfare jamming that disables satellite GPS signals.
- **Verification Method**: Test / Demonstration (Tier 8 Exit Criteria)
- **Acceptance Criteria**: Sub-meter drift bounds sustained during deliberate disabling of satellite GNSS signals during flight trials.

### 7.2 Multi-Spectral Perception & Surveillance

#### REQ-SYS-0002: Stabilized Multi-Spectral Day/Night Imaging
- **Statement**: The system shall capture continuous, hardware-synchronized daylight optical CMOS and uncooled Long-Wave Infrared (LWIR) video streams via a gyro-stabilized gimbal routed over multi-lane MIPI-CSI Gen3 buses into the edge compute engine.
- **Type**: Functional / Interface
- **Parent Traceability**: Features 5 & 13 / D1–D20
- **Implementing Node**: `MOD-02` (`EO-IR-GIMBAL`)
- **Source Reference**: `REA-T1-OVERVIEW-2026-V1.0`, Section 7 (p. 8), Section 8 (p. 9)
- **Rationale**: Provides persistent day/night tactical reconnaissance and target acquisition through fog, dust, snow, and smoke.
- **Verification Method**: Demonstration / Test (Tier 4 & Tier 9 Criteria)
- **Acceptance Criteria**: Stabilized dual-stream video delivered over MIPI-CSI Gen3 via Direct Memory Access (DMA) with zero frame drops under nominal flight vibration.

### 7.3 Heterogeneous Edge AI & Mission Intelligence

#### REQ-SYS-0003: Zero-Cloud Heterogeneous Neural Inference
- **Statement**: The system shall execute real-time pixel-level semantic segmentation and object detection entirely onboard utilizing INT8 quantized neural models hosted on dedicated heterogeneous CPU/GPU/NPU/DSP hardware without external cloud or ground station connectivity.
- **Type**: Functional / Performance
- **Parent Traceability**: Feature 8 / D1–D20
- **Implementing Node**: `MOD-03` (`EDGE-AI`), `STUDY-NODE-09`
- **Source Reference**: `REA-T1-OVERVIEW-2026-V1.0`, Section 2 (p. 3), Section 6 (p. 7), Section 7 (p. 8)
- **Rationale**: Congested tactical RF links and enemy electronic sniffing prevent offloading uncompressed raw high-definition video to remote servers.
- **Verification Method**: Demonstration / Analysis (Tier 1 & Tier 9 Criteria)
- **Acceptance Criteria**: INT8 TensorRT compiled neural model generates pixel segmentation masks and bounding boxes onboard in real time without network socket calls.

#### REQ-SYS-0004: Onboard Temporal Visual Change Detection
- **Statement**: The system shall perform automated temporal visual change detection directly on the airframe by comparing real-time video frames against historical terrain embeddings.
- **Type**: Functional
- **Parent Traceability**: Feature 15 / D1–D20
- **Implementing Node**: `MOD-03` (`EDGE-AI`)
- **Source Reference**: `REA-T1-OVERVIEW-2026-V1.0`, Section 5 (p. 6), Section 7 (p. 8)
- **Rationale**: Enables immediate airborne detection of camouflaged assets, troop movement, and newly constructed enemy fortifications.
- **Verification Method**: Demonstration (Tier 1 Algorithmic Criteria)
- **Acceptance Criteria**: Automated isolation of pixel-level change vectors between aligned real-time frames and stored baseline terrain embeddings.

#### REQ-SYS-0005: Neural Super-Resolution Image Reconstruction
- **Statement**: The system shall execute onboard neural super-resolution to reconstruct and enhance degraded optical and thermal image frames captured in adverse atmospheric conditions.
- **Type**: Functional
- **Parent Traceability**: Feature 17 / D1–D20
- **Implementing Node**: `MOD-03` (`EDGE-AI`)
- **Source Reference**: `REA-T1-OVERVIEW-2026-V1.0`, Section 2 (p. 3), Section 7 (p. 8)
- **Rationale**: High-altitude atmospheric haze, dust, and thermal sensor noise degrade raw sensor visual quality.
- **Verification Method**: Demonstration (Tier 1 Simulation Criteria)
- **Acceptance Criteria**: Reconstructed super-resolved imagery generated onboard prior to tactical display or optical laser downlink transmission.

#### REQ-SYS-0006: Autonomous Search & Rescue Path Planning
- **Statement**: The system shall autonomously plan and execute tactical search coverage paths and waypoint sequences onboard based on real-time mission parameters and sensor feedback.
- **Type**: Functional
- **Parent Traceability**: Feature 19 / D1–D20
- **Implementing Node**: `MOD-03` (`EDGE-AI`), `STUDY-NODE-08`
- **Source Reference**: `REA-T1-OVERVIEW-2026-V1.0`, Section 6 (p. 7), Section 7 (p. 8)
- **Rationale**: Permits dynamic path optimization across complex mountain topography without requiring ground pilot intervention.
- **Verification Method**: Demonstration / Test (Tier 2 SIL Criteria)
- **Acceptance Criteria**: Deterministic generation of collision-free search waypoints within Gazebo Digital Twin and PX4 flight controller.

### 7.4 Electronic Warfare & Acoustic Direction Finding

#### REQ-SYS-0007: Wideband RF Spectrum Sensing & ESM
- **Statement**: The system shall monitor the ambient RF electromagnetic spectrum across 400 MHz to 6 GHz to detect hostile radio emissions, characterize radar signatures, and generate RF spectrum occupancy grids.
- **Type**: Functional / Performance
- **Parent Traceability**: Feature 9 / D1–D20
- **Implementing Node**: `MOD-04` (`EW-DSP`), `STUDY-NODE-15`
- **Source Reference**: `REA-T1-OVERVIEW-2026-V1.0`, Section 7 (p. 8), Section 8 (p. 9)
- **Rationale**: Provides electronic awareness to identify hostile air-defense radar emissions and locate jammer emitters.
- **Verification Method**: Test / Analysis (Tier 4 Integration Criteria)
- **Acceptance Criteria**: Ingestion and classification of RF signals across 400 MHz to 6 GHz delivered via VITA 49 radio transport packets over PCIe/GbE.

#### REQ-SYS-0008: Acoustic Impulse TDoA Bearing Localization
- **Statement**: The system shall sample synchronized 4-channel acoustic pressure signals from a microphone array and calculate Time-Difference-of-Arrival (TDoA) bearing vectors to localize impulse noises such as gunfire and artillery.
- **Type**: Functional
- **Parent Traceability**: Feature 11 / D1–D20
- **Implementing Node**: `MOD-04` (`EW-DSP`), `STUDY-NODE-13`
- **Source Reference**: `REA-T1-OVERVIEW-2026-V1.0`, Section 7 (p. 8), Section 8 (p. 9)
- **Rationale**: Provides non-line-of-sight acoustic directional detection of hostile fire in mountain terrain.
- **Verification Method**: Demonstration / Test (Tier 4 Bench & Tier 9 Criteria)
- **Acceptance Criteria**: Calculation of acoustic bearing vectors with dedicated DSP thread using prioritized FIFO ring buffers under bench and flight trials.

### 7.5 Secure Communications & Data Links

#### REQ-SYS-0009: Directional Free-Space Optical (FSO) Communications
- **Statement**: The system shall transmit high-bandwidth mission intelligence and video streams over a directional narrow-beam Free-Space Optical laser link using closed-loop coarse-fine pointing, acquisition, and tracking (PAT).
- **Type**: Functional / Performance
- **Parent Traceability**: Feature 10 / D1–D20
- **Implementing Node**: `MOD-05` (`FSO-COMM`), `STUDY-EXT-01`
- **Source Reference**: `REA-T1-OVERVIEW-2026-V1.0`, Section 2 (p. 3), Section 7 (p. 8), Section 8 (p. 9)
- **Rationale**: Optical laser links are physically immune to radio frequency electronic warfare jamming and hostile RF interception.
- **Verification Method**: Demonstration / Test (Tier 9 Criteria)
- **Acceptance Criteria**: Establishment and tracking of line-of-sight laser communication link with friendly optical ground terminal under high wind shear.

#### REQ-SYS-0010: Resilient SDR RF Backup Command Link
- **Statement**: The system shall maintain an encrypted Software-Defined Radio (SDR) frequency-hopping RF channel that automatically activates as a fallback command and telemetry link when the optical laser link is obscured or degraded.
- **Type**: Functional / Interface
- **Parent Traceability**: Feature 10 / D1–D20
- **Implementing Node**: `STUDY-NODE-15`, `STUDY-EXT-02`
- **Source Reference**: `REA-T1-OVERVIEW-2026-V1.0`, Section 2 (p. 3), Section 7 (p. 8), Section 8 (p. 9)
- **Rationale**: Provides redundant command-and-control uplink capability if atmospheric clouds, heavy fog, or line-of-sight loss break the optical laser link.
- **Verification Method**: Test (Tier 4 Bench / Tier 7 Criteria)
- **Acceptance Criteria**: Automatic link switchover to encrypted frequency-hopping RF within defined loss-of-signal timeout without vehicle control loss.

### 7.6 Mission Effectors & Payload Release

#### REQ-SYS-0011: Precision Wind-Compensated Ballistic Cargo Delivery
- **Statement**: The system shall calculate real-time wind-compensated ballistic release trajectories and actuate a mechanical payload release mechanism for precision delivery of emergency logistic stores.
- **Type**: Functional
- **Parent Traceability**: Feature 6 / D1–D20
- **Implementing Node**: `MOD-06` (`PAYLOAD-POD`)
- **Source Reference**: `REA-T1-OVERVIEW-2026-V1.0`, Section 7 (p. 8), Section 8 (p. 9)
- **Rationale**: Provides emergency logistical resupply to forward-isolated troops in rugged, road-denied Himalayan outposts.
- **Verification Method**: Demonstration / Test (Milestone 4 Prototype)
- **Acceptance Criteria**: Actuation of mechanical unlatch at calculated ballistic release point based on real-time wind speed/direction and altitude radar data.

#### REQ-SYS-0012: Dual-Redundant Payload Interlock Safety
- **Statement**: The system shall enforce opto-isolated solid-state dual-redundant discrete logic interlocks that prevent uncommanded payload pod unlatching or effector actuation during power-on boot, software crashes, or fault conditions.
- **Type**: Safety / Interface
- **Parent Traceability**: Feature 7 / D1–D20
- **Implementing Node**: `MOD-06` (`PAYLOAD-POD`), `STUDY-NODE-07`
- **Source Reference**: `REA-T1-OVERVIEW-2026-V1.0`, Section 4 (p. 4), Section 8 (p. 9)
- **Rationale**: Prevents catastrophic accidental release of payloads or ordnance over friendly personnel or during degraded flight states.
- **Verification Method**: Test / Inspection (Tier 4 Benchtop Criteria)
- **Acceptance Criteria**: Zero uncommanded release signals observed during microcontroller boot sequence, CPU reset pulses, and simulated power rail drops.

### 7.7 Tactical Sensors & Subsurface Payloads

#### REQ-SYS-0021: Micro-GPR Subsurface Anomaly Detection Ingress
- **Statement**: The system shall ingest 16-bit IQ samples from a micro-Ground Penetrating Radar (GPR) over high-speed SPI / USB 3.0 into a dedicated DSP thread with prioritized FIFO ring buffers to prevent memory stalls.
- **Type**: Functional / Interface
- **Parent Traceability**: D1–D20 / Milestone 4
- **Implementing Node**: `MOD-04` (`EW-DSP`), `STUDY-NODE-12`
- **Source Reference**: `REA-T1-OVERVIEW-2026-V1.0`, Section 7 (p. 8), Section 8 (p. 9)
- **Rationale**: Enables airborne detection of buried caches, unexploded ordnance, and terrain stratigraphy from tactical altitudes.
- **Verification Method**: Demonstration / Test (Milestone 4 Prototype)
- **Acceptance Criteria**: Continuous streaming of 16-bit IQ samples across high-speed SPI/USB 3.0 into DSP ring buffer without data packet drops or buffer overruns.

#### REQ-SYS-0022: Airborne CBRN Environmental Hazard Sniffing
- **Statement**: The system shall sample atmospheric air particulate matter and gas concentrations via digital sensors and log CBRN hazard levels with geographic coordinate tags onto the mission telemetry stream.
- **Type**: Functional / Sensor
- **Parent Traceability**: D1–D20 / Milestone 4
- **Implementing Node**: `STUDY-NODE-14` (`CBRN-SNIFFER`)
- **Source Reference**: `REA-T1-OVERVIEW-2026-V1.0`, Section 3 (p. 4), Section 7 (p. 7), Section 8 (p. 9)
- **Rationale**: Provides forward reconnaissance and safety mapping for troop exposure to airborne chemical, biological, or radiological contaminants.
- **Verification Method**: Demonstration (Milestone 4 Prototype)
- **Acceptance Criteria**: Digital transmission of hazard detection flags and concentration readings over internal bus to ROS 2 mission logging nodes.

### 7.8 Avionics, Flight Control & Safety Architecture

#### REQ-SYS-0013: Asynchronous Bare-Metal Flight Control Isolation
- **Statement**: The system shall execute inner-loop attitude stabilization and rate control loops on a dedicated bare-metal 32-bit automotive/aerospace microcontroller (STM32 running PX4) completely decoupled from the Linux compute OS.
- **Type**: Safety / Architecture
- **Parent Traceability**: D1–D20 / Tier 3
- **Implementing Node**: `STUDY-NODE-07` (`PX4 MCU`), `STUDY-NODE-09`
- **Source Reference**: `REA-T1-OVERVIEW-2026-V1.0`, Section 6 (p. 7), Section 8 (p. 9)
- **Rationale**: Prevents complex non-real-time software processes (computer vision, AI, ROS 2) from compromising primary flight safety.
- **Verification Method**: Inspection / Test (Tier 3 HIL Criteria)
- **Acceptance Criteria**: Inner attitude loops execute deterministically on bare-metal microcontroller independent of Linux operating system state.

#### REQ-SYS-0014: Zero-Overhead Autopilot Watchdog Failsafe
- **Statement**: The flight autopilot shall maintain stable vehicle attitude, continue autonomous waypoint tracking, or trigger return-to-home without degradation if the onboard Linux AI compute engine experiences an exception, crash, or memory stall.
- **Type**: Safety / Reliability
- **Parent Traceability**: D1–D20 / Tier 2
- **Implementing Node**: `STUDY-NODE-07`, `STUDY-NODE-08`
- **Source Reference**: `REA-T1-OVERVIEW-2026-V1.0`, Section 8 (p. 9)
- **Rationale**: Ensures aircraft survivability against software runtime bugs or edge AI kernel exceptions.
- **Verification Method**: Test (Tier 2 SIL Criteria)
- **Acceptance Criteria**: Simulated Linux host crash or killing of ROS 2 daemon results in uninterrupted PX4 flight hold and autonomous return-to-home execution.

#### REQ-SYS-0023: Inner-Loop Flight Control Latency Threshold
- **Statement**: The inner attitude and rate control loop latency executing on the bare-metal flight controller microcontroller shall remain strictly under 1 millisecond.
- **Type**: Performance
- **Parent Traceability**: D1–D20 / Tier 3
- **Implementing Node**: `STUDY-NODE-07` (`PX4 MCU`)
- **Source Reference**: `REA-T1-OVERVIEW-2026-V1.0`, Section 10 (p. 11)
- **Rationale**: Sub-millisecond loop times are mandatory to maintain aerodynamic stability during violent mountain wind gusts and turbulent downdrafts.
- **Verification Method**: Test (Tier 3 HIL Exit Criteria)
- **Acceptance Criteria**: Real-time oscilloscope or hardware-in-the-loop (HIL) latency profiling verifies loop iteration execution time is under 1 millisecond.

### 7.9 High-Altitude Airframe, Propulsion & Environmental Envelopes

#### REQ-SYS-0015: Cold-Weather High-Altitude Operation (-20°C)
- **Statement**: The airframe, electric propulsion, electronic speed controllers, and battery management system shall sustain uninterrupted flight operations across high-altitude mountain environments down to -20°C.
- **Type**: Environmental / Performance
- **Parent Traceability**: D1–D20 / Tier 5
- **Implementing Node**: `STUDY-NODE-17`, `STUDY-NODE-19`
- **Source Reference**: `REA-T1-OVERVIEW-2026-V1.0`, Section 1 (p. 2), Section 9 (p. 10), Section 10 (p. 11)
- **Rationale**: High-altitude Himalayan frontiers (Siachen, Ladakh) exhibit extreme cold-soak and low atmospheric air densities.
- **Verification Method**: Test (Tier 5 Environmental Chamber Criteria)
- **Acceptance Criteria**: Uninterrupted electronics operation and motor throttle response sustained during sub-zero thermal chamber exposure down to -20°C.

#### REQ-SYS-0016: Faceted Low-RCS Stealth Airframe Construction
- **Statement**: The airframe structure shall incorporate faceted geometry, carbon-fiber composite materials, and radar-absorbing materials (RAM) to minimize radar cross-section (RCS) and visual detectability.
- **Type**: Physical / Structural
- **Parent Traceability**: D1–D20 / Milestone 3
- **Implementing Node**: `STUDY-NODE-18` (`AIRFRAME`)
- **Source Reference**: `REA-T1-OVERVIEW-2026-V1.0`, Section 2 (p. 3), Section 4 (p. 5), Section 9 (p. 10)
- **Rationale**: Reduces probability of detection and engagement by hostile air defense radars and electro-optical trackers.
- **Verification Method**: Analysis / Inspection (Milestone 3 Alpha Airframe)
- **Acceptance Criteria**: Fabrication of carbon-composite monocoque utilizing low-RCS design rules and verified structural integrity in Milestone 3.

#### REQ-SYS-0024: Electromagnetic Shielding for Wideband SDR Ingress
- **Statement**: The system shall incorporate physical RF shielding (EMI gaskets) and physical circuit isolation between flight motor power lines and the wideband SDR receiver circuitry.
- **Type**: Interface / EMC
- **Parent Traceability**: D1–D20 / Tier 4
- **Implementing Node**: `STUDY-NODE-15`, `STUDY-NODE-17`
- **Source Reference**: `REA-T1-OVERVIEW-2026-V1.0`, Section 8 (p. 9)
- **Rationale**: Prevents severe electromagnetic interference generated by high-current ESC motor switching pulses from degrading weak hostile RF signals.
- **Verification Method**: Test / Inspection (Tier 4 Bench Integration)
- **Acceptance Criteria**: Noise floor degradation on SDR receiver across 400 MHz to 6 GHz shall not exceed specified benchtop threshold during maximum motor throttle bursts per Tier 4.

### 7.10 Data Sovereignty, Cybersecurity & Cryptographic Silicon

#### REQ-SYS-0017: Hardware Root of Trust & Secure Boot
- **Statement**: The system shall enforce cryptographic verification of signed boot keys from hardware power-on, preventing execution of unauthorized or tampered bootloader, firmware, and operating system binaries.
- **Type**: Security / Cryptography
- **Parent Traceability**: D1–D20
- **Implementing Node**: `STUDY-NODE-10` (`ROT`)
- **Source Reference**: `REA-T1-OVERVIEW-2026-V1.0`, Section 1 (p. 2), Section 6 (p. 7), Section 8 (p. 9)
- **Rationale**: Eliminates supply chain vulnerabilities, unauthorized firmware modifications, and cyber backdoor insertion.
- **Verification Method**: Inspection / Test (Milestone 1 / Milestone 2 Bench)
- **Acceptance Criteria**: Successful secure boot execution verified using cryptographically signed boot keys; unverified binaries are rejected at power-on.

#### REQ-SYS-0018: Hardware-Enforced Zero-Trace Memory Sanitization
- **Statement**: The system shall execute automated cryptographic zero-trace flash and memory sanitization upon detection of unauthorized physical breach, chassis tampering, or capture.
- **Type**: Security / Cryptography
- **Parent Traceability**: D1–D20
- **Implementing Node**: `STUDY-NODE-10` (`ROT`)
- **Source Reference**: `REA-T1-OVERVIEW-2026-V1.0`, Section 1 (p. 2), Section 5 (p. 6), Section 8 (p. 9)
- **Rationale**: Prevents adversary recovery of proprietary software, cryptographic keys, and recorded tactical intelligence if the drone is downed.
- **Verification Method**: Test / Demonstration (Milestone 2 Bench Lab)
- **Acceptance Criteria**: Triggering tamper sensor switch or authorized emergency purge command executes irreversible zero-trace erasure of onboard flash memory partitions.

#### REQ-SYS-0020: Air-Gapped Local Networking & Zero-Copy IPC
- **Statement**: All internal communication between onboard software processes shall execute strictly over local shared memory (POSIX shm) or loopback Unix domain sockets, with physical and logical prohibitions against unvetted external IP networks.
- **Type**: Security / Interface
- **Parent Traceability**: D1–D20
- **Implementing Node**: `STUDY-NODE-08`, `STUDY-NODE-09`
- **Source Reference**: `REA-T1-OVERVIEW-2026-V1.0`, Section 8 (p. 9)
- **Rationale**: Prevents remote cyber penetration, unauthorized packet interception, and remote exploitation via wireless networks.
- **Verification Method**: Inspection / Analysis (Security Audit Gate)
- **Acceptance Criteria**: Network socket audits confirm zero unvetted external listening ports; all inter-process data exchanges use local POSIX shared memory.

### 7.11 Sovereign Software Middleware & Silicon Roadmap

#### REQ-SYS-0019: Swadeshi ROS 2 & Micro-XRCE-DDS Middleware Integration
- **Statement**: The system software stack shall utilize Swadeshi ROS 2 robotic middleware nodes coupled to PX4 Autopilot modules via secure Micro-XRCE-DDS agents over high-speed bus interfaces.
- **Type**: Software / Interface
- **Parent Traceability**: D1–D20
- **Implementing Node**: `STUDY-NODE-08`, `STUDY-NODE-07`
- **Source Reference**: `REA-T1-OVERVIEW-2026-V1.0`, Section 6 (p. 7), Section 8 (p. 9)
- **Rationale**: Guarantees 100% sovereign domestic intellectual property ownership over the robotic communications middleware layer.
- **Verification Method**: Inspection / Test (Tier 2 SIL / Tier 4 Bench)
- **Acceptance Criteria**: Deterministic exchange of MAVLink 2.0 / Micro-XRCE-DDS telemetry and waypoint topics between ROS 2 host and PX4 microcontroller.

#### REQ-SYS-0025: Indigenous Processor Architecture Roadmap Compatibility
- **Statement**: The onboard software architecture, containerized microservices, and toolchains shall maintain portability to facilitate progressive migration to C-DAC VEGA and IIT Madras SHAKTI processors.
- **Type**: Configuration / Architecture
- **Parent Traceability**: D1–D20 / Milestone 5
- **Implementing Node**: `STUDY-NODE-09` (`COMPUTE`)
- **Source Reference**: `REA-T1-OVERVIEW-2026-V1.0`, Section 1 (p. 2), Section 6 (p. 7), Section 11 (p. 12)
- **Rationale**: Achieves long-term national technological sovereignty by eliminating dependency on foreign semiconductor silicon.
- **Verification Method**: Analysis / Inspection (Milestone 5 Pre-Induction)
- **Acceptance Criteria**: POSIX compliance and modular code compilation verified against open-source RISC-V C-DAC VEGA and SHAKTI toolchains.

---

## 8. Requirement Attributes

To maintain rigorous configuration control, each requirement in the RE-T1 engineering database is recorded with the following standardized 16 attribute fields:

1. **Requirement_ID**: Unique identifier (`REQ-SYS-XXXX` provisional study format).
2. **Requirement_Title**: Concise technical title of the requirement.
3. **Requirement_Statement**: Exact normative engineering statement using formal modal verb ("shall").
4. **Requirement_Type**: Classification (Functional, Performance, Interface, Safety, Reliability, Environmental, Security, Configuration).
5. **Source_Document**: The authoritative source file establishing the requirement.
6. **Source_Section_or_Page**: Exact document section, table, or page number.
7. **Parent_Requirement_ID**: Traced parent capability (e.g. Feature 1, D1–D20).
8. **Related_Architecture_Node**: Target architectural node from `TECHNICAL_NODE_REGISTER.csv`.
9. **Rationale**: Technical justification explaining operational necessity.
10. **Verification_Method**: Primary method (Test, Demonstration, Analysis, Inspection).
11. **Acceptance_Criteria**: Measurable, objective pass/fail criteria.
12. **Priority**: Criticality ranking (HIGH, MEDIUM, LOW).
13. **Status**: Lifecycle state (PROVISIONAL (DRAFT), APPROVED, VERIFIED, DEFERRED).
14. **Verification_Evidence**: Cross-reference to test logs, calibration reports, or SIL runs.
15. **Revision**: Configuration version tracker (e.g., Rev A).
16. **Notes**: Engineering observations, limitations, or TBD flags.

---

## 9. Requirements Traceability

The RE-T1 engineering framework enforces **end-to-end bidirectional traceability**:
```
User Needs / Operational Challenges (Section 2)
  │
  ▼
Frozen iDEX Capabilities & Deliverables (Features 1–20 / D1–D20)
  │
  ▼
System Requirements Specification (REQ-SYS-0001 through REQ-SYS-0025)
  │
  ▼
Architecture Nodes & Interface Vectors (MOD-01..06, STUDY-NODE-07..20)
  │
  ▼
10-Tier Validation Ladder & Verification Test Cases (TC-SAMPLE-001..005)
```

The comprehensive mapping linking source pages, requirement identifiers, architecture components, interface vectors, verification techniques, and known issues is maintained in:  
[`day1_task2_requirements_setup/RE_T1_REQUIREMENTS_TRACEABILITY.csv`](file:///c:/Users/Admin/OneDrive/Desktop/Day1/day1_task2_requirements_setup/RE_T1_REQUIREMENTS_TRACEABILITY.csv)

---

## 10. Verification Approach

### 10.1 Standard Verification Methods
Verification of RE-T1 requirements is governed by four formal engineering methods:
1. **Test (T)**: Operational verification through direct measurement, instrumentation, and stimulus-response logging against quantitative criteria (e.g. oscilloscope latency measurement, environmental thermal chamber exposure).
2. **Demonstration (D)**: Verification through visual or observable operational execution without detailed instrumentation (e.g. automated waypoint sequencing, change detection mask display).
3. **Analysis (A)**: Theoretical modeling, calculation, simulation, or software profiling (e.g. radar cross-section electromagnetic modeling, TensorRT memory footprint calculation).
4. **Inspection (I)**: Visual, physical, or configuration audit against engineering drawings, source code standards, or hardware wiring harnesses (e.g. verifying opto-isolated solid-state interlock circuits, inspecting EMI gasket seals).

### 10.2 Integration with the 10-Tier Validation Ladder
Verification progression is gated by the formal exit criteria defined in Section 10 of `REA-T1-OVERVIEW-2026-V1.0`:

| Tier | Testing Stage | Relevant Requirements | Validation Scope | Exit Criteria |
| :---: | :--- | :--- | :--- | :--- |
| **Tier 1** | Algorithm Simulation | `REQ-SYS-0003`, `0004`, `0005` | Pure software modeling of VIO, pathing, and CNNs | Zero algorithmic divergence in nominal runs |
| **Tier 2** | Software-in-the-Loop (SIL) | `REQ-SYS-0006`, `0014`, `0019` | Full ROS 2 + PX4 dynamics in Gazebo mountain world | Deterministic flight control response |
| **Tier 3** | Hardware-in-the-Loop (HIL) | `REQ-SYS-0013`, `0023` | Real MCU and edge compute running against simulated sensors | Inner-loop latency under 1 millisecond |
| **Tier 4** | Benchtop Integration | `REQ-SYS-0002`, `0007`, `0012`, `0024` | Physical interconnection of all boards, SDR, and sensors | Zero bus collision; thermal limits verified |
| **Tier 5** | Environmental Chamber | `REQ-SYS-0015` | Sub-zero temperature stress (-20°C) and low pressure | Uninterrupted electronics operation |
| **Tier 6** | Tethered Flight Trials | `REQ-SYS-0013`, `0017` | Physical stabilization under tethered arrest | Stable closed-loop hover; zero oscillations |
| **Tier 7** | Controlled Free Flight | `REQ-SYS-0010` | Open-air baseline flight under nominal GNSS/clean RF | Accurate waypoint tracking and telemetry |
| **Tier 8** | GNSS-Denied Testing | `REQ-SYS-0001` | Satellite disabling; total reliance on VIO/DEM | Sub-meter drift bounds sustained |
| **Tier 9** | Integrated Payload Runs | `REQ-SYS-0008`, `0009`, `0021` | Simultaneous EO/IR, GPR, acoustic, and FSO laser links | All payloads active without compute drop |
| **Tier 10**| Field Demonstration | Complete RE-T1 Baseline | End-to-end tactical high-altitude frontier scenarios | Complete mission success per iDEX gates |

---

## 11. Assumptions, Constraints, and TBD Items

### 11.1 Engineering Assumptions
1. **Interim COTS Compute Substrate**: It is assumed that an interim commercial-off-the-shelf heterogeneous System-on-Module (such as an NVIDIA Jetson Orin NX/AGX carrier) will be utilized for Milestones 1 through 3 to execute TensorRT INT8 models prior to the readiness of indigenous C-DAC VEGA or SHAKTI silicon.
2. **Terrain Database Pre-Loading**: It is assumed that high-resolution Digital Elevation Model (DEM) tiles of the target flight sector are pre-loaded into local solid-state storage prior to mission deployment.

### 11.2 Mandatory Engineering Constraints
1. **Zero Personal Expenditure**: Strictly zero personal financial liability (INR 0) in compliance with Task Order `REA/2026/RE-T1/TRAIN-001/ADD-03`.
2. **Zero Public Cloud Dependency**: Strict prohibition against external cloud connectivity or commercial offloading.
3. **Air-Gapped Operation**: No unvetted listening network ports permitted on the tactical aircraft.

### 11.3 TBD (To Be Determined) Register
The following technical items remain unquantified in the available literature and are recorded in [`day1_task2_requirements_setup/RE_T1_REQUIREMENTS_ISSUES.csv`](file:///c:/Users/Admin/OneDrive/Desktop/Day1/day1_task2_requirements_setup/RE_T1_REQUIREMENTS_ISSUES.csv):
- `TBD-01`: Exact spatial resolution (meters) and update rate (Hz) for DEM terrain correlation.
- `TBD-02`: Quantitative optical ground sampling distance (GSD) and LWIR bolometer resolution.
- `TBD-03`: FSO laser wavelength (nm) and atmospheric extinction link margin.
- `TBD-04`: Maximum payload pod mass rating (kg) and release CEP accuracy (meters).
- `TBD-05`: Service ceiling (meters AMSL) and maximum allowable wind shear envelope.
- `TBD-06`: Target radar cross-section numerical value (dBsm) across tactical radar bands.
- `TBD-07`: Disarm interlock verification logic to prevent accidental zero-trace memory wiping on hard landings.

---

## 12. Change and Configuration Management

### 12.1 Proposed Requirements Management Workflow
To maintain strict configuration discipline, all prospective requirements modifications shall adhere to a structured 12-step engineering lifecycle:

```
[1. Identification] ──> [2. Source & Rationale Recording] ──> [3. Classification]
                                                                      │
                                                                      ▼
[6. Traceability]   <── [5. Quality Review]             <── [4. Unique ID Assignment]
       │
       ▼
[7. Verification Assignment] ──> [8. Change Request (CR)] ──> [9. Impact Analysis]
                                                                      │
                                                                      ▼
[12. Baseline Freeze]        <── [11. Version Control]    <── [10. CCB Review & Approval]
```

1. **Requirement Identification**: Requirements emerge strictly from operational mission needs, customer standards (iDEX/MoD), or safety mandates.
2. **Source and Rationale Recording**: Every requirement must cite its originating authority and technical justification.
3. **Requirement Classification**: Categorized into functional, performance, interface, environmental, safety, or security classes.
4. **Unique ID Assignment**: Allocated a permanent alphanumeric identifier following established naming conventions (`REQ-SYS-XXXX`).
5. **Quality Review**: Assessed for necessity, feasibility, unambiguous wording, and absence of vague qualifiers.
6. **Traceability Establishment**: Bidirectionally linked to parent capabilities, architecture nodes, and interface vectors.
7. **Verification Method Assignment**: Assigned an explicit verification method (T, D, A, I) and target exit tier.
8. **Change Request (CR) Recording**: Any modification to a baseline requirement requires a formal, numbered Engineering Change Request.
9. **Impact Analysis**: The Systems Requirements Engineer evaluates impacts across compute budgets, flight dynamics, power draw, and project schedule.
10. **Review and Approval**: Formal review conducted by the Configuration Control Board (CCB) led by the Project Lead.
11. **Version Control**: Approved changes trigger automated version incrementation (Rev A -> Rev B) with audit logs.
12. **Baseline Maintenance**: Re-baselined specifications are frozen at formal milestones (e.g. Milestone 1 SRS Freeze).

### 12.2 Systems Engineering Conceptual Distinctions

To ensure professional technical precision across all documentation, the following core systems engineering distinctions are formally established:

#### 1. Functional vs. Non-Functional Requirements
- **Functional Requirement**: Defines *what* the system must specifically do—its actions, operations, behaviors, and data transformations (e.g. `REQ-SYS-0001`: "The system shall calculate continuous 6-DOF vehicle pose estimations").
- **Non-Functional Requirement**: Defines *how well* or *under what conditions* the system must execute its functions—encompassing performance, environmental survivability, safety constraints, reliability, and security (e.g. `REQ-SYS-0023`: "Inner-loop flight control latency shall remain strictly under 1 millisecond"; `REQ-SYS-0015`: "Operation down to -20°C").

#### 2. Requirement vs. Design Decision
- **Requirement**: A vendor-neutral, implementation-agnostic capability or constraint necessary to satisfy an operational need (e.g. "The system shall maintain line-of-sight communications impervious to RF electronic warfare jamming").
- **Design Decision**: A specific engineering implementation, component selection, or architecture topology chosen by the engineering team to satisfy that requirement (e.g. "Implementing a Free-Space Optical laser diode transceiver with coarse-fine RS-422 gimbal PAT tracking").

#### 3. Verification vs. Validation
- **Verification** (*"Did we build the system right?"*): Objective evaluation confirming that the system, subsystem, or component complies with its specified technical requirements (conducted via the 10-Tier Validation Ladder, e.g., verifying inner-loop latency < 1 ms on an oscilloscope).
- **Validation** (*"Did we build the right system?"*): Operational evaluation confirming that the completed system satisfies the actual operational needs and mission objectives of the user in its intended operational environment (conducted in Tier 10 with MoD/iDEX evaluators under simulated frontier combat conditions).

#### 4. Draft Requirement vs. Approved Baseline Requirement
- **Draft Requirement**: A provisional requirement formulated by the engineering team that remains under technical review, lacks official sign-off, and is subject to revision or deletion (`Status: PROVISIONAL (DRAFT)`).
- **Approved Baseline Requirement**: A formally evaluated requirement that has cleared peer review, has been approved by the Configuration Control Board (CCB), and is frozen into the project specification (`Status: APPROVED BASELINE`).

#### 5. Verified Requirement vs. Unverified Requirement
- **Unverified Requirement**: An active requirement whose specified acceptance criteria have not yet been evaluated against physical test data, simulation runs, or formal inspection logs (`Status: PENDING VERIFICATION`).
- **Verified Requirement**: A requirement whose acceptance criteria have been rigorously evaluated and confirmed through documented, archived test evidence signed off by authorized testing authorities (`Status: VERIFIED`).

*Administrative Disclaimer*: The workflow outlined above represents the **proposed requirements management process** formulated by the Systems Requirements & Configuration Engineer for review. It does not constitute an approved corporate standard until formally authorized by the Project Lead.

---

## 13. Review and Approval

This document represents the initial engineering baseline for Milestone 1. It is submitted under **DRAFT FOR REVIEW** status. No formal corporate approval or binding sign-off is claimed until authorized signatories review and sign below:

| Review Role | Designated Authority | Review Comments | Approval Status | Signature & Date |
| :--- | :--- | :--- | :--- | :--- |
| **Author / Preparer** | Priyanka Sharma, Systems Requirements & Config Engineer | Initial baseline compiled from `REA-T1-OVERVIEW-2026-V1.0` and Task Order ADD-03. | SUBMITTED FOR REVIEW | *Priyanka Sharma*<br/>10 October 2026 |
| **Avionics & Flight Lead** | TBD (Technical Reviewer) | Pending Tier 3 HIL review | PENDING | *[Signature Required]*<br/>Date: ____________ |
| **Software & AI Lead** | TBD (Technical Reviewer) | Pending Tier 1 / ROS 2 review | PENDING | *[Signature Required]*<br/>Date: ____________ |
| **Project Lead & Authorizer**| Sarvesh Sharma, Founder & Project Lead | Pending formal CCB baseline freeze | PENDING | *[Signature Required]*<br/>Date: ____________ |

---

## 14. Revision History

| Revision | Release Date | Author | Description of Changes | Approval Reference |
| :---: | :---: | :--- | :--- | :---: |
| **Rev A (Draft)** | 10 October 2026 | Priyanka Sharma | Initial creation of RE-T1 System Requirements Specification baseline foundation under Day 1, Task 2. | `REA/2026/RE-T1/TRAIN-001/ADD-03` |
