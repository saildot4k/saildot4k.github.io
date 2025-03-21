## Crystal Chip FW R34 v3

[Crystal Chip FW R34 v3 with updated Dashboard Scripts by R3Z3N](https://github.com/saildot4k/Crystal-Chip-R34-v3/releases)

(RUNNING CHANGES as of 2/26/2025. I update the date as I go...)
    
    
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

    [:material-cloud-download: USB](https://github.com/saildot4k/BootManager-MegaPack/raw/refs/heads/main/BM_MegaPack_by_R3Z3N.zip)


-   __SD2PSX/PSXMemCard Gen2__

    ---

    Unzip and merge contents to root of your SD2PSX/PSXMemcard Gen2 MMCE device (THIS WILL WIPE YOUR BOOT CARD!) MUST BE ON [FW 1.1.1 or later!](https://sd2psxtd.github.io/download)

    [:material-cloud-download: SD2PSX](https://github.com/saildot4k/BootManager-MegaPack/raw/refs/heads/main/BM_MegaPack_by_R3Z3N_SD2PSX.zip)

-   __MemCardPro 2__

    ---

    Unzip and merge contents to root of your MemCardPro 2 MMCE device. Set Crystal Chip Channel 1 as your boot card. MUST BE ON [FW 1.4.0 or later!](https://distribution.appcake.co.uk/install/8bitmods/apps/memcard-pro2/public)

    [:material-cloud-download: MCP2](https://github.com/saildot4k/BootManager-MegaPack/raw/refs/heads/main/BM_MegaPack_by_R3Z3N_MCP2.zip)

</div>

Apps Included and updated as of 3/7/2027:

| Application               | USB (Fat16/32)                  | MMCE Device                       |
| :------------------------ | :-----------------------------: | :-------------------------------: |
| Crystal Chips BootManager | :material-close-circle-outline: | :material-check-circle:           |
| BM Themes/Languages       | :material-check-circle:         | :material-check-circle:           |
| NHDDL                     | :material-check-circle:         | :material-check-circle:           |
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
    - RetroLauncher is unable to be burned to CD
        - Can only be ran from USB!
    - OSDXMB can only be ran from USB!


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