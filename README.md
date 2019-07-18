# Huawei Matebook 13 Hackintosh Mojave LAST UPDATE 2019/07/18

## I'm not responsible for damage, termonuclear war or pregnant wife. Sorry for my bad english, i've done my best 
This guide is designed for Huawei Matebook 13.
After some night spent on it, almost all works(except WiFi).
In the next days I will try to mod bios to read broadcom WiFi card


nb. Many thanks to tonymac forum



**Whats work**
* Graphics accelaration
* Battery stats 
* trackpad
* sensors 
* audio
* almost all exept thing listed in "bugs"

**Bugs:**
* Bluetooth and Wifi wont working
* nb: wifi card is replaceble but bios need to be modified to get it working
* Brightness setting shortcuts
* Sometimes boot fail(work in progress)

**Raccomandations:**
* Format SSD to Mac  Mac OS Extended (Journaled)
* Use left usb port or will get errors during installation
* Use a usb hub during installation or a OTG usb C adaptator to use usb c port as usb
* During installation may occur that pc shut down after clover selection for the first two attempt
* Versions with Samsung PM981 NVMe need ssd to be replaced
* Versions with Western Digital nvme work out of the box 

**Installation**
* Download Osx from the appstore with a existing mac/hackintosh or with a vmware virtual machine(google is your friend)
* Format a usb drive, Mac OS(Journaled) with gpt partition scheme and rename it in "osx" (at least 8GB)
* Build the usb installer with this command:
> sudo "/Applications/Install macOS Mojave.app/Contents/Resources/createinstallmedia" --volume  /Volumes/osx --nointeraction 

osx is the name of the usb drive, so if you use different name you have to change it in the path of the command
* Install Clover [Download Clover v2.4k r4972](https://sourceforge.net/projects/cloverefiboot/files/Installer/Clover_v2.4k_r4972.zip/download)
* Choose Usb drive as destination of the install and then click on the "Ad hoc" button,
select "Clover for UEFI booting only" and continue the installation.
* On the efi partition of the usb drive(it's mounted by default after the clover installation, if you need to mount it use command 
> sudo diskutil mount disk1s1
'disk1s1' may differ according to your partition scheme, can find this command to see your partition scheme
>diskutil list

Once you have access of your usb drive EFi partition, copy the content of **CloverInstallation** in each corrisponding folder of your EFI/Clover partiton(delete the previus content)
* Now the installation should go on with no problems(If your screen turn off after Clover selection) just do another 2/3 attempts(system will reboot during installation, and you have to select the mac os HDD from clover selection in bootloader). Remember to format your drive. in Mac OS(Journaled) in disk utility in the installation, or the process will fail.

**Post Installation**
* After boot, install same clover used in the installation, but this time on HDD
* Extract **CloverPost** from my repository and copy the content in each EFI/Clover like you did for the installation process, but this time on the HDD
* Extract the **kext.zip** in the desktop and type this commands to install kext in Library/Extensions
> cd Desktop/kexts 

> sudo cp -R *.kext /Library/Extensions/ 
Now we need to rebuild kernel cache, so launch this other command
> sudo kextcache -i /
* Disable hibernation by launching this command one at time
> sudo pmset -a hibernatemode 0 

> sudo rm /var/vm/sleepimage 

> sudo mkdir /var/vm/sleepimage 

> sudo pmset -a standby 0 

> sudo pmset -a autopoweroff 0 

* Reboot and enjoy your Hackintosh(Some thing maybe wont work perfect, this is a continuos work in progress, so read carefully before complain"







I'm working on this project to get almost fully functional hackintosh build on this laptop
if you want to help me or join in project you can write me an email: edoardo001ct@gmail.com

_**If you want to buy me a beer please click here:**_
**[Buy me a beer](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=2NMM7HN9SJRVE&source=url
).** 

