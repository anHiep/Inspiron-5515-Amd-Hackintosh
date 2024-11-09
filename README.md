# Overview
- My OpenCore EFI for Dell Inspiron 5515 with AMD ryzen 5 5500u.
- Everything works well, except AirDrop and Finger Print due to hardware limits.
- You can clone it and use it for your own bootable USB. But you should follow the OpenCore's instructions to apply your own machine to the EFI.

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

    | Feature                              | Status | Dependency          |
    | :----------------------------------- | ------ | ------------------- |
    | Touch Sceen                          | ✅   | Lastest VoodooI2CHID.kext |
    | Keyboard                             | ✅   | Lastest VoodooI2C.kext and voodooPS2.kext |
    | Backlight (brightness control)       | ✅   | Lastest NootedRed.kext and SSDT-PNLF.aml from [chefkissinc](https://chefkissinc.github.io/applehax/nootedred/) |

</details>

