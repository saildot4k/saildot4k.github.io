---
hide:
  - navigation
---
# BOOTMANAGER Scripting Reference List (PBAT)

## **Variables**
Variables are used to store values.

To set a new variable, you have to specify the type :

```pbat
SET "STRING" "MY_VARIABLE" "Mod your life"
```

**Possible variable types are:**

- `STRING` : string (assumed if the below types are not set)

- `U8/S8` : Signed/Unsigned 8-bits number

- `U16/S16` : Signed/Unsigned 16-bits number

- `U32/S32` : Signed/Unsigned 32-bits number

!!! note "Signed/Unsigned definition"

    Signed numbers can be negatives, Unsigned can only be positives.


**Examples**

### SET
To store a string or number

```pbat
SET "U8" "MY_DIGIT" "235"
```

```pbat
SET "S32" "MY_OTHER_DIGIT" "-3420"
```


Once the type is set, you can assign a new value to the variable :

```pbat
SET "MY_DIGIT" "34"
```

*Call an existing variable*

To call an already defined variable, you have to surround it with `$` :

```pbat
ECHO "$MY_DIGIT$"
```

will display `34` in the output console for example PS2Client.


!!! note "Where to save defined variables:"

    The best place to define your variables and their types is in the file DEFCONF.PBT.

    If you want your variable to be saved in the configuration file of Boot Manager, the name MUST begin with "BM.CNF".

```pbat
SET "BM.CNF_MY_DEFINITION" "$MY_DIGIT$"
```


### UNSET
To remove a string or number

```pbat
UNSET "MY_DIGIT"
```


### SAVEVARS 
Save variables that start with `BM.CNF_`

```pbat
IF FAIL SAVEVARS "BM.CNF_*" "$BM.BM_PATH$/CONFIG/BMCONF.PBT"
        MESSAGE "$BM.TXT_SAVE_CONF_FAIL$"
    ELSE
        SET "BM.CONFIG_CHANGED" "0"
    ENDIF
    GOTO "MENU_MAIN"
ENDIF
```


## **Messages**
Messages can be displayed either on the output console, or in the TV screen.

### ECHO
To output text to console (PS2Client)

```pbat
ECHO "The value of MY_DIGIT is : $MY_DIGIT$"
```

will return the text and the contain of the variable in the output console which will be in most case the console where you launched ps2client.


### MESSAGE
To display text on the tv screen

```pbat
MESSAGE "Installation Complete!"
```

will return the text `Installation Complete!` on the TV screen.

*Escaping characters*

You can escape a character with ^

```pbat
MESSAGE "The Crystal Chip is ^"astonishing^""
```

The ^ will tell the MESSAGE command not to interpret the " next to it as the end of the string character.


## **Widgets**
Widgets is used to display menus in the screen. There are many Widget types to feet different needs.

### ADDWIDGET
To display a menu item

```pbat
ADDWIDGET "LABEL" "Main Menu"
```

Types of Widgets:


### LABEL
To display a title.

```pbat
ADDWIDGET "LABEL" "$TXT_LABEL$"
```

will display a title line with the text contained in the variable TXT_LABEL.


### INT
To set a variable with a number

```pbat
ADDWIDGET "INT" "Title" "Description" "MY_NUMBER" "0" "99" "1"
```

will display a widget to store a value between 0 and 99 in the variable MY_NUMBER. The user will be able to increment the number by 1.


### AXIS
To set axis numbers (X,Y)

```pbat
ADDWIDGET "AXIS" "Title" "Description" "VALUE_X" "VALUE_Y" "0" "1920" "1" "0" "1920" "2"
```

will display the widget which let the user to select a value for VALUE_X between 0 and 1920 with an increment of 1 and for VALUE_Y between 0 and 1920 with an increment of 2.


### IP
To set an IP address

```pbat
ADDWIDGET "IP" "Title" "Description" "IP_ADDRESS_1" "IP_ADDRESS_2" "IP_ADDRESS_3" "IP_ADDRESS_4"
```

to set variables IP_ADDRESS_1, IP_ADDRESS_2 etc. For example, if you wish to display this IP again, you'll have to call


