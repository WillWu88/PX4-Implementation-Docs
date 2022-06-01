# LQR Replacement Module
## 1. LQR Formulation
Because LQR is model dependent, we started by building a [[Quaternion]] based [[Quadcopter Model]].

Penalty terms are chosen as identities for now. Gains are calculated through MATLAB.

## 2. Simulation
#### A. Simulink Simulation
- Simulink diagram partially based on PX4 Support Package
- Relevant forces:
	1. Thrust
	2. Gravity
	3. Drag
- Moments are from controller outputs

###### Drag Simulation
PX4 Drag Equation:
$$F_D = C_D \cdot norm(v_{air}) \cdot v_{air}$$

See [[Controller Module Development]] for C++ implementation.

#flight_stack #development