<div align="center">

# Huawei Matebook 13 Hackintosh Catalina UPDATED 2020/04/05

## I've spent the majority of my spare time on this project, so if you want to support my work, consider donating a small sum (info at the end of the guide).

</div>

See what MacOS looks like on the Huawei Matebook 13 in this **[Youtube video](https://www.youtube.com/watch?v=bGCNpHCqUcA).** 

<hr>

**Join telegram group** https://t.me/hackintosh_matebook13

**In the next release**
I'm hoping to solve any bug you are reporting to me
- Internal intel wifi card support (There is som progress in intel wifi kext, hope to see a fully functional kext as we got with bluetooth)


**Changelog**
* **2020/04/10**
  - Found a fix for jack 3,5(works perfect) but broke mic(Guide to fix in "Optimization" at the end of the guide)
Still working to find a fix that make working jack and mic togheter. Any help is really appreciated.
* **2020/04/08**
  - Addes SSDT-USB for better battery drain
  - Fixed audio with hdmi
  - Fixed sleep after 15.4 update(Clover update)
  - Fixed logo resizing during boot, now apple remain with same size, only load bar change size. Overall is better but not          perfect
* **2020/04/05**
  - Fixed panic in installation and post with 10.15.4 update
* **2020/02/14**
  - English improved by [miit0o](https://github.com/miit0o)
* **2020/01/06**
  - Initial release (many thanks to frezs for some files, that made me do things in less time)

## I'm not responsible for damage, termonuclear war or pregnant wife. 
This guide is built around the Huawei Matebook 13.
After some nights spent on this project, almost everything is working (exept WiFi).
I will try to mod the BIOS to be able to read a broadcom WiFi card withing the next few days.

Many thanks to the tonymac forum guys for their awesome guides

**What's working**
* Graphics accelaration
* Battery stats 
* trackpad
* sensors 
* audio
* Internal bluetooth (now, without any workaround)
* almost everything exept things listed in "bugs"

**Bugs:**
* Camera (maybe not compatible with osx), will try to figure this out
* Wifi (some great news about it, project is running good and maybe we will get fully fuctional kext for intel wifi, as we got for intel bluetooth(works without hot boot)
* 3.5mm audio jack (You can still use bluetooth and USB headphones)
You tell me

**What you need:**
* A working mac (hackinosh or vmware virtual machine work as well)
* USB hub for the installation (connected on the usb port of Huawei original adaptator. If you have a usb type c otg connector you can use it to convert usb c to usb a)
* Usb drive(at least 16GB)

**Further notes and tips**
* Format SSD to Mac APFS
* Use left usb port or you'll get errors during installation
* Use a USB hub during installation or a OTG usb C adaptator to convert usb c port to usb a
* During installation may occur that pc shut down after clover selection for the first two attempt
* PC may shutdown during installation after clover selection (just the first two attempts)
* Versions with Samsung PM981 NVMe need ssd to be replaced
* Versions with Western Digital nvme work out of the box 

**Installation**

**Remember update kext in Clover/Kexts/other(After downloading my files for both installation and post installation), for example with Catalina 15.4 update my pc get panic until i updated in EFI folder(EFI wiilwhatevergreen and appleAlc kexts**

* Download macOS from the appstore with a existing mac/hackintosh or with a vmware virtual machine(google is your friend)
* Format a usb drive, Mac OS(Journaled) with gpt partition scheme and rename it in "osx" (at least 16GB)
* Build the usb installer with this command:
> sudo "/Applications/Install macOS Catalina.app/Contents/Resources/createinstallmedia" --volume  /Volumes/osx --nointeraction 

*Note: osx is the name of the usb drive, so if you use a different name you have to change it in the path of the command*

* Install latest Clover 
* Choose Usb drive as destination and click on the "Ad hoc" button,
select "Clover for UEFI booting only" and continue the installation.
* After Clover installation by default EFI partition of usb drive should be mounted, if not, you should mount it manually using this command 
> sudo diskutil mount disk2s1

'disk2s1' may change according to your partition scheme. To know which is the partition you need to mount(EFI of usb drive), use this other command

>diskutil list

Once you have access of your usb drive EFi partition, copy the "Clover" folder of **CATALINA CloverInstallation.zip** and replace the one in your EFI folder "EFI/CLOVER"
* Now the installation should go on with no problems 
  * If your screen turns off after Clover selection just do another 2/3 attempts (system will reboot during installation, select the mac os HDD from clover selection in bootloader). 

**Post Installation**
* After boot, install same clover used in the installation, but this time on HDD
* Extract **CATALINA CloverPost.zip** copy the "Clover" folder and replace the one in your EFI folder "EFI/CLOVER" like in the installation process, but this time on the HDD


* Reboot and enjoy your Hackintosh (Some stuff might not be working perfectly, but Hackintoshing is a continuous process, so read carefully before complaining"


**Optimizations**
* You can choose to have internal speaker and internal mic working, but not the audio jack, or internal speaker and jack working but no internal mic

*To make audio jack working
> Open Clover>Config.plist and in Device>Properties>PciRoot(9x9)/Pci(0x1f,0x3)>layout-id and insert value "28"
> Download AlcPlugFixx.zip from download section and extract it
> Launch "sudo mount -uw /" in terminal
> Open "AlcPlugFixx" and launch "autoinstall.command", wait 10 second, click "enter", close terminal and reboot laptop
* To make internal mic working
> Open Clover>Config.plist and in Device>Properties>PciRoot(9x9)/Pci(0x1f,0x3)>layout-id and insert value "13"
> reboot laptop



* If some apps are having trouble launching, try adding these commands to the bootflags 
> shikigva=32

> shiki-id=Mac-7BA5B2D9E42DDD94

* Remove red badges (1) from the settings icon in the dock when updates are available

>defaults write com.apple.systempreferences AttentionPrefBundleIDs 0

>killall Dock


* You can use the CPU friend Kext to get better battery life.
To install it, run this command:
> bash -c "$(curl -fsSL https://raw.githubusercontent.com/stevezhengshiqi/one-key-cpufriend/master/one-key-cpufriend.sh)"

You'll have to choose your configuration in the terminal. I've chosen 800MHz and maximum power saving. It'll generate two kext files on your desktop which you have to install to "/Library/Extensions".
Thanks to [Stevezhengshiqi OneKey CPU Friend](https://github.com/stevezhengshiqi/one-key-cpufriend).

**If after copying CloverPost.zip files  you get bootloop try deleting dsdt.aml from apci/patch(will brake blacklight shortcut, brightness slider in setting still working). Unfortunately some dsdt patches work only on my variant and I can't test on others**

I'm working on this project to build an almost fully functional hackintosh on this laptop.
If you want to gelp me or join the project, you can write me an email: [edoardo001ct@gmail.com](mailto:edoardo001ct@gmail.com)

_**If you want to buy me a beer please click here:**_
**[Buy me a beer](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=2NMM7HN9SJRVE&source=url
).** 
