# Task 2 — Complete Operation Schemas

Each operation is described using its purpose, preconditions, inputs, processing, outputs, postconditions, and failure/exception conditions.

---

## 1. PerformSelfCheck

**Purpose:** Verify that essential sensors and environmental-control devices are operational before normal conservation operation is allowed.

**Preconditions**
- Chamber power is available.
- System startup has begun.

**Inputs**
- Sensor status.
- Environmental-control device status.
- Power availability.

**Processing**
1. Test essential sensors.
2. Test environmental-control devices.
3. Record pass/fail results.
4. Determine whether all essential components are operational.

**Outputs**
- Self-check result.
- Component status information.

**Postconditions**
- If all essential components pass, the system is permitted to proceed to monitoring.
- If an essential component fails, normal conservation operation is blocked.

**Failure/Exception**
- Sensor failure.
- Environmental-control device failure.
- Insufficient power.

---

## 2. CheckSensorStatus

**Purpose:** Verify that required sensors are functioning correctly.

**Preconditions**
- System is powered.
- Sensor diagnostics can be executed.

**Inputs**
- Temperature sensor status.
- Humidity sensor status.
- Light sensor status.
- Vibration sensor status.
- Door sensor status.

**Processing**
- Test each required sensor and compare its status with the expected operational condition.

**Outputs**
- Sensor health result.

**Postconditions**
- Sensor status is known and recorded.
- Faulty sensors are identified.

**Failure/Exception**
- One or more essential sensors fail.

---

## 3. RecordArtifactInformation

**Purpose:** Record the identity of an artifact placed inside the chamber.

**Preconditions**
- System is operating.
- An artifact has been placed inside the chamber.

**Inputs**
- Artifact identification information.

**Processing**
- Validate and record the artifact identification data.

**Outputs**
- Stored artifact record.

**Postconditions**
- Artifact identity is available to the conservation system.

**Failure/Exception**
- Missing or invalid identification information.

---

## 4. LoadEnvironmentalProfile

**Purpose:** Load the environmental requirements associated with the artifact.

**Preconditions**
- Artifact information has been recorded.

**Inputs**
- Required temperature range.
- Required humidity range.
- Permitted vibration threshold.
- Other artifact-specific environmental limits.

**Processing**
- Validate and store the environmental limits.

**Outputs**
- Active environmental profile.

**Postconditions**
- Required environmental limits are available for monitoring and control.

**Failure/Exception**
- Missing, invalid, or incomplete environmental profile.

---

## 5. MonitorEnvironment

**Purpose:** Continuously monitor environmental and chamber conditions.

**Preconditions**
- Self-check has succeeded.
- Monitoring is permitted.

**Inputs**
- Temperature readings.
- Humidity readings.
- Light readings.
- Vibration readings.
- Door status.
- Artifact profile.
- Power status.

**Processing**
- Continuously collect sensor readings.
- Compare readings with permitted limits.
- Detect abnormal conditions.

**Outputs**
- Current environmental status.
- Detected abnormal conditions.

**Postconditions**
- The latest chamber condition is available for decision-making.

**Failure/Exception**
- Missing or invalid sensor readings.

---

## 6. CheckDoorStatus

**Purpose:** Determine whether the chamber door is open or closed.

**Preconditions**
- Door sensor is operational.

**Inputs**
- Door sensor reading.

**Processing**
- Read the door sensor and determine its current state.

**Outputs**
- Door status: OPEN or CLOSED.

**Postconditions**
- The system knows whether normal conservation activities may continue.

**Failure/Exception**
- Door sensor failure or invalid reading.

---

## 7. MeasureTemperature

**Purpose:** Determine whether the current temperature is within the artifact's permitted range.

**Preconditions**
- Temperature sensor is operational.
- Environmental profile is loaded.

**Inputs**
- Current temperature.
- Minimum permitted temperature.
- Maximum permitted temperature.

**Processing**
- Compare the current temperature with the permitted range.

**Outputs**
- Temperature status: within range or outside range.

**Postconditions**
- Temperature condition is classified.

**Failure/Exception**
- Invalid or unavailable temperature reading.

---

## 8. MeasureHumidity

**Purpose:** Determine whether the current humidity is within the artifact's permitted range.

**Preconditions**
- Humidity sensor is operational.
- Environmental profile is loaded.

