ggested to base the new files of the iris or solo files.  
The parameters, such as the vehicle mass, inertias, motor models, controller gains etc. can be changed in the new files to simulate a different vehicle.  
But one won’t necessarily b# Flight Controller Software
- Single Codebase
- Reactive design, includes
	- exchangable components
	- asynchronous messaging

## 0. Key Param
- Sampling rate: **1K Hz**
- Publishing rate: **250 Hz**


## 1. Flight Stack
- For detailed overview of the system, see [this video](https://www.youtube.com/watch?v=orvng_11ngQ) by the PX4 team

The flight stack's main function is to control the aircraft and estimate the states. The components include
- [[Esimator]]
- [[Commander]]
- [[Navigator]]
- [[Position and Velocity Controller]]
- [[Attitude Control]]
- [[Rate Control]]
- [[Mixer]]

**Our Research will focus on the [[#4 Research Focus]]**

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
- [[ROMFS]]
## 3. Drivers

## 4. Research Focus
### Stage 1: Attitude LQR Controller
- Substitute out the default PID Attitude and Rate Controller for LQR-based control

See [[LQR Controller]] for notes on design, [[Controller Module Development]] for implementation and development

## Appendix: References
-  

#main