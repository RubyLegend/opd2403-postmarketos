# OnePlus Pad 2 OPD2403 (PineappleP, Caihong) Mainline Bring-up

Mainline Linux port based on PostMarket OS for the OnePlus SM8650 (Caihong) platform. 
This device is based on Qualcomm Snapdragon 8 Gen 3 Processor, specifically SM8650 MTP base, which was successfully bricked previously by OnePlus ARB bit. Thankfully - managed to get it back online by myself.

## Current Status

| Feature | Status | Notes |
| :--- | :---: | :--- |
| **Boot / CPU** | 🟩 Working | SMP, CPUFreq, PSCI idle states |
| **Storage** | 🟨 Semi-working | UFS initializes, all partitions are visible, rootfs mount not tested yet, preserving Android for as much as possible |
| **Display** | 🟩 Working | Novatek NT36532 Dual DSI initialized with fixed upstream DSC configuration (see patch 0017) |
| **Touchscreen** | 🟩 Working | Novatek NT36532 (TDDI, SPI DMA, 144Hz) |
| **USB Peripheral** | 🟩 Working | Telnet / `usb_gadget` mode  |
| **USB Host** | 🟨 WIP / Partially working | Proprietary ADSP protocol to switch usb from `device` mode to `host`. Porting downstream driver to make it cleaner in a state machine |
| **PCIe / WiFi** | 🟨 WIP | Root Complex detected, Endpoint missing. Chip: Qualcomm "Kiwi" (WCN7850) |
| **Bluetooth** | 🟥 Not Started | Seems to be controlled over PCI Express |
| **Flash LED** | 🟩 Working | Routed via PM8550 |
| **Audio** | 🟨 WIP | LPASS, requires userspace (Pipewire)<br>6x Awinic `aw882xx_smartpa` initialized |
| **Camera** | 🟥 Not Started | CamSS, requires userspace (libcamera), Sensors: `sc1320cs` (Rear) / `sc820cs` (Front) |
| **Battery / Charger** | 🟨 Partial | PM8550B + Southchip `sc8547-slave` / `sc8547a` (SuperVOOC)<br>Out of the box qcom-battmgr driver already feeding power to the battery. 5V/2A is working. |
| **Sensors** | 🟥 Not Started | Somewhere in the _future_...<br>ALS/PS: `tcs3701` <br>Accel/Gyro: `icm4x607` <br>Mag: `mmc56x3x` |
| **GPS** | 🟥 Not Started | Somewhere in the _future_... |
| **NFC (over Pogo Keyboard)**| 🟥 Not Started | `qcom,sn-nci` |
| **Thermals** | 🟩 Working | VADC PMIC sensors mapped (`skin-temp`, `flash`, `wlan`, `battery`, etc.) |
| **GPU** | 🟨 WIP | Adreno 750 initializes (`renderD128`), firmware loading. Missing `vdd` and `vddcx` regulators (causes dummy regulator fallback). |
| **Remoteproc (ADSP/CDSP)** | 🟩 Working | Both ADSP and CDSP successfully initialized |
