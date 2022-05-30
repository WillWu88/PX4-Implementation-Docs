# Flight Controller Software
- Single Codebase
- Reactive design, includes
	- exchangable components
	- asynchronous messaging

## 0. Key Param
- Sampling rate: **1K Hz**
- Publishing rate: **250 Hz**

## 1. Flight Stack
The flight stack's main function is to control the aircraft and estimate the states. The components include
- [[Esimator]]
- [[Commander]]
- [[Navigator]]
- [[Position Controller]]
- [[Attitude Control]]
- [[Rate Control]]
- [[Mixer]]

### Runtime Enviornment
- Task, vs
- Work Queue Task

May need to figure this out later when implementing a controller

![Flight Stack Graph](https://docs.px4.io/master/assets/img/PX4_High-Level_Flight-Stack.18829d0a.svg)

Overall Controller Architecture

![Controller Architecture](https://docs.px4.io/master/assets/img/mc_control_arch.21116ef0.jpg)

## 2. Middleware
- [[Simulator]]
- [[UORB]]
- [[Mavlink]]
## 3. Drivers

## 4. Dev
#### Programming Conventions
- Gains are all of type *float*
- Unit Quaternion
- 

#### Including the module into build
1. Include source files, make CMakeLists.txt
2. Write Kconfig for the directory
3. Run -> make [build-tartget] boardconfig and select the module

#main