```pbat
ECHO "THE IP ADDRESS YOU'VE ENTERED IS $IP_ADDRESS_1$.$IP_ADDRESS_2$.$IP_ADDRESS_3$.$IP_ADDRESS_4$"
```


### CHOICE
To display a choice to set a numerical value to a variable

```pbat
ADDWIDGET "CHOICE" "Title" "Description" "MY_CHOICE"  "CHOICE 1" "CHOICE 2" "CHOICE 3"
```

will display a widget with the specified title and description (the description is displayed in the scroll bar), and will set the variable MY_CHOICE to "0", "1", or "2" depending of the user choice. `CHOICE` variables start with 0 and increment. `CHOICE 1` will be 0 when `$MY_CHOICE$` is recalled. `COICE 2` will be 1 and so forth.


### CALL
To call another section of the code

```pbat
ADDWIDGET "CALL" "Title" "Description" "$ARG0$" "THE_SECTION" "ARG2" "ARG3"...
```

will call the section `THE_SECTION` of the file `$ARG0$` (`$ARG0$` will be the file where this widget is executed. The section THE_SECTION is inside the same file). with arguments `ARG2` and `ARG3`.

The text `ARG2` and `ARG3` will be available in the section THE_SECTION by calling variables $ARG2$ and $ARG3$. (see Sections below)


#### SWITCH
When you have many case to treat, you can also use the `SWITCH` function.
Will be used with `ADDWIDGET "CALL"` or `ADDWIDGET "CHOICE"` 

```pbat
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


### COLOR

```pbat
ADDWIDGET "COLOR" "MYCOLOR" "Color Hint" "Variable"
```


### RETURN
To return to a previous menu/script

```pbat
ADDWIDGET "RETURN" "$BM.TXT_DONE$" "$BM.TXT_RETURN_CONFIG$"
```


## **Other Widget Commands**

### CLEARWIDGETS
Will clear the screen of all widgets.

```pbat
CLEARWIDGETS
``` 


### SETTITLE

`SETTITLE` will set the title of the current screen.

```pbat
SETTITLE "Install App to...
```

### EVAL
Used with `ADDWIDGET` and `SETTITLE` to evaluate nested variables

```pbat
EVAL SETTITLE "$$BM.TXT_$ARG2$_$ARG3$_FROM$$"
```

```pbat
EVAL ADDWIDGET "LABEL" "$$BM.TXT_$ARG3$$$"
```

## **Sections**

### GOTO
A PBAT script is divided into sections. You can define a new section using the sign `:`

You can navigate thru sections with the GOTO command. 

Do NOT use GOTO to jump to a label which is within an IF statement! Doing so will result in script failure. 

GOTO does NOT support passing arguments/values!

Here is a piece of code to understand how sections work :

```pbat
GOTO "MAIN_MENU"

:A_SECTION
    ECHO "We are in the A_SECTION section."

:MAIN_MENU
    ADDWIDGET "INT" "Value to export" "Choose a number that will be exported to another section" "THE_NUMBER" "0" "10" "1"
    ADDWIDGET "CALL" "Go to Config Menu" "Will display the Config Menu" "$ARG0$" "CONFIG_MENU" "$THE_NUMBER$"

:CONFIG_MENU
    CLEARWIDGETS
    MESSAGE "The Number you choose was : $ARG2$"
```


If this script is called, the section `MAIN_MENU` will be executed first because of the `GOTO`. In `MAIN_MENU`, the variable `$THE_NUMBER$` is choosen by the user and the code will jump to `CONFIG_MENU` with the variable exported.


## **Conditions**

### IF 

All conditions will start with `IF`. There exists `ELSIF`, `ELSE` and must be terminated with `ENDIF`. See below for further usage.

#### EQU, NEQ / GTE, GT, LTE, LT
Numerical Conditions

- `EQU` = Equal

- `NEQ` = NOT Equal

- `EQUC` = Equal ? (unknown...)

- `NEQC` = NOT Equal ? (unknown...)

- `GTE` = Greater than or equal

- `GT` = Greater than

- `LTE` = Less than or equal

- `LT` = Less than or equal


```pbat
IF EQU "$MY_VARIABLE$" "1"
    MESSAGE "The Variable was equal to 1"
