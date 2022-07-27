# Companion Controller

Building a new firmware module is hard. Many programming challenges exist. A new direction is to investigate is to set up an offboard, external computer that communicates with PX4 flight controller/send control signals directly. It is a [[LQR Controller]] that will incorporate [[Position and Velocity Controller]], [[Attitude Control]] and potentially [[Rate Control]]. 

An advantage of that is the implementation is theoretically simpler than my current approach. It will also be easier to debug. A disadvantage is that the new system require a lot of set up and debugging, and time is of essense. 

The companion computer will likely be a raspberry pi, running [[ROS]]. See [[C++ Notes]] and [[Python Notes]] for programming notes. 

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
- Flight mode enum:
	- `src/modules/commander/px4_custom_mode.h`
	- linked to `VEHICLE_CMD_DO_SET_MODE`

### Important Member functions
1. `publish_offboard_control_mode` : publish offboard control flags for [[offboard_control_mode]]
2. `publish_trajectory_setpoint` : publish position setpoints
3. `publish_vehicle_command` : tap into commander, set vehicle to offboard mode for [[vehicle_command]]

## 3. PX4 Offboard Controller Design

Previous examples have all centered around using LQR with the onboard rate controller. But underlying infrastructure supports outputting actuator signals. We will start with designing a LQR with torque as output, then falling back to rates if actuator signals are not fast enough.

### I. Messaging:
#### Publication:
- [[offboard_control_mode]]: set `actuator` to true, therefore disabling rate controller
- [[vehicle_control_mode]]: set `flag_control_offboard_enabled` to true, enabling offboard control mode
- [[vehicle_rates_setpoint]]: set rate setpoints (when we want to run the onboard rate controller)
- [[actuator_controls]]: control group: 0
	- remember to set landing gear
- [[vehicle_command]]: set vehicle to offboard mode. See above section for enum set up

#### Subscription
- time_sync
- position data
- velocity data
- attitude data
- rate data

### II. Library, Packages, API
- Created as a ROS Node
	- Explicit? See [[C++ Notes]]
	- see [[ROS]] for notes on nodes and development notes
- Modified `CMakeLists.txt` based on adding `frame_transform` library

### III. LQR Control Library
- **Requires [[Eigen]] 3.4**
- See [[Testing]] for incoporating gtest in ROS
- Refer to github change log and `CMakeLists.txt` for adding the lqr library

### IV. Control Signal Conditioning
- Refer to [[Mixer]] for calculation procedure
- 

## 4. Offboard Controller Setup
### **!!!!!! Set `COM_RCL_EXCEPT=4`**



## Appendix: Reference
- [Off-board control example](https://docs.px4.io/main/en/ros/ros2_offboard_control.html)
- [[ICRA18_Foehn.pdf]]

#development #flight_stack 