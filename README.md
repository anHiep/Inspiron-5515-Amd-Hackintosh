<h1 align="center">Hackintosh the Dell Inspiron 5515</h1>

<p align="center">
    <a href="https://support.apple.com/vi-vn/106337">
        <img src="https://img.shields.io/badge/Ventura-13.7.1-orange.svg"/></a>
    <a href="https://www.dell.com/support/home/en-vn/product-support/product/inspiron-15-5515-laptop/overview">
        <img src="https://img.shields.io/badge/Inspiron-5515-blue"/></a>
    <a href="https://github.com/acidanthera/OpenCorePkg">
        <img src="https://img.shields.io/badge/OpenCore-1.0.2-blue"/></a>
</p>

<p align="center">
    <a href="./Pictures/desktop.png" target="_blank">
        <img src="./Pictures/desktop.png" alt="Dell Inspiron 5515 macOS"> </a>
</p>

# Overview
**I am not responsible for any damages you may cause.**

**If my work here helped you. Please consider donating, it would mean a lot to me.**

**Any advice or suggestions would be greatly appreciated.**

- I will try my best to keep the EFI updated with OpenCore, Kext, NootedRed, ...
- This EFI is configured with MacOs Ventura, I currently can't manage to update to Sonoma

# Laptop Specification
- **Processor:** AMD Ryzen 5 5500U 2.1 GHz 

- **Ram:** 12 GB (dual channel, with [8gb Kingston Ram](https://memoryzone.com.vn/ram-laptop-kingston-ddr4-8gb-bus-3200mhz-kvr32s22s8-8) replaced for one broken 4gb ram)

- **SSD:** NVMe KIOXIA 256GB Media

- **Display:** 15.6" Full HD (1920 x 1080) with touch

- **Video Cardy**:
    - iGPU: AMD vega 7
    - dGPU: this laptop comes with no dGPU

# Summary
<details>
  <summary>What works</summary>
  <br>

  | Feature                              | Status | Dependency                                                     |
  | ------------------------------------ | ------ | -------------------------------------------------------------- |
  | Touch Screen (with gestures like trackpad) | ✅     | Latest VoodooI2C.kext, VoodooHID.kext                    |
  | Built-in Keyboard, Mouse             | ✅     | Latest VoodooI2C.kext, VoodooPS2.kext                          |
  | Trackpad Gestures                    | ✅     |                                                                |
  | Backlight (Brightness Control)       | ✅     | Latest NootedRed.kext, SSDT-PNLF.aml from [chefkissinc](https://chefkissinc.github.io/applehax/nootedred/) |
  | Keyboard brightness                  | ✅     | BrightnessKeys.kext                                            |
  | iServices (iMessage, FaceTime, App Store, iCloud, ...)| ✅     | Generate your own SMBIOS                              |
  | Graphic Acceleration                 | ✅     | Increase Vram to 2 GB using [Smokeless_UMAF](https://github.com/DavidS95/Smokeless_UMAF) |
  | Battery Percentage Indication        | ✅     |                                                                |
  | Processor Status                     | ✅     | VirtualSMC.kext                                                |
  | WiFi                                 | ✅     | AirportItlwm.kext                                              |
  | Bluetooth                            | ✅     | IntelBluetoothFirmware.kext, BlueToolFixup.kext                |
  | USB 2.0, USB 3.0, USB type C         | ✅     | USBToolBox.kext                                                |
  | Camera                               | ✅     |                                                                |
  | Audio                                | ✅     | AppleALC.kext                                                  |
  | HDMI                                 | ✅     |                                                                |

</details>

<details>
  <summary>What <strong>not</strong> works</summary>
  <br>

  | Feature                              | Status | Dependency                                                     |
  | ------------------------------------ | ------ | -------------------------------------------------------------- |
  | Air Drop/ Handoff                    | ❌     | Broadcom BlueTooth card                                        |
  | Finger Print                         | ❌     | Requires Apple M2 Chip (I don't know why)                      |
  | Bootcamp                             | ❌     | Maybe because ssd problems                                     |

</details>

<details>
  <summary>What is <strong>not</strong> tested</summary>
  <br>

  | Feature                              | Status | Dependency                                                     |
  | ------------------------------------ | ------ | -------------------------------------------------------------- |
  | Time Machine                         | 🕒     |                                                                |
  | Microphone                           | 🕒     |                                                                |
  | Screen Mirroring                     | 🕒     |                                                                |
  | SD Card Reader                       | 🕒     |                                                                |

</details>

# Some instructions & advices
<details>
  <summary>SSDTs</summary>
  <br>

  In the past, my friend had to write SSDT manually. But now we have a tool named [SSDTTime](https://github.com/corpnewt/SSDTTime)

  **Step 1:** Start with option ```P``` to dump the current system's DSDT. **Make sure to do this on the system where you want to install MacOS**

  **Step 2:** Some option that I need on my laptop
  - ```FixHPET``` (choose ```C``` when prompting)
  - ```USBX``` (choose default option ```B``` when prompting)
  - ```RTCAWAC```
  - ```PluginType``` (only on AMD laptop)
  - ```FakeEC Laptop```
  - ```PLNF```
  - ```XOSI``` (choose default option ```A``` when prompting)

  **Step 3:** Copy all the file end with ```*.aml``` in the ```Results``` folder. After that, paste these files into ```\EFI\OC\ACPI```

  **Step 4:** Merge ```patches_OC.plist``` by using the PatchMerge script included with SSDTTime. Remember to copy the ```config.plist``` in ```Results``` folder to ```\EFI\OC``` (I made a mistake when forgeting to copy the file and wasted a lot of time fixing touch screen with backlight)

</details>

<details>
  <summary>Increase VRAM</summary>
  <br>

  **Disclaimer:** This ```Smokeless_UMAF``` is significant **dangerous**, which can break your system's BIOS. **THINK TWICE** before commiting any changes. **USE AT YOUR OWN RISK**. 
  
  **Disclaimer:** **No one** is responsible for any damage.

  **Instruction:** I followed this [Youtube video](https://www.youtube.com/watch?v=mzLinRI1IVw) which uses [Smokeless_UMAF](https://github.com/DavidS95/Smokeless_UMAF)

</details>

# Credits    
- [Apple](https://www.apple.com) for macOS.
- [Acidanthera](https://github.com/acidanthera) for all the kexts/utilities.
- [corpnewt](https://github.com/corpnewt) for increadible tools like Propertree, MountEFI, SSDTTime
- [iamthaoly](https://github.com/iamthaoly) for SSDTTime guides
- [Dortania](https://github.com/dortania) for the OpenCore Install Guide.
- [Chefkissinc](https://chefkissinc.github.io) for great kexts, patches, guides for AMD hackintosh.
