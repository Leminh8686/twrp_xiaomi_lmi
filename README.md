# android_device_xiaomi_lmi
For building TWRP for Redmi K30 Pro / POCO F2 Pro

TWRP device tree for Redmi K30 Pro / POCO F2 Pro

Kernel and all blobs are extracted from [miui_LMI_20.5.24_80680c42ee_10.0.zip](https://airtel.bigota.d.miui.com/20.5.24/miui_LMI_20.5.24_80680c42ee_10.0.zip) firmware.

The Xiaomi Redmi K30 Pro / POCO F2 Pro (codenamed _"lmi"_) is a high-end smartphones from Xiaomi.

## Device specifications

| Device       | Xiaomi Redmi K30 Pro / POCO F2 Pro                       |
| -----------: | :------------------------------------------ |
| SoC          | Qualcomm SM8250 Snapdragon 865              |
| CPU          | 8x Qualcomm® Kryo™ 585 up to 2.84GHz        |
| GPU          | Adreno 630                                  |
| Memory       | 6GB / 8GB RAM (LPDDR4X and LPDDR5)                     |
| Shipped Android version | 10                               |
| Storage      | 128GB / 256GB (UFS 3.0 for 6/128 model, UFS 3.1 for later) flash storage |

## Features

**Works**

- Booting.
- [Decryption](https://github.com/simonsmh/android_bootable_recovery/commits/android-10.0).
- ADB
- MTP

**Not Working**

- Super partition functions (WIP)
- Vibration

POCO F2 Pro / Redmi K30 Pro is using Dynamic Partition! We need update from TWRP.

## Compile

First checkout minimal twrp with omnirom tree:

```
repo init -u git://github.com/minimal-manifest-twrp/platform_manifest_twrp_omni.git -b twrp-10.0
repo sync
```

Then add these projects to .repo/manifest.xml:

```xml
<project path="device/xiaomi/lmi" name="TeamWin/android_device_xiaomi_lmi" remote="github" revision="android-10.0" />
```

Finally execute these:

```
. build/envsetup.sh
lunch omni_lmi-eng
mka recoveryimage ALLOW_MISSING_DEPENDENCIES=true # Only if you use minimal twrp tree.
```

To test it:

```
fastboot boot out/target/product/lmi/recovery.img
```

## Thanks
- [FsCrypt fix by mauronofrio](https://github.com/mauronofrio/android_bootable_recovery)
- [Decryption by bigbiff](https://github.com/bigbiff/android_bootable_recovery)
- [Oneplus 8 TWRP by mauronofrio](https://github.com/mauronofrio/android_device_oneplus_instantnoodle_TWRP)
