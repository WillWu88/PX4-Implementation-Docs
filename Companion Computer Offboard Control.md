# Companion Controller

Building a new firmware module is hard. Many programming challenges exist. A new direction is to investigate is to set up an offboard, external computer that communicates with PX4 flight controller/send control signals directly. It is a [[LQR Controller]] that will incorporate [[Position and Velocity Controller]], [[Attitude Control]] and potentially [[Rate Control]]. 

An advantage of that is the implementation is theoretically simpler than my current approach. It will also be easier to debug. A disadvantage is that the new system require a lot of set up and debugging, and time is of essense. 

The companion computer will likely be a raspberry pi, running [[ROS]]

## 1. Messaging and Communication with [[PX4 Autopilot]]
- The vehicle will run in off-board mode. See [[Flight Mode]] for notes
- Instead of running uORB, the companion will run thru [[Fast DDS]]
- **Required packages**
	- `px4_ros_com`
	- `px4_msgs`


## Appendix: Reference


#development #flight_stack 