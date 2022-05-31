# Quadcopter Mathematical Model

## 1. Rotational
See [[Attitude Control]] for Quaternion math background

6 -> 7 states for rotation:

$$x_{rot} = \begin{bmatrix}q_0 & q_1 & q_2 & q_3 & p & q & r\end{bmatrix}^T$$
$$\dot{x}_{rot} = \frac{1}{2} \begin{bmatrix}-q_{1:3}^T  \vec{\Omega} \\ (S(q_{1:3}) + q_0 I)\vec{\Omega}\end{bmatrix}$$
$$S(q_{1:3}) = \begin{bmatrix}0 & -q_3 & -q_2 \\ q3 & 0 & -q_1 \\ -q_2 & q_1 & 0 \end{bmatrix}$$
Same moment/kinematic equations as DCM convention

See equation (11) ![[4481-hw3.pdf#page=4]]
## 2. Translational Kinematics
Translational kinematics remain largely the same. Will investigate later for [[Position Controller]]

## 3. Drone Physical Model Parameters

#### A. Gazebo Iris Quadcopter
- See iris.sdf for parameters
- $a$, $b$, $c$, and $d$ aerodynamic coefficients are only relevant in mixer. 
- since rotation doesn't involve thrust, there's no need for identifying equilibrium motor speed
- Gyroscopic moments and aerodynamic moments are removed for simplicity.
	- Investigate/add these terms back if the controller doesn't stabilize


#### B. Lab Drone

## Appendix: Reference
- [[Quaternion-Based-Model.pdf]]
- Aircraft Control and Simulation
	- Page 50-51: quaternion kinematics
- [[Quadcopter-sim.pdf]]
#math 