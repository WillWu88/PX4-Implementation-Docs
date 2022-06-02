# Attitude Control

## 1. Quaternion
See [[Quaternion]] for detailed notes on the quaternion framework.

## 2. Attitude Controller LQR Framework
- For modeling, see [[Quadcopter Model]]
- For LQR controller design with [[Rate Control]] integrated, see [[lqr_controll]]


## 3. Multi-copter Attitude Controller Implementation

For general control structure, refer to [[NuttX OS]]

### A. Input
- Receives $q_{sp}$ from "Acceleration and Yaw to Attitude" module
	- and current attitutde $q$ from sensor/estimator
- Indirectly receives input from [[Position and Velocity Controller]]

### B. Angle Controller
Angle Controller Diagram:
![P Controller](https://docs.px4.io/master/assets/img/mc_angle_diagram.90e53599.jpg)

- Updates at 250 Hz
- P controller

- Quaternion controllers can suffer from "*unwinding*", where the body goes through an unnecessary full rotation or it ends up at the double cover position. 

Technical Report Diagram:

![[att-ctrl-quat.pdf#page=6]]See Figure 3

###### Source Code:
- Link: ~/PX4/Firmware/src/modules/mc_att_control/AttitudeControl

###### Attitude Control Class
- setProportionalGain
	- yaw weight is limited between 0 and 1
- setRateLimit
- update
	- Return rates set point
	- in the form of *vector3f*

###### References
- Math
	- [[Matrix]]
	- [[Mathlib]]


### C. Attitude Controller Module:
###### Controller Messages
1. **Subscription**
- [[autotune_attitude_control_status]]
- [[manual_control_setpoint]]
- [[vehicle_attitude_setpoint]]
- [[vehicle_control_mode]]
- [[vehicle_status]]
- [[vehicle_land_detected]]

2. **Subscription Call Back**
- [[vehicle_attitude]]

3. **Publication**
- [[vehicle_rates_setpoint]]
- [[vehicle_attitude_setpoint]]

###### Inheritance, basis, etc
- Implemented as a **WorkItem**
- See [[ModuleBase]]

### D. Output
* Angular Rate $\Omega$ set points
* Feeds into [[Rate Control]]

#flight_stack