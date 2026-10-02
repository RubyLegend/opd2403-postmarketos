# OnePlus Pad 2 OPD2403 (PineappleP, Caihong) Mainline Bring-up

Mainline Linux port based on PostMarket OS for the OnePlus SM8650 (Caihong) platform. 
This device is based on Qualcomm Snapdragon 8 Gen 3 Processor, specifically SM8650 MTP base, which was successfully bricked previously by OnePlus ARB bit. Thankfully - managed to get it back online by myself.

## Current Status

| Feature | Status | Notes |
| :--- | :---: | :--- |
| **Boot / CPU** | 🟩 Working | SMP, CPUFreq, PSCI idle states |
| **Storage** | 🟩 Working | UFS initializes, all partitions are visible, rootfs mounts successfully, preserving Android for as much as possible, thus repartitioned system for a custom postmarketOS partition |
| **Display** | 🟨/🟩 Working | Novatek NT36532 Dual DSI initialized with fixed upstream DSC configuration (see patch 0017). Hardware mouse rendering still missing, only software mouse for now. |
| **Touchscreen** | 🟩 Working | Novatek NT36532 (TDDI, SPI DMA, 144Hz) |
| **USB Peripheral** | 🟩 Working | Telnet / `usb_gadget` mode  |
| **USB Host** | 🟩 Working | USB host mode initialize successfully without any issues. Baseus USB hub detected properly, with all USB devices, USB Ethernet and HDMI port. Seamless charging working as well. |
| **PCIe / WiFi** | 🟩 Working | Both Root Complex and WCN785x FastConnect 7800 wireless card are detected. Fully working. |
| **Bluetooth** | 🟨 Partial | Subsystem works. Pairing and audio playback works. Microphone input is not visible yet due to missing full audio subsystem. |
| **Flash LED** | 🟩 Working | Routed via PM8550 |
| **Buttons** | 🟩 Working | Properly mapped volume and power buttons. No issues. |
| **Audio** | 🟨 WIP | LPASS, requires userspace (Pipewire)<br>6x Awinic `aw882xx_smartpa` initialized |
| **Camera** | 🟥 Not Started | CamSS, requires userspace (libcamera), Sensors: `sc1320cs` (Rear) / `sc820cs` (Front) |
| **Battery / Charger** | 🟨 Partial | PM8550B + Southchip `sc8547-slave` / `sc8547a` (SuperVOOC)<br>Out of the box qcom-battmgr driver already feeding power to the battery. 5V/2A is working.<br>Not all properties of a battery can be read (like max capacity and estimated time to empty). Charge cycles also missing, but based on Android investigation - seems to be that they are not existant and purely userspace. Charging/discharging state is also somewhat broken. Needs further investigation. |
| **Sensors** | 🟥 Not Started | Somewhere in the _future_...<br>ALS/PS: `tcs3701` <br>Accel/Gyro: `icm4x607` <br>Mag: `mmc56x3x` |
| **GPS** | 🟥 Not Started | Somewhere in the _future_... |
| **NFC (over Pogo Keyboard)**| 🟥 Not Started | `qcom,sn-nci` |
| **Thermals** | 🟩 Working | VADC PMIC sensors mapped (`skin-temp`, `flash`, `wlan`, `battery`, etc.) |
| **GPU** | 🟩 Working | Adreno 750 initialized, firmware loaded. Graphics acceleration present, full OpenGL 4.6, 5.5 Gb VRAM, Vulkan API working, OpenCL 3.1. No issues detected. |
| **Remoteproc (ADSP/CDSP)** | 🟩 Working | Both ADSP and CDSP successfully initialized |
| **Suspend/Resume** | 🟨 Partial | Device successfully transitions to suspend (s2ram/s2idle, not sure which), and returns back in case no usb change happened.<br>If something happened on usb stack during wake up (plugged new device or unplugged charger/usb device) - kernel panic and reboot. Requires further investigation to somehow collect logs |
| **RAMOOPS** | 🟥 Not Working Yet | RAMOOPS region defined in dt, and have successfully attached kernel driver, but after a panic reboot - nothing is present in /sys/fs/pstore/, in both Android and Linux.<br>Assume that Qualcomm Watchdog wipes memory during panic reboot |
| **CoreDump reboot** | 🟥 Not Working Yet | Same as RAMOOPS. Manually initiated kernel panic is ignored by watchdog, thus coredump does not start. |
| **Idle Power Draw** | 🟩 OK | Around 0.7 W with display turned off. Around 2 W with full DE running. Under load - around 4-5 W. |
| **RTC** | 🟩 OK | Initiated, present in the system. Reports time since battery was connected (1970-06-23 23:40:58 as of writing). Not a real RTC clock in this way. On first installation without internet access it won't be able to synchronize time. After initial internet connection - everything works fine. Time drift without internet (in suspended mode) - present. Updating rtc module memory is not possible. Read-only access from the driver. |
