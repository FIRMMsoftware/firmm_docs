![Logo](img/FirmmLogo.png)

**NOTE**: *This process has been tested on a GE DISCOVERY MR750*

# Prerequisites for setup
* FIRMM version 3.2b or greater installed on a separate Linux computer that is networked to the scanner host computer. If FIRMM is not yet installed, visit [firmm.io](http://firmm.io) for more info.
* You will need to know the FIRMM user name and password, set during the installation of FIRMM. The user name is probably `firmmproc`.
* Both firmm_monitor and firmm_rsync.sh must be on the user's sdc's PATH

# Set default values
* Set REMOTEIP in firmm_rsync.sh to the IP Address of the computer running FIRMM
* Ensure that REMOTEUSER in firmm_rsync.sh matches the FIRMM user name (if the user name is `firmmproc` then it will)

# MR session instructions

Follow these steps every time you run an MR session.

* Run the localizers for the scan.
* Run firmm_monitor on the scanner machine, giving it the exam number as the only argument.
* Ensure that each series finishes running before the next starts.
* Any scans should be sent to the FIRMM computer
