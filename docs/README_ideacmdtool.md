![Logo](img/FirmmLogo.png)

**NOTE**: *FIRMM and ideacmdtool have been tested on both a Siemens Trio and Prisma.*

# Prerequisites for setup

* FIRMM version 2.1 or greater installed on a separate Linux computer that is networked to the scanner host computer. If FIRMM is not yet installed, visit [firmm.us](http://firmm.us) for more info.
* You will need to know the FIRMM computer IP address, referenced below as `[FIRMM_IP]`
* You will need to know the FIRMM user name and password, set during the installation of FIRMM. The user name is probably `firmmproc`.
* Select an available drive letter to use for mapping on the scanner host computer. In these instructions we use "Y:".
* Access to the "advanced user" on the Siemens scanner host computer

# Set default values

The instructions below will set the following defaults for ideacmdtool:

```
target port = -1
target path = y:
SendBuffered OFF
SendIMA OFF
```

* Make sure you're logged in as "advanced user". If you don't know what this means, ask your local Siemens tech.
* Press `Ctrl+Esc` to open the Windows start menu
* Click "Command Prompt" or "Run" and enter `cmd`
* Enter `ideacmdtool`
* Enter `4` (Online export defaults)
* Enter `1` (Target port), enter `-1`
* Enter `3` (Target path), enter `y:` (or whatever drive letter you want to use)
* Enter `4` (SendBuffered OFF)
* Enter `q` (back to main ideacmdtool menu)
* Enter `q` (exit ideacmdtool)

# Map FIRMM computer Samba share

Follow these instructions to map the FIRMM computer Samba share to a drive letter on the scanner host computer. We'll use "Y:" in this example, but you can use a different letter.

* Press `Ctrl+Esc` to open the Windows start menu, click "Computer" or "Windows Explorer"
* Click "Tools > map network drive", enter "Y:" and \\\\[FIRMM_IP]\\FIRMM_DICOM
* Make sure "use different credentials" is checked, click "OK"
* Enter [FIRMM_IP]\\firmmproc for the user name and enter the firmmproc password, click "OK"
* The DICOM folder should open

<div class="page-break"></div>

# MR session instructions

Follow these steps every time you run an MR session.

* Press `Ctrl+Esc` to open the Windows start menu, click "Computer" or "Windows Explorer"
* Make sure the "Y:" drive is mapped to the samba share on the FIRMM computer, \\\\[FIRMM_IP]\\FIRMM_DICOM. If it isn't, follow the instructions above to map it.
* On the scanner host computer, registrer a new patient.
* After the patient has been registered:
    - On the scanner computer, press `Ctrl-Esc`, select "Command Prompt" or "Run" and enter `cmd`
    - Enter `ideacmdtool`
    - Enter `5` for switches
    - Enter `8` to turn on DICOM transfer (SendIMA ON)
    - Enter `q`, enter `q` again to exit ideacmdtool, enter `exit` to exit command prompt
* Any scans that are "applied" after this should be sent to the FIRMM computer
