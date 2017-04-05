# Configurations

## Make virtual machines visit host physical machine and visit themselves each other.

<https://superuser.com/questions/406632/how-can-i-setup-a-guest-guest-network-connection-with-virtualbox>

    Open your VM settings
    Choose the Network section of the settings dialog
    On the Adapter 2 tab
        Check the box for Enable Network Adapter
        Changed Attached to to Host-Only Adapter
 