# Configurations

## Make virtual machines visit host physical machine and visit themselves each other.

<https://superuser.com/questions/406632/how-can-i-setup-a-guest-guest-network-connection-with-virtualbox>

    Open your VM settings
    Choose the Network section of the settings dialog
    On the Adapter 2 tab
        Check the box for Enable Network Adapter
        Changed Attached to to Host-Only Adapter
 
 ## Virtual box - Configure Full Screen for debian(jessie)

 <https://www.youtube.com/watch?v=KJ5pObje1Dk>

    su
    apt-get update && apt-get upgrade
    apt-get install build-essential module-assistant
    m-a prepare
    mount /media/cdrom   # if no cdrom found, click [Insert Guest Additions CD Image...] menu of VBox
    sh /media/cdrom/VBoxLinuxAdditions.run
    reboot
