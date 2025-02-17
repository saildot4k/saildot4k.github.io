# Overview

In Progress as of 2/14/2025

![Crystal Chip QR Code](https://ps2modchiptutorials.com/crystal-chips/Crystal_Chip_QR_Code.png){ width="270" align=left }

If you happened to come to this page due 
to this sticker then I thank you very much! 
Please email me [here]<info@ps2modchiptutorials.com> so that 
we may discuss futher.  
<br>
<br>
<br>
<br>  
## Features:

  * Dashboard (aka BootManager) with configuration and app launcher/installer  
  * Dashboard is fully scriptable by end user  
  * v1.0 - v1.2 Dashboard is ran from memory card 1 or 2, or hard drive  
  * v2.0 Pro and v2.0 Pro SLE Dashboard is ran from on chip flash  
  * Firmware and Dashboard scripting is open/documented. Closed source dahsboard and FPGA.

## Crystal Chip versions

???+ note
    
    All versions retain same functionality EXCEPT v2.0 PRO and v2.0 PRO SLE can boot the dashboard "BootManager"
    from it's internal dataflash storage. Full install of BootManager takes 875KB. If there is more storage avaliable,
    more apps can be installed to Crystal Chip Flash. Keep in mind if an app expects other files in the root directory
    of the application folder, it will not be able to use those files. For example WLE will not see IPCONFIG.DAT nor 
    LAUNCHELF.CNF

    !!! note
        
        v1.2 and later can be upgraded with 4MB dataflash: AT45DB321D-S or AT45DB321D-MW. I have several dozen in stock.
        v1.2 then would need to flash the 2.0 firmware.  Eventually I shall script to ask user if they have installed the larger dataflash.
        Go to BM/FWS/LATEST delete all but "FWARE20.CCI". Rename to "FWARE12DEV0.CCI". Then upgrade firmware choosing option 1.
    
![Crystal Chip Models](https://ps2modchiptutorials.com/crystal-chips/cc-site-backup/img/cc_hw_history.gif){ align=left }

