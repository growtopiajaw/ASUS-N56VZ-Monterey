# ASUS N56VZ Monterey

This EFI folder is initially based off of [HP-Probook-EliteBook-Package-Creator-OC](https://github.com/chris1111/HP-Probook-EliteBook-Package-Creator-OC) with N56VZ specific fixes being added over time.

NOTE: No additional support will be provided and you are on your own. This EFI is provided as-is. Please backup your EFI folder before doing anything.

## Table of Contents
- [Laptop Specifications](#laptop-specifications)
- [Whats working?](#whats-working)
- [Patches and Tools](#patches-and-tools)
- [EFI Hierarchy and Explanation](#efi-hierarchy-and-explanation)
- [Credits](#credits)


### Laptop Specifications
- CPU: Intel® Core™ i5-3210M
- iGPU: Intel® HD Graphics 4000
- dGPU: NVIDIA GeForce GT 650M 2GB
- RAM: 8GB 1333MHz DDR3
- Audio Codec: Realtek ALC663
- Ethernet: Qualcomm Atheros AR8161 Gigabit Ethernet
- Wi-Fi Card: N/A
- Bluetooth Card: N/A
- BIOS revision: Version 217
- Screen resolution: 1366x768
- Chipset: Intel HM76


### Whats working
| Feature | Status |
| ------ | ------ |
| **2.5mm Jack** | Untested |
| **3.5mm Audio Jack** | ✅ |
| **AirDrop** | ❌ |
| **ASUS Instant Key** | Untested |
| **Audio** | ✅ |
| **Battery Status** | ✅ |
| **Bluetooth** | N/A |
| **Brightness** | ❌ |
| **CD-ROM** | ✅ |
| **Charging** | ✅ |
| **Continuity** | N/A |
| **dGPU** | ❌ |
| **Ethernet** | ✅ |
| **Graphics acceleration** | ✅ |
| **HDMI** | Untested |
| **iGPU** | ✅ |
| **Keyboard function keys & backlight** | ✅ |
| **Microphone** | ✅ |
| **Microphone Jack** | Untested |
| **SD Card Slot** | Untested |
| **Sidecar** | N/A |
| **Sleep/Wake** | ✅ |
| **Touch Pad** | ✅ |
| **USB** | ✅ |
| **VGA Out** | Untested |
| **Web Camera** | ❌ |
| **Wi-Fi** | N/A |
* N/A: Not Available / Unavailable
* ✅: Working
* ❌: Not Working
* Untested: Not tested yet, might or might not be working.


### Patches and Tools
   * HD4000 patch for Monterey: https://github.com/chris1111/Patch-HD4000-Monterey
   * MaciASL: https://bitbucket.org/RehabMan/os-x-maciasl-patchmatic/downloads/
      * (DSDT.aml disassembly and patches, use RehabMan-MaciASL-2018-0507.zip)
   * USBToolBox: https://github.com/USBToolBox/tool
      * (USB Mapping)


### EFI Hierarchy and Explanation
```
├── EFI
│   ├── OC
│   │   ├── ACPI
│   │   │   ├── DSDT.aml - Built from scratch based on my specific N56VZ's ACPI table
│   │   │   ├── SSDT-1.aml - Graphics patch for NVIDIA GeForce GT 650M 2GB
│   │   │   ├── SSDT-EC.aml - Based on dortania's OpenCore guide recommendations
│   │   │   ├── SSDT-IMEI.aml - Based on dortania's OpenCore guide recommendations
│   │   │   ├── SSDT-PNLF.aml - Based on dortania's OpenCore guide recommendations
│   │   │   ├── SSDT-SBUS-MCHC.aml - Based on dortania's OpenCore guide recommendations
│   │   │   ├── SSDT-XOSI.aml - Based on dortania's OpenCore guide recommendations
│   │   │   └── SSDT.aml - Generated from ssdtPRGen.sh
│   │   ├── Kexts
│   │   │   ├── AppleALC.kext - Audio Codec patch
│   │   │   ├── AsusSMC.kext - ASUS Keyboard Backlight, FN Keys & Track Pad patch
│   │   │   ├── AtherosE2200Ethernet.kext - Qualcomm Atheros AR8161 Gigabit Ethernet patch
│   │   │   ├── Intel7Series-Injector.kext - Intel HM76 patch (might not be necessary)
│   │   │   ├── Lilu.kext - Required for most kexts to function
│   │   │   ├── SMCBatteryManager.kext - Battery status kext
│   │   │   ├── SMCProcessor.kext - Processor info kext
│   │   │   ├── USBToolBox.kext - Required for UTBMap.kext to function
│   │   │   ├── UTBMap.kext - USB Mapping
│   │   │   ├── VirtualSMC.kext - SMC patch
│   │   │   ├── VoodooPS2Controller.kext - Keyboard & Track Pad patch
│   │   │   │   └── Contents
│   │   │   │       └── PlugIns
│   │   │   │           ├── VoodooInput.kext
│   │   │   │           ├── VoodooPS2Keyboard.kext
│   │   │   │           ├── VoodooPS2Mouse.kext
│   │   │   │           └── VoodooPS2Trackpad.kext
│   │   │   └── WhateverGreen.kext - Graphics patch
```


### Credits
- chris1111 for HD4000 patch and base for this EFI
- signer for the base for this "What's Working" list