ELSE
    MESSAGE "The Variable was not equal to 1"
ENDIF
```


You can also turn this code differently:

```pbat
IF NEQ "$MY_VARIABLE$" "0"
    MESSAGE "The Variable was not equal to 0"
ELSE
    MESSAGE "The Variable was equal to 0"
ENDIF
```

You can evaluate if a number is larger or less than or equal another variable:

```pbat
IF GTE "$BM.BIOS_MAJOR_VER$$BM.BIOS_MINOR_VER$" "220"
    MESSAGE "Unit is SCPH-75k or later and does not support HDD!"
ENDIF
```


#### EXISTS
To know if a file/folder exists or not. This command should be used in a IF statement

```pbat
IF EXISTS "mc0:/MYFOLDER/MYSCRIPT.PBT"
    COPY "mc0:/MYFOLDER/MYSCRIPT.PBT" "mass:/MYFOLDER/MYSCRIPT.PBT"
ENDIF
```


#### MATCHES
To know if a STRING matches or not. This command should be used in a IF statement. If a wildcard is used, best to use it in first part of comparison. Second comparison should have NO wildcards.

```pbat
IF MATCHES "SCPH-300*" "$BM.CONSOLE_MODEL$"
    MESSAGE "Console is SCPH-300XX"
ENDIF
```


#### FAIL
Combine with other file manipulation commands, conditions or `LOADEXEC` or `LOADSRAM`. There may be more...

```pbat
IF FAIL COPY "mass:/MYFOLDER" "mc0:/MYFOLDER
    MESSAGE "Failed to copy MYFOLDER"
    IF FAIL RRM "mc0:/MYFOLDER"
        MESSAGE "Failed to remove mc0:/MYFOLDER!"
        RETURN -1
    ENDIF
ENDIF"
```

```pbat
IF NOT FAIL COPY "mc0:/BOOT" "mc1:/BOOT"
    MESSAGE "Successfully copied ^"mc0:/BOOT^" to ^"mc1:/BOOT^"!"
ENDIF
```


#### MODLOADED
Detemines if IRX is loaded. Unsure how to find names of loaded IRX as is not ELF name.

```pbat
IF NOT MODLOADED "dev9_driver"
    IF FAIL LOADEXEC "IRX" "$BM.DRIVER_PATH$/PS2DEV9.IRX"
        ECHO "Failed loading PS2DEV9.IRX!"
        RETURN -1
    ENDIF
ENDIF
```


#### ISIN
Determines if text is within a file.

```pbat
IF ISIN "MY_FILE.TXT" "HELLO_WORLD"
    MESSAGE "HELLO WORLD!"
ENDIF
```


#### NOT
Combine with `IF`/`ELSEIF` and another condition.

```pbat
IF NOT EXISTS "mc0:/SYS-CONF/IPCONFIG.DAT"
    FPRINT "mc0:/SYS-CONF/IPCONFIG.DAT" "192.168.0.10"
ENDIF
```


### ELSEIF / ELSE
You can imbricate more than one IF with the keyword `ELSIF` :

```pbat
IF EQU "$MY_VARIABLE$" "1"
    MESSAGE "The Variable was equal to 1"
ELSEIF EQU "$MY_VARIABLE$" "2"
    MESSAGE "The Variable was equal to 2"
ENDIF
```

You'll use the `ELSEIF` statement when you want to keep testing for values.

You will use the `ELSE` statement when none are true, the last ELSE will be executed.

```pbat
IF EQU "$MY_VARIABLE$" "1"
    MESSAGE "The Variable was equal to 1"
ELSE 
    MESSAGE "The Variable was something other than 1"
