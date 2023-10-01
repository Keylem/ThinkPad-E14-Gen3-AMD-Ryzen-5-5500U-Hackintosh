# ThinPad E14 Gen3 AMD Ryzen 5 5500U Hackitosh!

# For the moment, this repository won't receive any updates! Please fork it and build upon it!
[Neofetch](https://github.com/Keylem/ThinkPad-E14-Gen3-AMD-Ryzen-5-5500U-Hackintosh/blob/main/neofetch.png)

[Cinebench](https://github.com/Keylem/ThinkPad-E14-Gen3-AMD-Ryzen-5-5500U-Hackintosh/blob/main/benchmark.png)
 ### Intended to be run on Big Sur with recovery installer.
 !! If possible, use the ethernet port while installing from the recovery !!
 In the USB stick, to use recovery installer, use the EFI folder.
 After setting up the recovery, press "space" to unveil the hidden options
 Be cautious when resetting the nvram, as it is known to brick some thinkpads (mine didin't but be aware of it)
 !! After installing and setting up the system, mount your internal SSD's EFI partition and use the EFI folder provided in "EFI_TO_USE_AFTER_INSTALLATION" !!
 Please create an unique SMBIOS number using the MacBookPro16,3 scheme if you want to connect to your apple id at any point.

Status
--
- No graphics acceleration is available for Renoir right now (but will be at some point) so if possible please update the NootedRed.kext to it's newest from the artifacts tab --> https://github.com/NootInc/NootedRed/actions .
- Sleep should be OK by default (Hibernation needs emulated NVRAM to be set). But if you have any issues look at the sleep references at above. (Nevertheless set the GPU switheroo to 0 with "sudo pmset -a gpuswitch 0"
- Waking from sleep sometimes crashes trackpad (I2C) and trackpoint (PS2), presumably because of the Input.kext used in the both VoodooI2C and VoodooPS2. To make fix it disable either the TrackPoint or the TrackPad from the BIOS settings.
- CPU power Management is partially working, but needs AMD Power Gadget.app to function.
- Some adobe apps and docker containers straight up does not work
- 3.5mm Jack appears to be working but whether if it stays available after wake is still unknown as sleep is broken. 
- No mic is detected and the reason is unknown
- Startup dong is enabled by default
- Starts up with a pretty theme with the EFI intended to be used after installation.

What is working?
--
- Graphics detected
- Wifi works (must be replaced with an intel ax200/ax210 card)
- Bluetooth
- Trackpad with gestures
- Brightness control
- Battery Status
- Keyboard
- Ethernet Port
- Internal Sound with JACK (ALC257, layout-id=11)
- HDMI ourput


What will never be working?
--
- Fingerprint sensor (if possible disable it from the BIOS settings)

## ! Disclaimer !
* Do not trust the author to update this EFI, because of the lack of time and energy needed to maintain this project. Feel free to fork it and build upon it.

Recommended BIOS settings
--
- Secure boot --> Off
- Memory Protection --> Off
- TPM 2.0 --> Disabled
- Hyperthreading --> on
- Anything security related --> off ...
- Display --> set to 2GB minimum

To enable sleep
--
sudo pmset -a standbydelayhigh 0
sudo pmset -a ttyskeepawake 0   
sudo pmset -a gpuswitch 0    
sudo pmset -a halfdim 0  
sudo pmset -a womp 0      
sudo pmset -a acwake 0
sudo pmset -a networkoversleep 0```

sudo pmset -a hibernatemode 3

Then you can change all of the sleep values to your intent.

<details>  
<summary><strong>##  Hibernation and sleep setup reference</strong></summary>
</br>
[Script](https://www.tonymacx86.com/threads/release-sleeponlowbattery-solb.264785) that performs auto sleep/hibernate at low battery.

1. Open terminal
1. Enter commands below one by one

   Settings for AC:

   ```
   sudo pmset -c standby 1
   sudo pmset -c hibernatemode 0
   ```

   Setting for battery:

   ```
   sudo pmset -b standby 1
   sudo pmset -b standbydelayhigh 900
   sudo pmset -b standbydelaylow 60
   sudo pmset -b hibernatemode 25
   sudo pmset -b highstandbythreshold 70
   ```

   Settings for all:

   ```
   sudo pmset -a acwake 0
   sudo pmset -a lidwake 1
   sudo pmset -a powernap 0
   ```

To restore default system settings run

```
sudo pmset restoredefaults
```

<details>  
<summary><strong>Advanced energy management</strong></summary>

`acwake`: wake the machine when power source (AC/battery) is changed (value = 0/1)

`lidwake`: wake the machine when the laptop lid (or clamshell) is opened (value = 0/1)

`powernap`: enable/disable Power Nap on supported machines (value = 0/1)

`standbydelayhigh` and `standbydelaylow` specify the delay, in seconds,
before writing the hibernation image to disk and powering off memory for Standby.
standbydelayhigh is used when the remaining battery capacity is above `highstandbythreshold`(has a default value of 50 percent),
and standbydelaylow is used when the remaining battery capacity is below highstandbythreshold.

`hibernatemode` supports values of 0, 3, or 25. To disable hibernation, set hibernatemode to 0.  
`hibernatemode` = 0 by default on desktops. The system will not back memory up to persistent storage. The system must wake from the contents of memory; the system will lose context on power loss.  
`hibernatemode` = 3 by default on portables. The system will store a copy of memory to persistent storage (the disk), and will power memory during sleep. The system will wake from memory, unless a power loss forces it to restore from hibernate image.  
`hibernatemode` = 25 is only settable via pmset. The system will store a copy of memory to persistent storage (the disk), and will remove power to memory. The system will restore from disk image. If you want "hibernation" - slower sleeps, slower wakes, and better battery life, you should use this setting.

[Source](https://www.dssw.co.uk/reference/pmset.html)

</details>
</br>
</details>


For the R7 Model
--
If you ever intend to use this EFI with a 8 core R7, please modify BA060000 0000 value to BA080000 0000 on config.plist, then rename your CPU using CPU-Name.command

Thanks to the magicians who made it possible: 
--
- Visual Ehrmanntraut
- ExtremeXT
- NyanCatTW1
- Trassic
- 4TechGuns
- ... and many other NootedRed Testers
- RehabMan
- Dortania
