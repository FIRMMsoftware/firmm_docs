![Logo](img/FirmmLogo.png)

# Installation

Version 2.1 written by Eric Earl (OHSU), Jon Koller (WUSM), Rachel Klein (OHSU), and Andrew Van (WUSM).  There is a FAQ section for troubleshooting common installation and configuration problems at the end of this document.

## Prerequisites for installation

Either an Ubuntu or CentOS Linux system capable of running Docker and Samba.

**NOTE**: *FIRMM has been tested with these two operating systems by communicating DICOMs over the same network from a SIEMENS scanner to the FIRMM system using a Samba mount.  Basic Samba configuration and installation are included in FIRMM installation.  Automatic Docker install and configuration only included for Ubuntu 14+ and Redhat 7 systems.*

## Download & Install

Log in or `ssh -X` to your Linux machine of choice (Ubuntu 14+ or Redhat 7+ recommended).

### Download

Get FIRMM's installation package by either of the following two methods:

**1. Web browser method**

- Point your browser to **[the NITRC page for FIRMM](http://www.nitrc.org/projects/firmm)**, click "Downloads" on the left-hand menu and download the "offline install package" zip file for the release of your choice.
- Also make sure to download any relevant USAGE or README PDFs.
- Make a new directory and move the .zip file there. Example:

```
cd ~/Downloads
mkdir firmm
mv firmm-v2.1.0_offline_install_package.zip firmm/
```

- Change to the directory where you moved the .zip file and unzip it. Example:

```
cd firmm
unzip firmm-v2.1.0_offline_install_package.zip
```


**2. `wget` method**

- Make a new directory and use `wget` to grab the install package from there. Example:

```
cd ~
mkdir firmm
cd firmm
wget http://firmm.projects.nitrc.org/firmm-v2.1.0_offline_install_package.zip
```

- Unzip the file. Example:

```
unzip firmm-v2.1.0_offline_install_package.zip
```

### Install

There are two different ways to run the install file depending on your distribution.

For Debian/Ubuntu:

```
sudo ./FIRMM_basic_install.sh
```

For Redhat/CentOS:

```
su root
./FIRMM_basic_install.sh
```

The installation script will detect whether Docker and Samba are installed and install them if needed. Alternatively, the user can install Docker and Samba first, then run FIRMM_basic_install.sh.

![FIRMM basic install script](img/basic_install.png)

<div class="page-break"></div>

## Frequently Asked Questions (FAQ)

**Q. Does FIRMM store DICOMs?**

**A.** Any DICOMs used by FIRMM will be automatically deleted from the FIRMM computer after two days. Therefore, it is **very important** that users never count on FIRMM for long term data storage.

**Q. How do I get data from my scanner to FIRMM?**

**A.** To use FIRMM effectively, DICOMs need to be transferred as fast as possible to the incoming DICOM directory on the FIRMM host computer.

- **SIEMENS:** Set up and run `ideacmdtool` or the FIRMM start/stop shortcuts on your scanner.  Instructions for this are available in our ideacmdtool README or shortcuts README, respectively.
- **GE:** Please [email us](mailto:FIRMMsoftware@gmail.com) for help.
- **PHILIPS:** Please [email us](mailto:FIRMMsoftware@gmail.com) for help.

When the FIRMM installation script is run, it makes two Windows batch files on the FIRMM machine. They are called `FIRMM_session_start.bat` and `FIRMM_session_stop.bat`. Getting these to the scanner from the FIRMM host PC will allow SIEMENS users to use DICOM streaming start/stop shortcuts.  Read our shortcuts README for more information.

**Q. Does FIRMM work with GE or PHILIPS scanners?**

**A.** FIRMM is designed to work with any scanner as long as DICOM data can be sent to a Samba shared network directory on the FIRMM host computer.

**Q. How do I test FIRMM?**

**A.** After connecting to the FIRMM host computer via `ssh -X firmm_host` (where `firmm_host` is your FIRMM Linux system's name), run `FIRMM -t`. This will start FIRMM on the `firmm_host` computer and copy a few test DICOM series to the incoming DICOM directory specified in the settings. Remember to click **Start FIRMM** in the browser window.  FIRMM will close automatically a little after the test is finished.

**Q. How do I change the FD thresholds?**

**A.** Run `FIRMM -s` on the FIRMM host computer. This will open the settings menu.

**Q. Can I revert to a previously installed version of FIRMM if needed?**

**A.** Users can revert to a previous version of FIRMM if the minor version is the same (e.g. reverting from 2.1.1 to 2.1.0). This would normally occur only if a bugfix that was introduced within the minor version caused problems running FIRMM on the user's system.

To revert to a previous version, find the previous version of the `run.sh` file that was created by the FIRMM automatic updater. It will be stored in the same directory as your current `run.sh` and its name will contain the previous version number (e.g. `run.sh.2.1.0`). Re-save that previous file under the name `run.sh`, replacing or removing your current file. Then you can run FIRMM commands as normal and the desired version will be used.

**Q. Does FIRMM work with structural data?**

**A.** Not currently, but we plan to add this capability in an upcoming release.

**Q. Where has FIRMM been tested?**

**A.** As of the creation date of this document, FIRMM has been tested on the following systems/scanners:
- Intel Xeon E5-2640v3 (16GB RAM, HDD) with Siemens Prisma scanner
- Dell Optiplex with i5 processor (4GB RAM, HDD) with Siemens Skyra scanner
- Core i7-4790K (16GB RAM, SSD) with Siemens Prisma scanner

**Q. Why does FIRMM occasionally start processing a previous session when I start it?**

**A.** When FIRMM is launched, it looks for the latest directory in the DICOM streaming directory to process. If FIRMM is launched within 10 minutes of the conclusion of a **previous** scanning session for which DICOMs were sent to FIRMM, and no DICOMs from the **current** session have been sent yet, it will see the **previous** session as "new" and start processing it. To remedy this, close FIRMM and re-launch it **after** some DICOMs have been sent for your current session. These can be any DICOMs, e.g. localizer, AAscout, T1, etc. FIRMM will see the new folder and wait for types of scans it can process (EPI, BOLD, etc.).
