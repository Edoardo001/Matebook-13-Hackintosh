# Huawei Matebook 13 Hackintosh Catalina UPDATED 2020/02/06
## I've spent the majority of my spare time on this project, so if you want to support my works consider to make a donation(info at the end of the guide). 

**[Youtube video](https://www.youtube.com/watch?v=bGCNpHCqUcA).** 

**In the next release**
Hope to solve any bug you tell me
- Internal intel wifi card support(there are some progession in intel wifi kext, hope to see a fully functional kext as we got with bluetooth)


**Changelog**
* **2020/01/06**
- Initial release (many thanks to frezs for some files, that made me do things in less time)

## I'm not responsible for damage, termonuclear war or pregnant wife. Sorry for my bad english, i've done my best 
This guide is designed for Huawei Matebook 13.
After some night spent on it, almost all works(except WiFi).
In the next days I will try to mod bios to read broadcom WiFi card

nb. Many thanks to tonymac forum guys for their awesome guides

**Whats work**
* Graphics accelaration
* Battery stats 
* trackpad
* sensors 
* audio
* Internal bluetooth(now, without any workaround)
* almost all exept thing listed in "bugs"

**Bugs:**
* Camera(maybe not compatible with osx) will try
* Wifi(some great news about it, project is running good and maybe we will get fully fuctional kext for intel wifi, as we got for intel bluetooth(works without hot boot)
* Jack audio(can use any time of bluetooth hearphones or usb hearphones)
You tell me

**What you need:**
* A working mac(hackinosh or vmware virtual machine are good too)
* Usb hub for the installation(connected on the usb port of huawei original adaptator. If you have a usb type c otg connector you can use it to turn usb c port to usb a)
* Usb drive(al least 16GB)

**Raccomandations:**
* Format SSD to Mac  APFS
* Use left usb port or will get errors during installation
* Use a usb hub during installation or a OTG usb C adaptator to use usb c port as usb
* During installation may occur that pc shut down after clover selection for the first two attempt
* Versions with Samsung PM981 NVMe need ssd to be replaced
* Versions with Western Digital nvme work out of the box 

**Installation**
* Download Osx from the appstore with a existing mac/hackintosh or with a vmware virtual machine(google is your friend)
* Format a usb drive, Mac OS(Journaled) with gpt partition scheme and rename it in "osx" (at least 16GB)
* Build the usb installer with this command:
> sudo "/Applications/Install macOS Catalina.app/Contents/Resources/createinstallmedia" --volume  /Volumes/osx --nointeraction 

osx is the name of the usb drive, so if you use different name you have to change it in the path of the command
* Install latest Clover 
* Choose Usb drive as destination and click on the "Ad hoc" button,
select "Clover for UEFI booting only" and continue the installation.
* After Clover installation by default EFI partition of usb drive should be mounted, if not, you should mount it manually using this command 
> sudo diskutil mount disk2s1

'disk2s1' may change according to your partition scheme. To know which is the partition you need to mount(EFI of usb drive), use this other command

>diskutil list

Once you have access of your usb drive EFi partition, copy the "Clover" folder of **CATALINA CloverInstallation.zip** and replace the one in your EFI folder "EFI/CLOVER"
* Now the installation should go on with no problems(If your screen turn off after Clover selection) just do another 2/3 attempts(system will reboot during installation, select the mac os HDD from clover selection in bootloader). 

**Post Installation**
* After boot, install same clover used in the installation, but this time on HDD
* Extract **CATALINA CloverPost.zip** copy the "Clover" folder and replace the one in your EFI folder "EFI/CLOVER" like the installation process, but this time on the HDD


* Reboot and enjoy your Hackintosh(Some thing maybe wont work perfect, this is a continuos work in progress, so read carefully before complain"


**Optimizations**
* If some apps has problem starting, try add this bootflags 
> shikigva=32

> shiki-id=Mac-7BA5B2D9E42DDD94

* Remove red badge(1) of setting icon on the dock when updates are available

>defaults write com.apple.systempreferences AttentionPrefBundleIDs 0

>killall Dock


*To get better battery life, you can use cpu friend kext 
run this command 
> bash -c "$(curl -fsSL https://raw.githubusercontent.com/stevezhengshiqi/one-key-cpufriend/master/one-key-cpufriend.sh)"
You have to choose in terminal what configuration use, i've choosed 800mhz and maximum power saving. I will generate 2 kext on the desktop that you have to install in "/Library/Extensions" folder.
Thanks to [Stevezhengshiqi OneKey CPU Friend](https://github.com/stevezhengshiqi/one-key-cpufriend).



I'm working on this project to get almost fully functional hackintosh build on this laptop
if you want to help me or join in project you can write me an email: edoardo001ct@gmail.com

_**If you want to buy me a beer please click here:**_
**[Buy me a beer](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=2NMM7HN9SJRVE&source=url
).** 
