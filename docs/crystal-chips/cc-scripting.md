# BootManager Scripting Documentation

## Variables
Variables are used to store values.

To set a new variable, you have to specify the type :

```SET "STRING" "MY_VARIABLE" "Mod your life"```

**Possible variable types are:**

- STRING : string (assumed if nothing is set)

- U8/S8 : Signed/Unsigned 8-bits number

- U16/S16 : Signed/Unsigned 16-bits number

- U32/S32 : Signed/Unsigned 32-bits number

!!! note "Signed/Unsigned definition"

    Signed numbers can be negatives, Unsigned can only be positives.


**Examples**

#### SET
To store a string or number

```SET "U8" "MY_DIGIT" "235"```

```SET "S32" "MY_OTHER_DIGIT" "-3420"```


Once the type is set, you can assign a new value to the variable :

```SET "MY_DIGIT" "34"```

**Call an existing variable**

To call an already defined variable, you have to surround it with ```$``` :

```ECHO "$MY_DIGIT$"```

will display ```34``` in the output console for example PS2Client.


!!! note "Where to save defined variables:"

    The best place to define your variables and their types is in the file DEFCONF.PBT.

    If you want your variable to be saved in the configuration file of Boot Manager, the name MUST begin with "BM.CNF".

```SET "BM.CNF_MY_DEFINITION" "$MY_DIGIT$"```


#### UNSET
To remove a string or number

```UNSET "MY_DIGIT"```


## Messages
Messages can be displayed either on the output console, or in the TV screen.

#### ECHO
To output text to console (PS2Client)

```ECHO "The value of MY_DIGIT is : $MY_DIGIT$"```

will return the text and the contain of the variable in the output console which will be in most case the console where you launched ps2client.

#### MESSAGE
To display text on the tv screen

```MESSAGE "Installation Complete"```

will return the text on the TV screen.

**Escaping characters**

You can escape a character with ^

```MESSAGE "The Crystal Chip is ^"astonishing^"".```

The ^ will tell the MESSAGE command not to interpret the " next to it as the end of the string character.


## Widgets
Widgets is used to display menus in the screen. There are many Widget types to feet different needs.

### ADDWIDGET
To display a menu item

```ADDWIDGET "LABEL" "Main Menu"```

Types of Widgets:


#### LABEL
To display a title.

```ADDWIDGET "LABEL" "$TXT_LABEL$"```

will display a title line with the text contained in the variable TXT_LABEL.


#### INT
To set a variable with a number

```ADDWIDGET "INT" "Title" Description" "MY_NUMBER" "0" "99" 1```

will display a widget to store a value between 0 and 99 in the variable MY_NUMBER. The user will be able to increment the number by 1.


#### AXIS
To set axis numbers (X,Y)

```ADDWIDGET "AXIS" "Title" "Description" "VALUE_X" "VALUE_Y" "0" "1920" "1" "0" "1920" "2"```

will display the widget which let the user to select a value for VALUE_X between 0 and 1920 with an increment of 1 and for VALUE_Y between 0 and 1920 with an increment of 2.


#### IP
To set an IP address

```ADDWIDGET "IP" "Title" "Description" "IP_ADDRESS_1" "IP_ADDRESS_2" "IP_ADDRESS_3" "IP_ADDRESS_4"```

to set variables IP_ADDRESS_1, IP_ADDRESS_2 etc. For example, if you wish to display this IP again, you'll have to call


```ECHO "THE IP ADDRESS YOU'VE ENTERED IS $IP_ADDRESS_1$.$IP_ADDRESS_2$.$IP_ADDRESS_3$.$IP_ADDRESS_4$"```


#### CHOICE
To display a choice to set a numerical value to a variable

```ADDWIDGET "CHOICE" "Title" "Description" "MY_CHOICE"  "CHOICE 1" "CHOICE 2" "CHOICE 3"```

will display a widget with the specified title and description (the description is displayed in the scroll bar), and will set the variable MY_CHOICE to "0", "1", or "2" depending of the user choice.


#### CALL
To call another section of the code

