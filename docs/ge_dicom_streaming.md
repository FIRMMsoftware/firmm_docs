![Logo](img/FirmmLogo.png)

**NOTE**: *This process has been tested on a GE DISCOVERY MR750*

# Prerequisites for setup
* FIRMM version 3.2b or greater installed on a separate Linux computer that is networked to the scanner host computer. If FIRMM is not yet installed, visit [firmm.io](http://firmm.io) for more info.
* You will need to know the FIRMM user name and password, set during the installation of FIRMM. The user name is probably `firmmproc`.
* You will need to know the FIRMM computer IP address, referenced below as `[FIRMM_IP]`
* ssh keys will need to be set to enable connection from the scanner host to the FIRMM computer without requiring a password
* Both firmm_monitor and firmm_rsync.sh must be on the user's sdc's PATH
* Any data that will be used for FIRRM monitoring will have a pulse sequence name of 'research/ABCD/muxepi'

# Set default values
* Edit the firmm_monitor script to set the default values:
    - REMOTEIP: `[FIRMM_IP]`
    - REMOTEUSER: FIRMM user name
    - REMOTEDIR: Directory on FIRMM computer that FIRMM will point to

# MR session instructions

Follow these steps every time you run an MR session.

* Start the FIRMM software on the remote Linux computer. When prompted for the directory to look for dicom data, point it to `REMOTEDIR` from the firmm_monitor script.
* Run the localizers for the scan.
* Open a command window and run firmm_monitor on the scanner host, givin the exam number as the only argument.
* Keep the monitor running for the duration of the session. When a new series is started it will detect the series type. If it is a multiband functional run it will start the transfer to the FIRMM machine.
* If a series doesn't finish running before the next starts, then the new series will not be transferred to the FIRMM computer.
