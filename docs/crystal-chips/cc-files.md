## Crystal Chip FW 34 V5 by R3Z3N 6/27/2025

[:material-cloud-download: Crystal Chip FW R34 v5 with updated Dashboard Scripts by R3Z3N](https://github.com/saildot4k/Crystal-Chip-R34-v5/archive/refs/heads/v5.zip)

???+ note "R34 V5 Changes"
    Fixes/Changes:

    - SAS (Save Application Support) updated (and probably finalized). There is a script in BM/SCRIPTS/BMRTFLDR.PBT (BootManager Root Folder) \
        where root folders must be defined, similiar to how FMCB, PS2BBL and OSDMenu also need to define where apps are. 
        Edit as neeeded to add new folders, delete unneeded folders as necessary. To update, place file on root of
        any device that you have device drivers installed for. Simply run BootManager, Application Browser and RUN/INSTALL/REMOVE
        for said device and BootManager will copy the file where it needs to go and SHOULD remove the script from root of said device.
        If not please manually delete with another app or PC. Simply grab a file from ps2wiki.github.io and drop to root of memory card
        (once APPINFO.PBT is included with said app)

    - Powershell script to create APPINFO.PBT if title.cfg exists. APPINFO is now much more friendly for user, and allows device specific compatibily options

    - Added option to show directories when browsing for APPS, Devices and Themes

    - Added options to confirm Remove and Install apps/devices and themes which also recalls directory and appname when browsing so you do
        not loose track of which app you were installing or removing.

    - Device Manager now shows which device drivers are installed. Inform users when device drivers are missing such as when FTP is installed but NET 
        is missing. SCPH-75K and later will inform user if HDD driver is unneeded

    - Configuration Menus hide or inform users when device drivers are missing. For example NET/FTP/HOST and HDD. If NET is missing, FTP and HOST
        inform user NET is missing as that is the backing driver. 

    - Added ability to hide apps for RUN/INSTALL/REMOVE. Reference BM/APPS/OSDSYS/APPINFO.PBT or BM/APPS/BM/APPINFO.PBT

    - BootManager updates mc:/SYS-CONF/IPCONFIG.DAT if it exists so that your suite of apps that call your network config stay "synced"

    - BootManager Installer updated. Allows choosing device drivers before installing and checks if drivers are on source device.
        Informs user of Min/Max install just in case CC2.0/SLE users want to save space. Should fit on all 2.0 Models with full install.
        Warns user if critical or non critical files are not installed. Non critical files continues installing (such as missing icons)
        CC2.0 Installs no longer install other CC1.0 FW to flash to save more space.

    - 2 Tutorials under Configuration Menu so that users cannot forget how to update defined root folders, as well as how to use hotkeys.

    - Added French Language thanks to Wanderer!

    - Added Many more themes, 31 in total now. Still need to edit colors for font/title/menu/background. Please inform me if PAL, VGA or 480p
        alignment needs fixing and what your values are.

    - Fixed bug that "Medias" scripts would never be called

    - Memory Card Manager hides devices that may not be inserted

    - Easter Egg in menus.....

    - Besides themes and apps, this is probably the last update unless I figure out how to show which hotkeys are assigned to what application
        or god forbid any bugs I may have left. I may consolidate scripts if possible later.

    - OLD APPINFO.PBT is still supported under BM/APPS/ however all the SAS compliant scripts are updated. I recommend using those going forward.

    To Do:

    - Help Ripto create title.cfg for his AIO  (ALL IN ONE) app repository

    - Bundle the new apps for the MegaPack as they are added to ps2wiki.github.io


## Crystal Chip FW 34 V4 by R3Z3N 5/17/2025

???- note "R34 V4 Changes"
    Fixes/Changes:

    - SAS (Save Application Support) added as best as possible. Apps can be installed to:
        mc?:/APPFOLDER/ but this needs an matching mc?:/BM/APPS/APPFOLDER/APPINFO/PBT
        as there is a bug where we can not search for mc?:/*/APPINFO.PBT sadly. So this is a workaround.
        This is nice as apps will show in the OSDSYS now.

        Also:

        nonmc?:/APPFOLDER 

        nonmc?:/APPS/APPFOLDER

        fully work, no odd workarounds.

        Old APPINFO.PBT still supported.

    - Installing from source to source shows a warning, same for CDDVD (cant install/remove from that!) 
        nor run from PC HOST (not supported)

    - Power off added to BootManager. There is no proper restart.elf that I know of yet...

    - Fixed System Info not showing console model as needed MATCHES not EQU (and reverse the argument)

    - Fixed and added old themes which improperly used LOADING instead of the proper LOADIMG

    - v14 and later PS2s no longer show HDD options and do not auto load HDD drivers. 
        However the setting is still saved so swapping your memcard between PS2s if you
        have multiple chips still functions as you set it.

    - v12 and later no longer show MegaMemory Patcher option as Sony blocked it's use electrically for PSTwo Slims.

    - V16-v18 is now properly identified in Console Information

    - Added PowerShell scripts to create APPINFO.PBT recursively and non recursively.
        needs title.cfg included in app folder to create. However if apps need specifically
        boot command IE `SHUTDOWN MM` or SET `"BM.AUTOLOAD_FSD_EN" "0"` may need to be added to the
        run section. For example wLE ISR needs SHUTDOWN MM to run from USB.
        Also need to add REDIRFILE for the apps that support it.

    To Do:

    - Help Ripto create title.cfg for his AIO  (ALL IN ONE) app repository

    - Still work on 8MB firmware

    - Bundle the new apps for the MegaPack

## Crystal Chip FW R34 V3 4/29/2025

???- note "R34 V3 Changes"

    Fixes/Changes:

    - CC1.X firmware options to run BM from MemCard1,2, HDD and USB. HDD/USB boot needs HDD drivers on mc0:/BM/SHARED/
    HDD and USB are commented out, go ahead and uncomment out in BM/FWS/LATEST/FWINFO.PBT to experiment

    - MMCE device support for example SD2PSX, PsxMemCardGen2, MemCardPro2.
    [SD2PSXTD](https://sd2psxtd.github.io/)
    [MCP2](https://8bitmods.com/memcard-pro2-for-ps2-and-ps1-smoke-black/)

    -  ~~Used El Isras USB drivers for exfat support:~~ [BDM Assault](https://github.com/israpps/BDMAssault)
    REASON: Unable to get EXFAT drivers to run apps from USB. Needs further testing.

    - Security Settings added: when pin is set, advanced settings are unaccessible. 

    - Updated bminit.pbat to load IRX drivers from where BM is running from,
    otherwise with DEV1/2 would not see/run apps from mc0/1/USB/HDD.

    - Updated HDDMOUNT.IRX and BM/SCRIPTS/HDDLOAD.PBT to load __common HDD partition
    instead of +Crystal. This is to keep things consistent with the homebrew community

    - Changed scripts to allow apps to be installed when booted from recovery cd.

    - Changed scripts to only show options for chip installed! IE no more seeing DFFS
    options on CC 1.XS

    - Changed scripts so that FW choices are only applicable to the chip installed.
    IE CC1.0-1.2 can choose BM run point, CC2.0 DFFS only.

    - BootManager app install no longer installs FW files to the dffs: partition to save 
    51KB for CC2.0 owners.

    - Show Info gives a little more clarity IE where is BM executed from, what console region codes stand for etc.

    - Cotton Candy theme added, each version of the Crystal Chip is represented!

    - Added Italian and Spanish language translations.


## BootManager MegaPack Downloads

<div class="grid cards" markdown>

-   __USB (Fat16/32)__

    ---

    Unzip and merge with the Firmware Download or move the the root of your USB stick

    [:material-cloud-download: USB](https://github.com/saildot4k/BootManager-MegaPack/raw/refs/heads/main/BM_MEGAPACK.zip)


-   __SD2PSX/PSXMemCard Gen2__

    ---

    Unzip and merge contents to root of your SD2PSX/PSXMemcard Gen2 MMCE device (THIS WILL WIPE YOUR BOOT CARD!) MUST BE ON [FW 1.2.0 or later!](https://sd2psxtd.github.io/download)

    [:material-cloud-download: SD2PSX](https://github.com/saildot4k/BootManager-MegaPack/raw/refs/heads/main/COMBINED_MMCE.zip)

-   __MemCardPro 2__

    ---

    Unzip and merge contents to root of your MemCardPro 2 MMCE device. Set Crystal Chip Channel 1 as your boot card. MUST BE ON [FW 1.4.0 or later!](https://distribution.appcake.co.uk/install/8bitmods/apps/memcard-pro2/public)

    [:material-cloud-download: MCP2](https://github.com/saildot4k/BootManager-MegaPack/raw/refs/heads/main/COMBINED_MMCE.zip)

</div>

Apps Included and updated as of 3/7/2025:

| Application                   | USB (Fat16/32)                  | MMCE Device VMC                  |
| :----------------------------| :-----------------------------: | :-------------------------------: |
| Crystal Chips BootManager    | :material-close-circle-outline: | :material-check-circle:           |
| BM Themes                    | :material-check-circle:         | :material-check-circle:           |
| Apollo Save Tool             | :material-check-circle:         | :material-check-circle:           |
| Cheat Device MMCE            | :material-check-circle:         | :material-check-circle:           |
| GSM                          | :material-check-circle:         | :material-check-circle:           |
| NHDDL                        | :material-check-circle:         | :material-check-circle:           |
| OPL 1.2.0 B2049 GID          | :material-check-circle:         | :material-check-circle:           |
| OPL 1.2.0 B2207              | :material-check-circle:         | :material-check-circle:           |
| OPL MMCE Beta 2              | :material-check-circle:         | :material-check-circle:           |
| OPL MMCE Beta 3              | :material-check-circle:         | :material-check-circle:           |
| PSBBN Launcher               | :material-check-circle:         | :material-check-circle:           |
| Simple Media System          | :material-check-circle:         | :material-check-circle:           |
| unoffical OPL                | :material-check-circle:         | :material-check-circle:           |
| unofficial OPL Betrayal      | :material-check-circle:         | :material-check-circle:           |
| wLE ISR HDD                  | :material-check-circle:         | :material-check-circle:           |
| wLE ISR XF MM                | :material-check-circle:         | :material-check-circle:           |
| wLE ISR XF MX                | :material-check-circle:         | :material-check-circle:           |
| wLE KHN                      | :material-check-circle:         | :material-check-circle:           |
| wLE XFW                      | :material-check-circle:         | :material-check-circle:           |
| BOOT Folder for other chips  | :material-check-circle:         | :material-check-circle:           |
| PS2 Link                     | :material-check-circle:         | :material-check-circle:           |
| PS2 Link Highloading         | :material-check-circle:         | :material-check-circle:           |
| PS2 BIOS Drain               | :material-check-circle:         | :material-check-circle:           |
| PS2 HDD Checker              | :material-check-circle:         | :material-check-circle:           |
| Memory Card Annihilator      | :material-check-circle:         | :material-check-circle:           |
| Mechacon Crash Tester        | :material-check-circle:         | :material-check-circle:           |
| MX4SIO Tester                | :material-check-circle:         | :material-check-circle:           |
| OG Memory Card Tester        | :material-check-circle:         | :material-check-circle:           |
| Pad Tester                   | :material-check-circle:         | :material-check-circle:           |
| PS2 HDD Tester               | :material-check-circle:         | :material-check-circle:           |
| PS2 RDRAM Test               | :material-check-circle:         | :material-check-circle:           |
| PS2 Temps                    | :material-check-circle:         | :material-check-circle:           |
| PicoDrvie                    | :material-check-circle:         | :material-check-circle:           |
| Xbox 2 PS2                   | :material-check-circle:         | :material-check-circle:           |
| Xbox 2 PS2 Memory Card       | :material-check-circle:         | :material-check-circle:           |
| 3D Pinball Player            | :material-check-circle:         | :material-check-circle:           |
| HERMES                       | :material-check-circle:         | :material-check-circle:           |
| OSDMenu                      | :material-check-circle:         | :material-check-circle:           |
| PowerOff                     | :material-check-circle:         | :material-check-circle:           |
| DKWDRV                       | :material-check-circle:         | :material-check-circle:           |
| POPSLOADER                   | :material-check-circle:         | :material-check-circle:           |
| Restart                      | :material-check-circle:         | :material-check-circle:           |
| IGR to Boot Card             | :material-check-circle:         | :material-check-circle:           |
| SYS-CONF                     | :material-check-circle:         | :material-check-circle:           |
| NEUTRINO                     | :material-check-circle: USB Root| :material-check-circle: MMCE root |
| RETROLauncher                | :material-check-circle: USB Root| :material-check-circle:           |
| OSD-XMB                      | :material-check-circle: USB Root| :material-check-circle:           |
| XEB+ NEEDS INSTALL           | :material-close-circle-outline: USB Root | :material-close-circle-outline:   |





??? note "Missing App Notes"

    - XEB+ Xmas Edition must be acquired from official sources due to license
        - Can only be ran from USB!
    - RetroLauncher is unable to be burned to CD so it is not included on the CD installer.
        - Can only be ran from USB!
    - OSDXMB can only be ran from USB!

## APPINFO.PBT SAS (SAVE APPLICATION SUPPORT) Example

???- note "APPINFO.PBT SAS Example"
    ```pbat linenums="1" hl_lines="10-17 19 20 24-28"
    # SAS (Save Application Support) compliant BM Script
    # Due to wildcard bug on memory card and mmce, bootdevice:/BM/SCRIPTS/BMRTFLDR must exist to work. Update as needed.

    # Change this information to describe the application and where it should be ran from for memcard (SAS) or other devices (SAS_NON_MC)
    # SAS is the App folder name. SAS_NON_MC defines if app is in root of non-memcard device (non_mc:/$SAS$) or APP folder (non_mc:/APPS/$SAS$)
    # This is so that you do not have to edit any info below line 28.
    #
    # Some devices are case sensitive! Make sure your case matches!
    #
    # Source: website here
    SET "TITLE" "Appname"
    SET "VERSION" "version"
    SET "AUTHOR" "authors here"
    SET "DESC" "Short blurb"
    SET "MEDIAS" ""
    SET "ELF" "PS2Temps.elf"
    SET "SAS" "DST_PS2TEMPS"
    # Comment out 1 of the 2 lines below. If app is in non-mc:/$SAS$ comment out the second, if in non-mc:/APPS/$SAS$ comment out the first
    # SET "SAS_NON_MC" "$SAS$"
    SET "SAS_NON_MC" "APPS/$SAS$"
    #
    # If an app does not boot, then one of these compatibility options may need to be set to 0, 1, 2 or 3
    # 0= No compatibility options, 1= SHUTDOWN "MM", 2= SET "BM.AUTOLOAD_FSD_EN" "0", 3= CC SLEEP
    SET "COMP_MODE_MC" "0"
    SET "COMP_MODE_MMCE" "0"
    SET "COMP_MODE_USB" "0"
    SET "COMP_MODE_HDD_APA" "0"
    SET "COMP_MODE_DFFS" "0"
    #

    # Do not change these 2 lines!
    GOTO "$ARG1$"
    RETURN -1

    # Used for Autoboot Labels
    :LABEL_NAME
        ADDWIDGET "LABEL" "$ARG2$$TITLE$ v$VERSION$"
        EXIT 0

    :QUERY
        ADDWIDGET "CALL" "$TITLE$" "$BM.TXT_VERSION$: $VERSION$ $BM.TXT_AUTHOR$: $AUTHOR$ $BM.TXT_DESC$: $DESC$" $ARG2$ "$ARG0$" "$ARG3$" "$ARG4$" "$ARG5$" "$TITLE$" "$PWD$" "$SAS$" "$SAS_NON_MC$"
        EXIT 0

    :INSTALL
            IF MATCHES "mc?" "$ARG2$"
                GOTO "INSTALL_TO_MC"
            ELSEIF NOT MATCHES "mc?" "$ARG2$"
                GOTO "INSTALL_TO_NONMC"
            ENDIF

    :INSTALL_TO_MC
        IF FAIL COPY "$PWD$" "$ARG2$:/$SAS$"
            ECHO "Failed installing $TITLE$"
            MESSAGE "Failed installing $TITLE$"
            RRM "$ARG2$:/$SAS$"
            RETURN -1
        ENDIF
        EXIT 0

    :INSTALL_TO_NONMC
        IF FAIL COPY "$PWD$" "$ARG2$:/$SAS_NON_MC$"
            ECHO "Failed installing $TITLE$"
            MESSAGE "Failed installing $TITLE$"
            RRM "$ARG2$:/$SAS_NON_MC$"
            RETURN -1
        ENDIF
        EXIT 0

    :REMOVE
        IF FAIL RRM "$PWD$"
            IF FAIL RRM "$PWD$"
            IF FAIL RRM "$PWD$"
                MESSAGE "Failed removing $TITLE$"
                RETURN -1
            ENDIF
            ENDIF
        ENDIF
        EXIT 0

    :RUN
        IF MATCHES "mc?:/*" "$PWD$"
            GOTO "RUN_MC"
        ELSEIF MATCHES "mmce?:/*" "$PWD$"
            GOTO "RUN_MMCE"
        ELSEIF MATCHES "mass:/*" "$PWD$"
            GOTO "RUN_USB"
        ELSEIF MATCHES "pfs0:/*" "$PWD$"
            GOTO "RUN_HDD_APA"
        ELSEIF MATCHES "dffs:/*" "$PWD$"
            GOTO "RUN_DFFS"
        ENDIF

    :RUN_MC
        IF EQU "$COMP_MODE_MC$" "1"
            SHUTDOWN "MM"
        ELSEIF EQU "$COMP_MODE_MC$" "2"
            SET "BM.AUTOLOAD_FSD_EN" "0"
        ELSEIF EQU "$COMP_MODE_MC$" "3"
            SETBIOS "OFF"
            SHUTDOWN "ALL"
        ENDIF
        GOTO "RUN_COMP_MODE"

    :RUN_MMCE
        IF EQU "$COMP_MODE_MMCE$" "1"
            SHUTDOWN "MM"
        ELSEIF EQU "$COMP_MODE_MMCE$" "2"
            SET "BM.AUTOLOAD_FSD_EN" "0"
        ELSEIF EQU "$COMP_MODE_MMCE$" "3"
            SETBIOS "OFF"
            SHUTDOWN "ALL"
        ENDIF
        GOTO "RUN_COMP_MODE"

    :RUN_USB
        IF EQU "$COMP_MODE_USB$" "1"
            SHUTDOWN "MM"
        ELSEIF EQU "$COMP_MODE_USB$" "2"
            SET "BM.AUTOLOAD_FSD_EN" "0"
        ELSEIF EQU "$COMP_MODE_USB$" "3"
            SETBIOS "OFF"
            SHUTDOWN "ALL"
        ENDIF
        GOTO "RUN_COMP_MODE"

    :RUN_HDD_APA
        IF EQU "$COMP_MODE_HDD_APA$" "1"
            SHUTDOWN "MM"
        ELSEIF EQU "$COMP_MODE_HDD_APA$" "2"
            SET "BM.AUTOLOAD_FSD_EN" "0"
        ELSEIF EQU "$COMP_MODE_HDD_APA$" "3"
            SETBIOS "OFF"
            SHUTDOWN "ALL"
        ENDIF
        GOTO "RUN_COMP_MODE"

    :RUN_DFFS
        IF EQU "$COMP_MODE_DFFS$" "1"
            SHUTDOWN "MM"
        ELSEIF EQU "$COMP_MODE_DFFS$" "2"
            SET "BM.AUTOLOAD_FSD_EN" "0"
        ELSEIF EQU "$COMP_MODE_DFFS$" "3"
            SETBIOS "OFF"
            SHUTDOWN "ALL"
        ENDIF
        GOTO "RUN_COMP_MODE"

    :RUN_COMP_MODE
        LOADEXEC "PBAT" "$BM.SCRIPTS$/LOADEXEC.PBT" "$PWD$/$ELF$"
        EXIT 0

    ```


## APPINFO.PBT Example for BM/APPS/

???- note "APPINFO.PBT Example"
    ```pbat linenums="1"
    # Change this information to describe the application.
    SET "TITLE" "APP TITLE"
    SET "VERSION" "version here"
    SET "AUTHOR" "who made the app"
    SET "DESC" "Description of the app"
    SET "MEDIAS" ""
    #

    # Do not change these 2 lines!
    GOTO "$ARG1$"
    RETURN "-1"

    :LABEL_NAME
        ADDWIDGET "LABEL" "$ARG2$$TITLE$ v$VERSION$"
        EXIT "0"

    :QUERY
        ADDWIDGET "CALL" "$TITLE$" "$BM.TXT_VERSION$: $VERSION$ $BM.TXT_AUTHOR$: $AUTHOR$ $BM.TXT_DESC$: $DESC$" $ARG2$ "$ARG0$" "$ARG3$" "$ARG4$" "$ARG5$"
        EXIT "0"

    :INSTALL
        IF FAIL COPY "$PWD$" "$ARG2$:/BM/APPS/APP_TITLE"
            MESSAGE "Failed installing $TITLE$!"
            RRM "$ARG2$:/BM/APPS/APP_TITLE"
            RETURN -1
        ENDIF
        EXIT 0

    :REMOVE
        IF FAIL RRM "$PWD$"
            MESSAGE "Failed removing $TITLE$!"
            RETURN -1
        ENDIF
        EXIT 0

    :RUN
    #   SET "BM.AUTOLOAD_FSD_EN" "0"
    #   SHUTDOWN "MM"
        LOADEXEC "PBAT" "$BM.SCRIPTS$/LOADEXEC.PBT" "$PWD$/APPFILENAME.ELF"
        EXIT "0"
    ```

???+ note ""BM.AUTOLOAD_FSD_EN" "0""
    "BM.AUTOLOAD_FSD_EN" allows you to disable the automatic loading of 
    USB and Memory Card drivers when loading homebrew applications.
    May need to use if an app does not start

???+ note "SHUTDOWN ""MM""
    Shuts down the Memory Module
    May need to use if an app does not start


## APPINFO.PBT with 3 Boot Options Example

???- material-script-text "APPINFO.PBT Example w 3 Boot Options"
    ```pbat linenums="1"
    # Change this information to describe the application.
    SET "TITLE" "APP TITLE"
    SET "VERSION" "version here"
    SET "AUTHOR" "who made the app"
    SET "DESC" "Description of the app"
    SET "MEDIAS" ""
    #

    # Do not change these 2 lines!
    GOTO "$ARG1$"
    RETURN "-1"

    :LABEL_NAME
        ADDWIDGET "LABEL" "$ARG2$$TITLE$ v$VERSION$"
        EXIT "0"

    :QUERY
        ADDWIDGET "CALL" "$TITLE$" "$BM.TXT_VERSION$: $VERSION$ $BM.TXT_AUTHOR$: $AUTHOR$ $BM.TXT_DESC$: $DESC$" $ARG2$ "$ARG0$" "$ARG3$" "$ARG4$" "$ARG5$"
        EXIT "0"

    :INSTALL
        IF FAIL COPY "$PWD$" "$ARG2$:/BM/APPS/APP_TITLE"
            MESSAGE "Failed installing $TITLE$!"
            RRM "$ARG2$:/BM/APPS/APP_TITLE"
            RETURN -1
        ENDIF
        EXIT 0

    :REMOVE
        IF FAIL RRM "$PWD$"
            MESSAGE "Failed removing $TITLE$!"
            RETURN -1
        ENDIF
        EXIT 0

    :RUN
        ADDWIDGET "CALL" "$TITLE$ with SHUTDOWN" "Launch $TITLE$ with the SHUTDOWN Option" "$ARG0$" "RUN_WITH_OPTION" "1"
        ADDWIDGET "CALL" "$TITLE$ with autoload of drivers OFF" "Launch $TITLE$ with the AUTOLOAD_FSD_EN option" "$ARG0$" "RUN_WITH_OPTION" "2"
        ADDWIDGET "CALL" "$TITLE$ without any option" "Launch $TITLE$ without any option" "$ARG0$" "RUN_WITH_OPTION" "0"
        RETURN 0

    :RUN_WITH_OPTION
        ECHO "$ARG2$"
        SWITCH "$ARG2$"
            CASE 1
            #SHUTDOWN
                ECHO "SHUTDOWN"
                SHUTDOWN "MM"
                BREAK
            CASE 2
            #DRIVERS ON
                ECHO "CC DRIVERS ON"
                SET "BM.AUTOLOAD_FSD_EN" "0"
                BREAK
            CASE 0
            #NONE
                DEFAULT
                ECHO "NONE"
                BREAK
        ENDS

        LOADEXEC "PBAT" "$BM.SCRIPTS$/LOADEXEC.PBT" "$PWD$/WLE.ELF"
        EXIT 0
    ```


## To Do

- [x] SAS support (Apps from root with prefixes IE mc?:/APP_WLE-ISR-EXFAT-MMCE or mc?:/APP_OPL-MMCE-BETA2)
- [ ] CC1.X Boot method failover IE try next memcard
- [x] CC1.X BootManager boots from USB 
    Commented out in BM/FWS/LATEST/FWINFO.PBT for advanced users to use
- [x] BM can be ran from Hard Drive (HDD drivers MUST be installed tp mc0)
    * [x] Uploaded to github
    * [ ] Script for ease of use
    * [ ] Document for ease of use
- [x] HDD IRXs not installed for V14 and later PS2s
- [-] CC2.0 8MB Dataflash support in FW
    * [-] 1056 Page Support for AT45DB642D in testing
    * [-] 256 Page Support for AT45DB621E in testing