## Preparation
- [KernelSU](https://github.com/tiann/KernelSU/releases) / [KernelSU Next](https://github.com/KernelSU-Next/KernelSU-Next/releases) / [Magisk](https://github.com/topjohnwu/Magisk/releases)
- [Payload dumper go](https://github.com/ssut/payload-dumper-go)
- Full ota package for your device
- [Modified OrangeFox recovery](https://github.com/realme-pineapple-devs/recovery_device_realme_pineapple/releases)
> [!CAUTION]
> Current version of this recovery is still WIP and also doesn't have required for the project features yet. This warning will be removed as soon as all necessary stuff will be fixed.

## Installing custom recovery
- Download both **.img** and **.zip** files from release page.
- Reboot into bootloader by powering off device, then powering it on by holding both **volume-** and **power** buttons at the same time.
- Connect your device to computer and type next command in terminal:
```
$ fastboot flash recovery /path/to/recovery.img
```
- Reboot into recovery using any comfortable for you way
- In recovery, enable ADB sideload, reconnect device to computer and type next command:
```
$ adb sideload /path/to/recovery-zip-package.zip
```
Device will automatically reboot into new custom recovery.

## Rooting
### init_boot.img extraction
- Unpack payload.bin from your full ota archive and place it into dumper's folder.
- Run the next command to unpack payload.bin:
```
# For Windows:
$ payload-dumper-go.exe /path/to/payload.bin

# For Linux:
$ payload-dumper-go /path/to/payload.bin
```
- Copy init_boot image from the folder where payload was extracted to (usually its "extracted-...") to your phone.
### KernelSU Next / KernelSU
There are 2 modes in which KernelSU (Next) can work: [GKI](https://kernelsu.org/guide/installation.html#gki-mode) and [LKM](https://kernelsu.org/guide/installation.html#lkm-mode)

#### GKI mode (both KernelSU and its "Next" fork)
- Download AnyKernel3 release of KernelSU Next GKI for your kernel (e.g. AnyKernel3-android14-6.1.99_2024-10.zip. For our device related packages are android14-6.1.XX)
- Reboot into custom recovery, then enable ADB sideload.
- Connect your phone to computer and type next command into terminal:
```
$ adb sideload /path/to/gki-package.zip
```
- Reboot into system and you are done! (Don't forget to install manager app)

#### LKM mode
- Move extracted init_boot image to your device.
- Open installed your root manager app.
- Choose "select a file" in installation choices, then choose extracted init_boot image in opened file manager. Patch the image.
- Move patched init_boot image to your computer, then reboot your device into bootloader, connect it to computer and type into terminal:
```
$ fastboot flash init_boot /path/to/patched-init-boot.img
```
Reboot your device into system and you are done!

### Magisk
Perform same set of moves, which were described for [LKM mode in KernelSU](https://github.com/InternalHellhound/realme-bale-linwin-project/main/Guides/English/Miscellaneous/Rooting.md#lkm-mode).
