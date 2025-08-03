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
   Bridged Adapter
6. Power on VM
7. Select Install Rocky 9.6
8. Select Software Selection
     Check:
     Server with GUI
     Virtualization Tools
     Basic Web Server
     Development Tools
     RPM Development Tools
     Security Tools
     Done
9. Set Root password, create a user account, verify installation destination, set the name of the vm in Network & Hostname, and finally set the timezone.
10. Begin Installation, reboot when prompted.
11. Login to the VM
12. Select Device on the VBox window, then "insert guest additions cd image"
13. Run the installation when prompted, a VirtualBox Guest Additions Installation window will populate.
14. Reboot VM once install is complete: [capstone@wazuhserver ~]$ reboot
15. Created a shared folder for git. Open Gitbash and type: mkdir ~/git **Note - Download Gitbash here: https://git-scm.com/downloads **
16. Attached the shared folder to the VM. VM Window --> Devices --> Shard Folder --> Shared Folders Settings
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
20. Obtain Wazuh filees
    curl -sO https://packages.wazuh.com/4.12/wazuh-install.sh
    chmod 744 wazuh-install.sh
    ./wazuh-install.sh -dw rpm -da x86_64
21. curl -sO https://packages.wazuh.com/4.12/config.yml
22. Edit the config.yml
    Change IP address for indexer, server, and dashboard to 127.0.0.1 since this machine will be an all-in-one server.
23. Run the ./wazuh-install.sh -g to create the certificates. For a multi-node cluster, these certificates need to be later deployed to all Wazuh instances in your cluster.
24. mkdir /git/wazuh
25. Copy or move the following files to /git/wazuh
    wazuh-install.sh
    wazuh-offline.tar.gz
    wazuh-install-files.tar
26. Installing Wazuh
    Create install.sh in the wazuh directory
    #!/bin/bash
    

