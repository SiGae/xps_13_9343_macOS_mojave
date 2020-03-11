# macOS 13 Mojave on XPS 13 9343

## Table of Contents

> 1. Before you get started,
> 2. What to bring
> 3. Installation disc production
> 4. Install
> 5. After installation
> 6. Note site
> 7. Update Log

***
## 1. Before you get started,
* Thank you to everyone who helped you write this article.
* The author hates English, but will mix english as much as possible to make it possible for people from other countries to do references.
* If you're a talented person, we'll replace most of the English words with Korean.
* If you have any questions, please contact us by e-mail or leave the issue and we will respond.
* PR is always welcome
* Cautions
  * This guide does not address apple's recommendations and is not the author's responsibility for any occurrence spurred by following this guide.
  * Following this guide does not guarantee that it will be installed.
  * You may fail during installation.
  * Even if the installation is successful, there is no guarantee that minor patches will continue normally.
  * The author reveals that the set values, such as the installation on a laptop with macOS 10.12 Sierra, have been successful in a different state than the factory was shipped.
  * The author's recommendation is not to blind this guide and to purchase a real mac.
  * Do not use this guide for commercial purposes. It's a document that's not worth it, and it's widespread.
  * Do not apply this guide to other laptops. A high probability of failing.
  * The guide is short, but the stress of installation is considerable. It is recommended that you try it after taking a blood pressure medication.

* The motivation to write a guide
  * In 17 years, while looking for material to install 10.12 Sierra on my laptop, I saw a guide in Korean and it was successful to install it, so I hope others will help raise Hackintosh.
  * For backup supped in case of an emergency
  * Getting tired of the task
* On my laptop, which has been installed, the following features do not work
  * 1. Touchpad 2 points - all actions except zoom in/out and scroll
  * 2. 4 touchpad - all movements
  * 3. SD Card Reader
  * 4. Watch Netflix
  * 5. No sound is transmitted when external monitor is output
***
## 2. What to bring
1. __DELL XPS 13 9343__
2. __USB memory__
3. Computer with __macOS_
5. ___uniBeast__ (https://www.tonymacx86.com/resources/unibeast-9-1-0-mojave.418/) (subscription required)__
6. __[Clover Bootloader](https://sourceforge.net/projects/cloverefiboot/)__

7. Clover Configurator
6. __Empty schedule and full of passion__

* The author has prepared this way.

1. The only XPS to have 13 9343 

* i7 5500U
     * LPDDR3 8GB (4GB+4GB)
     * FHD non-Touch
     * 256GB M.2 AHCI SSD
     * DW1560
     * macOS 10.12.6 Sierra

2. ADATA S102 pro 16GB USB
  3. Classes are available 2 hours after the start time of installation
***
## 3. Creating an installation disk
1. Clone this Repo using Git. 
2. Disk Utility formats USB in Mac OS extended format.
3. Download macOS mojave from the App Store
4. Run UniBeast, press the next button hard, select UEFI and Legacy, select UEFI and wait for copy to complete.
5. When Copy is complete, delete the EFI folder inside the USB's EFI partition and paste the EFI folder in clone repo.
6. Run Clover Bootloader, press the Continue button twice, press customize, check the install clover on boot-only installation_ and __ESP __UEFI, then press the install button.

***
## 4. Install
1. Keep the power of the laptop while the USB is counted
2. Press F2 to enter bios setup.
3. General -> Enter the Boot Sequence menu and set usb to the top of the boot ranking. (If you don't specify a separate name when you format the USB memory, you can add it by clicking the Add Boot Option button in boot list Option.)
4. General -> Enable Legacy Option ROMs option from advanced Boot Options menu
5. Security -> Disable the Intel Platform Trust Technology menu from the PTT Security menu
6. Secure Boot -> Disabled features from secure Boot Enable menu
7. Save and exit.
8. When you boot into Clover after rebooting, you enter the option menu on the second line.
9. Add -v to boot args item so that you can search for errors during installation and leave the option menu
10. Select install macOS from "USB name" on the first line.
11. Once you enter the installation screen, you can choose to disk utility and format the SSD you want to install in APFS format. (If you don't format the entire SSD, you'll get an error.)
12. If you follow the instructions on the screen to proceed with the installation, the reboot will be n times. 
13. When the installation is complete, the Clover screen will have a disc called Boot macOS from "USB name". Boot with that item
14. There are various settings, without wi-fi connection, no Apple account connection.
15. The installation is complete.

*** 
## 5. After installation
1. Open the terminal and enter the following code:
```
sudo rm -rf/System/Library/Extensions/AppleACPIPS2Nub.kext
sudo rm -rf/System/Library/Extensions/ApplePS2Controller.kext
sudo rm -rf/System/Library/Extensions/ApplePS2SmartPad.kext

sudo rm -rf/Library/Extensions/AppleACPIPS2Nub.kext
sudo rm -rf/Library/Extensions/ApplePS2Controller.kext
sudo rm -rf/Library/Extensions/ApplePS2SmartPad.kext
```
1. Mount both the EFI partition in the SSD and the EFI partition in the USB
1. Copy the voodoops2controller.text file in the efi/clover/kexts/others folder of the EFI partition on USB to /Library/Extensions folder
2. Remove the EFI folder inside the EFI partition on the SSD and copy the EFI folder on the EFI partition on the USB.
3. Open the config.plist file in the EFI folder with clover configulator and enter the smbios tab
4. Press the shake button next to the Week of Manufacturer and Unit Number items.
5. Copy the serial number generated in the Serial menu at the bottom.
6. Attach the serial to the Board Serial Number entry and enter five additional digits of any HEX code.
7. Save it.
8. Open the terminal and enter the following code:
```
sudo touch/system/library/extensions &amp; sudo kextcache -u /
```
9. Turn off the power, unplug the USB and reboot
10. If the boot is successful, connect to the Internet and register your Apple account
11. If Facetime and message don't work, see http://jsnhacknote.blogspot.com/2017/01/1010-imessage.html

## 6. Note site, people 
* [XPS13 9343 macOS Mojave] (https://yyfnsa.com/xps13-9343-macos.html)
* [Guide] Dell XPS 13 9343 Sierra] (https://www.tonymacx86.com/threads/guide-dell-xps-13-9343-sierra.206399/)
* [Catch the iMessage at Hackintosh 10.10+ (http://jsnhacknote.blogspot.com/2017/01/1010-imessage.html)
* [OS-X-Voodoo-PS2-Controller] (https://github.com/RehabMan/OS-X-Voodoo-PS2-Controller)
* [How to use markdown] (https://gist.github.com/ihoneymon/652be052a0727ad59601)
##### Special Thanks to 
* [KT_score] (https://www.clien.net/service/popup/userInfo/posts/r3markable?) - The enemies of the untitled disk will be paid back.
* [toothpaste] (https://www.clien.net/service/popup/userInfo/basic/dladsds123) - Bob Friend
