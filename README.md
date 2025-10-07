 # HP Z840 macOS Tahoe

![Screenshot](Images/screenshot.png)

## 🔍 Overview
This repository contains all the necessary resources to get macOS Tahoe up and running on your HPN Z840 (Potentially also on Z440 and Z640). While this repository is primarily a compilation of existing resources and tools, it includes all the essential components to ensure smooth installation and performance on your Z840.

## Hardware Info

### System Specs

Component     | Details                                                       
-------------:|-------------------------------------------------------------- 
**Mainboard** | Stock HP board
**CPU**       | Dual Intel Xeon E5-2697A v4 (64) @ 2.60GHz        
**RAM**       | 320 GB DDR4 2400 Mhz Samsung
**dGPU**      | AMD Radeon RX 6600 XT (8 Gb)
**Audio**     | Realtek® ALC1220-VB (Layout-id: `11`)
**Ethernet** <br>(on-board) | Intel Ethernet Connection

## ℹ️ Current Status

| Feature | Status | Notes |
| ------------- | ------------- | ------------- |
| **Graphics** | ✅ Working | Works with native supported AMD card |
| **Speakers and Headphones via headphone jack** | ✅ Working | Clear audio, no issues detected |
| **Ethernet** | ✅ Working | One of the built-in Ethernet port is functional. 2nd one needs to be disabled |
| **NVMe SSD** | ✅ Working | Supported with the correct NVMeFix kext
## ℹ️ Not working
| Feature | Status | Notes |
| ------------- | ------------- | ------------- |
| **Sleep wake** | ❌ Not Working | Currently the device doesn't go to sleep automatically |

## ! Notes

Set 'Security -> SecureBootModel' to 'Disabled' (case sensitive) during installation. Once you are up and running, you can set it back to 'Default'.

Whatevergeen was causing blackscreen after verbose logs, so I switched to NootRX and it performs much better compared to Whatevergeen.

### ℹ️ Changing Serial Number, Board Serial Number, and SmUUID

To use iMessage and other Apple services, you need to generate your own serial numbers. This can be done using [Hackintool](https://github.com/benbaker76/Hackintool). Go to the “Serial“ tab and make sure model is set to MacPro. Use the barcode-with-apple button to check your generated serial numbers. If the website tells you that the serial number isn't valid, everything is fine. Otherwise, you have to generate a new set.

Next you will have to copy the following values from Hackintool to your config.plist:
- Serial Number -> Root/PlatformInfo/Generic/SystemSerialNumber
- Board Number -> Root/PlatformInfo/Generic/MLB
- SmUUID -> Root/PlatformInfo/Generic/SystemUUID

Reboot and Apple services should work.

If they don't, follow [this in-depth guide](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html). It goes deeper into ROM, clearing NVRAM, clearing Keychain (missing this step might cause major issues), and much more.
