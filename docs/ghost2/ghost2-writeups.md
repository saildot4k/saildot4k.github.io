## BOOT MODE FOR G.2


Tap RESET button on PS2 a number of times after power up. The modes are as follows:
(from STANDBY, when the LED on reset button is RED)

1. Default mode - with autodetect and all features on. This is the only mode users probably will ever need except recovery mode which has to be entered at least once to program eeprom.

2. Ghost mode - the same as above (1) but switches chip off when the game is loaded. This is to be compatible with some utilities such as RegionX, players etc. When you load for example RegionX disk and you're asked to insert movie disk to play, the chip is already off at that time and when you put the disk the machine will not detect it as ps2disk - the mod chip is off (in sleep state). It will be activated every time you press the RESET button, but only to load the game, then it goes to sleep again. This mode is enabled in sw so we can reprogram it to anything else later on if needed.

3. Chip off - switches mod chip off completely, ps2 behaves as it has not been modified.

4. Flash upgrade - the same as (1) but enables write to EEPROM - in all previous modes any write/erase/modify operations are not possible because EEPROM is hardware write protected. We use it during development to reprogram EEPROM via network adaptor or USB.

5. Recovery mode - used to program EEPROM for the first time (blank EEPROM), to reprogram it if corrupted etc. This mode doesn't apply a single patch to cdvd nor bios bus, that's why it is possible to reprogram EEPROM when it's not usable. User doesn't need to do anything - just enter recovery the mode, put the recovery CD and wait for the recovery process to complete. Please note - as there are NO PATCHES applied to ps2 in recovery mode we have to use 2 version of recovery disk - one for Jap region, and one for PAL region. This is because Japanese and PAL ps2 check for "Licensed by.." string when load PSX disk (and in this case the recovery disk as a PSX disk for ps2). American machines don't do this check by some reason so you can use either Jap or PAL recovery CD. It doesn't matter which one to use as there's no differences in EEPROM file. So customers will need to download ISO image of recovery disk for either JAP or PAL region, Americans can use either of them.

It might look complicated, but it's not :). As we stated above the only mode you need is (1) - just power up your machine normally by pressing RESET or EJECT. PS2 will remain in ANY of those modes until you go back to STANDBY or switch off the power. The modes can be changed ONLY from STANDBY - afterwards you can tap and press whatever you like, as many times as you like and it will not change the mode.

From STANDBY, when you press RESET the machine is switched on and you have 2 seconds to tap RESET again after the BLUE LED turns on. When you tap RESET again the BLUE LED goes off and when it turns on again you've got 2 seconds to tap RESET if needed, etc…

| Mode          | Number of Reset Taps |
| :-----------: | :------------------: |
| Default       | 1                    |
| Ghost         | 2                    |
| Chip Off      | 3                    |
| Flash Upgrade | 4                    |
| Recovery Mode | 5                    |

EXAMPLE1: to switch CHIP OFF you need to:

From STANDBY >> RESET (wait for blue led on), RESET (wait for blue led on), RESET (in 2 sec you're in the mode)

EXAMPLE2: to enter RECOVERY mode:

From STANDBY >> RESET (wait for blue led on), RESET (..), RESET (..), RESET (..), RESET (in 2 sec you're in the mode)

???+ note "PSTwo Slim"

    For v12+ (SCPH-70k+) : You can use the Green Led as Timing Indication since there is no Blue Led anymore on this sytem.


## Boot Hotkey options:

![G2_Hotkeys](assets/G2_Hotkeys.png){ width="800" }


- L1 = Force Games to load in PSX mode (if you want to skip auto-detect,
when you know the disk is PSX format).
- R1 = Fast Boot for PS2 disks (skips PS2 Logo).
- TRIANGLE = Ghost2 Manager - Ghost2 Manager must be installed and a memory
card must be present in slot 1.
- O = Dev Mode (starts file boot.elf).
- X = Override Dev Mode (if it's been selected as default mode in GH2 Manager).
- Arrow UP = load boot0.elf from memory card 1.
- Arrow RIGHT = load boot1.elf from memory card 1.
- Arrow DOWN = load boot2.elf from memory card 1.
- Arrow LEFT = load boot3.elf from memory card 1. 

## Issues

Use FW 1.31 and G2 Manager 1.30. 2.22 never had a released G2 manager that works...

Use PS2 in RGB video out else accessing PS2 Browser (OSDSYS) has no video output.