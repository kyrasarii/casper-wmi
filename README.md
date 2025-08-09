#  **Casper Linux WMI Driver** 
Welcome to the **ultimate Linux kernel module** for **Casper Excalibur laptops**! Take full control of your keyboard backlight and hardware monitoring with this powerful, feature-packed driver. Let's light up your laptop experience! ✨

---

## 🚀 **Features**

This driver unleashes the full potential of your Casper Excalibur laptop, bringing advanced hardware control directly to your fingertips:

### ⌨️ **Keyboard Backlight Control**  
- **Full RGB control** via `/sys/class/leds/casper::kbd_backlight/` interface for stunning visual customization.

### 📊 **Hardware Monitoring**  
- **Real-time fan speeds** and **PWM control** through the hwmon interface for optimal thermal management.
- **Power plan management** to optimize performance and battery life.

### 🔧 **Multi-Model Support**  
- **Broad compatibility** across multiple Casper Excalibur models with intelligent hardware detection.

### 🔍 **Smart Detection**  
- **DMI-based model detection** ensures proper driver behavior for your specific laptop variant.

---

## 🛠️ **Installation Guide**

Ready to supercharge your **Casper Excalibur** with advanced hardware control? Follow these steps for the ultimate setup:

### Prerequisites
- **Linux kernel headers** for your current kernel version
- **Build tools** (`make`, `gcc`, etc.)
- **Root access** for module installation

### Quick Installation

1. **Clone and build the module**:
    ```bash
    git clone https://github.com/kyrasarii/casper-wmi.git
    cd casper-wmi
    make
    ```

2. **Test the module** (quick verification):
    ```bash
    sudo insmod casper-wmi.ko
    ```

3. **Test keyboard backlight magic**:
    ```bash
    echo "372ffffff" | sudo tee /sys/class/leds/casper::kbd_backlight/led_control
    ```

### Permanent Installation (Recommended)

For the **ultimate experience** with automatic loading on every boot:

1. **Install with proper compression**:
    ```bash
    sudo zstd casper-wmi.ko -o /lib/modules/$(uname -r)/kernel/drivers/platform/x86/casper-wmi.ko.zst
    ```

2. **Update module dependencies** (crucial step!):
    ```bash
    sudo depmod -a
    ```

3. **Set up automatic loading**:
    ```bash
    sudo nano /etc/modules-load.d/casper-wmi.conf
    ```
    
    Add this magic line:
    ```
    casper-wmi
    ```

4. **Verify manual loading** (optional but recommended):
    ```bash
    sudo modprobe casper-wmi
    lsmod | grep casper
    ```

5. **Test the boot process**:
    ```bash
    sudo modprobe -r casper-wmi  # Unload for testing
    sudo reboot
    ```

6. **Confirm success**:
    ```bash
    lsmod | grep casper
    ```

---

## 🎮 **Usage & Control**

Your laptop is now **supercharged**! Here's how to harness its power:

### 🌈 **LED Control**
- **Keyboard backlight interface**: `/sys/class/leds/casper::kbd_backlight/led_control`
- **Zone-specific control**: Send hex values for precise RGB customization
- **Multiple lighting modes**: Explore different effects and patterns

### 🌡️ **Hardware Monitoring**
- **Fan speeds**: Monitor via hwmon interface (`/sys/class/hwmon/hwmon*/`)
- **Power management**: Access and control power plans for optimal performance
- **Real-time data**: Get live hardware statistics and thermal information

### 🔧 **Advanced Configuration**
- **Custom commands**: Hex values for LED zones defined in `casper-wmi.c`
- **Hardware info access**: Complete system monitoring capabilities
- **Performance tuning**: Fine-tune your laptop's behavior

---

## 🔍 **Troubleshooting**

Having issues? No worries! Here's your **debug toolkit**:

### Common Solutions
- **Check kernel messages**: `dmesg | grep casper` for detailed driver information
- **Verify module loading**: `lsmod | grep casper` to confirm the driver is active
- **Missing sysfs interface?** Ensure your laptop model is supported and the module loaded correctly
- **BIOS compatibility**: Check the DMI table in `casper-wmi.c` for your specific model

### Quick Diagnostics
```bash
# Check if module is loaded
lsmod | grep casper

# View driver messages
dmesg | tail -20

# Verify sysfs interface
ls -la /sys/class/leds/casper::kbd_backlight/
```

---

## 🤝 **Contributing**

Join the **Casper WMI community**! We welcome contributions that make this driver even better:

- **🐛 Bug Reports**: Found an issue? Let us know!
- **🚀 Feature Requests**: Have ideas for new functionality?
- **💻 Code Contributions**: Pull requests for bug fixes and improvements
- **📱 Model Support**: Help us add support for more Casper Excalibur variants
- **📚 Documentation**: Improve guides and examples

---

## 🙏 **Credits & Acknowledgements**

A huge thank you to:

- **Linux Kernel Community**: For providing the foundation and APIs that make this possible
- **Casper Excalibur Users**: For testing, feedback, and feature requests
- **WMI Subsystem Developers**: For the excellent framework this driver builds upon
- **Open Source Community**: For the collaborative spirit that drives innovation

---

Transform your **Casper Excalibur** into the ultimate Linux powerhouse! If you have any questions, issues, or want to contribute, don't hesitate to open an issue or pull request. Happy hacking! 🚀💖
