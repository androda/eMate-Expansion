[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)

<img align="right" width="400" height="215" src="https://github.com/androda/eMate-Expansion/blob/main/DRAM_Plus_Flash/Images/ModuleFront.PNG?raw=true">

# Overview
This project encompasses two different types of upgrades for the eMate 300.  One of them is DRAM_Only and does not increase program storage space.  The other is DRAM_Plus_Flash, which increases system RAM and flash storage space for programs.

Both modules increases System RAM from 900k to about 3900k.

The "Plus Flash" style increases Internal Storage from about 1600k to about 3600k.

See the Images folder, 'emate without expansion' and 'emate with expansion' images.  Your exact System Memory and Internal Storage amounts will differ slightly based on current usage, installed applications, etc.

# Caveats
On my tester eMate, after installing and removing these upgrade modules several times it now presents me with an error saying "This unit requires immediate repair.  Factory calibration data has been lost.  It will not charge batteries until this is resolved."  This error message has not prevented me from using the device normally, though it's correct that the battery does not charge.

This error message seems to have a variety of causes which are not well understood, and will be the subject of a project later on to try and resolve the error.  [This thread on NewtonTalk](https://web.archive.org/web/20220817134007/https://marc.info/?l=newtontalk&m=152884887314832&w=2) mentions that the calibration data is stored in a part of the flash memory which is not normally erased.  We probably need a tool to back up and restore the calibration data because flash memory does not store data forever, and the calibration data will eventually wear out.

# ! Important Notes !
Remove all power sources from your eMate before installation.  Ideally, remove the power adapter and battery several hours before installing the module.  This gives time for any internal capacitors to drain.

On initial powerup after installation, your eMate will *fully erase all internal storage* !  This is normal and expected.  This rease and reset takes a few minutes, so leave your eMate plugged in and undisturbed.  It'll start up once the process is complete.

Removing the module in the future will cause the same behavior, a full reset.  *You must back up your data before installing or removing the module!*

# License
This work is licensed under a
[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-nc-sa/4.0/).

# Schematics
The schematics are available to download in their respective folders.

# Bill of Materials
 * PCB is 1mm thickness
 * 2x `MT4LC4M16R6-5S` (or lower latency versions of these chips).  -S suffix is required!
 * 1x `E28F016SV` (larger storage densities may be supported but have not been tested)  <-- Not used on DRAM_Only style
 * 5x Ceramic Capacitor (0603 footprint) : Note that the value of these capacitors is not extremely important.  Prototypes were assembled with 4.7uF capacitors, and it is likely that values of between 100nF and 10uF will work properly.

# Notes
* The DRAM_Only module has been tested to install and remove without causing a full system erase like the Plus Flash style
* The DRAM_Plus_Flash module has been tested to boot in an eMate and shows the increased RAM and Storage amounts.  Not much additional testing has been done - would be good to install a bunch of software to use some space on the flash and be sure that it's working.
* There are some differences between these Micron RAM chips and those on the original upgrade module.  These chips are EDO and 64 megabit, compared to the original chips being FPM and 16 megabit.  The eMate only sees the amount of RAM which the original upgrade gives - not the full 64 megabits per chip.
* The CL-PS7010 RAM interface chip used by the eMate is, interestingly, the same as used by the Newton 2100.  The 2100 comes with EDO RAM chips.  There is no datasheet available for the CL-PS7010 - I believe it's an Apple-custom part.  However there is a datasheet for its cousin the [CL-PS7110](https://github.com/androda/eMate-Expansion/blob/main/Datasheets/CL-PS7110.pdf), which appears to basically be the combination of the eMate's ARM710 chip and the original CL-PS7010.  Thie chip supports lots of RAM, and it may be possible to poke a configuration register in the 7010 to see more RAM - but methods for doing that will require investigation

# Credits
Special thanks is owed to the following:
1. Colin from [This Does Not Compute](https://www.patreon.com/thisdoesnotcompute/) ([YouTube](https://www.youtube.com/channel/UCEp20NgOZHmgWdbQdHSxgjw)) for loaning the eMate Expansion for reverse engineering.
2. Stephen Arsenault, for performing the reverse engineering work on the original module
3. The [Open Retro SCSI Discord Server](https://discord.gg/5AtypUqFCT) for fostering community development on retro hardware.
