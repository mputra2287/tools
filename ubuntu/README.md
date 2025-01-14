# GNU/Linux Ubuntu installation, settings and tricks

## (1) Ubuntu installation via usb-stick

### (1.1) Create Booteable UBS-stick 

#### Requirements
* A 2GB or larger USB stick/flash drive
* Ubuntu Desktop 14.04 or later installed
* An Ubuntu ISO file from:
	* [Ubuntu 16.04 (Xenial Xerus)](http://releases.ubuntu.com/16.04/)
		* 16.04.5-desktop-amd64.iso
	* [Ubuntu 18.04 (Bionic Beaver)](http://releases.ubuntu.com/18.04/)
		* 18.04.2-live-server-amd64.iso, 2019-02-14, 834M
		* 18.04.2-desktop-amd64.iso, 2019-02-10 00:27, 1.9G
	* [Ubuntu 20.04 (Focal Fossa)](http://releases.ubuntu.com/focal/)
		* ubuntu-20.04.1-desktop-amd64.iso	2020-07-31 16:52 	2.6G  
	* [Ubuntu 22.04.1 LTS (Jammy Jellyfish)](https://releases.ubuntu.com/jammy/)
		* 2023-07-11 20:14:19 (6.94 MB/s) - ‘ubuntu-22.04.2-desktop-amd64.iso’ saved [4927586304/4927586304]
	* [Ubuntu 22.10 LTS (Kinetic Kudu)](https://releases.ubuntu.com/kinetic/)
		* ubuntu-22.10-desktop-amd64.iso	2022-10-20 07:22	3.8G	
	* [Ubuntu 23.04 (Luna Lobster)](https://releases.ubuntu.com/lunar/)
		* 2023-07-11 21:30:07 (6.99 MB/s) - ‘ubuntu-23.04-desktop-amd64.iso’ saved [4932407296/4932407296]

#### Download iso image
```
cd ~/Downloads && mkdir -p ubuntu && cd ~/Downloads/ubuntu
wget https://releases.ubuntu.com/jammy/ubuntu-22.04.2-desktop-amd64.iso
wget https://releases.ubuntu.com/lunar/ubuntu-23.04-desktop-amd64.iso
```

#### Launch 'Startup Disk Creator'
* Install usb-creator from the terminal with`sudo apt install usb-creator-gtk` [more](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#2)
* Insert your USB stick (select ‘Do nothing' if prompted by Ubuntu)  
* On Ubuntu 18.04 and later, use the bottom left icon to open ‘Show Applications'. In older versions of Ubuntu, use the top left icon to open the dash  
* Use the search field to look for **Startup Disk Creator**   
* Select Startup Disk Creator from the results to launch the application. 

#### ISO and USB selection
It's likely that both your Ubuntu ISO and the correct USB device will have been 
detected and set as ‘Source disc image' and ‘Disk to use' in the application window. 
If not, use the ‘Other' button to locate your ISO file and select the exact USB 
device you want to use from the list of devices.

Click **Make Startup Disk** to start the process.  
[more](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#3)

#### Confirm USB device
Before making any permanent changes, you will be asked to confirm the USB 
device you've chosen is correct and you will provide your administrator password. 
This is important because any data currently stored on this device will be destroyed.  
[more](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#4)


#### Installation complete  
That's it! You now have Ubuntu on a USB stick, bootable and ready to go.  
[more](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#5)

### (1.2) Boot from USB flash drive

* :warning: **NOTE** Turn off BitLocker in Windows before install Ubuntu [:link:](https://www.youtube.com/watch?v=2mFeoiExeX0)

* :warning: **NOTE** You might got a single HDD/SSD set up in RAID (RST) mode, and the Ubuntu installer won't recognize your HDD/SSD until you switch your disk setting in the BIOS from RAID to AHCI. Please refer to this instructions > https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst 


Most computers will boot from USB automatically. Simply insert the 
USB flash drive and either power on your computer or restart it [:link:](https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#3). 
At boot time, press "F12" key to go into the BIOS settings (or Escape, F2 and F10 as alternatives) and make sure that you have set Boot from Removable Devices/USB option at the top. Save and exit BIOS. This will allow you to boot into live USB [:link:](https://itsfoss.com/reinstall-ubuntu/).

### (1.3) Setting up options for new installation
1. Once you are in the live USB, choose to install Ubuntu. 
	You should see the same welcome window we saw in the previous 
	Install from DVD step, prompting you to choose your language 
	and either install or try the Ubuntu desktop.
2. You’ll get the usual option for choosing your language and keyboard layout. 
3. Wireless. You’ll also get the option to download updates etc.
	"I don't want to connect to a Wi-Fi network right now"
	**NOTE** Go ahead with regular installation option as wireless will slowdown your regular installation.

4. Updates and other software
	* **Minimal installation** with web browser and basic utilities
  		* **NO** Download updates while installing Ubuntu
	  	* **NO** Install third-party software for graphics and WiFi hardware and additional format media formats
5. Install type
	* Install Ubuntu alongside Windows Boot Manager
		* Erase Ubuntu version and reinstall 
		* INSTALL NOW
	* Where are you?

6. Who are you?
  * Your name: **mxochicale**
  * Your computer's name: **machine-version**
  * Pick a username: **mxochicale**
  * Choose Password:
  * Confirm Password:
    * Require my password to login

7. Complete installation and remove the installation medium then prese ENTER!!!

### (1.3) References
* https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu
* https://www.youtube.com/watch?v=RghpdQH1bpo
* https://www.youtube.com/watch?v=lIF8e_5F9B4
* https://itsfoss.com/reinstall-ubuntu/
* https://www.youtube.com/watch?v=2mFeoiExeX0 


## Setting up new installation
### (2.1) Install [basics.sh](basics.sh) tools which also update and upgrade OS
```
wget https://raw.githubusercontent.com/mxochicale/tools/master/ubuntu/basics.bash
```
and run
```
sudo echo
bash basics.bash
rm basics.bash 
```

### (2.2) Add aliases and functions to .bashrc file 
```
wget https://raw.githubusercontent.com/mxochicale/tools/main/bashrc/append_aliases_to_bashrc.bash
```

append lines to bashrc:
```
bash append_aliases_to_bashrc.bash
```

Reload bashrc file
```
source ~/.bashrc
```

```
cd
rm append_aliases_to_bashrc.bash
```

### (2.3) Setup .vimrc
```
cd
wget https://raw.githubusercontent.com/mxochicale/tools/master/vim/.vimrc
```
See [here](https://github.com/mxochicale/tools/tree/master/vim) for more about vim configuration 


### (2.4) Github Setting up
* set up
```
git config --global user.name "Miguel Xochicale"
git config --global user.email "email@sth.com"
```
* Setting up SSH keys
See further details [here](../github/SSH.md)


### Settings of the terminal 
	preferences
		General: Use the system fixed width font > Ubuntu Mono Regular 13
		Colors: Green on black
		Background > Transparent background 0.9  
	[close]

### File Manager Preferences
	1. Open Files
	2. Edit > Preferences> Behaviour
	3. [CLICK] Single click to open items


### Setting left-handed mouse
  Go to Setting Manager to configure the left-handed mouse

### Unlock libre office launchers and others from the desktop
by removing from favorites with a right-click!

### Install google chrome
* see installations [tools/chrome](../chrome)


## (3) Tricks for Ubuntu
This section contains a list a collection of tricks for Ubuntu and Ubuntu-like distributions (i.e. Debian).

### Ubuntu 16.04
#### Remove show desktop in the alt-tab application switcher 
```
sudo apt-get install compizconfig-settings-manager
```
Now open CCSM and search for Ubuntu Unity plugin, go to Switcher tab. 
Then tick the check box next to `Disable Show Desktop in the switcher` 

[:link:](https://askubuntu.com/questions/167263/how-can-i-remove-show-desktop-from-the-alt-tab-application-switcher)


#### Unity grabs Alt and Super key
```
sudo apt-get install compizconfig-settings-manager
```
Start it from the Dash or by typing `ccsm` from the terminal  
Type "Ubuntu Unity plugin" in the filter box on the left, and click on the Ubuntu Unity Plugin:

General >> `key to show the HUD when tapped` >> "< Disabled >"     
Launcher >> `Key to show the Dash, Launcher and Help Overlay` >>  "< Disabled >"  

References
* [how-do-i-prevent-ubuntu-from-capturing-the-alt-key-to-show-the-hud](https://askubuntu.com/questions/151951/how-do-i-prevent-ubuntu-from-capturing-the-alt-key-to-show-the-hud)
* [-unity-grabs-alt-and-super-key](https://askubuntu.com/questions/764253/virtualbox-in-ubuntu-16-04-unity-grabs-alt-and-super-key)


#### Increase/Decrease Shell Workspaces
Start it from the Dash or by typing `ccsm` from the terminal  
Select `General Options` >> Deskop Size

or 

Change the number of columns, type the following command, changing the final number to the number you wish. Press Enter. [:link:](https://help.ubuntu.com/stable/ubuntu-help/shell-workspaces.html)
```
gsettings set org.compiz.core:/org/compiz/profiles/unity/plugins/core/ hsize 3`
```

#### Make the selected tab in the terminal more prominet
For Ubuntu 14.04 and 16.04, create a file named `~/.config/gtk-3.0/gtk.css` and place
the following into it
```
TerminalWindow .notebook tab {
    background-color: #e2e0dd;
}

TerminalWindow .notebook tab:active {
    background-color: #f2f1f0;
}
```
[:link:](https://askubuntu.com/questions/40332/how-to-make-selected-tab-in-terminal-more-prominent)


#### Disable the screensaver-lock
Go to System Settings...Brightness and Lock:  
The default screensaver idle time is 10 minutes, and the screen is locked once the screensaver activates:  
You can adjust the idle time (or disable the screensaver), and also disable the lock:  
Simply close Brightness and Lock to apply the new settings.

[:link:](https://askubuntu.com/questions/177348/how-do-i-disable-the-screensaver-lock)


#### suspend-hibernate-from-command-line
Install

```
sudo apt-get install powermanagement-interface

```
Then
```
sudo pm-suspend
```
[:link:](https://askubuntu.com/questions/1792/how-can-i-suspend-hibernate-from-command-line)




#### Move faster in Bash command line
http://teohm.com/blog/shortcuts-to-move-faster-in-bash-command-line/

#### Sorry Ubuntu 16.04 has experienced internal error solve

1.Open a terminal window.   
2.Type in the following commands, then hit Enter after each:   
```
sudo gedit /etc/default/apport

enabled=0
```

https://www.youtube.com/watch?v=w7FEA1N11jo


#### How to give this permission (-r--rwx-rw-) using CHMOD? [duplicate]

```
chmod
```

[:link:](https://unix.stackexchange.com/questions/259088/how-to-give-this-permission-r-rwx-rw-using-chmod/259092) [:link:](https://unix.stackexchange.com/questions/259088/how-to-give-this-permission-r-rwx-rw-using-chmod/259092)


#### nautilus-open-terminal
```
sudo apt-get install nautilus-open-terminal
nautilus -q  
```
https://askubuntu.com/questions/207442/how-to-add-open-terminal-here-to-nautilus-context-menu


