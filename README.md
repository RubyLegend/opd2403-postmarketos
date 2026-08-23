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
| **USB Host (OTG)** | 🟨 WIP | Missing VBUS boost / Role-switch |
| **PCIe / WiFi** | 🟨 WIP | Root Complex detected, Endpoint missing |
| **Bluetooth** | 🟥 Not Started | Seems to be controlled over PCI Express |
| **Flash LED** | 🟩 Working | Routed via PM8550 |
| **Ambient light sensor** | 🟥 Not Started | Investigating... |
| **Audio** | 🟥 Not Started | LPASS, requires userspace (Pipewire) |
| **Camera** | 🟥 Not Started | CamSS, requires userspace (libcamera) |
| **Battery / Charger** | 🟥 Not Started | SuperVOOC / PMIC routing |
| **Sensors** | 🟥 Not Started | Somewhere in the _future_... |
| **GPS** | 🟥 Not Started | Somewhere in the _future_... |
