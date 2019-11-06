![Logo](img/FirmmLogo.png)

**NOTE**: *This process has been tested on a GE DISCOVERY MR750*

# Prerequisites for setup
* FIRMM version 3.2b or greater installed on a separate Linux computer that is networked to the scanner host computer. If FIRMM is not yet installed, visit [firmm.io](http://firmm.io) for more info.
* You will need to know the FIRMM user name and password, set during the installation of FIRMM. The user name will be `firmmproc` unless FIRMM was installed sudo-less, in which case it will be the installer's user name. It is referenced below as `FIRMM_USER`.
* You will need to know the FIRMM computer IP address, referenced below as `FIRMM_IP`.
* ssh keys will need to be set to enable connection from the scanner host to the FIRMM computer without requiring a password, see instructions below.
* Copy firmm_monitor and firmm_rsync.sh from `${INCOMING_DICOM_DIR}/DICOM_stream_shortcuts/` to `/usr/g/bin/`.
* Sequences with a pulse sequence description (DICOM tag [0019,109E]) of 'EPI' will be sent to the FIRMM computer via rsync.

# Set ssh key instructions
1. Open terminal on the computer running FIRMM.
2. Type `ssh-keygen -t rsa -b 4096`.
3. Hit enter three times. This will create the ssh key at the default path and create it without a password.
4. Open terminal on the scanner host computer.
4. Type `scp FIRMM_USER@FIRMM_IP:~/.ssh/id_rsa.pub ~/`.
6. Type `mkdir -p ~/.ssh`.
7. Type `touch ~/.ssh/authorized_keys`.
8. Type `cat ~/id_rsa.pub >> ~/.ssh/authorized_keys`.
9. Type `rm ~/id_rsa.pub`.

# MR session instructions

Follow these steps every time you run an MR session.

* Start the FIRMM software on the remote Linux computer.
* Run the localizers for the scan.
* Open a command window and run firmm_monitor on the scanner host, giving the exam number as the only argument.
* Keep the monitor running for the duration of the session. When a new series is started it will detect the series type. If it is a multi-band functional run it will start the transfer to the FIRMM machine.
* If a series doesn't finish running before the next starts, then the new series will not be transferred to the FIRMM computer.
