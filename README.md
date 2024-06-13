# Jetson_BOOT_setup
## Setup and installation of BOOTing process for Orin Nano and AGX orin_32.
1. **REQUIREMENT FOR HOST MACHINE:**
    - Host machine should be AMD or X86_64 ARCH and with Ubuntu 16.04 or 18.04 or 20.04 or 22.04:
2. **INSTALL JETSON SDK MANAGER:**
    - Login to the [website](https://developer.nvidia.com/sdk-manager) and download SDK
    - Install with ` sudo apt install ./sdkmanager_[version]-[build#]_amd64.deb`
    - launch SDK Manager with the command, `sdkmanager` 
3. **DOWNLOAD JETPACK FOR TARGET:**
    - After installing "sdkmanager", now select the target and host machine in GUI
    - And in same page select which jetpack to be installed for target, our case "jetpack 6.0"
    - Give continue and Download the package by selecting the location, our case `"$HOME/nvidia-sdk/Jetapck_6.0_Linux_JETSON_<device: AGX_ORIN_TARGETS>/Linux_for_Tegra"`

4. **RECOVERY MODE FOR DIFFERENT BOARDS:**
    - After installing SDK manager move to `Linux_for_Tegra` folder which will be in ***nvidia_sdk download*** folder and export it like below:
    - ` export JETPACK=$HOME/nvidia-sdk/Jetapck_6.0_Linux_JETSON_<device: AGX_ORIN_TARGETS>/Linux_for_Tegra`
5. **INSTALATION IN TARGET MACHINE:**
    - After connecting the usb and  power recovery mode use below to code snippets to
    - ` lsusb ` to list usb added and check `Bus 001 Device 015: ID xxx:xxx NVIDIS Corp. Tegra On-Platform Operation`.
    - ` cd $JETPACK ` move to boot file directory
    - ` sudo ./flash.sh <target board name>  <root device name: where to boot : eMMc, USB, NVMe>`
    - in our case `sudo ./flash.sh jetson-agx-orin-devkit mmcblk0p1`
    - Device like 
        * jetson-agx-orin-devkit
        * jetson-agx-orin-devkit-as-jao-40w
        * jetson-agx-orin-devkit-as-nx-16gb
        * jetson-agx-orin-devkit-as-nx-8gb
    - and root device like:
        * ' mmcblk0p1'----- internal eMMC.
        * ' sda1 '---------- external  USB devices (USB memory stick, HDD)
    
    [READ MORE HERE](https://developer.ridgerun.com/wiki/index.php/NVIDIA_Jetson_Orin/JetPack_5.0.2/Flashing_Board#Option_#1:_eMMC)
    - [NVIDIA Jetson Xavier FLASHING](https://developer.ridgerun.com/wiki/index.php/Xavier/JetPack_5.0.2/Flashing_Board)
