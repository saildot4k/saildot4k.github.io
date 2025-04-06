# Matrix PicFix


Why? In an attempt to curb piracy, $ony designed the laser to fail and burn up. Sadly this [backfired](https://www.gamesindustry.biz/sony-reaches-settlement-in-ps2-disc-read-error-case#:~:text=Now%20a%20settlement%20has%20been,their%20console%20%2D%20at%20SCEA's%20discretion.)

![Mermaid Chart](assets/picfix/whylaserburns_mermaid.jpg)
Courtesy of [El Isra](https://github.com/israpps)

Invented by the Matrix Team, they designed a cheap and easy fix for V9-V12 PS2s, documented [here](https://github.com/MechaResearch/MechaPwn/blob/master/docs/PICfix.md) and refined by HaloSlayer255 and [ModzvillUSA](https://modzvilleusa.com/products/ps2-matrix-picfix-for-v9-v12-ps2-consoles)


I (R3Z3N) simply applied some artistic touch to make this an easier install that will look professional with decent soldering skills. CLEAN YOUR FLUX BOYS!


### $ony Laser fix identification

If your PS2 is the following model with the circutry in red, you DO NOT NEED THIS FIX!

![Sony Laser Fix](assets//picfix/70k%20laser%20fix.jpg)

### Mechacon Crash Tester App

El Isra made a PS2 app which identifies if your console is safe, unsafe or uknown. Run the ELF on your PS2 with your desired exploit/elf launcher of choice:

[Mechacon Crash Tester](https://github.com/israpps/MechaconCrashTestAPP)

![Mechacon Crash Tester](https://www.psx-place.com/attachments/_e3271012_20240808144428-png.43804/)

## Appreciation and Thanks to:
[Atheris](https://linktr.ee/atherismods), [SylverRez](https://github.com/m4x10187) and [PCM720](https://github.com/pcm720) for kicad, electrical and logo help!


## Parts Needed

[100nF 0603 Capacitor](https://www.mouser.com/c/passive-components/capacitors/ceramic-capacitors/mlccs-multilayer-ceramic-capacitors/multilayer-ceramic-capacitors-mlcc-smd-smt/?capacitance=0.1%20uF&case%20code%20-%20in=0603&length=1.6%20mm%20%280.063%20in%29&termination=Standard&tolerance=10%20%25&voltage%20rating%20dc=25%20VDC&width=0.8%20mm%20%280.031%20in%29&instock=y&sort=pricing)

[1.5K Ohm 0603 Resistor](https://www.mouser.com/c/passive-components/resistors/smd-resistors-chip-resistors/thick-film-resistors/?case%20code%20-%20in=0603&packaging=Cut%20Tape&power%20rating=250%20mW%20%281%2F4%20W%29~~333%20mW%20%281%2F3%20W%29&resistance=1.5%20kOhms&tolerance=5%20%25&instock=y&sort=pricing&rp=passive-components%2Fresistors%2Fsmd-resistors-chip-resistors%2Fthick-film-resistors%7C~Power%20Rating)

[2.2K Ohm 0603 Resistor](https://www.mouser.com/c/passive-components/resistors/smd-resistors-chip-resistors/thick-film-resistors/?case%20code%20-%20in=0603&packaging=Cut%20Tape&power%20rating=250%20mW%20%281%2F4%20W%29~~333%20mW%20%281%2F3%20W%29&resistance=2.2%20kOhms&tolerance=5%20%25&instock=y&sort=pricing&rp=passive-components%2Fresistors%2Fsmd-resistors-chip-resistors%2Fthick-film-resistors%7C~Power%20Rating)

[PIC 12F508 IC SOIC-8 Package](https://www.mouser.com/ProductDetail/Microchip-Technology/PIC12F508-I-SN?qs=mcPJWgAPNrfwaHSjpX90MQ%3D%3D)

Pic 12F508 files, choose based on your programmer:

[MFIX_H8.HEX](assets/picfix/MFIX_H8.HEX)

[MFIX_H16.HEX](assets/picfix/MFIX_H16.HEX)

## Programming PIC12F508

### Tools needed:

[:material-cloud-download: PicKit 3 Programmer Software 3.10](assets/picfix/PICkit3%20Programmer%20Application%20Setup%20v3.10.zip)

[PicKit 3](https://www.amazon.com/Gosono-PICKIT3-Programmer-Programming-Universal/dp/B07D1443M5/ref=sr_1_13_sspa?crid=2T75QRA5FHZDI&dib=eyJ2IjoiMSJ9.YevQ8Jf0hTdiqUtSofPn9aQN35WtDal5rQHtHAFc6W6zPtKX7LZky4ZC4m7z0KeY4cNpvX01FMz3HNMwouxwub8csjFjD9uYDBTkE64VUWVNeYa04OkCtY0yMC2nACelf_7Pds0z8L1rZAVKml-Fwa30i4t2NcAAz7WRm42R9LkCOD7E9C9_T-O29B3sPvp6PsSdu0bl8Sk6yJUrMsRmwG_sO0rW3--F4y-m-c3-yz0K-RKAwMMX_ku8yTvkcpJDp4EF4ZLvntKw00hqDq99cTU0GSktjWLmtCuqmOnOFms.ss9JZldEX7IeF-1XSAfcpQwL7uqoHXkjZLyh78jlaFI&dib_tag=se&keywords=pic+kit+3&qid=1743917759&s=industrial&sprefix=pic+kit+3%2Cindustrial%2C150&sr=1-13-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9tdGY&psc=1)

[SOP8 to DIP8 adapter](https://www.amazon.com/HiLetgo-Programmer-Adapter-Socket-Converter/dp/B01HTC5DKS/ref=sr_1_5?crid=2UBCL6KVM78KW&dib=eyJ2IjoiMSJ9.0YtQZfQXY8SM_my4pw3Wp7w_zM3WItFnLhs9jBkH_YEiGTXrB2-ZpUPMZmPnI1jAVSFudzCoLeNbiC6bhV8jo7jxFkhXp56jsdliK5SHjxIiMoIzB6rlV0wtNVJK131NK7ugAmFtRJhUxqYojQtj03JX2azkew_zxVkDBT6VF1XI92JY-7Ke3ZO0HRRKYnvsgWPPfRszVEBvGCW9Fc6_lbPPJtGS76fkVCN2C-hGDfQ.N9zJPfDjsMyo4oBLfYXw0N8hqByAffVQ5wub2oZIM-U&dib_tag=se&keywords=soic+adapter&qid=1743917897&sprefix=soic+adapter%2Caps%2C180&sr=8-5)

Tutorial incoming....sorry. If you'd like to help please reach out!


## Flex PCBs

### SCPH-700XX Flex PCB

Gerbers will be released once a small batch of 52 is sold! 300 PCBs ordered. If you are an installer and would like a sample, please let me [know!](mailto:info@ps2modchiptutorials.com)

![V12 Flex Front](assets/picfix/SCPH-700XX/PicFix_V5_Thin.png)

![V12 Flex Front](assets/picfix/SCPH-700XX/PicFix_V5_Thin%20back.png)