# Bidirectional Requirements Traceability Matrix (RTM) - Baseline

**Status:** LOCKED (tag: baseline-v1.0)

## Forward Traceability

| Req ID  | Design Element | Test Case ID | Implementation Artifact | Coverage |
|---------|----------------|--------------|-------------------------|----------|
| REQ-001 | PWM Generator Module (50 Hz) | TC-PWM-01 | src/pwm_driver.c | 100% |
| REQ-002 | Attitude PID Controller | TC-ATT-02 | src/attitude_pid.c | 100% |
| REQ-003 | ESC Timing Interface | TC-ESC-03 | src/esc_latency.h | 100% |
| REQ-004 | Thermal Protection & BMS Monitor | TC-THERM-04 | src/lipo_thermal.c | 100% |
| REQ-005 | Configuration Control Process | TC-CFG-05 | .git + this RTM | 100% |

## Backward Traceability

| Artifact / Test | Traces To | Notes |
|-----------------|-----------|-------|
| src/pwm_driver.c | REQ-001 | FREQUENCY_HZ = 50 |
| src/attitude_pid.c | REQ-002 | Gains tuned for 50 Hz |
| src/esc_latency.h | REQ-003 | Max latency <= 8 ms |
| src/lipo_thermal.c | REQ-004 | Soft limit 55C, hard 60C |
| .git + RTM_Baseline.md | REQ-005 | Master locked |

**Bidirectional Coverage: 100%**
