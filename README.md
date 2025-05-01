# Linux keyboard backlight driver for Casper Excalibur laptops
I'm working on sending a patch to lkml. Until then, this works for me.

# How to build and install
```
$ make
$ sudo insmod casper-wmi.ko
```
LED Control
echo "312ff0000" > /sys/class/leds/casper\:\:kbd_backlight/led_contr

Power Control
echo 1 > /sys/class/hwmon/hwmon8/pwm1_mode

Fan Monitor
cat /sys/class/hwmon/hwmon8/fan1_input
