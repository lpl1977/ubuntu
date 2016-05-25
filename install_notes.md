##Notes on installing Ubuntu 14.04 LTS and preparing for PLDAPS  

####Install Ubuntu 14.04 LTS  
* Usually this is done from a USB stick you can create following instructions you can find on the internet, e.g.  http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx   
* I did not use logical volume management on the rig machines.  

####Before anything else:
1.  Start with only a single monitor connected.  
2.  Change NVIDIA driver to current tested version in Software and Updates (on 02/12/16 that is 352.63).  The most recent driver on the NVIDIA webiste does not appear to be, in general, compatible with lightdm (the windows manager).

####Get ready to install packages
1.  Update software
2.  Restart if requested  
3.  Get Synaptic Package Manager
4.  Try the following (not sure if it matters)  
```
sudo apt-get upgrade
sudo apt-get update
sudo apt-get autoremove
```

####Install some packages (they can all go on one line)
```
sudo apt-get install build-essential git xclip gksu subversion linux-lowlatency   
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
```

####Install MATLAB
1.  Download MATLAB installer from the mathworks website.  Keep the installer to easily download and update other toolboxes later.
2.  Run the installer as `sudo ./install`
3.  Download MATLAB 8.6 and image processing toolbox (needed by PLDAPS)
4.  Set the initial working folder in Preferences->General

####Download Psychophysics Toolbox  
http://psychtoolbox.org/download/#Linux  
Use the subversion based installation  
sudo apt-get install subversion  
sudo apt-get install linux-lowlatency 
Run DownloadPsychToolbox('/home/username/Documents/MATLAB/')  
Get the libdc1394-22 on Synaptic if there is a problem running Screen  

Now activate the second monitor (Datapixx monitor)  
Run XOrgConfCreator and allow it to create the X configuration file.  
Run XOrgConfSelector and make sure the configuration file is selected.  
Log out and log back in.  At this point the Datapixx monitor should be screen 1.  Note that there is not an xorg.conf file in /etc/X11/ as NVIDIA driver installation would normally try and create; instead, there are configuration files in the folder /etc/X11/xorg.conf.d  

Installing PLDAPS  
Install git:  
sudo apt-get install git  
https://help.github.com/articles/set-up-git/#platform-linux  
git config --global user.name <my name>
git config --global user.email <my email address>
Generate the ssh key.  I use the name as a passphrase.  
sudo apt-get install xclip  
Create clone of my PLDAPS fork  
sudo git clone https://github.com/lpl1977/PLDAPS.git  
Set the upstream fork to be the HukLab fork  
https://help.github.com/articles/syncing-a-fork/  

Install Datapixx toolbox from VPixx website.  Make sure the toolbox takes precedence over the Psychtoolbox versions.
