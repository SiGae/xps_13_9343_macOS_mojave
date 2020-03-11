macOS 13 Mojave on XPS 13 9343
Contents

        Before you start
        materials
        Installation disc production
        install
        After installation
        Reference site
        Update Log 

1. Before you start

    Thanks to everyone who helped to write this document.

    Authors hate English, but we will use English as much as possible to make it easier for people from other countries to refer to.

    If you can write an English guide, I will replace most English words with Korean notation.

    If you have any questions, please contact us by e-mail or leave as an issue and we will respond.

    PR is always welcome

    Precautions
        We note that this guide does not cover Apple's recommendations and the author is not responsible for what happens if you follow this guide.
        Following this guide does not guarantee installation.
        It may fail during installation.
        Even if the installation is successful, there is no guarantee that minor patches will proceed normally.
        The author says that the set values ​​were successful in a different state from the factory, such as installing on a laptop with macOS 10.12 Sierra.
        The author's recommendation is to purchase Real Mac without blinding this guide.
        Do not use this guide for commercial purposes. It's not worth it, and if it's widespread it gets embarrassed.
        Do not apply this guide to other notebooks. It fails with a high probability.
        The guide is short, but the stress from installation is significant. It is recommended to try after taking blood pressure medication. 

    Guide writing motivation
        As I was looking for materials to install 10.12 Sierra on my laptop in 17 years, I read the guide in Korean and succeeded in installing it, so I hope that it will help others to upload the hackintoshi.
        For backup in case of emergency
        Tired of assignment 

    The following features do not work on my laptop after installation.
            Touchpad 2 points-all actions except zoom in / out and scrolling 
            Touchpad 4 points-all actions 
            SD card reader 
            Watch Netflix 
            No sound is transmitted when the external monitor is output 

2. Preparation

    DELL XPS 13 9343

    USB memory

    computer with macOS

    UniBeast (subscription required)

    Clover Bootloader

    Clover Configurator

    Empty schedule and overflowing passion 

    The author prepared like this.

        The only XPS 13 9343 you have
            i7 5500U
            LPDDR3 8GB (4GB + 4GB)
            FHD non-Touch
            256GB M.2 AHCI SSD
            DW1560
            macOS 10.12.6 Sierra 

        ADATA S102 pro 16GB USB

        2 hours after the start time of installation 

3. Installation disc production

    Clone this repo using Git.
    Format USB in Mac Utility Extended (journaling) format in Disk Utility.
    Download macOS mojave from the App Store
    Run UniBeast, press the next button hard, select UEFI on the screen to select UEFI and Legacy, and wait for Copy to complete.
    When copying is complete, delete the EFI folder inside the USB EFI partition and paste the EFI folder in the cloned repo.
    Run Clover Bootloader, tap the Continue button twice, click customize, check UEFI boot-only installation and Clover installation on ESP, and then click the Install button. 

4. Installation

    Power on the laptop with the USB plugged in
    Press F2 to enter Bios Setup.
    Enter the General-> Boot Sequence menu and set USB as the top boot priority. (If you did not specify a name when formatting the USB memory, add it by clicking the Add Boot Option button in the Boot list Option.)
    Enable the Legacy Option ROMs option in the General-> Advanced Boot Options menu.
    Disable Intel Platform Trust Technology menu in Security-> PTT Security menu
    Disable the function in Secure Boot-> Secure Boot Enable menu.
    Save and exit.
    After rebooting, when booting with Clover, enter the option menu on the second line.
    Add -v to Boot args item to search for errors during installation and exit from option menu
    Select install macOS from "USB name" in the first line.
    When entering the installation screen, select the disk utility and format the SSD to be installed in APFS format. (If you do not format the entire SSD, an error occurs.)
    If you proceed with the installation according to the instructions on the screen, the reboot will proceed n times.
    When installation is complete, a disk named Boot macOS from "USB name" is created on the Clover screen. Boot to that item
    There are various settings, but without Wi-Fi connection or Apple account connection.
    Installation is complete. 

5. After installation

    After opening the terminal, enter the following code.

    sudo rm -rf /System/Library/Extensions/AppleACPIPS2Nub.kext sudo rm -rf /System/Library/Extensions/ApplePS2Controller.kext sudo rm -rf /System/Library/Extensions/ApplePS2SmartTouchPad.kext sudo rm -rf /Library/Extensions/AppleACPIPS2Nub.kext sudo rm -rf /Library/Extensions/ApplePS2Controller.kext sudo rm -rf /Library/Extensions/ApplePS2SmartTouchPad.kext 

    Mount both EFI partitions on SSD and EFI partitions on USB
    Copy the voodoops2controller.text file in the efi / clover / kexts / others folder of the EFI partition on USB to the / Library / Extensions folder
    Remove the EFI folder inside the EFI partition on the SSD and copy the EFI folder from the EFI partition on the USB.
    Open the config.plist file in the EFI folder with the clover configulator and enter the smbios tab.
    Click the shake button next to Week of Manufacturer and Unit Number.
    Copy the serial number created in the Serial menu at the bottom.
    After attaching the relevant serial to the Board Serial Number item, enter 5 additional random HEX codes.
    Save it.
    Open a terminal and enter the following code.

      sudo touch /System/Library/Extensions && sudo kextcache -u / 

    Turn off the power, unplug the USB and reboot
    If booting is successful, connect the Internet and register your Apple account.
    If facetime and message don't work, please refer to here 

6. Reference sites, people

    XPS13 9343 macOS Mojave 引导
    [Guide] Dell XPS 13 9343 Sierra
    Hacking 10.10+ iMessages
    OS-X-Voodoo-PS2-Controller
    How to use markdown 

Special Thanks to

    KT_score -The untitled disc's enemies will be paid back someday.
    Toothpaste -rice friend 

7. Update Log

    19/03/17 1st completion
    19/03/17 typo correction
    19/03/26 10.14.4 Installation correspondence
    19/04/14 DSDT added 