ENDIF
```


### ENDIF
Any condition starting with `IF` must have an `ENDIF`

```pbat
IF
ELSEIF
ELSEIF
ELSE
ENDIF
```


## **File Manipulation**
File manipulation is useful for installation scripts (in APPINFO.PBT). You can manipulate files on any device :

- `mc0` (for memory card 1)
- `mc1` (for memory card 2)
- `mass` (for USB device)
- `mmce0` (for MMCE device 1)
- `mmce0` (for MMCE device 2)
- `pfs0` (for internal HDD, uses __common partition)
- `dffs` (for internal Chip flash memory CC 2.0 ONLY, don't forget 1.1/1.2 can be turned into 2.0!)
- `host` (for remote host. Only available if ps2client is launched on the PC and the network and the host server are started on Boot Manager) 

Combine the below commands with `IF FAIL` and `ELSEIF FAIL` for error handling.


### COPY
To copy file/directory from source to destination :

```pbat
COPY "host:/FOLDER" "mass:/FOLDER/FOLDER2"
```

will copy contents source folder to destintaion folder if intermediary folders exist.

```pbat
COPY "host:/FOLDER1/FILE.TXT" "mass:/FOLDER1/FOLDER2/FILE.TXT"
```

will copy the single file, but will NOT create destination folder structure if it does not exist.

Notes: copying a file to a file only works if prior directories already exist on destination.

```pbat
COPY "host:/FOLDER" "mass:/FOLDER1NOTEXISTS/FOLDER2/FILE.TXT"
```

^DOES NOT WORK!

```pbat
COPY "host:/FOLDER" "mass:/FOLDER1NOTEXISTS/FOLDER2/"
```

This does work to create an empty `mass:/FOLDER1` but will say it fails if used with `IF COPY FAIL`. Note the ending `/`


### RM/RRM
To delete a file or directory

`RM` Remove

`RRM` Recursive Remove

```pbat
RRM "mc0:/TMPFOLDER"
```

Most likely same script as informed by Crystal Chip Team since there is little reason for RM to exist.

### FORMAT
To erase file system and initialize Memory Card or Crystal Chip flash

```pbat
FORMAT "dffs:/"
```


### MKDIR
To create a new folder.

```pbat
MKDIR "mass:/MYFOLDER"
```

will create a folder MYFOLDER in the USB mass storage.

Note: MKDIR will not create mutliple folders for example if MYFOLDER, FOLDER and FOLDER3 do not exist:

```pbat
IF NOT EXISTS "mass:/MYFOLDER/FOLDER2/FOLDER3"
    IF FAIL MKDIR "mass:/MYFOLDER/FOLDER2/FOLDER3"
        MESSAGE "FAILED TO CREATE DIRECTORY!"
    ENDIF
ENDIF
```

The workaround is to exploit a bug that thinks it failed

```pbat
COPY $PWD$ "mass:/MYFOLDER/MYFOLDER2/MYFOLDER3"
```

DO NOT PRECEDE WITH `IF FAIL` as it does think it failed. Contents of folders will not be harmed in my testing if some of it exists.


### REDIRFILE
To symlink a file to another location. Only works if the environment you use doesn't reboot IOP too soon IE PS2LINK

```pbat
REDIRFILE "$PWD$/IPCONFIG.DAT" "$BM.BM_PATH$/CONFIG/IPCONFIG.DAT"
```

`"$PWD$/IPCONFIG.DAT"` is where you want the file to "appear" and `"$BM.BM_PATH$/CONFIG/IPCONFIG.DAT"` is where the file currently resides.

### UNMOUNT
To unmount a device such as HDD

```pbat
UNMOUNT "pfs0:"
```


### FPRINT
To write out text into a file.

```pbat
FPRINT "mass:/MY_TEXT.TXT"  "This text will be written into MY_TEXT.TXT."
```

Be careful, if the file exists already, the content will be replaced though a bug does exist where text is appended instead of file replaced especially if file has line breaks.


## **Executing and passing variables between sections/scripts**
To call/execute another section of the same or different script, elf or irx and pass variables or args as `ARG1`-`ARGX`

```pbat
LOADEXEC "TYPE" "ARG0" "ARG1" "ARG2"
```

Will execute a "TYPE" of loadexec: `PBAT`,`PBATS` `EEELF`, `IRX`


### PBAT
To execute another PBAT script and pass variables.

```pbat
LOADEXEC "PBAT" "MY_FILE.PBT" "MY_ARGUMENT1" "MY_ARGUMENT2"
```

will execute a PBAT file named MY_FILE.PBT and GOTO section "MY_ARGUMENT1" (ARG1) with "MY_ARGUMENT2" set as variable ARG2. Most of the time, you'll specify a section of the same PBAT script to be executed as the argument. 

In the called script, MY_ARGUMENT2 will be the first variable in the afformentioned called script, which can be recalled in said script with $ARG2$


### PBATS
To execute multiple PBAT scripts and pass variables.

```pbat
LOADEXEC "PBATS" "MY_*.PBT" "MY_ARGUMENT1" "MY_ARGUMENT2"
```

PBATS is usually used to call multiple scripts to print APPS,DEVS,THEMS,LANGS to screen as choices. In the called PBAT GOTO section will most likely be `ADDWIDGET "CALL"`...to pass ARGS back to this script.

In the called script, MY_ARGUMENT2 will be the first variable in the afformentioned called script, which can be recalled in said script with $ARG2$


### EEELF
To execute an ELF file and pass arguments.

```pbat
LOADEXEC "EEELF" "MY_FILE.ELF" "MY_ARGUMENT1" "MY_ARGUMENT2"
```

will execute MY_FILE.ELF with MY_ARGUMENT1 and MY_ARGUMENT2 passed to the elf should it support arg(v).


### IRX
To load a an IRX module. Most IRXs do not support arg(v).

```pbat
LOADEXEC "IRX" "MY_FILE.IRX"
```

will execute an IRX (device driver usually) to add functionality to BOOTMANAGER. Most IRXs do not support arg(v).


## **Wildcards**

- `*` wildcard(s)

- `?` single character wildcard

When used with conditions, be sure to set in first variable.

Also used often to call multiple PBATS via `LOADEXEC "PBATS"` to show apps/devices avaliable.

```pbat
IF MATCHES "SCPH-300*" "$BM.CONSOLE_MODEL$"
    MESSAGE "Console is SCPH-300XX"
