# Attitude Control

## 1. Quaternion
#### Euler's Rotation Theorem
- In 3-d space, any displacement of a rigid body such that there exist a fixed point is equivalent to a rotation around an axis that runs through the fixed point
- Axis-angle representation: a unit vector $\hat{e}$, and a rotation angle $\theta$ . 

#### Unit Quaternion
Very similar to [[#Euler's Rotation Theorem]], quaternion visualizes a fixed amount of rotation around an **unit vector** in the form of $i, j$ and $k$. 

$$q = e^{\frac{\theta}{2}(e_x i + e_y j + e_z k)} = \cos{\frac{\theta}{2}} + (e_x i + e_y j + e_z k)\sin{\frac{\theta}{2}}$$
Rotation of a 3-d point, $p$

$$\hat{p} = q \cdot p \cdot q^{-1}$$
**Quaternion has a double cover**

#### Quaternion Properties
- Noncommutativity
- Norm $$norm(q) = \sum_{i=0}^{i=3} q^2_i$$
- Inverse: $$q^{-1} = \frac{1}{norm(q)} \cdot (q_0, -q^r)$$
and much more

## 2. Attitude Controller LQR Framework
- For modeling, see [[Quadcopter Model]]
- For LQR controller design with [[Rate Control]] integrated, see [[lqr_controll]]


## 3. Multi-copter Attitude Controller Implementation

For general control structure, refer to [[NuttX OS]]

### A. Input
- Receives $q_{sp}$ from "Acceleration and Yaw to Attitude" module
	- and current attitutde $q$ from sensor/estimator
- Indirectly receives input from [[Position Controller]]

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