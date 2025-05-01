# Linux keyboard backlight driver for Casper Excalibur laptops
I'm working on sending a patch to lkml. Until then, this works for me.

# How to build and install
```
$ make
$ sudo insmod casper-wmi.ko
```
echo "312ff0000" | sudo tee /sys/class/leds/casper::kbd_backlight/led_control
