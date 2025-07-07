============================
ChangeLog for DMS3 Hardware:
============================

Plus (2004-06-30)
------------

 * Reduced wire count
 * Compatible with V1-V10 consoles from Japan/Asia, Europe/UK and USA/Canada.
 * Eliminated GND bounce problems which affected some V3, V4 and V9 consoles.
 * Faster and more reliable flash upgrade process, 97% success rate on first attempt.
 * DVD-RW and +RW require 1 wire extra to be soldered.


v9 (2003-11-16)
------------

 NOTE: This version is only compatible with model numbers that begin with 500xxx, aka v9 and v10 consoles.

 * Internal logic got redesigned
 * Works now even more reliable and more stable as before


v2.0 (2003-03-18):
------------

 * Removes the v8 DVD-R check (DVD recordable protection)
 * Fixing disc authentication for incorrectly mastered PS2 discs (some DVD Rips)


v1.0 (2003-02-17)
------------

 * Initial release, first batch came with a upgrade CD that upgraded the flash to v1.1


 ------------

 DMS3 operation and configuration tips
Note: Configuration Menu is only supported in flash version 2.0 or higher. Dev.olution Mode 2 is only supported in flash version 1.8 or higher.

DMS3 Startup Modes:
!(dms3_controller-modes)[assets/dms3_controller-modes.jpg]

PS2 - X
PSX - O - Circle
DVD - # - Square
DEV1 - /\ - Triangle - Load DMS3 Explorer from memcard
DEV2 - START - Load DMS3 HDD Explorer from HDD

Fast Boot:

Hold SELECT upon startup

Stealth Mode/Disabled - Audio Mode:

Hold eject for more than 1 second

Flash Upgrade Disc:

L1+L2+R1+R2 - Erase upgraded flash block, overwrite with factory firmware

Boot Factory Flash:

3 x Reset - Press reset 3 times, once every time the eject and reset lights up - Temporarily reverts back to original DMS3 firmware

Configuration Menu:
(Credit to dms forum)
Default Boot:

devolution 1 -> dms explorer v1 (mc version)
devolution 2 -> dms explorer v2 (hd version)
Normal -> need explaining? (start the mod into ps2 mode with the normal ps2 boot screen)
Fast boot -> like normal but this make the ps2 boot screen don't showing up and going directly to the game
MM16 Enabled:

ON -> you can use the mega memory 16 card (from datel) without booting the games with megamemory manager (from datel and with the card)
OFF -> you can't use the megamemory 16 card without booting the games with megamemory manager
PS2 Video Fix Colour:

None -> what is outputted from the game itself (ntsc for ntsc games, pal for pal games
colour carrier -> change only the color so without a multi standard tv but with a tv capable to don't rolling the image you can see color and have the original resolution and HZ of the original game
video mode -> change the mode into the native mode of the console (pal for pal console, ntsc for ntsc console) this is like pacthing games with pacthing utilities and then burning it
PSX video fix enabled:

on -> activates the video fix also for psx games and not only for ps2 games
off -> deactivates video fix also for psx games

ATAD auto-pacth enabled:

In order to use a non-Sony HDD with HDD-enabled games, you must first enable the ATAD auto patching.