## [Crystal Chip FW R34 v3 with updated Dashboard Scripts by R3Z3N](https://github.com/saildot4k/Crystal-Chip-R34-v3/releases)

??? note "Additions by R3Z3N 2/22/25"
    Release 34 V3 by R3Z3N Feb 26 2025 (RUNNING CHANGES. I update the date as I go...)
       
        
        - CC1.X firmware options to run BM from MemCard1,2, HDD and USB. HDD/USB boot needs HDD drivers on mc0:/BM/SHARED/
        HDD and USB are commented out, go ahead and uncomment out in BM/FWS/LATEST/FWINFO.PBT to experiment

        - MMCE device support for example SD2PSX, PsxMemCardGen2, MemCardPro2.
	    [SD2PSXTD](https://sd2psxtd.github.io/)
        [MCP2](https://8bitmods.com/memcard-pro2-for-ps2-and-ps1-smoke-black/)

        -  ~~Used El Isras USB drivers for exfat support: BDM Assault (https://github.com/israpps/BDMAssault)~~
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


## [BM MegaPack for CD/USB](https://github.com/saildot4k/BootManager-MegaPack/raw/refs/heads/main/BM_MegaPack_by_R3Z3N.zip)

Unzip and merge with the Firmware Download or move the the root of your USB stick

## [BM MegaPack for SD2PSX/PSXMemcard Gen2](https://github.com/saildot4k/BootManager-MegaPack/raw/refs/heads/main/BM_MegaPack_by_R3Z3N_SD2PSX.zip)

Unzip and merge contents to root of your SD2PSX/PSXMemcard Gen2 MMCE Device


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
