[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)

<img align="right" width="400" height="215" src="https://github.com/androda/eMate-Expansion/blob/main/Images/ModuleFront.PNG?raw=true">

# Overview
This Newton eMate 300 Memory Expansion Module increases System RAM from 900k to 3900k, and Internal Storage from about 1600k to about 3600k.  See the Images folder, 'emate without expansion' and 'emate with expansion' images.  Your exact System Memory and Internal Storage amounts will differ slightly based on current usage, installed applications, etc.

# ! Important Note !
On initial powerup after installation, your eMate will *fully erase all internal storage* !  I don't know why, but on initial installation of the module your eMate will automatically perform a full hard reset including loss of all installed programs and data.  After this, your eMate will behave as normal (but you have to reinstall everything).  The erase and reset takes a few minutes.
It's likely that removing the module after installation and reset will perform the same operation, erasing all storage to return to factory state.

# License
This work is licensed under a
[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-nc-sa/4.0/).

# Schematics
The schematics are available to download in [PNG Format](https://github.com/androda/eMate-Expansion/blob/main/Schematics/Schematic.png)

# Bill of Materials
 * 2x `MT4LC4M16R6-5S` (or lower latency versions of these chips).  -S suffix is required!
 * 1x `E28F016SV` (larger storage densities may be supported but have not been tested)
 * 5x Ceramic Capacitor (0603 footprint) : Note that the value of these capacitors is not extremely important.  Prototypes were assembled with 4.7uF capacitors, and it is likely that values of between 100nF and 10uF will work properly.

# Notes
* This module has been tested to boot in an eMate and shows the increased RAM and Storage amounts.  Not much additional testing has been done - would be good to install a bunch of software to use some space on the flash and be sure that it's working.
* There are some differences between these Micron RAM chips and those on the original upgrade module.  These chips are EDO and 64 megabit, compared to the original chips being FPM and 16 megabit.  The eMate only sees the amount of RAM which the original upgrade gives - not the full 64 megabits per chip.
* The CL-PS7010 RAM interface chip used by the eMate is, interestingly, the same as used by the Newton 2100.  The 2100 comes with EDO RAM chips.  There is no datasheet available for the CL-PS7010 - I believe it's an Apple-custom part.  However there is a datasheet for its cousin the [CL-PS7110](https://github.com/androda/eMate-Expansion/blob/main/Datasheets/CL-PS7110.pdf), which appears to basically be the combination of the eMate's ARM710 chip and the original CL-PS7010.  Thie chip supports lots of RAM, and it may be possible to poke a configuration register in the 7010 to see more RAM - but methods for doing that will require investigation

# Credits
Special thanks is owed to the following:
1. Colin from [This Does Not Compute](https://www.patreon.com/thisdoesnotcompute/) ([YouTube](https://www.youtube.com/channel/UCEp20NgOZHmgWdbQdHSxgjw)) for loaning the eMate Expansion for reverse engineering.
2. Stephen Arsenault, for performing the reverse engineering work on the original module
3. The [Open Retro SCSI Discord Server](https://discord.gg/5AtypUqFCT) for fostering community development on retro hardware.
