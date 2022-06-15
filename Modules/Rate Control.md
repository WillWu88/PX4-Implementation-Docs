# Rate Controller

The default angular rate controller uses a [[PID Controller]]

Angular Rate Controller Diagram:
![Controller Diagram](https://docs.px4.io/master/assets/img/mc_angular_rate_diagram.d3b839d2.jpg)

- [ ] KPID Controller -> question for Yunshen
- Anti-windup is integrated

[[LQR Controller]]

#### Messages associated with Rate Control
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


#flight_stack 