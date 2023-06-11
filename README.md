# ThinPad E14 Gen3 AMD Ryzen 5 5500U Hackitosh!
[Uploading Ekran Resmi 2023-06-11 03.33.03.png…]()
[Ekran Resmi 2023-05-30 13 03 40](https://github.com/Keylem/ThinkPad-E14-Gen3-AMD-Ryzen-5-5500U-Hackintosh/assets/52345143/eafb33ae-95af-4bc0-8aa6-b5ab6c9a4286)

 ### Intended to be run on Big Sur with recovery installer.
 !! If possible, use the ethernet port while installing from the recovery !!
 In the USB stick, to use recovery installer, use the EFI folder.
 After setting up the recovery, press "space" to unveil the hidden options
 Be cautious when resetting the nvram, as it is known to brick some thinkpads (mine didin't but be aware of it)
 !! After installing and setting up the system, mount your internal SSD's EFI partition and use the EFI folder provided in "EFI_TO_USE_AFTER_INSTALLATION" !!
 Please create a unique SMBIOS number using the MacBookPro16,3 scheme if you want to connect to your apple id at any point.

Status
--
- No graphics acceleration is available for Renoir right now (but will be at some point) so if possible please update the NootedRed.kext to it's newest from the artifacts tab --> https://github.com/NootInc/NootedRed/actions .
- Sleep should be modified to use hibernation value 3 (broken by design for now because fo the NootedRed
- CPU power Management is partially working, but needs AMD Power Gadget.app to function.
- Some adobe apps and docker containers straight up does not work
- 3.5mm Jack (bcs I don't have wired headphones so I can not test it)
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
- Internal Sound (ALC257, layout-id=11)


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

To enable Sleep
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

For the R7 Model
--
If you ever intend to use this EFI with a 8 core R7, please modify BA060000 0000 value to BA080000 0000 on config.plist, then rename your CPU using CPU-Name.command
