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
- Version control
	- fast_dds 2.0.2
	- fast_rtps_gen: 1.04

## 2. PX4 Offboard Control Example Dissection
- For PX4: configure send/receive topics at: `msg/tools/urtps_bridge_topics.yaml`
	- use the following script in the same folder to update urtps message in ROS folder
```shell
./uorb_to_ros_urtps_topics.py -i urtps_bridge_topics.yaml -o updated.yaml
# then copy updated.yaml to ros package template folder and rename it
```
- didn't enable virtual thumbsticks in PX4, so offboard control can't takeoff
- Position follows north-east-down


## Appendix: Reference
- [Off-board control example](https://docs.px4.io/main/en/ros/ros2_offboard_control.html)
- [[ICRA18_Foehn.pdf]]

#development #flight_stack 