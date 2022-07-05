# Controller Module Development

## 0. Checklist & Questions

### A. Checklist
- [x] [[#2 LQR Math Class]]
	- [x] Math Lib
	- [x] Unit Tests
- [ ] [[#3 LQR Module Class]]
- [ ]  Cmake, compiler config

### B. Questions
- [ ] Yaw speed?
- [ ] Data hazard handling
- [ ] Floating point calculation: error around 0.005
- [x] Template class, derived class (module params, module base, etc)
- [ ] Methodologies

## 1. Procedures and Conventions
#### Specified Language Versions
- C++ 14
- C 11
#### Programming Conventions
- Gains are all of type *float*
- Unit Quaternion

#### Including the module into build
1. Include source files, make CMakeLists.txt
2. Write Kconfig for the directory
3. Run -> make [build-tartget] boardconfig and select the module
```shell
make <build_target> boardconfig
```


#### Gazebo Models, Parameter Extraction and Custom Model Simulation
- Model files are located in: *Tools/sitl_gazebo/models*
- World files are located in: *Tools/sitl_gazebo/worlds*
- Airframe files are under: *ROMFS/px4-fmu_common/init.d-posix/airframes*
	- rCS, the startup script, is also located in *ROMFS/px4-fmu_common*
	- Remember to also add the target to CMakeLists.txt
- Lastly, add model to: *platforms/posix/cmake/sitl_target.cmake*
- Run command: *make px4_sitl gazebo_my_vehicle*
- [Ref](https://discuss.px4.io/t/create-custom-model-for-sitl/6700/3)

### Warning: do not run *"cmake ."*
- Preserve the original Makefile, which contains all the necessary build targets

### Projectile Set Up
- .cache and compile_commands.json help clang to index heder files

## 2. LQR Math Class
### A. Member Variables
- Private
	- gain matrix
	- attitude set point
	- rate set point
	- yaw speed set point (?)
	- Limit (?)
	- Control Allocation Feedback

### B. Functions
* Public
	* Update
		* **Landing Logic Needed**
	* set K matrix
	* set attitude set points
	* adaptAttitudeSetpoint (?)
	* setRateLimit(?)
	* setSaturationStatus
		* how to use these status?
	* getRateControlStatus

### C. References
- [[Matrix]]
- [[Limits]]
- [[Mathlib]]
- [[Mixer]]
- [[rate_ctrl_status]]
- px4_platform_common/defines.h

### D. Eigen Library
- Set up
	- added cmakelist
	- edited cmakelist in relevant places
	- may need more config
- Notes on usage [[Eigen]]

### E. Unit Tests
- Our goal is to test the functions and internal calculations of "LQRControl"
- Refer to [[Testing]] for unit test notes
- Unit test list
- [x] Conversion tests
- [x] Run update once 


## 3. LQR Module Class
### A. [[ModuleBase]] functions and design
Public: 
- `custom_command`
- `task_spawn`
- `print_usage`
- `init`

Private:
- `Run`
	1. Check if program should exit
	2. Check if parameters have changed
	3. If either attitude or angular velocity is updated:
		- [x] Handle updated readings
		- [x] check if any relevant topics are updated
		- [ ] handle manual points (optional)
		- [ ] flight modes?
		- [x] run the controller
	5. publish control signals
- `parameters_updated`
	- set LQR gain matrix
- `throttle_curve` : adjust input throttle

This module class will serve as a combination between [[Attitude Control]] and [[Rate Control]]. See their respective pages for [[uORB]] messaging implementation.

### B. Related Messages:
#### A. Messages associated with Attitude Control
- Subscription
	- [[autotune_attitude_control_status]]
	- [[manual_control_setpoint]]
	- [[vehicle_attitude_setpoint]]
	- [[vehicle_control_mode]]
	- [[vehicle_status]]
	- [[vehicle_land_detected]]
- Subscription Call Back Work Item
	- [[vehicle_attitude]]
- Publication
	- [[vehicle_rates_setpoint]]
	- [[vehicle_attitude_setpoint]]

#### B. Messages associated with Rate Control
- Subscription
	- [[battery_status]]
	- [[control_allocator_status]]
	- [[landing_gear]]
	- [[manual_control_setpoint]]
	- [[vehicle_angular_acceleration]]
	- [[vehicle_control_mode]]
	- [[vehicle_land_detected]]
	- [[vehicle_rates_setpoint]]
	- [[vehicle_status]]
- Subscription Call Back
	- [[vehicle_angular_velocity]]
- Publication
	- [[actuator_controls]]
	- [[actuator_controls_status]]
	- [[rate_control_status]] (Publication Multi)
	- [[vehicle_rates_setpoint]]
	- [[vehicle_thrust_setpoint]]
	- [[vehicle_torque_setpoint]]
- Extra
	- [[parameter_update]]

[[CMake]]
[[KConfig]]
[[C++ Notes]]


## 4. Debugging
per Prof. Shidal's advice, a good way to learn about the system is to step through the debugger and examine the relationship between each module.

See [[GDB]] for notes on using the debugger.
``` shell
make px4_sitl gazebo_iris_gdb # debug in gdb
```

- Testing checklist
- [ ] Compilation Erros
- [x] Data flow: logging control, setpoint and state signals
- [ ] System data flow: where to, where from 
- [ ] Control signal correctness: am I publishing the right signals

### Function Tests
- Refer to [[Testing]] for function tests

### Logging, Messaging and Data Processing
- Refer to [[Logging]] for logging signals

### Data Flow
![[control_data_flow.jpg]]


### Simulation
See [[System Identification]] for physics parameters
- Lockstep: actuator signals now come with timesteps, making it possible to pause
- we can also control the speed of simulation with `PX4_SIM_SPEED_FACTOR`
- 

## Appendix: References
- [[MPC-PX4 Implementation.pdf]]


#development 