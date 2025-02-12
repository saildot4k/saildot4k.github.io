Infinity option configuration menu :
------------------------------------

Press TRIANGLE + CIRCLE to enter the configuration menu.


PS2 SCREEN FIX   : OFF    : Disables PS2 video fix.

                   COLOR  : Games will be output on their original video mode (PAL/NTSC)
                            with color correction applied to match your PS2 region.

                   PAL    : Force video mode to PAL

                   NTSC   : Force video mode to NTSC

                   PAL60  : Force all games to NTSC with color correction.
                            Games will run faster but screen might need adjusting.

                   VGA    : Enable 640x480 VGA mode.

Y SCREEN FIX     : OFF    : Y screen position fix is disabled.

                   AUTO   : Y position fix enabled with default settings.
                            Should be fine for most television sets. 

                   +/- N  : Fine tune Y position.
                            Positive values move the screen down, Negative values move it up.

PSX SCREEN FIX   : ON/OFF : Enable/Disable PSX screen fix

PSX MULTI DISK   : ON/OFF : Enable/Disable PSX multi disk support

MC16 PATCH       : ON/OFF : Enable/Disable D4TEL memory card support

ATAD AUTO PATCH  : ON/OFF : Enable/Disable ATAD auto patch

MACROVISION FIX  : ON/OFF : Enable/Disable Macrovision patch

GREEN FIX        : ON/OFF : Enable/Disable green correction on DVD movies

DVD VIDEO REGION : 1..8   : Selects the DVD player region.
                            Use it to match the corresponding region on RCE protected discs.

DVD9 DL SUPPORT  : ON/OFF : Enable/Disable Double Layer patch

BOOT MODE        : AUTO   : Normal behaviour. All discs wil autoboot.

                   FAST   : FastBoot.
                            Same as pressing SELECT on boot.

                   INFMAN : Execute Infinity Manager on mc0:
                            Same as Pressing TRIANGLE on boot.

                   DEV1   : Execute BOOT.ELF on mc0:
                            Same as Pressing R1 on boot.
 
                   DEV2   : Execute BOOT.ELF on HDD
                            Same as Pressing L1 on boot.
 
                   DVDV   : Force DVD video mode.
                            Same as Pressing CIRCLE on boot.

PAD DETECT TIME  : 2..10  : Select time to wait for connected pad on boot.
                            Only useful if pad is left unconnected.

BOOT LOGO        : ON/OFF : Enable/Disable Matrix boot logo.




BURNING TO CD:
--------------

- Create a directory on your desktop or other location of your HD.
- Unzip the ".cue" and ".bin" files present inside the .zip file into this directory.
- Open your preferred burning program (Nero, alcohool120%, etc etc.) and choose
  option to burn a "CD-ROM ISO".
- Press the file selection button and choose file type "Image Files (.cue)".
- Navigate to the directory where you unzipped the V1.93 files and select the 
  "infv193.cue" file.
- Burn the CD.


UPGRADING INFINITY:
-------------------

- Insert the burned CD into the PS2 and press reset.
  The CD should boot authomatically and you will be presented with the Upgrade sreen.
- Follow instructions on screen to upgrade Infinity.


**********************************************************************************

- NOTE  : You can always recover from a bad flash by entering recovery mode.
  ====    This will let you boot the upgrade disc to reflash your Infinity.

          To enter recovery mode:

          V1-V12 and V14 PAL :
          ====================

          Hold the reset button until the blue eject light turns on.
          

          V14+ USA and JAP
          ================

          USA : Hold reset until blue eject lights turn on, wait 3 seconds and
          tap reset again.

          JAP : Hold reset until blue eject lights turn on, wait 3 seconds and
          tap reset, wait 3 more seconds and tap reset again.

**********************************************************************************


STANDARD OPERATION FOR THE MATRIX INFINITY:
===========================================

BOOT OF PS2 / PS1 / DVD MOVIES: 
-------------------------------

- Insert the disc inside the PS2.
- The infinity will recognize the kind of disc you inserted and select
  the appropriate boot system.


TURNING OFF THE INFINITY:
-------------------------

- Press START on joypad 1 until the writing "DISABLED" will appear on screen. 
- Press reset once.
- The Infinity is now disabled until PS2 is turned off to Standby Position.


FAST BOOT OF PS2 GAMES: 
-----------------------

- Press SELECT on joypad 1.
- PS2 Logo will be skipped and game will boot directly.


FORCING PS1/DVD MODE: 
---------------------

- Press CIRCLE on joypad 1.
 (This option is only needed just in case someone needs to force the PS2
  to boot in PS1/DVD mode).


FORCING AUTO MODE: 
---------------------

- Press CROSS on joypad 1.
  Useful to temporarily skip the default boot mode when set to something
  other than AUTO.


LAUNCHING MEMORY CARD APPLICATIONS:
-----------------------------------

- Press TRIANGLE on joypad 1.
- If installed, the Infinity Manager will appear and show a list of
  installed applications.

  -or-

- Press R1/R2/L2 on joypad 1.
- This will launch the following applications according to the button pressed :
  
  R1 : "mc0:BOOT/BOOT.ELF"
  R2 : "mc0:BOOT/BOOT2.ELF"
  L2 : "mc0:BOOT/BOOT3.ELF"


LAUNCHING HDD APPLICATION (DEV2 MODE):
--------------------------------------

- Press L1 on joypad 1.
- If correctly installed, the default application will be executed from the HDD.



**********************************************************************************

VGA MODE
--------

To use your PS2 in full VGA glory you will need a compatible VGA monitor and an
external VGA adapter (either an original Blaze adapter or an homebrew one).
Before enabling VGA mode in the configuration screen, test the adapter and
the monitor with the original vga software to make sure they are working properly.

NOTE : If you enable VGA mode in the config screen and your adapter or monitor is
       not working properly, you will be stuck with a black screen. To return to
       the normal functionality just reflash your infinity using recovery mode.
       Read "UPGRADING INFINITY" section in this text file  for instructions on
       how to enter recovery mode and reflash your infinity.
