# Jiro-SDM845M Local Manifests

Official local manifest repository for maintaining and building **LineageOS on Mainline Linux Kernel (Linux 6.x LTS)** for Qualcomm Snapdragon 845 devices, specifically **Xiaomi POCO F1 (`beryllium`)**.

## Architecture Overview
This distribution leverages the official LineageOS Mainline framework:
* `device/mainline/common`: Generic upstream kernel Android board and init scripts.
* `device/mainline/qcom-common`: Qualcomm SoC mainline configurations and `lk2nd` bootloader integration.
* `hardware/mainline/*`: Open-source HALs for standard Linux interfaces (IIO sensors, ALSA audio, sysfs LEDs/vibrators).
* `external/linux-firmware-mainline`: Firmware binaries from `kernel.org`.
* `device/xiaomi/beryllium`: POCO F1 mainline device tree.
* `kernel/xiaomi/sdm845`: Linux 6.x LTS kernel with in-tree SDM845 and Beryllium DTS support.

## Usage
Clone or copy `beryllium_mainline.xml` into your ROM source tree's `.repo/local_manifests/`:
```bash
mkdir -p .repo/local_manifests
curl -sL https://raw.githubusercontent.com/Jiro-SDM845M/local_manifests/main/beryllium_mainline.xml -o .repo/local_manifests/beryllium_mainline.xml
repo sync -j$(nproc --all)
```
