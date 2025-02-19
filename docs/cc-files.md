## R34 V3 Firmware and Dashboard by R3Z3N

[Crystal Chip FW R34 v3 with updated Dashboard Scripts](https://github.com/saildot4k/Crystal-Chip-R34-v3/releases)


??? note "Additions by R3Z3N 1/26/25"
    Release 34 V3 by R3Z3N Jan 26 2025 (RUNNING CHANGES. I update the date as I go...)
       
        
        - CC1.X firmware options to run BM from MemCard1 or 2. makeit_nocd does have scripts to
	    build FW for running from USB/HDD but seems pointless. Options added in BM for full ease
        of use. HDD workign but I need to think about how to direct users to install BM.

        - MMCE device support for example SD2PSX, PsxMemCardGen2, MemCardPro2.
	    [SD2PSXTD](https://sd2psxtd.github.io/)
        [MCP2](https://8bitmods.com/memcard-pro2-for-ps2-and-ps1-smoke-black/)

        - Exfat USB support via [BDM Assault](https://github.com/israpps/BDMAssault)

        - Security Settings added: when pin is set, advanced settings are unaccessible. 

        - Updated bminit.pbat to load IRX drivers from where BM is running from,
        otherwise with DEV1/2 would not see/run apps from mc0/1/USB/HDD.
	
        - Updated HDDMOUNT.IRX and BM/SCRIPTS/HDDLOAD.PBT to load __common HDD partition
        instead of +Crystal. This is to keep things consistent with the homebrew community
	    
        - Changed scripts to allow apps to be installed when booted from recovery cd.
  	
        - Changed scripts to only show options for chip installed! IE no more seeing DFFS
        options on CC 1.0 and 1.1. 1.2 no longer shows remove dffs:/BM
 	
        - Changed scripts so that FW choices are only applicable to the chip installed.
        IE CC1.0-1.2 can choose BM run point, CC2.0 DFFS only.
       
        - Show Info gives a little more clarity IE where is BM executed from, what console region codes stand for etc.

        - Cotton Candy theme added, each version of the Crystal Chip is represented!

        - Added Italian and Spanish language translations.

## To Do
- [ ] SAS support (Apps from root with prefixes IE mc?:/APP_WLE-ISR-EXFAT-MMCE or mc?:/APP_OPL-MMCE-BETA2)
- [ ] SAS build for BootManager and it's folder structure
- [ ] CC1.X Boot method failover IE try next memcard
- [ ] CC1.X BootManager boots from USB 
- [ ] CC2.0 8MB Dataflash support in FW
    * [ ] 1056 Page Support for AT45DB642D in testing
    * [ ] 256 Page Support for AT45DB621E in testing
-[x] BM can be ran from Hard Drive 
    * [ ] Script for ease of use
    * [ ] Document of ease of use
- [ ] HDD IRXs not installed for V14 and later PS2s

## APPINFO.PBT Example
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


## APPINFO.PBT w 3 Boot Options Example
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
