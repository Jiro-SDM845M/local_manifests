# Local Manifests for Xiaomi POCO F1 (`beryllium`) on LineageOS Mainline

This repository provides the local manifest required to build **LineageOS Mainline** (Linux 6.x / 7.x) on the **Xiaomi POCO F1 (`beryllium`)** and SDM845 family.

## Architecture: Direction A (Lean Firmware Symlink)
- **No separate proprietary vendor repository**: Firmware blobs (`adsp`, `cdsp`, `modem`, `venus`, `tas2559`) are dynamically symlinked to the device's native `/vendor/firmware_mnt/image/` partition at runtime.
- **Open-source Userspace**: Mesa Freedreno Turnip Vulkan, open-source QRTR/QMI RIL (`qrild`), and AIDL audio HAL.

## How to Use

1. Initialize your LineageOS tree (e.g. `lineage-24.0`):
   ```bash
   repo init -u https://github.com/LineageOS/android.git -b lineage-24.0 --git-lfs
   ```

2. Add this local manifest:
   ```bash
   git clone https://github.com/Jiro-SDM845M/local_manifests.git .repo/local_manifests
   ```

3. Sync all repositories:
   ```bash
   repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags
   ```

4. Build LineageOS for POCO F1:
   ```bash
   source build/envsetup.sh
   lunch lineage_beryllium-ap2a-userdebug
   m bacon
   ```
