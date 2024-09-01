# ThinPad E14 Gen3 AMD Ryzen 5 5500U Hackitosh!

# For the moment, this repository won't receive any updates! Please fork it and build upon it!
[Neofetch](https://github.com/Keylem/ThinkPad-E14-Gen3-AMD-Ryzen-5-5500U-Hackintosh/blob/main/neofetch.png)

[Cinebench](https://github.com/Keylem/ThinkPad-E14-Gen3-AMD-Ryzen-5-5500U-Hackintosh/blob/main/benchmark.png)
 ### Why it is a BAD idea to use a premade EFI?
 The configuration of a machine can DRASTICALLY change from one machine to another. That change also includes the displacement of the primary disc on the motherboard, the addition of a second disc, the use of a different wifi card, the BIOS settings etc. A personnal anectode: when I was trying to set up my machine for the second time, I noticed that whenever I forget to plug in the SSD that came with the machine and only left the secondary SSD that I installed afterwards, I wasn't able to use the webcam! That was also the primary cause of the sleep problems of my machine. As you can see, maybe there is nothing to do with a PCIE device and a USB device (an internal one...) it was still causing problems. You may use this repo as a blueprint, but building up everything from scratch will certaily lead to less headache/time/effort... it is not so hard to do so. check this guide: [guide](https://chefkissinc.github.io/applehax/nootedred/)
 ### Intended to be run on Big Sur with recovery installer.
 !! If possible, use the ethernet port while installing from the recovery !!
 In the USB stick, to use recovery installer, use the EFI folder.
 After setting up the recovery, press "space" to unveil the hidden options
 Be cautious when resetting the nvram, as it is known to brick some thinkpads (mine didin't but be aware of it)
 !! After installing and setting up the system, mount your internal SSD's EFI partition and use the EFI folder provided in "EFI_TO_USE_AFTER_INSTALLATION" !!
 Please create an unique SMBIOS number using the MacBookPro16,3 scheme if you want to connect to your apple id at any point. --> https://github.com/corpnewt/GenSMBIOS

Status
--
- MacOS Sonoma Support (Can be updated directly from BigSur after changing the EFI and using the ethernet cable)
-Directly use the Sonoma EFI when installing if you want to use Sonoma.
- Because of the licensing issues, NootedRed.kext has to be installed directly from it's github actions page --> https://github.com/ChefKissInc/NootedRed
 Please place the NootedRed.kext inside EFI/OC/Kexts
- CPU power Management is partially working. But laptop still generates a lot of heat.
- Some adobe apps and docker containers straight up does not work
- Starts up with a pretty theme with the EFI intended to be used after installation.
- Almost perfect waking from hibernation with hibernate 25, hibernate 3 is still broken. sometimes problems with darkwake.
- L1 level powersave for every available device
- Power Button seems to be not working (when pressed, nothing happens)

What is working?
--
- Graphics (with accelerated encoding and decoding(experimental))
- Wifi works (must be replaced with an intel ax200/ax210 card)
- Bluetooth
- Trackpad with gestures
- Brightness control
- Battery Status
- Keyboard
- Ethernet Port
- Internal Sound with JACK (ALC257, layout-id=11)
- HDMI output
- Microphone
- FileValut encription support (encouraged)
- Mute button, airplane button (must be used with YogaSMC)


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

To play with sleep opitions
--
type "man pmset" on your terminal.


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
