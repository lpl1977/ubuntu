##Notes on installing Ubuntu 14.04 LTS and preparing for PLDAPS  

####Install Ubuntu 14.04 LTS  
* Usually this is done from a USB stick you can create following instructions you can find on the internet, e.g.  http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx   
* I did not use logical volume management on the rig machines.  

####Before anything else:
1.  Start with only a single monitor connected on the DISPLAYPORT output of the graphics card.  
2.  Change NVIDIA driver to current tested version in Software and Updates (on 02/12/16 that is 352.63).  The most recent driver on the NVIDIA webiste does not appear to be, in general, compatible with lightdm (the windows manager).

####Get ready to install packages
1.  Update software
2.  Restart if requested  
3.  Get Synaptic Package Manager; this will be important for later steps when certain libraries are missing.
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
5.  Restart the computer

####Install Psychophysics Toolbox  
1.  Follow instructions at http://psychtoolbox.org/download/#Linux  
2.  Use the subversion based installation  
3.  Run DownloadPsychToolbox('/home/username/Documents/MATLAB/')  
4.  Use Synaptic Package Manager to find libdc1394-22 and install it
5.  Restart the computer
6.  Start MATLAB in super user mode i.e. `sudo matlab`
7.  Run a demo to make sure PTB is installed.  There will be an error if you didn't get the library.
7.  Quit MATLAB.

####Now activate the second monitor (Datapixx monitor)  
1.  Start MATLAB in super user mode
2.  Attach Datapixx to the computer with the DVI port.  If all goes well the desktop should spread across both screens.
3.  Run XOrgConfCreator and allow it to create the X configuration file.  Make sure and let it do a dual screen setup.  Follow the onscreen instructions.  I didn't bother with any advanced settings.  Accept the filename it proposes.
4.  Run XOrgConfSelector and make sure the configuration file is selected.  
5.  Log out and log back in.  At this point the Datapixx monitor should be screen 1.  If you  mouse over to it the pointer will turn to a black X with a white outline on a black background.  Note that there is not an xorg.conf file in /etc/X11/ as NVIDIA driver installation would normally try and create; instead, there are configuration files in the folder /etc/X11/xorg.conf.d  
6.  Run a PTB demo in MATLAB to make sure that everything is copacetic.  You should see that the NVIDIA GPU is used and that beamposition timestamping is enabled.  If all has gone well then the PTB screen will be screen 1 and the refresh rate will be around 120 Hz.  If this is not the case, you'll need to debug this.  Ask somebody for help or turn to the PTB user forum.
7.  As you try demos and startup PLDAPS you'll need to run various calibrations; just follow the instructions.

####Installing PLDAPS  
1.  Set up git on the computer.  Some helpful instructions can be found at https://help.github.com/articles/set-up-git/#platform-linux  
2.  Clone my PLDAPS fork--I prefer to use SSH for this.

####Install Datapixx toolbox   
This can come from VPixx website, but I had to get several files from VPixx and put them in the appropriate place.  At this point, copying from astaroth seems to be the best bet.  Make sure the toolbox takes precedence over the Psychtoolbox versions.

####Install updates for Eyelink
1.  Get the encryption key for the Eyeink repositories.  That can be found here:  http://download.sr-support.com/software/sr-research-public-key  Once you download it, import it under Authentication in the Software & Updates.
2.  Add the repositories for SR-Research  
  * deb http://download.sr-support.com/software SRResearch main
  * deb http://download.sr-support.com/
3.  Download and install the depository for the 64 bit Dataviewer (as of May 25, 2016 still in beta):  https://drive.google.com/a/sr-research.com/file/d/0B6lPq22M74XKVnN1cU5QcTBiekU/view?usp=drive_web
4.  Also install some packages:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```
5.  Finally install the hasp driver for your Data Viewer license key, which can be downloaded from the following link: http://sentinelcustomer.safenet-inc.com/sentineldownloads/?s=&c=all&p=all&o=Linux&t=Runtime+%26+Device+Driver&l=all#
