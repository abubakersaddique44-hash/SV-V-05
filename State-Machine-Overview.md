# State Machine Overview

The scenario contains the following major system states:

1. **Startup / Self-Check**
2. **MONITORING**
3. **CONSERVATION_ACTIVE**
4. **PROTECTION_MODE**
5. **VIBRATION_RESPONSE**
6. **Safe Shutdown**

## Important Transitions

### Startup → MONITORING
Occurs when all essential sensors and environmental-control devices pass the self-check.

### MONITORING → CONSERVATION_ACTIVE
Requires:
- Artifact information recorded.
- Environmental profile loaded.
- Chamber door closed.
- Required sensors operational.

### CONSERVATION_ACTIVE → PROTECTION_MODE
Occurs when temperature or humidity cannot be corrected within the allowed recovery period.

### CONSERVATION_ACTIVE → VIBRATION_RESPONSE
Occurs when significant vibration is detected while an artifact is inside.

### CONSERVATION_ACTIVE → Door-related suspension
Occurs immediately when the chamber door is opened. Normal conservation activities must not continue while the chamber is open.

### VIBRATION_RESPONSE → CONSERVATION_ACTIVE
Requires vibration to remain below the permitted threshold for the required stabilization period and successful verification of other required conditions.

### Power Loss → Emergency Power
If emergency power is available, the system switches to it.

### Power Loss → Safe Shutdown
If emergency power is unavailable, the system records the incident and enters safe shutdown.

### Artifact Removal
Artifact removal is permitted only after the system verifies that the chamber is safe and no active protection response is underway.

## Key Safety Principle

The system does not assume that issuing a correction command means the artifact is safe. Sensor readings must verify that the environmental condition has actually recovered.
