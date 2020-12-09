# easyHackUSB
A simple Python script to construct a bootable Hackintosh Install USB.

Currently, the script can only run on macOS and can only be used to make Intel Hackintosh USBs.

**KEEP IN MIND:** This script will only construct the **bare minimum**. Configuring the config, installing more kexts, adding SSDTs etc. has to be done manually.

The config.plist will always be the sample one that comes with the bootloader of choice (Clover/OpenCore).
If you have a system that closely resembles a Mac, Clover **might** boot macOS but OpenCore definitely will not.
## Development Status
**easyHackUSB** is **70%** done.

**Current task:** Step 3. - Finishing up - Downloading kexts

## How it Works
The script is pretty simple.
Everything the script does is just automate the steps found on the [Dortania Guide](https://dortania.gitbook.io).
It **does not** however make a universal bootable USB.
The script is laid out like this:
### 1. - Getting Info
* Get path to macOS Installer
* Get architecture (x86(x32)/x64)
* Get system type (AMD/Intel)
* Get BIOS type (UEFI/Legacy)
* Get bootloader the User wants to use (Clover/OpenCore)
### 2. - Preparing the USB
* Get disk number and format USB
* Execute createinstallmedia from the installer
* Mount EFI and download bootloader of choice **If bootloader is Clover, it's going to be downloaded according to the specified architecture**
* Move bootloader from temp directory to USB
### 3. - Finishing up
* Download and move essential kexts (VirtualSMC, Lilu, WhateverGreen, AppleALC) to EFI
* **(Only if BIOS is Legacy and bootloader is OpenCore)** Run BootInstall_IA32.tool or BootInstall_X64.tool according to architecture.
