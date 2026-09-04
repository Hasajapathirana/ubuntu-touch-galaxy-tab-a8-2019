# Ubuntu Touch 24.04 for the Samsung Galaxy Tab A8 2019

Ubuntu Touch 24.04 port for the Galaxy Tab A8 2019 (gtowifi), Snapdragon 429

Note - This port will work on both T290/T295  versions but sim card functionallity is not test

The kernel source is [here](https://github.com/Hasajapathirana/android_kernel_samsung_sdm429.git) , halium-13.0 branch.

# Ubuntu touch Port status

The tablet boot into GUI , most stuff work fine as per below table 

| Component | Status | Notes |
|---|---|---|
| **Display** | ✅ | |
| **Shell** | ✅ |  |
| **GPU** | ✅ |  |
| **Touchscreen** | ✅ |  |
| **Backlight** | ✅ | Screen brightness control |
| **Buttons** | ✅ | Power and volume |
| **Wi-Fi** | ✅ | |
| **Speakers / microphones** | ✅ |  |
| **Vibration** | ✅ |  |
| **Motion sensors** | ✅ |  |
| **Battery and charging** | ✅ |  |
| **Storage** | 🟡 |  MicoSD card is untested |
| **Package management** | ✅ |  |
| **Core applications** | ✅ | Morph browser, File manager and Terminal launch and survive reboots |
| **Waydroid** | ✅ | |
| **Audio** | ✅ | |
| **USB gadget** | 🟡 | MTP works but default but config needs to be set up|
| **Bluetooth** | ❌ | Configs are not set |
| **Cameras** | ❌ | Not started |

✅ tested on the physical tablet · 🟡 partially working · ❌ known not to work
or not integrated · ❔ not tested yet · — not applicable

## Building

Requires a Linux host and should be on the tab LineageOS 20 (anything higher or lower wont work)

```bash
git clone https://github.com/Hasajapathirana/ubuntu-touch-galaxy-tab-a8-2019.git samsung-gtowifi
cd samsung-gtowifi
sudo chmod 644 overlay/system/etc/deviceinfo/devices/gtowifi.yaml
./build.sh -b workdir
./build/prepare-fake-ota.sh ./out/device_gtowifi_usrmerge.tar.xz ota
./build/system-image-from-ota.sh ota/ubuntu_command images
```

## Installing ##

Notes - I will soon add a flashable till now you have to flash it manually

**Warning flash this at your own risk**
Requirments - Unlocked Bootloader, TWRP installed , sdcard or usbotg to flash boot.img (unless heimdall is used), A laptop or PC
1. You have to install LineageOS 20 for this from [here](https://lineage-archive.timschumi.net/build/21269) 
2. Using TWRP flash the boot.img to BOOT partition or use heimdall
3. Wipe Data
4. Now on the pc within the location of ubuntu.img ( **If not rename rootfs.img to ubuntu.img**) and adb push ubuntu.img /data/
 
