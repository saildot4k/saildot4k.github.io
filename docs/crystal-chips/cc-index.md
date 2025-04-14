# Overview

## Crystal Chip Documentation Progress
???+ note "Progress as of 3/3/2025"

    - [ ] Crystal Chip documentation
        * [x] Install Diagrams
        * [ ] Video Tutorials
            * [x] Firmware & BootManager Installation
            * [x] Installing and Running Apps
            * [x] R34 v3 Changes (out of date), MMCE added
            * [ ] Configuration options overview
            * [ ] Using App MegaPacks
            * [ ] Using PS2Client/Link to help debug
        * [ ] Written Tutorials
        * [x] Files
            * [x] Firmware/Bootmanager
            * [x] BM Megapack by R3Z3N
                * [x] CD/USB Megapack
                * [x] SD2PSX/PSXMemcard Gen 2 Megapack
                * [x] MemcardPro 2 Megapack
            * [x] Default APPINFO.PBT
        * [ ] PBT Scripting overview (wiki is outdated)
        * [x] Archived Websites
            * [x] Crystal Chip website
            * [x] Crystal Chip wiki

## Option to repurchase
???+ note "Option to Repurchase"

    ![Crystal Chip QR Code](assets/Crystal_Chip_QR_Code.png){ width="290" align=left }

    If you happened to come to this page due to this sticker then I thank you very much! 

    Please email me [here](mailto:info@ps2modchiptutorials.com) so that we may discuss futher as I would love to keep these chips in the hands of enthusiasts.


## Crystal Chip versions
    
![Crystal Chip Models](cc-site-backup/img/cc_hw_history.gif)


## Dashboard "BootManager" may be installed to and ran from
| Crystal Chip | Memcard 1                       | Memcard 2                       | :material-usb: USB              | :material-harddisk: HDD          | :material-memory: On-Chip Flash                 | :material-lan-connect: PC Host |
| :----------: | :-----------------------------: | :-----------------------------: | :-----------------------------: | :-----------------------------:  | :---------------------------------------------: | :----------------------------: |
| 2.0 Pro SLE  | :material-close-circle-outline: | :material-close-circle-outline: | :material-close-circle-outline: | :material-close-circle-outline:  | :material-check-circle: 2MB Dataflash           | :material-check-circle:        |
| 2.0 Pro      | :material-close-circle-outline: | :material-close-circle-outline: | :material-close-circle-outline: | :material-close-circle-outline:  | :material-check-circle: 1MB Dataflash           | :material-check-circle:        |
| 1.2 Lite     | :material-check-circle:         | :material-check-circle:         | In Progress                     | :material-check-circle:          | :material-close-circle-outline: 128KB Dataflash | :material-check-circle:        |
| 1.1 Lite     | :material-check-circle:         | :material-check-circle:         | In Progress                     | :material-check-circle:          | :material-close-circle-outline: 4KB EEPROM      | :material-check-circle:        |
| 1.0 Lite     | :material-check-circle:         | :material-check-circle:         | In Progress                     | :material-check-circle:          | :material-close-circle-outline: 4KB EEPROM      | :material-check-circle:        |

???+ note "BootManager"
    Bootmanager therefore must be installed to either Dataflash, MemoryCard or HDD. This is not your usual Matrix Infinity.
    It is much much better


## BootManager Run/Install/Remove device support
| :material-disc: CD/DVD  | :material-usb: USB Fat16/32 | Memory Card             | :material-sd: MMCE device     | :material-harddisk: HDD | :material-lan-connect: PC Host   |
| :---------------------: | :--------------------------: | :---------------------: | :---------------------------: | :---------------------: | :------------------------------: |
| :material-check-circle: | :material-check-circle:      | :material-check-circle: | :material-alert-circle-check: | :material-check-circle: | :material-check-circle:          |

???+ note "PC Host"
    
    Use [PS2 Client](https://github.com/ps2dev/ps2client) and from where you installed/extracted run:
    ```ps2client -h hostname/ip listen```
    Homebrew must be in same folder thatn PS2 Client is running from. 
    IE: ~/PS2Client/BM/APPS/APPFOLDER/
    You still need an associated APPINFO.PBT

???+ note "MMCE devices"

    It is best to install apps to MMCE devices using your PC. It seems there are bugs such as moving files
    between mc0/1 and mmmce0/1. I hope for updated IRXs or it just may be a limitation to the SIO2 Bus.

???+ note "USB Exfat"

    In Progress...Using BDM Assault for Exfat allows Install/Remove but oddly not Run. BDM Assault hotswap does work. I hope to fix.


## CC 1.1 to 2.0 Conversion
CC 1.1 and later can be upgraded with 4MB dataflash: AT45DB321D-S or AT45DB321D-MW. I have several dozen in stock. [Email me](info@ps2modchiptutorials.com) if you would like to upgrade. There are no changes needed in software/firmware/scripting. Solder on and go! Reference the attached picture to see where pin 1 (the black dimple dot on the EEPROM/DATAFLASH) is and how the flash is rotated 90 degrees clockwise from the CC1.1 to the CC1.2 and later. In this case it was already a CC2.0.

![CC11to2conversion](assets/CC11to2_conversion.jpg){ width="400"}









