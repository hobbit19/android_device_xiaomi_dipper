TWRP device tree for Xiaomi Mi 8

All blobs are extracted from miui_MIMIX2S_8.10.11_13b40c2eee_9.0 firmware.

The Xiaomi Mi 8 (codenamed _"dipper"_) is a high-end smartphone from Xiaomi.

It was announced in May 2018. Release date was June 2018.

## Device specifications

Basic   | Spec Sheet
-------:|:-------------------------
SoC     | Qualcomm SDM845 Snapdragon 845
CPU     | Octa-core (4x2.8 GHz Kryo 385 Gold & 4x1.8 GHz Kryo 385 Silver)
GPU     | Adreno 630
Memory  | 6 GB RAM
Shipped Android Version | 8.1 with MIUI 9.5
Storage | 64/128/256 GB
Battery | Non-removable Li-Ion 3400 mAh battery
Display | 1080 x 2248 pixels, 18:9 ratio, 6.21 inches, Super AMOLED (~402 ppi density)
Camera  | Dual 12 MP, 4-axis OIS, 2x optical zoom, dual PDAF, dual-LED (dual tone) flash

## Device picture

![Xiaomi Mi 8](https://cdn2.gsmarena.com/vv/pics/xiaomi/xiaomi-mi8-2.jpg)

## Features

Works:

- ADB
- Decryption of /data `fc1335025b030d58a82155c9ebd4cb98ccb56508`
- Screen brightness settings
- Now UI is very smooth `16d831bee5a660f5ac6da0d8fff2b3ec4697d663`
- Vibration on touch `c7c78d2fea4e9a53da09657ccb4155ec1344bd03`
- Correct screenshot color `8e4e8ec2f9890db53a6ecd1fa99fb73385271831`

Not Working:

- MTP FFS `d97d43360f6b9d3b9b6861b5566e85726a13109b`

## Compile

First checkout minimal twrp with omnirom tree:

```
repo init -u git://github.com/minimal-manifest-twrp/platform_manifest_twrp_omni.git -b twrp-9.0
repo sync
```

Then add these projects to .repo/manifest.xml:

```xml
<project path="device/xiaomi/dipper" name="TeamWin/android_device_xiaomi_dipper" remote="github" revision="android-9.0" />
```

Finally execute these:

```
. build/envsetup.sh
lunch omni_dipper-eng
mka recoveryimage ALLOW_MISSING_DEPENDENCIES=true # Only if you use minimal twrp tree.
```

To test it:

```
fastboot boot out/target/product/dipper/recovery.img
```
## Contributors

[Here](https://github.com/TeamWin/android_device_xiaomi_dipper/graphs/contributors)

## Thanks

- @travismills82 for his TWRP tree used as skeleton: [twrp_android_device_samsung_star2qltechn](https://github.com/travismills82/twrp_android_device_samsung_star2qltechn)

- @TeamWin for sagit TWRP tree used for partial decryption works: [android_device_xiaomi_sagit](https://github.com/TeamWin/android_device_xiaomi_sagit)

- @timesleader for dipper TWRP tree used for adb works:[android_device_xiaomi_dipper](https://github.com/timesleader/android_device_xiaomi_dipper)

- @wuxianlin for enchilada TWRP tree used for init.rc works:[android_device_oneplus_enchilada](https://github.com/TeamWin/android_device_oneplus_enchilada)

- @notsyncing for polaris TWRP tree used as base: [android_device_oneplus_enchilada](https://github.com/notsyncing/android_device_xiaomi_polaris)
