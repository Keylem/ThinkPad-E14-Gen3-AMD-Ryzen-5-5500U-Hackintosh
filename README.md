# ThinPad E14 Gen3 AMD Ryzen 5 5500U Hackitosh
 ### Intended to be run on Big Sur with an recovery installer.
 !! If possible, use the ethernet port while installing from the recovery !!
 After setting up the recovery, press "space" to unveil the hidden options
 Be cautious when resetting the nvram, as it is known to brick some thinkpads (mine didin't but be aware of it)

Status
--
- No graphics acceleration is awailable for Renoir right now.
- Sleep should be modified to use hybernation value 3
- Sound not working (because of laziness)
- CPU power Management is partially working, but needs AMD Power Gadget.app to fonction.
- Some adobe apps and docker containers straight up does not work
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
* Do not trust the author to update this EFI, because of the lack of time and energy needed to maintain this project. Feel free to fork it and build upon it.

Recommended BIOS settings
--
- Secure boot --> Off
- Memory Protection --> Off
- TPM 2.0 --> Disabled
- Hyperthreading --> on
- Anything security related --> off ...

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
