# Controller Module Development

## 1. Procedures and Conventions

#### Programming Conventions
- Gains are all of type *float*
- Unit Quaternion

#### Including the module into build
1. Include source files, make CMakeLists.txt
2. Write Kconfig for the directory
3. Run -> make [build-tartget] boardconfig and select the module

#### Gazebo Models, Parameter Extraction and Custom Model Simulation
- Model files are located in: *Tools/sitl_gazebo/models*
- World files are located in: *Tools/sitl_gazebo/worlds*
- Airframe files are under: *ROMFS/px4-fmu_common/init.d-posix/airframes*
	- rCS, the startup script, is also located in *ROMFS/px4-fmu_common*
	- Remember to also add the target to CMakeLists.txt
- Lastly, add model to: *platforms/posix/cmake/sitl_target.cmake*
- Run command: *make px4_sitl gazebo_my_vehicle*
- [Ref](https://discuss.px4.io/t/create-custom-model-for-sitl/6700/3)

#development 