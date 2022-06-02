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

###### I. Drag Simulation
PX4 Drag Equation:
$$F_D = C_D \cdot norm(v_{air}) \cdot v_{air}$$
By feeding in gaussian-distributed random signal as $v_{air}$, we're able to simulate wind as small disturbances.

###### II. Troubleshooting
- Error: altitude doesn't respond to setpoint, hover at negative height
	- Cause: incorrect sign in dynamics equations
	- Solution: 
		1. plot out error and commanded wrench
		2. compare gains to error
		3. check signs and correct dynamics equation


###### III. Successive Loop Closure, Cascaded LQR and Difference in Update Frequency
- **Guidelines**
	- Each successive loop must be lower in bandwidth (typically by a factor of 5-10)

- Splitting the controllers
	1. Structure? How does each loop pass down set points like PID?
	2. Substitution: subsititude P and V loop with PID
	3. Block out $K_{lqr}$ matrix based on different update speed
	4. How do we implement different update speed? Rate Transition Blocks?

###### IV. LQR with Different Update Frequency and Zero Order Hold
We started by modelling the difference in sampling rates. Position and Velocity states are now sampled at $50Hz$, rotation states (in quaternion) are sampled at $250Hz$, and rotational rate states are sampled at $1000Hz$. Below shows the simulation result. 

![[Rate_Trans_Sim-Error.jpg]]

The controller clearly tracks the reference signals asymptotically. 

###### V. Position, Velocity PID + Attitude LQR
We now investigate if we can formulate a LQR attitude & rate controller based on our current framework. 

- **PID Tuning**
	- 


## References
- [4481 Lecture 13_14 Slides](!https://wustl.instructure.com/courses/78192/files/4148862?module_item_id=1221526)

See [[Controller Module Development]] for C++ implementation.
#flight_stack #development