ENDIF
```

## **Keeping Script in Memory**

### KEEP
Loads script in ram for quicker recall

```pbat
KEEP
```

### RETURN
Remove the script from memory if the return value is <0

```pbat
RETURN 0
```

### EXIT
Exit from the script (0 )and do not keep it in memory (-1)

```pbat
EXIT 0
```

### KILLSESS
I believe to exit a script and not keep in memory FROM another script that is currently "running". Reference BM/SCRIPTS/BMMENUS.PBT

```pbat
KILLSESS "$BM.SCRIPTS$/CONFMENU.PBT"
```

### SKIPBACK
When returning from a submenu, this menu is skipped(ie returns to the menu before this menu).

```pbat
SKIPBACK
```

## **Theme Specific**

### LOADIMG/UNLOADIMG
Load and unload an image for a theme

```pbat
LOADIMG "mc0:/BM/THMS/MYTHEME/IMAGE.BMP"
```


## **Pre-Defined Variables**

### PARSEPATH
To be able to recall specifc parts or whole path of script.

```pbat
PARSEPATH "$PWD$" "SRC_DEV" "SRC_PATH" "SRC_FILE" 
```

Will let you call Path working directory, source device, source path and source file.

Note: you can always call `$PWD$`, but the others require `PARSEPATH` to define and recall.


### Crystal Chip Info
- `$BM.MAJOR_VER$` - BootManager major version

- `$BM.MINOR_VER$` - BootManager minor version

- `$BM.PATCH_VER$` - BootManager patch version

- `$BM.CC_MAJOR_VER$` - Crystal Chip major version

- `$BM.CC_MINOR_VER$` - Crystal Chip minor version

- `$BM.BM_PATH$` - Path to root BM folder ie device:/BM Note there is no `/` included

- `$BM.SCRIPTS$` - Path to BOOTMANAGER scripts folder. Typically device:/BM/SCRIPTS Note there is no `/` included

- `$BM.DRIVER_PATH$` - Path to SHARED folder. Typically device:/BM/SHARED Note there is no `/` included


### PS2 Info
- `$BM.CONSOLE_MODEL$` - PS2 Console model IE SCPH-70012 (best model!)

- `$BM.CONSOLE_REGION$` - PS2 Console Region

- `$BM.BIOS_MAJOR_VER$` - PS2 BOOTROM major version

- `$BM.BIOS_MINOR_VER$` - PS2 BOOTROM minor version

- `$BM.ROMVER_REGION$` - PS2 BOOTROM Region

- `$BM.MECHA_REGION$` - PS2 Mechacon Region


## **Compatibility CMDs**

### SETAUTH
Set disc type forced authentication:

- `OFF`

- `PS1`

- `PS2`

```pbat
SETAUTH "PS2"
```

### SETBIOS
Set the bios pathes type:

- `OFF`

- `PS1`

- `PS2`

```pbat
SETBIOS "PS2"
```

### SHUTDOWN 
Shutdown portions of how Crystal Chips work:

- `ALL`

- `MM` - Memory Module

- `MMIOP` - Memory Module on IOP

```pbat
SHUTDOWN "MM"
```


## **Memory Manipulation**

### PEEK/POKE
`PEEK` = look at ram addreess and store as value, `POKE` = insert value at ram address.

`PEEKB`, `PEEKH`, `PEEKW`, `POKEB`, `POKEH`, `POKEW`

- `B` - Byte

- `H` - Half Word

- `W` - Word

```pbat
PEEKB "0x1F40200F" "MY_VAR_NAME"
```

Reference BM/DEVS/CDVD/DEVINFO.PBT

```pbat
POKEW "0x00101234" "0x12"
```


## **CDVD Commands**

### GETDISKTYPE
Gets disk type as hex value "0xXX"

```pbat
GETDISKTYPE "DISK_TYPE"
```

### PARSCNF
Parses CNF file on root of disk to store as variable. Reference BM/SCRIPTS/BMCONT.PBT

```pbat
PARSECNF "cdrom0:\SYSTEM.CNF" "BM.BOOT_TYPE" "BM.BOOT_NAME"
```

### CYCLETRAY
Causes the CDVD drive to recheck the disc. Parameters can be `WAIT`, `NOWAIT` or nothing (which is the same as `WAIT`). `WAIT` means "wait until disc has authenticated and fail if disc does not authenticate". `NOWAIT` returns immediately after telling the CDVD drive to reauthenticate.

```pbat
CYCLETRAY "WAIT"
```

### LOADSRAM
Used to pass PS1 logo check without displaying logo

```pbat
LOADSRAM "mc0:/BOOT/BM/PS1LOGO.BIN"
```

For BOOTROM 2.00 and lower (SCPH-700XX or earlier)

```pbat
LOADSRAM "mc0:/BOOT/BM/PS1LOGO2.BIN"
```

For BOOTROM 2.20 and greater (SCPH-750XX or later)


## **Reboot IOP and reload modules**

### REBOOTIOP
Reboot IOP and reload modules

```pbat
REBOOTIOP "rom0:UDNL rom0:OSDCNF"
```


## **Needs documentation and testing:**

SETENV - "SETENV" allows you to create a variable which are shared with all sessions: `SETENV "MY_SHARED_VAR" "My shared value"` DOES THIS STILL EXIST? 

### Found by running BM.ELF in PCSX2 and looking at memory.
Need to test these to document properly as they are not documented at all. Found in RAM by running BM2.ELF in PCSX2

`GETDVDREG`, `EXECCMD`, `CC`, `ILLEGAL`, `CDSTOP`, `GETDVDREG`, `BGCOLOR`, `SETBACK`, `SETEXIT`, `LIBLOADED`, `TOUCH`, `ADDMACRO`, `BOOT`, `DUMPIOP`, `DISCONNECT`, `FINDPAD`, `FINDCTP1`, `EXECMD`, `STABLE`, `ERROR`, `COMPLETE`, `FAILED`, `BUSY`


## **Debugging**

### Use ECHO and PS2 Client
When debugging paste ECHO where you want in the script. Then run PS2Client to see output via ECHO

```pbat
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
    ECHO ""
    ECHO ""
```


### PS2Client

Paste and edit this text into plain text file saved as LauchBM2.bat

```
ps2client -h 192.168.0.10 execee host:/BM/BM2.ELF
```

In the folder that has PS2Client, paste your BM folder

You can then edit the scripts, and reload menu on Crystal Chip BootManager to see your changes. I recommend to comment out scripts with KEEP for quick testing, though that may break things like PIN testing or adjusting Theme Configurations.