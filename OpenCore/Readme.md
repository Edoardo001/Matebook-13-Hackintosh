  <h1>First open core version for our matebook 13</h1>

*i have very little time to work on this project because of my work and my exams, but thanks to the help provided by the guys in our awesome group, we've now have a pretty stable opencore version*

 [Official open core guide](https://www.youtube.com/watch?v=bGCNpHCqUcA), here you can find a lot useful information about installation. Just follow that guide and use our EFI prepared for our laptop. Or follow my Catalina guide and in the post install, after installing clover, delete "EFI" folder in "EFI partition, and put this one with open core.


Just put EFI folder in EFI partition.


**Try this only if you have an usb with bootloader, or system backup to enter system in case of EFI corruption**
 <details>
<summary>Changelog</summary>
 06/06/2020
- Fixed brigthness keys(thanks to Kitsu Liu)
- Fixed logo ridimensioning during boot
  
 </details>

<h2>Post installation fix and patches</h2>
 
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
  
> 1 -  bash -c "$(curl -fsSL https://raw.githubusercontent.com/xzhih/one-key-hidpi/master/hidpi.sh)"

> 2 -  Select 1 Enable HIDPI

> 3 -  Select 3 MacBook Pro

> 4 -  Select 6 Manual input resolution 

> 5 -  Insert: 2160x1440 1920x1280 1600x1066 1280x854 1080x720
</details>

<details>
<summary>Fix iCloud request login on every boot in settings</summary>
sudo -v
> killall -9 accountsd com.apple.iCloudHelper
> defaults delete MobileMeAccounts
> rm -rf ~/Library/Accounts
> killall -9 accountsd com.apple.iCloudHelper
> sudo reboot

</details>
