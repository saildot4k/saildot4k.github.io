# Toxic OS App Installation (DMS4 Pro / DMS4 SE Pro)
Temporarily copied from dreaded [PS2-Home](https://www.ps2-home.com/forum/viewtopic.php?p=18198&sid=3a2efd97958e065dc1ed8932217f37be#p18198)

You need to create an install script that ToxicOS can use to install your apps.

Each script contains a list of applications, each application entry having information and directions for installation and optionally un-installation associated with it.

Each application entry is made up by placing information inside tags. Most tags are required however some are optional.

## Install Script Example

```
[APP]
[HEADER]
[TITLE]
MY APP TITLE
[/TITLE]
[EXEC]
/APPFOLDER/MY_APP.ELF
[/EXEC]
[/HEADER]
[INSTALL]
_MKDIR /APPFOLDER
COPY /APPFOLDER/MY_APP.ELF /APPFOLDER/MY_APP.ELF
[/INSTALL]
[UNINSTALL]
REMOVE /APPFOLDER/MY_APP.ELF
_RMDIR /APPFOLDER
[/UNINSTALL]
[/APP]
```

## Headers
Each application entry starts with `[APP]` and ends with `[/APP]`. Each entry must have a `[HEADER]` and `[INSTALL]` section both of which must have a closing tag `/`. The `[UNINSTALL]` section is optional but recommended.

The following fields are placed inside the `[HEADER]` section:

- `[TITLE]` : Title/name for the application - REQUIRED!

- `[EXEC]` : Path of executable once installed - REQUIRED!

- `[AUTHOR]` : Name of author(s) responsible for the application - optional.

- `[DESC]` : Description of the application - optional.


## Actions
Inside the `[INSTALL]` or `[UNINSTALL]` sections you place the actions required for that operation. The old HDD Explorer scripts required that each action be specified inside an `[ACTION]` tag, however this is not required with the ToxicOS scripts - just place one action per line.

Supported actions are as follows:

- `COPY [source] [dest]` - Copy the source file to the path specified by dest.

- `REMOVE [file]` - Remove a file.

- `MKDIR [dir]` - Make a directory.

- `RMDIR [dir]` - Remove a directory.

## Action Fail
When a `_` charater is added to the start of the action, i.e. `RMDIR` becomes `_RMDIR`, then if that action fails the installation process will continue. Otherwise if an action fails the installation process will fail and ToxicOS will give an error.

Filenames specified in an installation script are not absolute, they are relative to a certain location. This location depends on where the application is being installed to (memory card or HDD) or from. You do not need to be concerned with where files end up on the memory card or HDD, but note that when specifying a source file in the install section, that file is relative to the directory where the installation script is stored.

ToxicOS allows whitespace in installation scripts as well as comments. Any text after a # character is treated as a comment.