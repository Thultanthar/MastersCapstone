1. Download Oracle VirtualBox: https://www.virtualbox.org/wiki/Downloads
2. Once installed download Rocky Linux DVD ISO: https://download.rockylinux.org/pub/rocky/9/isos/x86_64/Rocky-9.6-x86_64-dvd.iso
3. Open VirtualBox
4. VM Creation:
   Name: "<vm name>"
   Folder: Default Path
   ISO Image: "<Path to Rocky ISO>"
   Check Skip Unattended Installation
   Base Memory: 8192
   Processors: 4
   Hard Disk Size: 100GB
5. Power on VM
6. Select Install Rocky 9.6
7. Select Software Selection
     Check:
     Server with GUI
     Virtualization Tools
     Basic Web Server
     Development Tools
     RPM Development Tools
     Security Tools
     Done
8. Set Root password, create a user account, verify installation destination, set the name of the vm in Network & Hostname, and finally set the timezone.
9. Begin Installation, reboot when prompted.
10. Login to the VM
11. Select Device on the VBox window, then "insert guest additions cd image"
12. Run the installation when prompted, a VirtualBox Guest Additions Installation window will populate.
13. Reboot VM once install is complete: [capstone@wazuhserver ~]$ reboot
14. Created a shared folder for git. Open Gitbash and type: mkdir ~/git **Note - Download Gitbash here: https://git-scm.com/downloads **
15. Attached the shared folder to the VM. VM Window --> Devices --> Shard Folder --> Shared Folders Settings
     Select the Folder with the + icon
     Folder Pather: Select Other and find the git folder we created in your home directory c:/Users/UserName/git
     Folder Name will be git
     Mount point will be /git as well
     Check Auto-mount and Make Permanent
     Finally select OK, OK
16 On your VM type: sudo mkdir /git
17. If you run into issues with the mount do the following
     Map to a location other than the user folder.
18. Navigate to the git folder using git bash on the host system.
19. Run a git clone "<this repo's url>"
20. 
