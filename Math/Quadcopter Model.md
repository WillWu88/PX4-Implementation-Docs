# Quadcopter Mathematical Model

## 1. Rotational
See [[Quaternion]] for Quaternion math background

6 -> 7 states for rotation:

$$x_{rot} = \begin{bmatrix}q_0 & q_1 & q_2 & q_3 & p & q & r\end{bmatrix}^T$$
$$\dot{x}_{rot} = \frac{1}{2} \begin{bmatrix}-q_{1:3}^T  \vec{\Omega} \\ (S(q_{1:3}) + q_0 I)\vec{\Omega}\end{bmatrix}$$
$$\begin{align} S(q_{1:3}) = \begin{bmatrix}0 & -q_3 & -q_2 \\ q3 & 0 & -q_1 \\ -q_2 & q_1 & 0 \end{bmatrix} \end{align}$$
Same moment/kinematic equations as DCM convention

See equation (11) ![[4481-hw3.pdf#page=4]]

#### Quaternion and Controllability
7 -> 6 states for rotation
- Since the rotational quaternions are unit quaternions, $q_0$ is constrained
- If we take the above equation and directly linearize if, we would get a singular kalman controllability matrix
- We can reduce $\dot{x}_{rot}$ to a 3x3 matrix
$$\dot{\begin{bmatrix}q_1 \\ q_2 \\ q_3\end{bmatrix}} = \frac{1}{2}(S(q_{1:3}) + q_0 I)\vec{\Omega} = \frac{1}{2} (S(q_{1:3}) + \sqrt{1-(q_1^2 + q_2^2 + q_3^2)} I)\vec{\Omega}$$

## 2. Translational Kinematics
The principles of translational kinematics remain largely the same under our framework with quaternion rotations. We can either convert quaternion to DCM and keep our previous matrix, or associate the three unit quaternion terms with gravity rotation and frame transform.

- See [[Quaternion]] for Quaternion-DCM conversion
- We can multiply the converted DCM to convert forces
	- $q_0 = \sqrt{1-(q_1^2 + q_2^2 + q_3^2)}$
- **All rotations are in "ZYX" order**


## 3. Drone Physical Model Parameters

#### A. Gazebo Iris Quadcopter
- See iris.sdf for parameters
- $a$, $b$, $c$, and $d$ aerodynamic coefficients are only relevant in mixer. 
- since rotation doesn't involve thrust, there's no need for identifying equilibrium motor speed
- Gyroscopic moments and aerodynamic moments are removed for simplicity.
	- Investigate/add these terms back if the controller doesn't stabilize


#### B. Lab Drone
- [ ] Identify Moments of Inertia and relevant parameters


## Appendix: Reference
- [[Quaternion-Based-Model.pdf]]
- Aircraft Control and Simulation
	- Page 50-51: quaternion kinematics
- [[Quadcopter-sim.pdf]]
- [[Tailsitter_report Daniel.pdf]]

#math 