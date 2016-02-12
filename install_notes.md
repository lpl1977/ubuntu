Notes on installing Ubuntu 14.04 LTS and preparing for PLDAPS

After installing Ubuntu 14.04 LTS use Software Updater to install updates.
Change NVIDIA driver to current tested version in Software and Updates (on 02/12/16 that is 352.63).  The most recent driver on the NVIDIA webiste does not appear to be, in general, compatible with lightdm.

Run the following to get compilers
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential

Download MATLAB installer from the mathworks website; useful to keep the installer to easily download and update other toolboxes later.  Run the installer as
sudo ./install
Only download MATLAB 8.6

Download Psychophysics Toolbox
http://psychtoolbox.org/download/#Linux
