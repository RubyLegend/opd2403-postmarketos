# OnePlus SM8650 (Caihong) Mainline Bring-up

Mainline Linux port based on PostMarket OS for the OnePlus SM8650 (Caihong) platform. 

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
| **Flash LED** | 🟥 Not Started | PMIC GPIO / LPG |
| **Audio** | 🟥 Not Started | LPASS, requires userspace (Pipewire) |
| **Camera** | 🟥 Not Started | CamSS, requires userspace (libcamera) |
| **Battery / Charger** | 🟥 Not Started | SuperVOOC / PMIC routing |
