##Notes on installing Ubuntu 14.04 LTS and preparing for PLDAPS  

####Start with only a single monitor connected.  

####After installing Ubuntu 14.04 LTS use Software Updater to install updates.  
--Find Sofware Updater in the Ubuntu Software Center  
--Restart if requested  
--Try the following (not sure if it matters)  
```
sudo apt-get upgrade
sudo apt-get update
sudo apt-get autoremove
```

####IMPORTANT TO DO THIS SECOND:  
Change NVIDIA driver to current tested version in Software and Updates (on 02/12/16 that is 352.63).  The most recent driver on the NVIDIA webiste does not appear to be, in general, compatible with lightdm.

Download from here the files  
Package.list  
Repo.keys  
sources.list  
sources.list.save  
These were created with the commands from http://askubuntu.com/questions/9135/how-to-backup-settings-and-list-of-installed-packages  
```
dpkg --get-selections > ~/Package.list  
sudo cp -R /etc/apt/sources.list* ~/  
sudo apt-key exportall > ~/Repo.keys  
```
and can be installed with    
```
apt-cache dumpavail > ~/temp_avail
sudo dpkg --merge-avail ~/temp_avail
rm ~/temp_avail
sudo apt-key add ~/Repo.keys  
sudo cp -R ~/sources.list* /etc/apt/  
sudo apt-get update  
sudo apt-get install dselect   
sudo dpkg --set-selections < ~/Package.list  
sudo dselect  
```

Run the following to get compilers  
sudo apt-get update  
sudo apt-get upgrade  
sudo apt-get install build-essential  

Download Synaptic Package Manager

Download MATLAB installer from the mathworks website; useful to keep the installer to easily download and update other toolboxes later.  Run the installer as  
sudo ./install  
Download MATLAB 8.6 and image processing toolbox (needed by PLDAPS)
Can set the initial working folder in Preferences->General

Download Psychophysics Toolbox  
http://psychtoolbox.org/download/#Linux  
Use the subversion based installation  
sudo apt-get install subversion  
sudo apt-get install linux-lowlatency 
Run DownloadPsychToolbox('~/Documents/MATLAB/')  
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
