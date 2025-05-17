## Crystal Chip FW 34 V4 by R3Z3N 5/17/2025

[Crystal Chip FW R34 v3 with updated Dashboard Scripts by R3Z3N](https://github.com/saildot4k/Crystal-Chip-R34-v3/releases)

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

## Crystal Chip FW R34 v3 4/29/2025

???- note "R34 V3 Changes"
    (RUNNING CHANGES as of 4/29/2025. I update the date as I go...)
        
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

    - v14 and later PS2s no longer show HDD options and do not auto load HDD drivers. 
    However the setting is still saved so swapping your memcard between PS2s if you
    have multiple chips still functions as you set it.

    - v12 and later no longer show MegaMemory Patcher option as Sony blocked it's use electrically for PSTwo Slims.

    - V16-v18 is now properly identified in Console Information

## BootManager MegaPack Downloads

<div class="grid cards" markdown>

-   __USB (Fat16/32)__

    ---

    Unzip and merge with the Firmware Download or move the the root of your USB stick

    [:material-cloud-download: USB](https://github.com/saildot4k/BootManager-MegaPack/raw/refs/heads/main/BM_MegaPack_by_R3Z3N.zip)


-   __SD2PSX/PSXMemCard Gen2__

    ---

    Unzip and merge contents to root of your SD2PSX/PSXMemcard Gen2 MMCE device (THIS WILL WIPE YOUR BOOT CARD!) MUST BE ON [FW 1.1.1 or later!](https://sd2psxtd.github.io/download)

    [:material-cloud-download: SD2PSX](https://github.com/saildot4k/BootManager-MegaPack/raw/refs/heads/main/MMCE.zip)

-   __MemCardPro 2__

    ---

    Unzip and merge contents to root of your MemCardPro 2 MMCE device. Set Crystal Chip Channel 1 as your boot card. MUST BE ON [FW 1.4.0 or later!](https://distribution.appcake.co.uk/install/8bitmods/apps/memcard-pro2/public)

    [:material-cloud-download: MCP2](https://github.com/saildot4k/BootManager-MegaPack/raw/refs/heads/main/MMCE.zip)

</div>

Apps Included and updated as of 3/7/2027:

| Application               | USB (Fat16/32)                  | MMCE Device                       |
| :------------------------ | :-----------------------------: | :-------------------------------: |
| Crystal Chips BootManager | :material-close-circle-outline: | :material-check-circle:           |
| BM Themes/Languages       | :material-check-circle:         | :material-check-circle:           |
| NHDDL Nightly 03/29/25    | :material-check-circle:         | :material-check-circle:           |
| OPL 1.2 Beta 2201         | :material-check-circle:         | :material-check-circle:           |
| OPL 1.2 Beta 2049         | :material-check-circle:         | :material-check-circle:           |
| OPL 1.2 MMCE Beta 2       | :material-check-circle:         | :material-check-circle:           |
| OPL 1.2 for RetroGem      | :material-check-circle:         | :material-check-circle:           |
| RetroGem Disc Launcher    | :material-check-circle:         | :material-check-circle:           |
| Simple Media System       | :material-check-circle:         | :material-check-circle:           |
| RetroLauncher             | :material-check-circle:         | :material-close-circle-outline:   |
| OSDXMB                    | :material-check-circle:         | :material-close-circle-outline:   |
| XEB+ launch script        | :material-check-circle:         | :material-close-circle-outline:   |
| XEB+                      | :material-close-circle-outline: | :material-close-circle-outline:   |
| Apollo Save Tool          | :material-check-circle:         | :material-check-circle:           |
| wLaunchElf by ISR         | :material-check-circle:         | :material-check-circle:           |
| wLaunchElf by kHn         | :material-check-circle:         | :material-check-circle:           |
| wLaunchElf Official       | :material-check-circle:         | :material-check-circle:           |
| Memory Card Annihilator   | :material-check-circle:         | :material-check-circle:           |
| PS2 Link                  | :material-check-circle:         | :material-check-circle:           |
| PS2 Link HL               | :material-check-circle:         | :material-check-circle:           |
| HDD Tester                | :material-check-circle:         | :material-check-circle:           |
| PS2 RDRAM Test            | :material-check-circle:         | :material-check-circle:           |
| Mechacon Crash Test       | :material-check-circle:         | :material-check-circle:           |
| Pad Tester                | :material-check-circle:         | :material-check-circle:           |
| PS2 Temps                 | :material-check-circle:         | :material-check-circle:           |
| Neutrino                  | :material-check-circle:         | :material-check-circle: MMCE root |


??? note "Missing App Notes"

    - XEB+ Xmas Edition must be acquired from official sources due to license
        - Can only be ran from USB!
    - RetroLauncher is unable to be burned to CD so it is not included on the CD installer.
        - Can only be ran from USB!
    - OSDXMB can only be ran from USB!

## APPINFO.PBT SAS (SAVE APPLICATION SUPPORT) Example

??? note "APPINFO.PBT SAS Example
    ```
    # SAS (Save Application Support) compliant BM Script:
    # Due to wildcard bug on memory card, APPINFO.PBT can not be in root folders where elf exists, so APPINFO.PBT will be in mc?:/BM/APPS/
    # Memory Card structure mc?:/BM/APPS/$SAS$/APPINFO.PBT and elf in mc?:/$SAS$/APPINFO.PBT
    # Non-Memory Card Structure: device:/$SAS$/APPINFO.PBT or device:/APPS/$SAS$/APPINFO.PBT NOTE: $PWD$ should work for both.

    # Change this information to describe the application and where it should be ran from for memcard (SAS) or other devices (SAS_NON_MC)
    # SAS is the App folder name. SAS_NON_MC defines if app is in root of non-memcard device (non_mc:/$SAS$) or APP folder (non_mc:/APPS/$SAS$)
    # This is so that you do not have to edit any info below line 20. 
    #
    # Some devices are case sensitive! Make sure you case matches!
    #
    SET "TITLE" "PS2Temps"
    SET "VERSION" "1.0"
    SET "AUTHOR" "jolek and akuhak"
    SET "DESC" "Monitor your PS2 CPU and Mechacon Temps (if applicable)"
    SET "MEDIAS" ""
    SET "ELF" "PS2Temps.elf"
    SET "SAS" "DST_PS2TEMPS"
    # Comment out 1 of the 2 lines below. If app is in non-mc:/$SAS$ comment out line 19. If app is in non-mc:/APPS/$SAS$ comment out line 18
    # SET "SAS_NON_MC" "$SAS$"
    SET "SAS_NON_MC" "APPS/$SAS$"
    #


    # Do not change these 2 lines!
    GOTO "$ARG1$"
    RETURN -1

    # :LABEL_NAME
    #     ADDWIDGET "LABEL" "$ARG2$$TITLE$ v$VERSION$"
    #     EXIT 0

    :QUERY
        ADDWIDGET "CALL" "$TITLE$" "$BM.TXT_VERSION$: $VERSION$ $BM.TXT_AUTHOR$: $AUTHOR$ $BM.TXT_DESC$: $DESC$" $ARG2$ "$ARG0$" "$ARG3$" "$ARG4$" "$ARG5$"
        EXIT 0

    :INSTALL
        PARSEPATH "$PWD$" "SRC_DEV" "SRC_PATH" "SRC_FILE"

        IF MATCHES "mc?" "$SRC_DEV$"
            IF MATCHES "mc?" "$ARG2$" 
                GOTO "INSTALL_MC_TO_MC"
            ELSEIF NOT MATCHES "mc?" "$ARG2$"
                GOTO "INSTALL_MC_TO_NONMC"
            ENDIF
        ELSEIF NOT MATCHES "mc?" "$SRC_DEV$"
            IF MATCHES "mc?" "$ARG2$"
                GOTO "INSTALL_NONMC_TO_MC"
            ELSEIF NOT MATCHES "mc?" "$ARG2$"
                GOTO "INSTALL_NONMC_TO_NONMC"
            ENDIF

    :INSTALL_MC_TO_MC
        # Copies where APPINFO.PBT can be found in mc?:/BM/APPS/$SAS$                          
        IF FAIL COPY "$PWD$" "$ARG2$:/BM/APPS/$SAS$"
            MESSAGE "Failed installing APPINFO.PBT"
            RRM "$ARG2$:/BM/APPS/$SAS$"
            RETURN -1
        # Copies SAS app folder from root of mc? for SAS support
        ELSEIF FAIL COPY "$SRC_DEV$:/$SAS$" "$ARG2$:/$SAS$"
            MESSAGE "Failed installing $TITLE$"
            RRM "$ARG2$:/$SAS$"
            RETURN -1
        ELSEIF NOT EXISTS "$ARG2$:/BM/bman.icn"
            GOTO "INSTALL_MC_ICON"
        ELSEIF NOT EXISTS "$ARG2$:/BM/icon.sys"
            GOTO "INSTALL_MC_ICON"
        ENDIF
        EXIT 0

    :INSTALL_MC_TO_NONMC
        IF FAIL COPY "$SRC_DEV$:/$SAS$" "$ARG2$:/$SAS_NON_MC$"
            MESSAGE "Failed installing $TITLE$"
            RRM "$ARG2$:/$SAS_NON_MC$"
            RETURN -1
        ENDIF
        EXIT 0

    :INSTALL_NONMC_TO_NONMC
        IF FAIL COPY "$PWD$" "$ARG2$:/$SAS_NON_MC$"
            MESSAGE "Failed installing $TITLE$"
            RRM "$ARG2$:/$SAS_NON_MC$"
            RETURN -1
        ENDIF
        EXIT 0

    :INSTALL_NONMC_TO_MC
        # Creates folder and copies where APPINFO.PBT can be found in mc?:/BM/APPS/$SAS$     
        # NOTE: COPY function below fails HOWEVER does create the $SAS$ folder with nothing in it...
        # this is why I (R3Z3N) do not use IF FAIL COPY. Trust me, I tried the usual way as found in the BM installer APPINFO.PBT with MKDIR
        # Odd. Had to use a bug to create this folder...notice the slash at end of destination
        COPY "$PWD$" "$ARG2$:/BM/APPS/$SAS$/"
        # Copies where APPINFO.PBT can be found in mc?:/BM/APPS/$SAS$/APPINFO.PBT
        IF FAIL COPY "$ARG0$" "$ARG2$:/BM/APPS/$SAS$/APPINFO.PBT"
            MESSAGE "Failed installing APPINFO.PBT"
            RRM "$ARG2$:/BM/APPS/$SAS$"
            RETURN -1
        # Copies SAS app folder to root of mc? for SAS support  
        ELSEIF FAIL COPY "$PWD$" "$ARG2$:/$SAS$"
            ECHO "Failed installing $TITLE$"
            MESSAGE "Failed installing $TITLE$"
            RRM "$ARG2$:/$SAS$"
            RETURN -1
        # Create icons if needed so OSDSYS does not show corrupt
        ELSEIF NOT EXISTS "$ARG2$:/BM/bman.icn"
            GOTO "INSTALL_MC_ICON"
        ELSEIF NOT EXISTS "$ARG2$:/BM/icon.sys"
            GOTO "INSTALL_MC_ICON"
        ENDIF
        EXIT 0

    :INSTALL_MC_ICON
        IF FAIL COPY "$BM.BM_PATH$/bman.icn" "$ARG2$:/BM/bman.icn"
            MESSAGE "Failed to install $BM.BM_PATH$/bman.icn"
            RETURN -1
        ELSEIF FAIL COPY "$BM.BM_PATH$/icon.sys" "$ARG2$:/BM/icon.sys"
            MESSAGE "Failed to install $BM.BM_PATH$/bman.icn"
            RETURN -1
        ENDIF
        EXIT 0

    :REMOVE
        PARSEPATH "$PWD$" "SRC_DEV" "SRC_PATH" "SRC_FILE"

        IF MATCHES "mc?" "$SRC_DEV$"
            GOTO "REMOVE_MC"
        ELSEIF NOT MATCHES "mc?" "$SRC_DEV$"
            GOTO "REMOVE_PWD"
        ENDIF

    :REMOVE_MC
        IF FAIL RRM "$SRC_DEV$:/$SAS$"
            MESSAGE "Failed removing $SRC_DEV$:/$SAS$"
            RETURN -1
        ENDIF
        GOTO "REMOVE_PWD"

    :REMOVE_PWD
        # Odd bug: needs to loop 2x to remove contents, otherwise first run only APPINFO.PBT is removed
        IF FAIL RRM "$PWD$"
            GOTO "REMOVE_PWD"
            MESSAGE "Failed removing $TITLE$"
            RETURN -1
        ENDIF
        EXIT 0

    :RUN
        PARSEPATH "$PWD$" "SRC_DEV" "SRC_PATH" "SRC_FILE"

        IF MATCHES "mc?" "$SRC_DEV$"
            LOADEXEC "PBAT" "$BM.SCRIPTS$/LOADEXEC.PBT" "$SRC_DEV$:/$SAS$/$ELF$"
            EXIT 0
        ELSEIF MATCHES "host" "$SRC_DEV$"
            MESSAGE "Run with PS2Client instead!"
            EXIT 0
        ELSEIF NOT MATCHES "mc?" "$SRC_DEV$"
            IF MATCHES "host" "$SRC_DEV$"
                MESSAGE "Run with PS2Client instead on PC!"
                EXIT 0
            ELSE
                LOADEXEC "PBAT" "$BM.SCRIPTS$/LOADEXEC.PBT" "$PWD$/$ELF$"
                EXIT 0
            ENDIF
        ENDIF
        EXIT 0
    ```


## APPINFO.PBT Example

??? note "APPINFO.PBT Example"
    ```
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

??? material-script-text "APPINFO.PBT Example w 3 Boot Options"
    ```
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

- [ ] SAS support (Apps from root with prefixes IE mc?:/APP_WLE-ISR-EXFAT-MMCE or mc?:/APP_OPL-MMCE-BETA2)
- [ ] SAS build for BootManager and it's folder structure
- [ ] CC1.X Boot method failover IE try next memcard
- [ ] CC1.X BootManager boots from USB 
- [ ] CC2.0 8MB Dataflash support in FW
    * [ ] 1056 Page Support for AT45DB642D in testing
    * [ ] 256 Page Support for AT45DB621E in testing
- [x] BM can be ran from Hard Drive (HDD drivers MUST be installed tp mc0)
    * [x] Uploaded to github
    * [ ] Script for ease of use
    * [ ] Document for ease of use
- [ ] HDD IRXs not installed for V14 and later PS2s