```ADDWIDGET "CALL" "Title" "Description" "$ARG0$" "THE_SECTION" "ARG_2" "ARG_3"...```

will call the section "THE_SECTION" of the file $ARG0$ ($ARG0$ will be the file where this widget is executed. The section THE_SECTION is inside the same file). with arguments ARG_2 and ARG_3.

The text ARG_2 and ARG_3 will be available in the section THE_SECTION by calling variables $ARG2$ and $ARG3$. (see Sections below)


##### SWITCH
When you have many case to treat, you can also use the ```SWITCH``` function.
Will be used with ```ADDWIDGET CALL``` or ```ADDWIDGET CHOICE``` 

```
SWITCH "$BM.CNF_VMODE$"
    CASE 1
    # PAL
        SET "BM.CNF_SCREEN_X" "0"
        SET "BM.CNF_SCREEN_Y" "0"
        BREAK
    CASE 2
    # VGA
        SET "BM.CNF_SCREEN_X" "0"
        SET "BM.CNF_SCREEN_Y" "0"
        BREAK
    CASE 3
    # 480P
        SET "BM.CNF_SCREEN_X" "0"
        SET "BM.CNF_SCREEN_Y" "0"
        BREAK
    CASE 0
    # NTSC
    DEFAULT
        SET "BM.CNF_SCREEN_X" "0"
        SET "BM.CNF_SCREEN_Y" "0"
        BREAK
ENDS
```

You can see that the BREAK command is used to go out of the SWITCH as soon as a case has been treated. You can add DEFAULT to take in consideration this CASE if non corresponds.


#### COLOR

```ADDWIDGET "COLOR" "MYCOLOR" "Color Hint" "Variable"```


#### RETURN
To return to a previous menu/script

```ADDWIDGET "RETURN" "$BM.TXT_DONE$" "$BM.TXT_RETURN_CONFIG$"```


## Other Widget Commands

#### CLEARWIDGETS

```CLEARWIDGETS``` without arguments will clear the screen of any widget.

#### SETTITLE

```SETTITLE``` will set the title of the current screen.

```SETTITLE "Install App to...```


## Sections

#### GOTO
A PBAT script is divided into sections. You can define a new section using the sign ":"

You can navigate thru sections with the GOTO command.

Here is a piece of code to understand how sections work :

```
GOTO "MAIN_MENU"

:A_SECTION
    ECHO "We are in the A_SECTION section".

:MAIN_MENU
    ADDWIDGET INT "Value to export" "Choose a number that will be exported to another section" "THE_NUMBER" "0" "10" "1"
    ADDWIDGET CALL "Go to Config Menu" "Will display the Config Menu" "$ARG0$" "CONFIG_MENU" " "$THE_NUMBER$"

:CONFIG_MENU
    CLEARWIDGETS
    MESSAGE "The Number you choose was : $ARG2$"
```


If this script is called, the section MAIN_MENU will be executed first because of the GOTO. In MAIN_MENU, the variable $THE_NUMBER$ is choosen by the user and the code will jump to CONFIG_MENU with the variable exported.

## Conditions

### IF 

All conditions will start with `IF`. There exists `ELSIF`, `ELSE` and `ENDIF`. See below for further usage.

#### EQU / NEQ
`EQU` = Equal
`NEQ` = NOT Equal
`EQUC` = Equal ? (unknown...)
`NEQC` = NOT Equal ? (unknown...)


```
IF EQU "$MY_VARIABLE$" "1"
    MESSAGE "The Variable was equal to 1"
ELSE
    MESSAGE "The Variable was not equal to 1"
ENDIF
```


You can also turn this code differently :

```
IF NEQ "$MY_VARIABLE$" "0"
    MESSAGE "The Variable was not equal to 0"
ELSE
    MESSAGE "The Variable was equal to 0"
ENDIF
```


#### EXISTS
To know if a file/folder exists or not. This command should be used in a IF statement

```
IF EXISTS "mc0:/MYFOLDER/MYSCRIPT.PBT"
    COPY "mc0:/MYFOLDER/MYSCRIPT.PBT" "mass:/MYFOLDER/MYSCRIPT.PBT"
ENDIF
```


