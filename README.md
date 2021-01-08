TWRP device tree for Asus Zenfone 5z

The Asus Zenfone 5z (codenamed _"Z01RD"_) are high-end smartphones from Asus.
Asus Zenfone 5z was announced and released in June 2018.

## Device specifications

Basic   | Spec Sheet
-------:|:-------------------------
SoC     | Qualcomm SDM845 Snapdragon 845
CPU     | Octa-core (4x2.8 GHz Kryo 385 Gold & 4x1.8 GHz Kryo 385 Silver)
GPU     | Adreno 630
Memory  | 4GB / 6GB / 8GB RAM (LPDDR4X)
Shipped Android Version | 8.0 with ZenUI 5
Storage | 64/128/256 GB UFS2.1
Battery | Non-removable Li-Po 3300 mAh
Display | 1080 x 2246 pixels, 18.7:9 ratio, 157.48 mm (6.2 in), IPS LCD (~402 ppi density)
Height | 153 mm (6.02 in)
Width | 75.7 mm (2.98 in)
Diameter | 7.9 mm (0.31 in)
Weight | 165 g (5.82 oz)
Build | Glass front (Gorilla Glass), aluminum back, aluminum frame
SIM | Hybrid Dual SIM (Nano-SIM, dual stand-by, dual Volte)
Extras  | Dual speakers, NFC, microSD Card
Rear Camera 1 (IMX363) | 12MP, 4-axis OIS, f/1.8, 1/2.55" large sensor size, 1.4µm large pixel size, dual-pixel PDAF, 83° FOV, dual-LED (dual tone) flash
Rear Camera 2 (ov8856) | 8MP, f/2.0, 120° wide-angle camera
Front Camera (ov8856) | 8MP, 1.12µm, f/2.0, 84° FOV, 1080p 30 fps video

## Device picture

![Asus Zenfone 5z](https://i.imgur.com/SL8yhBe.jpg)


## Kernel

Prebuilt kernel source:
https://github.com/5z-devs/android_kernel_asus_sdm845

## Compile

First download omni-9.0 tree:

```
repo init -u git://github.com/minimal-manifest-twrp/platform_manifest_twrp_omni.git -b twrp-9.0
```

Then we will create the local_manifests folder and the asus.xml file

```
mkdir -p .repo/local_manifests
touch .repo/local_manifests/asus.xml
```

Then add these projects to .repo/local_manifests/asus.xml:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<manifest>
  <!-- device trees -->
  <project name="teamwin/android_device_asus_Z01RD" path="device/asus/Z01RD" remote="github" revision="android-9.0"/>

</manifest>
```

Now you can sync your source:

```
repo sync
```

To auotomatic make the twrp installer, you need to import this commit in the build/make path: https://gerrit.omnirom.org/#/c/android_build/+/33182/

Finally execute these:

```
. build/envsetup.sh
export ALLOW_MISSING_DEPENDENCIES=true
export LC_ALL=C
lunch omni_Z01RD-eng
mka adbd recoveryimage
```
