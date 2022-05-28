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

## 2. Multi-copter Attitude Controller Implementation

For general control structure, refer to [[NuttX OS]]

#### I. Angle Controller
Angle Controller Diagram:
![P Controller](https://docs.px4.io/master/assets/img/mc_angle_diagram.90e53599.jpg)

- Updates at 250 Hz
- P controller
- Receives $q_{sp}$ from "Acceleration and Yaw Attitude" module
	- and current attitutde $q$ from sensor/estimator

Technical Report Diagram:

![[att-ctrl-quat.pdf#page=6]]See Figure 3

##### Source Code:
- Link: ~/PX4/Firmware/src/modules/mc_att_control/AttitudeControl

###### Attitude Control Class
- setProportionalGain
	- yaw weight is limited between 0 and 1
- setRateLimit
- update

###### References
- Math
	- [[Matrix]]
	- [[Mathlib]]

#### II. Rate Controller
Angular Rate Controller Diagram:
![Controller Diagram](https://docs.px4.io/master/assets/img/mc_angular_rate_diagram.d3b839d2.jpg)

- [ ] KPID Controller -> question for Yunshen
- Anti-windup is integrated


#flight_stack