#### MATCHES
To know if a STRING matches or not. This command should be used in a IF statement. If a wildcard is used, best to use it in first part of comparison. Second comparison should have NO wildcards.

```
IF MATCHES "SCPH-300*" "$BM.CONSOLE_MODEL$"
    MESSAGE "Console is SCPH-300XX"
ENDIF
```


#### GTE, GT, LTE, LT
`GTE` = Greater than or equal

`GT` = Greater than

`LTE` = Less than or equal

`LT` = Less than or equal

```
IF GTE "$BM.BIOS_MAJOR_VER$$BM.BIOS_MINOR_VER$" "220"
    MESSAGE "Unit is SCPH-75k or later and does not support HDD!"
ENDIF
```


#### FAIL
Combine with other commands to execute if command failed.

```
IF FAIL COPY "mass:/MYFOLDER" "mc0:/MYFOLDER
    MESSAGE "Failed to copy MYFOLDER"
    IF FAIL RRM "mc0:/MYFOLDER"
        MESSAGE "Failed to remove mc0:/MYFOLDER!"
        RETURN -1
    ENDIF
ENDIF"
```


### ELSEIF / ELSE
you can imbricate more than one IF with the keyword ```ELSIF``` :

```
IF EQU "$MY_VARIABLE$" "1"
    MESSAGE "The Variable was equal to 1"
ELSEIF EQU "$MY_VARIABLE$" "2"
    MESSAGE "The Variable was equal to 2"
ENDIF
```

You'll use the ```ELSEIF``` statement when you want to keep testing for values.

You will use the ```ELSE``` statement when none are true, the last ELSE will be executed.

```
IF EQU "$MY_VARIABLE$" "1"
    MESSAGE "The Variable was equal to 1"
ELSE 
    MESSAGE "The Variable was something other than 1"
ENDIF
```

### ENDIF
Any condition starting with `IF` must have an `ENDIF`

```
IF
ELSEIF
ELSEIF
ELSE
ENDIF
```


## File Manipulation

File manipulation is useful for installation scripts (in APPINFO.PBT). You can manipulate files on any device :