**Inputs**
- Current humidity.
- Minimum permitted humidity.
- Maximum permitted humidity.

**Processing**
- Compare the current humidity with the permitted range.

**Outputs**
- Humidity status: within range or outside range.

**Postconditions**
- Humidity condition is classified.

**Failure/Exception**
- Invalid or unavailable humidity reading.

---

## 9. CorrectTemperature

**Purpose:** Attempt to restore temperature to the permitted range.

**Preconditions**
- Artifact is inside the chamber.
- Environmental profile is loaded.
- Temperature is outside the permitted range.
- Required control mechanism is available.

**Inputs**
- Current temperature.
- Permitted temperature range.
- Recovery-period limit.

**Processing**
- Activate the appropriate environmental-control mechanism.
- Continue monitoring temperature.

**Outputs**
- Temperature-control command.
- Updated temperature readings.

**Postconditions**
- A correction attempt has been initiated.
- The system must verify actual recovery before declaring the condition safe.

**Failure/Exception**
- Control mechanism unavailable.
- Temperature remains outside range during the allowed recovery period.

---

## 10. CorrectHumidity

**Purpose:** Attempt to restore humidity to the permitted range.

**Preconditions**
- Artifact is inside the chamber.
- Environmental profile is loaded.
- Humidity is outside the permitted range.
- Required control mechanism is available.

**Inputs**
- Current humidity.
- Permitted humidity range.
- Recovery-period limit.

**Processing**
- Activate the appropriate humidity-control mechanism.
- Continue monitoring humidity.

**Outputs**
- Humidity-control command.
- Updated humidity readings.

**Postconditions**
- A correction attempt has been initiated.
- Recovery must be verified by sensor readings.

**Failure/Exception**
- Control mechanism unavailable.
- Humidity remains outside range during the allowed recovery period.

---

## 11. VerifyEnvironmentalRecovery

**Purpose:** Confirm that an environmental condition has actually returned to its permitted range after correction.

**Preconditions**
- A temperature or humidity correction has been attempted.
- Relevant sensor is operational.

**Inputs**
- Current sensor reading.
- Artifact environmental limits.
- Recovery-period information.

**Processing**
- Read the relevant sensor.
- Compare the reading with the permitted range.
- Determine whether recovery has been maintained within the required period.

**Outputs**
- Recovery verified: YES or NO.

**Postconditions**
- If recovery is verified, normal operation may continue when other conditions are satisfied.
- If recovery fails within the allowed period, protection action is required.

**Failure/Exception**
- Condition does not recover within the allowed recovery period.
- Sensor reading becomes unavailable.

---

## 12. DetectVibration

**Purpose:** Detect significant vibration that could increase risk to the artifact.

**Preconditions**
- Vibration sensor is operational.
- Artifact is inside the chamber.

**Inputs**
- Current vibration reading.
- Permitted vibration threshold.

**Processing**
- Compare vibration level with the permitted threshold.

**Outputs**
- Vibration status.

**Postconditions**
- Significant vibration is identified when the threshold is exceeded.

**Failure/Exception**
- Vibration sensor failure or invalid reading.

---

## 13. VerifyVibrationStabilization

**Purpose:** Confirm that vibration has remained below the permitted threshold for the required stabilization period.

**Preconditions**
- A significant vibration event has been detected.
- Vibration sensor is operational.

**Inputs**
- Vibration readings.
- Permitted vibration threshold.
- Required stabilization period.

**Processing**
- Continuously sample vibration.
- Verify that readings remain below the threshold for the complete stabilization period.

**Outputs**
- Stabilization result.

**Postconditions**
- If successful, the system may consider returning to normal operation after all other required checks pass.

**Failure/Exception**
- Vibration exceeds the threshold again.
- Sensor becomes unavailable.

---

## 14. SuspendConservationActivities

**Purpose:** Immediately suspend normal conservation activities when continuing them could increase risk to the artifact.

**Preconditions**
- Artifact is inside the chamber.
- A suspension condition has been detected, such as an open door or significant vibration.

**Inputs**
- Door status.
- Vibration status.
- Environmental status.

**Processing**
- Stop normal conservation activities that should not continue during the abnormal condition.
- Maintain necessary monitoring.

**Outputs**
- Suspension command/status.

