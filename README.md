# Linux keyboard backlight driver for Casper Excalibur laptops
I'm working on sending a patch to lkml. Until then, this works for me.

# How to build and install
```
$ make
$ sudo insmod casper-wmi.ko
```
sudo echo "312ff0000" > /sys/class/leds/casper::kbd_backlight/led_control


echo 1 > /sys/class/hwmon/hwmon/pwm1_mode
