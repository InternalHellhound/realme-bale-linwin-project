## Rolling back to Android 14
**This section is written for those, who have updated their phones to Android 15 and wants to unlock bootloader. If your device already runs Android 14, you can skip this section and get straight to the [unlock](https://github.com/InternalHellhound/realme-bale-linwin-project/edit/main/Guides/English/Miscellaneous/Unlock_BL.md#oem-unlock). This procedure also WILL ERASE your data, so do all necessary data backup before rolling back.**
* First and foremost, you need to get [rollback package](https://rbp01.realme.net/GT_Neo6/RMX3852_11_A_OTA_0240_all_25cztf_10010111.zip).
* As soon as you download your rollback package, enable developer options on your device.
* Turn on airplane mode on your device and find "Software update" (com.oplus.ota) app on your device.
* Clear all of its data and then return into Settings -> About device -> Software update.
* Press on 3 dots at the top right corner of your screen and choose "Local install".
* Select your rollback package via opened file manager and hit "install" button.
* After rollback has been applied, reboot your device via software update and wait for it to wipe all user data and reboot back into system.

## OEM unlock 
**Android 14 only!**
* First make sure to enable [USB debugging](https://developer.android.com/studio/debug/dev-options#enable) and OEM unlock in Android. Make sure you are also using **3rd party cable** and you already have backup of all of your data, since device **WILL BE ERASED** after unlocking bootloader!
* Set your device language to English.
* Log into your realme (heytap) account or sign it up on your device.
* Download latest DeepTest for your device. Wait for last day of your current month at 7pm (UTC+3) or first day of your next month and then open it and press "Apply for deep testing".
* Wait approximately 5-7 days, you could get accepted even earlier.
* If you got accepted, you will find a button "Enter deep testing". press it and you will be rebooted into bootloader.
* Connect your device to PC, open terminal with android platform tools installed and write next command:
```
$ fastboot flashing unlock
```
* On your device, accept unlock by pressing first **Volume Down** and then **Power** buttons.
* Your device will automatically wipe itself and reboot with unlocked bootloader!