**Postconditions**
- Normal conservation activities are suspended until required verification is completed.

**Failure/Exception**
- Required control mechanism fails to respond.

---

## 15. ActivateProtectionControls

**Purpose:** Prioritize artifact protection when an environmental condition cannot be corrected within the allowed recovery period.

**Preconditions**
- Environmental recovery has failed or another protection condition has been confirmed.

**Inputs**
- Environmental condition.
- Artifact environmental profile.
- Available protection controls.

**Processing**
- Reduce light exposure where appropriate.
- Activate additional environmental controls.
- Maintain monitoring.

**Outputs**
- Protection-control commands.
- Protection status.

**Postconditions**
- Additional protective measures are active.

**Failure/Exception**
- Protection mechanism unavailable or fails.

---

## 16. GenerateOperatorAlert

**Purpose:** Notify the museum operator that a protection response or significant abnormal condition requires attention.

**Preconditions**
- A condition requiring operator notification has been detected.

**Inputs**
- Incident type.
- Environmental readings.
- Artifact information.
- Current system condition.

**Processing**
- Create and issue an alert containing relevant incident information.

**Outputs**
- Operator alert.

**Postconditions**
- Alert is generated and recorded.

**Failure/Exception**
- Alert mechanism unavailable.

---

## 17. SwitchToEmergencyPower

**Purpose:** Maintain system operation using emergency power after normal power is lost.

**Preconditions**
- Normal power has failed.
- Emergency power is available.

**Inputs**
- Normal power status.
- Emergency power availability.

**Processing**
- Detect power loss.
- Activate emergency power source.
- Verify emergency power availability.

**Outputs**
- Emergency power status.

**Postconditions**
- System continues operating on emergency power.

**Failure/Exception**
- Emergency power unavailable or fails to activate.

---

## 18. RecordPowerFailure

**Purpose:** Record a power-loss incident for system history and operator awareness.

**Preconditions**
- Normal power loss has been detected.

**Inputs**
- Time of power failure.
- Power status.
- Emergency power status.

**Processing**
- Record the power incident and relevant system condition.

**Outputs**
- Power-failure record.

**Postconditions**
- Power incident is stored for later review.

**Failure/Exception**
- Recording/storage mechanism unavailable.

---

## 19. VerifySafeCondition

**Purpose:** Verify that the chamber and artifact are in a safe condition before normal operation or artifact removal.

**Preconditions**
- A safety verification has been requested.
- Required sensors are operational.

**Inputs**
- Environmental readings.
- Door status.
- Sensor status.
- Vibration status.
- Protection status.
- Artifact status.

**Processing**
- Verify environmental conditions.
- Verify sensor health.
- Verify vibration has stabilized when required.
- Verify no active protection response is underway.

**Outputs**
- Safe-condition result.

**Postconditions**
- System confirms whether the chamber is safe.

**Failure/Exception**
- Any required safety condition is not satisfied.

---

## 20. AuthorizeArtifactRemoval

**Purpose:** Allow an operator to remove an artifact only when the chamber is confirmed safe.

**Preconditions**
- Artifact is inside the chamber.
- Safe condition has been verified.
- No active protection response is underway.

**Inputs**
- Safe-condition result.
- Protection status.
- Artifact status.

**Processing**
- Check all removal requirements.
- Authorize removal only if all requirements are satisfied.

**Outputs**
- Removal authorization: GRANTED or DENIED.

**Postconditions**
- Artifact removal is permitted only after successful safety verification.

**Failure/Exception**
- Chamber is unsafe.
- Active protection response exists.
- Required verification is incomplete.

---

## 21. PerformSafeShutdown

**Purpose:** Safely shut down the chamber when normal power is lost and emergency power is unavailable.

**Preconditions**
- Normal power has failed.
- Emergency power is unavailable.

**Inputs**
- Power status.
- Emergency power status.
- Current chamber condition.

**Processing**
- Record the power incident.
- Stop non-essential operations safely.
- Preserve necessary incident information.
- Place the system in a safe shutdown condition.

**Outputs**
- Shutdown status.
- Power-failure record.

**Postconditions**
- Chamber is safely shut down.
- Normal conservation operation is not active.

**Failure/Exception**
- Shutdown mechanism fails or required information cannot be recorded.
