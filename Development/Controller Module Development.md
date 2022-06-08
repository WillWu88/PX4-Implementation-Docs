# Controller Module Development

## 0. Checklist
- [ ] [[#2 LQR Math Class]]
	- [ ] Math Lib
	- [ ] Unit Tests
- [ ] [[#3 LQR Module Class]]
- [ ]  Cmake, compiler config

## 1. Procedures and Conventions

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
- Set up:
- Notes on usage [[Eigen]]

## 3. LQR Module Class



[[CMake]]
[[KConfig]]
[[C++ Notes]]


## Appendix: References
- [[MPC-PX4 Implementation.pdf]]


#development 