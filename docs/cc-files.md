## R34 V3 Firmware and Dashboard by R3Z3N

[Crystal Chip FW R34 v3 with updated Dashboard Scripts](https://github.com/saildot4k/Crystal-Chip-R34-v3/releases)

Additions since 2007:

Release 34 V3 by R3Z3N Jan 26 2025 (RUNNING CHANGES. I update the date as I go...)
    Fixes/Changes
        - CC1.X firmware options to run BM from MemCard1 or 2. makeit_nocd does have scripts to
	      build FW for running from USB/HDD but seems pointless. Options added in BM for full ease
              of use.

        - MMCE device support for example SD2PSX, PsxMemCardGen2, MemCardPro2.
              Follow the same structure on root of MMCE device SD card as 
              one would for the BM folder. As long as APPINFO.PBT (each app needs one)
              points to where the ELF exists, then any app can be anywhere, not just
              device:/BM/APPS/APPFOLDERHEREwithAPPINFO.PBT
	      UPDATE: A few issues still exist. Keep in mind not all apps support running
	      from all devices. However I plan on making a change so that user can choose 
              to autoload USB and/or MMCE just like HDD is currently. Please be patient. 
              REASON: sometimes some device drivers interfere with others especially USB
              with other devices.
	      https://sd2psxtd.github.io/

	- Security Settings added: when pin is set, advanced settings are unaccessible. 

        - Updated bminit.pbat to load IRX drivers from where BM is running from,
              otherwise with DEV1/2 would not see/run apps from mc0/1/USB/HDD.
	
        - Updated source OSDPAY.S to load USBHDFSD.IRX instead of the outdated
              USB_MASS.IRX. Booting from Dev2 (USB) is still broken
	
        - Updated HDDMOUNT.IRX and BM/SCRIPTS/HDDLOAD.PBT to load __common HDD partition
              instead of +Crystal. This is to keep things consistent with the homebrew community
	
        - Edited BM/FWS/LATEST/FWINFO.PBT to give FW boot choices as to where to load BM from
	
        - Commented out install script for USB FW as currently not working.
              Others can experiment as needed by editing BM/FWS/LATEST/FWINFO.PBT
	
        - Used El Isras USB drivers for exfat support: BDM Assault (https://github.com/israpps/BDMAssault)
  	
        - Changed scripts to allow apps to be installed when booted from recovery cd.
  	
        - Changed scripts to only show options for chip installed! IE no more seeing DFFS
              options on CC 1.0 and 1.1. 1.2 no longer shows remove dffs:/BM
 	
        - Changed scripts so that FW choices are only applicable to the chip installed.
              IE CC1.0-1.2 can choose BM run point, CC2.0 DFFS only.
       
        - Show Info gives a little more clarity IE where is BM executed from, what console region codes stand for etc.

	- Cotton Candy theme added, each version of the Crystal Chip is represented!

	- Added Italian and Spanish language translations.


## APPINFO.PBT Example
Example APPINFO.PBT

