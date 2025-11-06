
-----

# Hackintosh EFI for Huawei Matebook D15 2020 (BOHB-WAX9)

OpenCore EFI Configuration for **macOS Tahoe 26.1** on the Huawei Matebook D15 2020 (BOHB-WAX9).

##  

## 🚨 IMPORTANT: How to Use This EFI

**You MUST generate your own SMBIOS values before using this EFI.**

Using the `PlatformInfo` values in the provided `config.plist` will cause issues with iServices and could get your Apple ID banned.

### How to Generate a New SMBIOS

1.  Download [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS).
2.  Run the script.
3.  Select option 1: **"Download/Update MacSerial"**.
4.  Select option 3: **"Generate SMBIOS"**.
5.  When asked for a model, type `MacBookPro16,3` (this is a good match for your 10th-gen i3 CPU).
6.  The script will generate a **Serial**, **Board Serial (MLB)**, and **SmUUID**.
7.  Open your `EFI/OC/config.plist` with a plist editor (like ProperTree or OCAT).
8.  Go to the `PlatformInfo > Generic` section.
9.  Copy and paste the generated values into the following fields:
      * `SystemSerialNumber` -\> **Serial**
      * `MLB` -\> **Board Serial**
      * `SystemUUID` -\> **SmUUID**
10. Save the `config.plist` file, and you are ready to boot.

-----

## Hardware Specifications

| Component | Model |
| :--- | :--- |
| **Processor** | Intel Core i3-10110U @ 2.10GHz |
| **Graphics** | Intel UHD Graphics |
| **RAM** | 8GB (Onboard) |
| **Storage** | Samsung SSD 990 Evo plus 1TB |
| **Wireless** | Intel Wireless-AC 9560 160MHz |
| **Audio** | Everest ESSX8336 (Intel SST) - **Not Supported** |

-----

## 📝 General Notes

This EFI was created after an update from macOS Ventura. It felt a bit laggy at first, as most of the Kexts had to be changed, and the data migration was minimal (almost like a clean install).

In general use, it's quite smooth. Due to the low 8GB of RAM and older i3 CPU, it can stutter under very heavy loads. However, for light tasks like typing, general studying, or even editing FHD 60fps video, it works comfortably.

-----

## 💻 System Status

### ✅ What Works

  * **Wi-Fi:** Functional via `itlwm.kext` and the [HeliPort](https://github.com/OpenIntelWireless/HeliPort) app.
  * **Keyboard & Trackpad:** Functions perfectly, including all Fn keys.
  * **Webcam:** Working.
  * **Ports:** All USB ports and the HDMI port are working.
  * **iServices:** iCloud login and App Store downloads work (after generating your own SMBIOS).
  * **Hardware Info:** CPU and iGPU information (i3-10110U, Intel UHD) display correctly.

### ❌ What Doesn't Work / Issues

  * **Native Wi-Fi Interface:** The default macOS Wi-Fi menu does not work. You **must** use the HeliPort app to connect to Wi-Fi.
  * **Bluetooth:** Not working. May require an external USB Bluetooth adapter or further USB port mapping.
  * **AUDIO (NOT WORKING):**
      * The built-in **Everest ESSX8336 (Intel SST) audio chip is NOT SUPPORTED** in macOS.
      * Attempts with SOF, VoodooHDA, and AppleHDA patches were all unsuccessful.
      * **You must use an external USB sound card or USB/Bluetooth headphones for all audio.**
  * **Apple Continuity:** AirDrop, CarPlay, Handoff, and other continuity features are not functional.
