# Overview

In Progress as of 2/14/2025

## Option to repurchase

![Crystal Chip QR Code](https://ps2modchiptutorials.com/crystal-chips/Crystal_Chip_QR_Code.png){ width="290" align=left }

If you happened to come to this page due 
to this sticker then I thank you very much! 
Please email me [here](mailto:info@ps2modchiptutorials.com) so that 
we may discuss futher as I would love to keep these
chips in the hands of enthusiasts.
<br>
<br>
<br>


## Crystal Chip versions { align=left }
    
![Crystal Chip Models](https://ps2modchiptutorials.com/crystal-chips/cc-site-backup/img/cc_hw_history.gif){ align=left }
???+ note "Feature Differences"
    
    All versions retain same functionality EXCEPT v2.0 PRO and v2.0 PRO SLE can boot the dashboard "BootManager"
    from it's internal dataflash storage. Otherwise BootManager will need to be installed to Memcard1,2 or HDD. 
    Full install of BootManager takes 875KB. If there is more storage avaliable, more apps can be installed to 
    Crystal Chip Flash. If an app expects other files in the root directory of the application folder, it will 
    NOT be able to use those files. For example WLE will not see IPCONFIG.DAT nor LAUNCHELF.CNF

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

## Dashboard "BootManager" may be installed to and ran from:
| Crystal Chip | Memcard 1        | Memcard 2        | USB              | HDD              | On-Chip Flash                    | PC Host         |
| :----------: | :--------------: | :--------------: | :--------------: | :--------------: | :------------------------------: | :-------------: |
| 1.0 Lite     | :material-check: | :material-check: | :material-close: | :material-check  | :material-close: 4KB EEPROM      | :material-check |
| 1.1 Lite     | :material-check: | :material-check: | :material-close: | :material-check  | :material-close: 4KB EEPROM      | :material-check |
| 1.2 Lite     | :material-check: | :material-check: | :material-close: | :material-check  | :material-close: 128KB Dataflash | :material-check |
| 2.0 Pro      | :material-close: | :material-close: | :material-close: | :material-close: | :material-check: 1MB             | :material-check |
| 2.0 Pro SLE  | :material-close: | :material-close: | :material-close: | :material-close: | :material-check: 2MB             | :material-check |

???+ note "BootManager"
    Bootmanager therefore must be installed to either Dataflash, MemoryCard or HDD. This is not your usual Matrix Infinity.
    It is much much better

    ???+ note "Dataflash Upgrade Parts"
        
        v1.2 and later can be upgraded with 4MB dataflash: AT45DB321D-S or AT45DB321D-MW. I have several dozen in stock.
        v1.2 then would need to flash the 2.0 firmware.  Eventually I shall script to ask user if they have installed the larger dataflash.
        Go to BM/FWS/LATEST delete all but "FWARE20.CCI". Rename to "FWARE12DEV0.CCI". Then upgrade firmware choosing option 1.

## Devices supported to run homebrew from
| CD/DVD           | USB Exfat/Fat    | Memory Card      | MMCE device      | HDD              | PC Host          |
| :--------------: | :--------------: | :--------------: | :--------------: | :--------------: | :--------------: |
| :material-check: | :material-check: | :material-check: | :material-check: | :material-check: | :material-check: |

???+ note "PC Host"
    
    Use [PS2 Client](https://github.com/ps2dev/ps2client) and from where you installed/extracted run:
    ```ps2client -h hostname/ip listen```
    Homebrew must be in same folder thatn PS2 Client is running from. 
    IE: ~/PS2Client/BM/APPS/APPFOLDER/
    You still need an associated APPINFO.PBT








