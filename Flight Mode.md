# Flight Modes

## 1. Offboard Mode
- For controlling vehicle movement and attitude
- Sending rate setpoints

## 2. Adding a new Flight Mode
- Followed reference [1]
- Added new vehicle status flag: `offboard_control_full_signal_lost`
- There's actually no need to add a new flight mode, as `offboard_control_mode` already have an actuator flag


## Appendix: References
1. [Adding a new flight mode](https://uav-lab.org/2016/11/07/px4-research-log-10-adding-a-new-flight-mode-preparation/)


#development #mid  