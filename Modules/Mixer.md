# Mixer

- Saturation Requirements goes here
- vehicle dependent

## 1. Mixer Module
- file path: `src/lib/mixer_module`
- Mixer matrices: `ROMFS/px4fmu_common/mixers`

### Current Mixer:
- Airframe Script -> Mixer File -> Geometry File -> Auto Generated Table (c/c++)

## 2. Dynamic Mixing
- Multicopter system does not use dynamic mixing as of now
- Control Allocation: see diagram below

![[control_data_flow.jpg]]

- [[Quadcopter Model]] aware

## Appendix: Reference
- [Mixing System Rework](https://www.youtube.com/watch?v=xjLM9whwjO4)
- [PX4 Mixer Documentaiton Page](https://docs.px4.io/main/en/concept/mixing.html)


#flight_stack