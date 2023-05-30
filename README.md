# ThinPad E14 Gen3 AMD Ryzen 5 5500U Hackitosh
 ### Intended to be run on Big Sur with an recovery installer.
 !! If possible, use the ethernet port while installing from the recovery !!

Status
--
- Not Usable, opening chrome/firefox crashes system
- Doesn't wake up from sleep (but opening and closing lid does not crash)
- Sound not working (because of laziness)
- CPU power Management is not working (and probably never will be)
- Some adobe apps and docker containers straight up does not work
- USB ports didn't mapped (bcs of laziness again)
- 3.5mm Jack (bcs I don't have wired headphones)

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


What will never be working?
--
- Fingerprint sensor

## ! Disclaimer !
* Do not trust the author to update this EFI, because of the lack of time and energy needed to maintain this project. Feel free to fork it and build upon it *

Recommended BIOS settings
--
- Secure boot --> Off
- Memory Protection --> Off
- TPM 2.0 --> Disabled
- Hyperthreading --> on
- Anything security related --> off ...
