# Raspberry Pi

[[Companion Computer Offboard Control]]

## 1. Compiling [[ROS]] from source
- Too time consuming, skipped

## 2. Running [[ROS]] in Docker

## 3. Setting Up Pi Zero as a serial gadget
- modify `config.txt` and add `dtoverlay=dwc2` at the buttom
- modify `cmdline.txt` and add `modules-load=dwc2,g_serial` after `rootwait`
- enable getty service
- install `minicom` on host computer and select the right `tty` port


## Appendix: Reference
- [Pi Serial Gadget Setup](https://learn.adafruit.com/turning-your-raspberry-pi-zero-into-a-usb-gadget/serial-gadget) 

#hardware 