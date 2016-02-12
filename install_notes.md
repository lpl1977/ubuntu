Notes on installing Ubuntu 14.04 LTS and preparing for PLDAPS

Start with only a single monitor connected.
After installing Ubuntu 14.04 LTS use Software Updater to install updates.
Change NVIDIA driver to current tested version in Software and Updates (on 02/12/16 that is 352.63).  The most recent driver on the NVIDIA webiste does not appear to be, in general, compatible with lightdm.

Run the following to get compilers  
sudo apt-get update  
sudo apt-get upgrade  
sudo apt-get install build-essential  

Download Synaptic Package Manager

Download MATLAB installer from the mathworks website; useful to keep the installer to easily download and update other toolboxes later.  Run the installer as  
sudo ./install  
Only download MATLAB 8.6  
Can set the initial working folder in Preferences->General

Download Psychophysics Toolbox  
http://psychtoolbox.org/download/#Linux  
Use the subversion based installation  
sudo apt-get install subversion  
sudo apt-get install linux-lowlatency 
Run DownloadPsychToolbox('~/Documents/MATLAB/')  
Get the libdc1394-22 on Synaptic if there is a problem running Screen  

Now activate the second monitor (Datapixx monitor)  
Run XOrgConfCreator and allow it to create the X configuration file
