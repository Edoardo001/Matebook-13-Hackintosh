  ## I've spent the majority of my spare time on this project, so if you want to support my work, consider donating a small sum (info at the end of the guide).
  
  <h1>OpenCore Matebook 13 build</h1>
 
 > latest update 14/07/20

*i have very little time to work on this project because of my work and my exams, but thanks to the help provided by the guys in our awesome group, we've now have a pretty stable opencore version*

 [Official open core guide](https://dortania.github.io/OpenCore-Install-Guide/), here you can find a lot useful information about installation. Just follow that guide and use our EFI prepared for our laptop. Or follow my Catalina guide and in the post install, after installing clover, delete "EFI" folder in "EFI partition, and put this one with open core.

**Join telegram group** https://t.me/hackintosh_matebook13


<details>
  <summary> New installation</summary>
What you need:

A working mac (hackinosh or vmware virtual machine work as well)
USB hub for the installation (connected on the usb port of Huawei original adaptator. If you have a usb type c otg connector you can use it to convert usb c to usb a)
Usb drive(at least 16GB)
Further notes and tips

Format SSD to Mac APFS
Use left usb port or you'll get errors during installation
Use a USB hub during installation or a OTG usb C adaptator to convert usb c port to usb a
Versions with Samsung PM981 NVMe need ssd to be replaced
Versions with Western Digital nvme work out of the box

Installation

**Remember update kext in EFI/OC/Kexts(After downloading, to have latest ones)

I've used to write guide myself, but OpenCore guys, have done a greato job, so it's useless to rewrite it, just follow the steps to make usb, and put my EFI folder in the EFI partition

Here, how to build the usb for the installation:
https://dortania.github.io/OpenCore-Desktop-Guide/installer-guide/


Post Installation

After boot, mount the EFI partition of the internal disk
/
Extract OpenCorePost.zip copy the "EFI" folder your EFI partition(like in the installation process, but this time on the HDD)


Reboot and enjoy your Hackintosh (Some stuff might not be working perfectly, but Hackintoshing is a continuous process, so read carefully before complaining"


</details>
<details>
  <summary> Conversion from Clover</summary>
*No dual boot support for now*

Who have a working Clover build, just have to put EFI folder in EFI partition(Delete all files and folders from EFI partition before).
The folder efi must be in the efi partition(don't put files directly in the EFI partition),  so the path must be EFI/EFI/OC and EFI/EFI/BOOT.

**Try this only if you have an usb with bootloader, or system backup to enter system in case of EFI corruption**

</details>

<details>
<summary>Known bugs</summary>

- Camera(for most of the hackintosh laptops, the camera works out of the box, for now we have to surrender)

- Wifi(Testing beta wifi kext, better wait for now) 

- You tell me
  
 </details>

 <details>
<summary>Changelog</summary>
  14/07/2020

- Fixed audio jack(Thanks to our telegram friend Alex Larionov that found a Combojack working with our layout id)

- Updated bluetooth kext for better stability
  
  
 02/07/2020

- Fixed random boot fails

- Separated build for mx graphics version and intel hd graphics only version
 
 17/06/2020

- Raised min cpu frequency that causes lags



 16/06/2020

- Enabled AppleCpuPmCfgLock for better power managment

- Added proper usb mapping to fix sleep issues and obtain better battery life 

- Fixed sleep

- Added proper CpuFriendKext to reach lower frequencies when laptop is in idle and max frequencies when it's needed according with our cpu capabilities 

- Now Opencore has an bios entry to prevent others os updates corrupt osx boot 

- Remove deprecated values from Config.plist
  

 06/06/2020

- Fixed brigthness keys(thanks to Kitsu Liu)

- Fixed logo ridimensioning during boot
  
 </details>

<h2>Post installation fix and patches</h2>

<details>
<summary>Fix Wifi</summary>

> Download Itwlm kext here https://github.com/OpenIntelWireless/itlwm/releases and put in EFI/OC/KEXT and enable in config.plist in Kernel>add>itlwm by set "TRUE" in "Enabled"


> Download Heliport here https://github.com/OpenIntelWireless/HeliPort/releases and install it

> Reboot and enjoy working Wi-Fi

</details>
 
 <details>
<summary>Deleting clover footprints(for who come from Clover)</summary>
Following this awesome guide https://github.com/dortania/OpenCore-Desktop-Guide/tree/master/clover-conversion
</details>

<details>
<summary>Fix alt and ctrl inverted</summary>

> Go in settings>keyboard and click on "Modifier keys", invert options and command key. Voila!
</details>

<details>
<summary>Enable HIDPI (Many thanks to Xzhih)</summary>

```
 1 -  bash -c "$(curl -fsSL https://raw.githubusercontent.com/xzhih/one-key-hidpi/master/hidpi.sh)"

 2 -  Select 1 Enable HIDPI

 3 -  Select 3 MacBook Pro

 4 -  Select 6 Manual input resolution 

 5 -  Insert: 2160x1440 1920x1280 1600x1066 1280x854 1080x720
```
</details>

<details>
<summary>Fix iCloud request login on every boot in settings</summary>

```
sudo -v
killall -9 accountsd com.apple.iCloudHelper
defaults delete MobileMeAccounts
rm -rf ~/Library/Accounts
killall -9 accountsd com.apple.iCloudHelper
sudo reboot
```

</details>

<details>
<summary>Fix sleep issues</summary>
Disable some hibernation behaviours that not works well on hackintoshes
  
  ```
 sudo pmset -a hibernatemode 0
 sudo rm -rf /private/var/vm/sleepimage
 sudo touch /private/var/vm/sleepimage
 sudo chflags uchg /private/var/vm/sleepimage
 sudo pmset -a standby 0
 sudo pmset -a autopoweroff 0
 sudo pmset -a powernap 0
 sudo pmset -a proximitywake 0
 sudo pmset -b tcpkeepalive 0
```

</details>

<details>
<summary>Fix Audio Jack(thanks to randomprofilename)</summary>
https://github.com/randomprofilename/ComboJack
  

  ```
  Since in my build i've  integrated verbstub kext, you have just to download Combojack and run install.sh in terminal, with this command(ensure you are in the extract folder where install.sh is located)

> ./install.sh
```

</details>

_**If you want to buy me a beer please click here:**_
**[Buy me a beer](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=2NMM7HN9SJRVE&source=url
).**
