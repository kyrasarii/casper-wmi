# Casper Linux WMI Driver

A Linux kernel module to control keyboard backlight and hardware monitoring on Casper Excalibur laptops.

## Features

- Keyboard backlight control via `/sys/class/leds/casper::kbd_backlight/`
- Hardware monitoring (fan speeds, PWM control, power plans) through hwmon interface
- Support for multiple Casper Excalibur models
- DMI-based model detection for proper driver behavior

## Installation

1. **Build the module:**
   ```sh
   make
   ```

2. **Insert the module:**
   ```sh
   sudo insmod casper-wmi.ko
   ```

3. **Test keyboard backlight control:**
   ```sh
   echo "372ffffff" | sudo tee /sys/class/leds/casper::kbd_backlight/led_control
   ```

4. **(Optional) Install compressed module:**
   ```sh
   sudo zstd casper-wmi.ko -o /lib/modules/$(uname -r)/kernel/drivers/platform/x86/casper-wmi.ko.zst
   ```

## Usage

- The driver registers a sysfs interface at `/sys/class/leds/casper::kbd_backlight/led_control` for keyboard backlight control.
- Fan speeds and power plans are accessible via the hwmon subsystem (e.g., `/sys/class/hwmon/hwmon*/`).
- Supported commands (hex values) for LED zones and hardware info are defined in `casper-wmi.c`.


## Troubleshooting

- Check `dmesg` for messages from the module.
- If the sysfs interface is missing, verify your model is supported and the module is loaded.
- For BIOS or model support issues, refer to the DMI table in `casper-wmi.c`.

## Contributing

Feel free to open issues or pull requests for additional models, bug fixes, or improvements.
