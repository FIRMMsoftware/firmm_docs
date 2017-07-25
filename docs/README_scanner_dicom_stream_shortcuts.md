![Logo](img/FirmmLogo.png)

# FIRMM DICOM Stream Shortcuts

The following is a detailed document describing how to setup and use FIRMM's built-in DICOM stream start and stop shortcuts for a SIEMENS scanner.  These SIEMENS shortcut files are generated upon FIRMM install and can be copied over to the SIEMENS scanner using the Advanced User Mode or Administrative access.

## Creating the shortcut files

Upon installing FIRMM (*read the FIRMM_INSTALLATION.pdf for full installation instructions*) the install script outputs a mostly-ready set of FIRMM shortcuts for use with a SIEMENS scanner.  Review the shortcut files output to the `~/FIRMM/v2.1.0/support_files` folder (*default for your FIRMM user*) for accuracy with regards to your FIRMM username, FIRMM Samba password, and IP address.

*NOTE: Only SIEMENS scanners using the VE11B and VE11C softwares have been tested to work with these shortcuts.*

## Copying the shortcuts from your FIRMM Linux Computer

The `~/FIRMM/v2.1.0/support_files` folder contains two Windows MS-DOS BAT (a.k.a. batch) files, two icon files and two shortcut files for use on the scanner computer:

- `FIRMM_session_start.bat`
- `FIRMM_session_stop.bat`
- `FIRMM_logo_color.ico`
- `FIRMM_logo_grey.ico`
- `FIRMM_session_start.lnk`
- `FIRMM_session_stop.lnk`

There are many ways to copy the shortcut files, either locally with a flash drive or other removable media or remotely via network transfer protocols like SCP or RSYNC.  For Windows users, you may want to try **[WinSCP](https://winscp.net/eng/index.php)** for simple network access to your FIRMM computer's file system.

## Setup on the scanner computer

- **ADVANCED USER NOTE:** If you are not already logged in to advanced user, press `Ctrl+Esc` on the keyboard to open the start menu and click `Advanced User`.  You might need to consult your local scanner tech to get the password or help you do this.
- **VE11C NOTE:** If your scanner is running VE11C, you may also need to disable embedded control while you are copying the shortcuts in order for them to work. Press `Ctrl+Esc` on the keyboard to open the start menu and click `MREmbeddedControlGUI` (search for it in the search bar if you don't see it to click).  Turn off embedded control, but leave the GUI open.  You might need to consult your local scanner tech to get the password or help you do this.


1. Copy the batch files, shortcuts and icons to a folder on your scanner computer.  We recommend a folder like `T:\FIRMM` (on some SIEMENS Prisma scanners, `T:` is mapped as `C:\Medcom\user`).
1. On the keyboard, press `Ctrl+Esc` to open the start menu. Open Windows Explorer or click `Computer` and navigate to the folder from above.
1. Independently for the `FIRMM_session_start` and `FIRMM_session_stop` files, **CAREFULLY** right-click and hold the mouse button on the file, move it a bit to "pick it up", then while holding the mouse button down, press `Ctrl+Esc` on the keyboard and drag and drop each shortcut file into the top of the start menu.  When you release the right mouse button you will want to choose the **Create shortcut here** option.


- **NOTE: MAKE SURE YOU TURN EMBEDDED CONTROL BACK ON VIA THE MR EMBEDDED CONTROL GUI!!!** If you don't you'll probably get in trouble with your scanner tech.

<div class="page-break"></div>

## How to use these shortcuts

Once the shortcuts are made and available on the scanner computer, all that remains is to test them.  The best practice is to:

1. Register a patient/subject.
1. Start the DICOM stream with your scanner computer start menu shortcut.
1. Begin acquisition.
1. Open FIRMM on another computer and click **Start**.
1. Continue acquisition to the end (*FIRMM will only display an FD trace and time estimates after the first EPI scan*).
1. **AFTER ACQUISITION IS OVER:** Stop the DICOM stream with your other scanner computer start menu shortcut.

That's it!  Please enjoy the use of these FIRMM shortcuts and provide any feedback or questions to the [FIRMM email account](mailto:firmmsoftware@gmail.com) or the [FIRMM website](http://firmm.us).
