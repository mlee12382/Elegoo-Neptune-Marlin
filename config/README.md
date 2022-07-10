## Disclaimer

The code within this repository comes with no guarantee; the use of this code is your responsibility.

I take NO responsibility and liability for how you choose to use any of the source code available here. By using any of the files available in this repository, you understand that you are AGREEING TO USE AT YOUR OWN RISK.

These configurations have been ported from Trey Wentz 2.0.93 firmware and updated to the current version of Marlin. Original files can be found [here:](https://github.com/just-trey/Marlin/tree/elegoo-neptune-2/). 

# Marlin 2.1.1 - Color UI and LVGL UI - 3D Printer Firmware compiled for Elegoo Neptune 2 / 2S /2D

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

**Note:** The configuration and compiled versions are available in this bundle. 

This is a package of Marlin 2.1.1 bugfix configurations for the Elegoo Neptune 2, Elegoo Neptune 2S, and Elegoo Neptune 2D. The source is a fork from [Marlin 2](https://github.com/MarlinFirmware/Marlin/releases). 

These files are provided as opensource under the same [GPL v3](https://www.gnu.org/licenses/gpl-3.0) license as Marlin 2.

# What are the features I get from using this?

All versions provided come with these features.

1. A safe version of alternative firmware.
   - I found a few configurations online and in repos that were not appropriately configured (Thermal runway protection was off or busted) 
2. An alternative UI
   - Not as "pretty," but much more helpful
   - Update many configuration values (including ESTEPS) right on the screen
   - PID Autotuning for the nozzle AND bed from the UI. 
3. [S-Curve Acceleration](https://github.com/synthetos/TinyG/wiki/Jerk-Controlled-Motion-Explained)
4. Adaptive Step Smoothing
5. ARC Support Enabled
6. **M600** Change filament at layer.
7. The screen will update if you are printing from Octoprint.

BLTouch versions also include:
1. Z Level Offset Wizard
2. **Live Z** Support
3. Bed tramming wizard option (I mean, you still need to level every once and a while)

# Do I lose any features if I use this?

The following items are not supported with ColorUI:

1. If you have a WIFI Card, it WILL NOT WORK (MKS made that call, not me) 
2. Power loss detection does not work (MKS made that call, not me) 
3. Icon Previews do not exist in UI (Feature not available in the stock marlin color UI)

## NOTE: LVGL seems to be broken and unusable based on feedback I have received so far, I am only leaving the files up in case someone wants to play around with it and try to make it work themselves, I am not recommending it's use at this point in time. :(
If you use LVGL versions of the firmware you will have fewer advanced features available from the touchscreen but you will retain WIFI add-on compatibility and Icon Previews. If you choose to use the LVGL firmware you will also need to download the assests folder and include it with the appropriate elegoo.bin file on the sd card when you flash the firmware or you will not have all the icons, etc.

# Setup and install

## Getting things ready

NOTE: I recommend you use an sd card 8GB or less Formatted as FAT32 for installing. Using anything larger has been an issue with some users. If you do not have one (you can use the card that came with the printer), this is the one I use [(non-affiliate link)](https://amzn.to/3JIOzYL)

1. If you have tuned your printer (especially e-steps), I highly recommend you connect and run an M503 and record your values. This process will erase any values changed from a stock install. 
2. [Download the latest version here](https://github.com/just-trey/Marlin/releases/latest/download/Neptune-2.zip).
3. Extract the zip file on your computer
4. Copy the desired `elegoo.bin` configuration to your SD Card. No other files are needed to install, with the exception of using the LVGL firmware in which case you will also need the 'assets' folder with the 140 .bin files inside. 
   
   ***NOTE:*** **IT IS IMPORTANT YOU KNOW THE VERSION OF THE ZNP ROBIN NANO BOARD YOU HAVE, AND YOU NEED TO USE THAT VERSION OF THE FIRMWARE**
  
   - The directory structure is as follows though slightly modified since there are now more options: 
     
     ![dir structure](https://user-images.githubusercontent.com/10281380/148702987-9dd38cbb-fac2-4b16-aa44-5f9b72192f2a.jpg)

   - All firmware and configurations for v1.2 boards are in the v1.2 directorys
   - All firmware and configurations for v1.3 boards are in the v1.3 directorys
   - All firmware and configurations for the 2S are in the v1.3 directorys
   - If you *DO NOT* have a BLTOUCH, use the file in the STOCK directory
   - If you *DO* have a BLTOUCH, use the file in the BLTOUCH directory
   - If you are using WIFI use the corresponding directory from the LVGL_UI folder with the WIFI tag, ie. LVGL_UI\v1.3\2S\BLTouch_WIFI\ in the case of a 2S with BLTouch and Wifi. ## SEE NOTE ABOVE: USE AT YOUR OWN RISK, NOT WORKING PROPERLY
   - Neptune 2D versions are available with STOCK and BLTOUCH support following the same structure

## Install

1. Power off your printer
2. Put the sd card in with the appropriate `elegoo.bin` file... *Reminder: Did I mention to make sure you have the correct version for your board?*
3. Turn on your printer.
4. The firmware will install.
5. Once installed, click on the calibration touchpoints. When the touch calibration is complete, it will display a confirmation message. You may think it froze but give it a little time.

   Please note: After you click the bottom right calibration point, reboot your machine if it prompts you to click the top left again. I have never had to do this more than twice when installing the firmware. This is [being tracked as a potential Marlin bug](https://github.com/MarlinFirmware/Marlin/issues/23435).

6. Remove the SD Card from your machine
  
## Recommended next steps 

### PID AUTOTUNE your machine.

*Did you know?* - Elegoo ships with some default values for this, but they can vary with *every* machine. PID tuning is a safety feature, and unless you want my machine's values, I suggest you do this.

1. From the main screen click on *settings icon -> Configuration -> Advanced Settings -> NEXT ARROW (>) -> Tempeture -> PID AUTOTUNE E1*
2. The nozzle will heat up and down for a few minutes. When completed, the screen will display a confirmation message on the bottom of the status screen.
3. From the main screen click on *settings icon -> Configuration -> Advanced Settings -> NEXT ARROW (>) -> Tempeture -> NEXT ARROW (>) -> PID AUTOTUNE BED*
4. The bed will heat up and down for a few minutes. When completed, the screen will display a confirmation message on the bottom of the status screen.
5. From the main screen click on the *settings icon -> Configuration -> NEXT ARROW (>) -> Store settings*

### Adjust ESTEPS.

NOTE: If you have a Neptune 2s or Neptune 2d and have not calibrated your ESTEPS, you can skip this section.

1. From the main screen click on *settings icon -> Configuration -> Advanced Settings -> Steps/mm -> E steps/mm
2. Set the default value of 90 (Elegoo Neptune 2 defaults) OR the value you have tuned for your printer.
3. Click the checkmark.
4. Click the back icon 2 times.
5. Click Configuration -> NEXT ARROW (>) -> Store settings

## TIPS

### Z Offest Wizard Location

Located at: *settings icon -> Configuration -> Advanced Settings -> NEXT ARROW (>) -> Tempeture -> NEXT ARROW (>) -> Probe Offsets*

### BT Touch Probe offsets

You can modify the offset of your probe within the touch screen interface to center your nozzle. 
For example: If you happen to use [this dual fan printhead](https://www.thingiverse.com/thing:4949488), the X offset is 47.5
You can set this at: *settings icon -> Configuration -> Advanced Settings -> Probe Offsets*

### Live Z Offset (Baby Stepping) Location

While printing:  *settings icon -> Tune -> NEXT ARROW (>) -> Probe Z Offset*

# FAQ's

Q. Why only one file? What happened to the `elegoo.txt` file and the fonts and images?

A. Marlin 2 does not use any additional files for the provided configurations. If you were to compile using LVGL, you would also get an `assets` folder. 

Q. The touch screen does not seem very responsive. Especially at the bottom of the screen. What's up with that?

A. Yup. Due to the screen size and touch areas I recommend using a stylus! [I found one that works well and made a side holder for it](https://thangs.com/trey.wentz/Screen%20stylus%20(remix)-43510?manualModelView=true). 

Q: How do I know what version board I have?
A: There are two ways to identify what version board you have. 
  - Via the stock firmware interface:
    - From the main screen, click on * Settings -> About *
    - If the *Firmware* version is 1.x.x, you have a v1.2 board.
    - If the *Firmware* version is 2.x.x, you have a v1.3 board.
  - Via the Serial number:
    - If the last block of the serial number starts with an A you have a v1.2 board
    - If the last block of the serial number starts with an X you have a v1.3 board
  - Visual confirmation (more effort, but if you are not running stock firmware, the only way):    
  - Power off, unplug and remove the bottom plate cover from your machine (Note: One screw that attaches near the LCD is shorter than the rest. Be sure to put that screw back in the same place when you put it back together, or you can crack or put a dimple on the top of the case) 
  - The version number is printed directly on the board

    ![1-2board](https://user-images.githubusercontent.com/10281380/147952867-216f31e7-3df8-4679-9e6e-3f61c7d24c45.jpg)
    ![1-3board](https://user-images.githubusercontent.com/10281380/147952884-c4643537-1928-45d9-ae86-38522722a18b.jpg)