- mc0 (for memory card 1)
- mc1 (for memory card 2)
- mass (for USB device)
- mmce0 (for MMCE device 1)
- mmce0 (for MMCE device 2)
- pfs0 (for internal HDD, uses __common partition)
- dffs (for internal Chip flash memory CC 2.0 ONLY, don't forget 1.1/1.2 can be turned into 2.0!)
- host (for remote host. Only available if ps2client is launched on the PC and the network and the host server are started on Boot Manager) 

Combine the below commands with `IF FAIL` and `ELSEIF FAIL` for error handling


#### COPY
To copy file/directory from source to destination :

```COPY "host:/FOLDER" "mass:/FOLDER/FOLDER2"``` will copy contents source folder to destintaion folder if intermediary folders exist.

```COPY "host:/FOLDER/FILE.TXT" "mass:/FOLDER1/FOLDER2/FILE.TXT"``` will copy the single file, but will NOT create destination folder structure if it does not exist.

Notes: copying a file to a file only works if prior directories already exist on destination.

```COPY "host:/FOLDER" "mass:/FOLDER1/FOLDER2/FILE.TXT"``` DOES NOT WORK

```COPY "host:/FOLDER" "mass:/FOLDER1/FOLDER2/"``` This does work to create an empty mass:/FOLDER1 but will say it fails if used with ```IF COPY FAIL```


#### RM
To delete a file or directory

```RM "mc0:/TMPFOLDER"```

will completely delete the folder TMPFOLDER and its contains.```

Most likley the same script as RRM


#### RRM
To delete a file or directy and it's sub-folders (recursively remove). For Example mc0:/TMPFOLDER/SUBFOLDER1

```RRM "mc0:/TMPFOLDER```

Most likely the same script as RM

#### MKDIR
To create a new folder.

```MKDIR "mass:/MYFOLDER"```

 will create a folder MYFOLDER in the USB mass storage.

 Note: MKDIR will not create mutliple folders for example if MYFOLDER, FOLDER and FOLDER3 do not exist:

```
IF NOT EXISTS "mass:/MYFOLDER/FOLDER2/FOLDER3"
    IF FAIL MKDIR "mass:/MYFOLDER/FOLDER2/FOLDER3"
        MESSAGE "FAILED TO CREATE DIRECTORY!"
    ENDIF
ENDIF
```

The workaround is to exploit a bug that thinks it failed

```COPY $PWD$ "mass:/MYFOLDER/MYFOLDER2/MYFOLDER3"```

DO NOT PRECEDE WITH `IF FAIL` as it does think it failed. Contents of folders will not be harmed in my testing if some of it exists.


#### REDIRFILE
To symlink a file to another location. Only works if the environment you use doesn't reboot IOP too soon IE PS2LINK

```REDIRFILE "$PWD$/IPCONFIG.DAT" "$BM.BM_PATH$/CONFIG/IPCONFIG.DAT"```

```"$PWD$/IPCONFIG.DAT"``` is where you want the file to "appear" and ```"$BM.BM_PATH$/CONFIG/IPCONFIG.DAT"``` is where the file currently resides.


#### FPRINT
To write out text into a file.

```FPRINT "mass:/MY_TEXT.TXT"  "This text will be written into MY_TEXT.TXT."```

Be careful, if the file exists already, the content will be replaced though a bug does exist where text is appended instead of file replaced especially if file has line breaks.


## LOADEXEC - Passing Variables
To call/execute another part of the same script or another script and pass variables or args.

``````LOADEXEC "TYPE" "ARG0" "ARG1" "ARG2"```

Will execute a "TYPE" of loadexec: `PBAT`,`PBATS` `EEELF`, `IRX`

#### LOADEXEC "PBAT"
```LOADEXEC "PBAT" "MY_FILE.PBT" "MY_ARGUMENT1" "MY_ARGUMENT2"```

will execute a PBAT file named MY_FILE.PBT with the arguments specified. Most of the time, you'll specify a section of the same PBAT script to be executed as the argument. 

In the called script, MY_ARGUMENT2 will be the first variable in the afformentioned called script, which can be recalled in said script with $ARG2$

#### LOADEXEC "PBATS"
```LOADEXEC "PBATS" "MY_*.PBT" "MY_ARGUMENT1" "MY_ARGUMENT2"```

PBATS is usually used to call multiple scripts to print APPS,DEVS,THEMS,LANGS to screen as choices. In the called PBAT GOTO section will most likely be ADDWIDGET "CALL"...to pass ARGS back to this script.

In the called script, MY_ARGUMENT2 will be the first variable in the afformentioned called script, which can be recalled in said script with $ARG2$

#### LOADEXEC "EEELF"
```LOADEXEC "EEELF" "MY_FILE.ELF" "MY_ARGUMENT1" "MY_ARGUMENT2"```

will execute MY_FILE.ELF with MY_ARGUMENT1 and MY_ARGUMENT2 passed to the elf should it support arg(v).

#### LOADEXEC "IRX"
```LOADEXEC "IRX" "MY_FILE.IRX"```

will execute an IRX (device driver usually) to add functionality to BOOTMANAGER. Most IRXs do not support arg(v).

## Keeping Script in Memory

#### KEEP
Loads script in ram for quicker recall

```KEEP```



## Needs documentation:

EVAL SETTITLE - Evaluate a title, usually with nested $BM.TXT_MYTEXT$

EVAL ADDWIDGET - Evaluate a widget, usually with nested $BM.TXT_MYTEXT$

SKIPBACK - When returning from a submenu, this menu is skipped(ie returns to the menu before this menu).

RETURN 0/-1 - Remove the script from memory if the return value is <0

EXIT - 0/-1 Exit from the script (0 )and do not keep it in memory (-1)

FORMAT

$BM.MAJOR_VER$ - BootManager major version

$BM.MINOR_VER$ - BootManager minor version

$BM.PATCH_VER$ - BootManager patch version

$BM.CC_MAJOR_VER$ - Crystal Chip major version

$BM.CC_MINOR_VER$ - Crystal Chip minor version

CYCLETRAY - Causes the CDVD drive to recheck the disc. Parameters can be "WAIT", "NOWAIT" or nothing(which is the same as "WAIT"). "WAIT" means "wait until disc has authenticated and fail if disc does not authenticate". "NOWAIT" returns immediately after telling the CDVD drive to reauthenticate.

PARSEPATH "$PWD$" "SRC_DEV" "SRC_PATH" "SRC_FILE" - Will let you call Path working directory, source device, source path and source file.

LOADEXEC "EEELF" "$ARG1$" $ARG2$ - Executes an elf on EE (ARG1) and passes an argument to it. See NHDDL APPINFO.PBT or OSDSYS APPINFO.PBT

LOADEXEC "PBAT" "$ARG1$" $ARG2$ - Executes a PBAT script ARG1 with ARG2 passed into it as ARG1. Remember ARG0 is always current running script, ARG1 is the current GOTO in the current running script after LOADEXEC...All arguments after are the ARG2 and greater.

LOADEXEC "IRX" 

REBOOTIOP "rom0:UDNL rom0:OSDCNF"

PEEK(B,H,W) "0x12345678"- PEEK BYTE, HALF-WORD, WORD

POKE(B,H,W) "0x12345678" - PEEK BYTE, HALF-WORD, WORD

IF NOT MODLOADED "dev9_driver" - Detemines if IRX is loaded. Unsure how to find names of loaded IRX as is not ELF name.

UNMOUNT 

SAVEVARS - Save variables

SETAUTH - Set the disc authentication type: "OFF", "PS1" or "PS2"

SETBIOS - Set the bios patches type: "OFF", "PS1" or "PS2"

SHUTDOWN - Shutdown all "ALL", Memory Module "MM", MMIOP "MMIOP"

LOADIMG/UNLOADIMG - load and unload an image for theming

KILLSESS (or kill session, need to recall)

ISIN - if text is within a file

PARSECNF - parses disc CNF. Reference BM/SCRIPTS/BMCONT.PBT

```*``` wildcard(s)

```?``` single character wildcard

Found by running BM.ELF in PCSX2 and looking at memory.

Need to test....

GETDVDREG, EXECCMD, CC, ILLEGAL, CDSTOP, GETDVDREG, BGCOLOR, SETBACK, SETEXIT, LIBLOADED, DUMPIOP
TOUCH, ADDMACRO, BOOT, DUMPIOP,  and NEQC and EQUC (EQU, NEQ is equal not equal, so what is NEQC?)
DISCONNECT, FINDPAD, FINDCTP1, EXECMD, STABLE, ERROR, COMPLETE, FAILED, BUSY


## Useful Tips

#### Use ECHO and PS2 Client
When debugging paste variables where you want in the script. Then run PS2Client to see output via ECHO


```
    PARSEPATH "$PWD$" "SRC_DEV" "SRC_PATH" "SRC_FILE"

    ECHO ""
    ECHO ""
    ECHO ARG0: $ARG0$
    ECHO ARG1: $ARG1$
    ECHO ARG2: $ARG2$
    ECHO ARG3: $ARG3$
    ECHO ARG4: $ARG4$
    ECHO ARG5: $ARG5$
    ECHO ARG6: $ARG6$
    ECHO ARG7: $ARG7$
    ECHO ARG8: $ARG8$
    ECHO ARG9: $ARG9$
    ECHO ARG10: $ARG10$
    ECHO ARG11: $ARG11$
    ECHO ARG12: $ARG12$
```

#### PS2Client

Paste and edit this text into plain text file saved as LauchBM2.bat

```ps2client -h 192.168.0.10 execee host:/BM/BM2.ELF```

In the folder that has PS2Client, paste your BM folder

You can then edit the scripts, and reload menu on Crystal Chip BootManager to see your changes. I recommend to comment out scripts with KEEP for quick testing, though that may break things like PIN testing or adjusting Theme Configurations.