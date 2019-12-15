## TWRP device tree for Xiaomi CC9 / MI 9 Lite (Pyxis)

Basic   | Spec Sheet
-------:|:----------
CPU     | Hexa-Core Kryo 360 Silver 1.7GHz
CPU     | Dual-Core Kryo 360 Gold 2.2GHz
Chipset | Qualcomm Snapdragon 710, SDM710
GPU     | Adreno 616
ROM     | 128GB
RAM     | 6GB
Android | 9.0
Battery | 4030 mAh, Li-Po
Display | 1080x2340 pixels, 6.39 AMOLED
Rear Camera  | 48MP+8MP+2MP, AI Dual Camera
Front Camera | 32MP

![Xiaomi MI 9 Lite](https://fdn2.gsmarena.com/vv/pics/xiaomi/xiaomi-mi-cc9-2.jpg "Xiaomi MI 9 Lite")

## Features

Works:

- ADB
- Decryption of /data
- Screen brightness settings
- Correct screenshot color
- MTP
- Flashing (opengapps, roms, images and so on)
- Backup/Restore (Needs more testing)
- USB OTG
- Android Pie and Q Support
- Vibration support

## Compile

First checkout minimal twrp with omnirom tree:

```
repo init -u git://github.com/minimal-manifest-twrp/platform_manifest_twrp_omni.git -b twrp-9.0
repo sync
```

Then add these projects to .repo/manifest.xml:

```xml
<project path="device/xiaomi/pyxis" name="brigudav/android_device_xiaomi_pyxis-twrp" remote="github" revision="master" />
```

Finally execute these:

```
. build/envsetup.sh
lunch omni_pyxis-eng
mka recoveryimage ALLOW_MISSING_DEPENDENCIES=true # Only if you use minimal twrp tree.
```

Install:

```
fastboot flash recovery recovery.img
```
