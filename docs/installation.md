![Logo](img/FirmmLogo.png)

# Prerequisites for installation

A Linux system capable of running either Docker or Singularity for FIRMM software and either Samba or rsync for DICOM transfer.

**NOTE**: *FIRMM has been tested with several different flavors of Linux operating systems by communicating DICOMs over the same network from Siemens (tranfer via Samba) and GE (transfer via rsync) scanners.  Basic Samba configuration and installation are included in FIRMM installation, along with DICOM transfer scripts to be copied to the scanner host.  Automatic Docker install and configuration only included for Ubuntu 16 through Ubuntu 18 and Redhat 7 systems.  If you have a different operating system, simply install Docker or Singularity separately before installing FIRMM.*

### Download FIRMM's installation package from NITRC

Log in or `ssh -X` to your Linux machine of choice (Ubuntu 16+ or Redhat 7+ recommended).

Point your browser to **[the NITRC page for FIRMM](http://www.nitrc.org/projects/firmm)**, click "Downloads" on the left-hand menu and download the "offline install package" zip file for the release of your choice.  Make a new directory and move the .zip file there. Example:

```
cd ~/Downloads
mkdir firmm
mv firmm-v3.2.5_offline_install_package.zip firmm/
```

Change to the directory where you moved the .zip file and unzip it. Example:

```
cd firmm
unzip firmm-v3.2.5_offline_install_package.zip
```

### Run the Installer

There are two different ways to run the install file depending on your distribution.

For Debian/Ubuntu:

```
sudo ./FIRMM_install.sh
```

For Redhat/CentOS, you might need to "su root" instead of "sudo":

```
su root
./FIRMM_install.sh
```

The installation script will present a series of questions so you can choose between a Siemens or GE installation and between a Docker or Singularity installation.

There will be notes at the end of the install about usage for FIRMM, and for setting up DICOM transfer for the chosen scanner vendor. Also make sure to check the other pages on this documentation site for DICOM transfer information.

Good luck!
