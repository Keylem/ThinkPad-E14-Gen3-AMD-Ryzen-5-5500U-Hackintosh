# ThinPad E14 Gen3 AMD Ryzen 5 5500U Hackitosh
 ### Intended to be run on Big Sur with an recovery installer.
 !! If possible, use the ethernet port while installing from the recovery !!
 After setting up the recovery, press "space" to unveil the hidden options
 Be cautious when resetting the nvram, as it is known to brick some thinkpads (mine didin't but be aware of it)

Status
--
- Not for daily usage, opening chrome/firefox crashes system (because of the lack of hardware acceleration)
- Doesn't wake up from sleep (but opening and closing lid does not crash)
- Sound not working (Labeled as ALC257 in linux but does not work)
- partial CPU Power Management with AMDRyzenCPUPowerManagement.kext and AMD Power Gadget.app
- Some adobe apps and docker containers straight up does not work (because of the lack of intel features)
- 3.5mm Jack (bcs I don't have wired headphones)

What is working?
--
- Graphics detected (you can see the screen)
- Wifi works (must be replaced with an intel ax200/ax210 card)
- Bluetooth
- Trackpad with gestures
- Brightness control
- Battery Status
- Keyboard
- Ethernet Port


What will never be working?
--
- Fingerprint sensor

## ! Disclaimer !
* Do not trust the author to update this EFI, because of the lack of time and energy needed to maintain this project. Feel free to fork it and build upon it.

Recommended BIOS settings
--
- Secure boot --> Off
- Memory Protection --> Off
- TPM 2.0 --> Disabled
- Hyperthreading --> on
- Anything security related --> off ...
