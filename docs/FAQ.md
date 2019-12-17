![Logo](img/FirmmLogo.png)

## Does FIRMM store DICOMs?

Any DICOMs used by FIRMM will be automatically deleted from the FIRMM computer after two days. Therefore, it is **very important** that users never count on FIRMM for long term data storage.

## How do I get data from my scanner to FIRMM?

To use FIRMM effectively, DICOMs need to be transferred as fast as possible to the incoming DICOM directory on the FIRMM host computer.

- **SIEMENS:** Set up and run `ideacmdtool` or the FIRMM start/stop shortcuts on your scanner.  Instructions for this are available in our ideacmdtool README or shortcuts README, respectively.
- **GE:** Please [email us](mailto:info@firmm.io) for help.
- **PHILIPS:** Please [email us](mailto:info@firmm.io) for help.

When the FIRMM installation script is run, it makes two Windows batch files on the FIRMM machine. They are called `FIRMM_session_start.bat` and `FIRMM_session_stop.bat`. Getting these to the scanner from the FIRMM host PC will allow SIEMENS users to use DICOM streaming start/stop shortcuts.  Read our shortcuts documentation for more information.

## Does FIRMM write out motion data?

FIRMM writes out a CSV file with FD and motion numbers (with and without respiration filter) for each session. Assuming your FIRMM user home directory is something like `FIRMM_USER_HOME=/home/firmmproc`, the CSV can be found in the following directory on the FIRMM computer: `${FIRMM_USER_HOME}/FIRMM/v3.2.5b/sessions/FIRMM_logs`.

## Does FIRMM work with GE or PHILIPS scanners?

FIRMM is designed to work with any scanner as long as DICOM data can be sent to a SAMBA shared network directory on the FIRMM host computer.  All of our documentation and DICOM streaming shortcuts, etc., are currently built for ease of use with SIEMENS scanners and SIEMENS' real-time DICOM transfer.  With the release of version 3.2.5 we have added support for GE scanners. We are still working on support for a PHILIPS mode for FIRMM.

## How do I test FIRMM?

After connecting to the FIRMM host computer via `ssh -X firmm_host` (where `firmm_host` is your FIRMM Linux system's name), run `FIRMM -t`. This will start FIRMM on the `firmm_host` computer and copy a few test DICOM series to the incoming DICOM directory specified in the settings. Remember to click **Start FIRMM** in the browser window.  FIRMM will close automatically a little after the test is finished.

## How do I change the FD thresholds?

The FD thresholds can be adjusted **before beginning a session** by using the settings tab in the FIRMM GUI. See our Usage documentation for more information.

## Can I revert to a previously installed version of FIRMM?

Users can revert to a previous version of FIRMM if the minor version is the same (e.g. reverting from 2.1.1 to 2.1.0). This would normally occur only if a bugfix that was introduced within the minor version caused problems running FIRMM on the user's system.

To revert to a previous version, find the previous version of the `run.sh` file that was created by the FIRMM automatic updater. It will be stored in the same directory as your current `run.sh` and its name will contain the previous version number (e.g. `run.sh.2.1.0`). Re-save that previous file under the name `run.sh`, replacing or removing your current file. Then you can run FIRMM commands as normal and the desired version will be used.

## Does FIRMM work with structural data?

Not currently, but we plan to add this capability in an upcoming release.

## Where has FIRMM been tested?

As of the creation date of this document, FIRMM has been tested on the following systems/scanners:

- Intel Xeon E5-2640v3 (16GB RAM, HDD) with Siemens Prisma scanner
- Dell Optiplex with i5 processor (4GB RAM, HDD) with Siemens Skyra scanner
- Core i7-4790K (16GB RAM, SSD) with Siemens Prisma scanner

## What is the FIRMM FD filter?

New changes in MRI acquisition procedures bring new opportunities and challenges to BOLD imaging. One of the most drastic changes in acquisition procedures in recent years is the introduction of multiband imaging. However, an unintended consequence of the improved temporal and spatial resolution that accompanies multiband imaging is artifacts in motion estimates from post-acquisition frame alignment procedures, caused primarily by chest motion during respiration. Chest motion, secondary to respiration, changes the magnetic field (B0) and 'tricks' any frame-to-frame alignment procedure used in real-time motion monitoring into correcting a 'head movement' even though no actual head movement existed. In the newest version of FIRMM, an optional band-stop (or notch) filter to remove such respiration-related artifacts from motion estimates is available, thus giving a more accurate real-time representation of motion. For more detail, see our upcoming publication.

## Why did FIRMM stop receiving DICOMs after the scanner upgrade to VE11C?

FIRMM uses a SAMBA network mount to communicate between the SIEMENS scanner computer and the FIRMM computer. If you had previously used a SAMBA configuration file (located at `/etc/samba/smb.conf`) that had the line `guest ok = yes`, then with VE11C that will not work anymore. The solution is to replace the `guest ok = yes` line with `valid users = username` where `username` should be the FIRMM username. You will then need to have an administrator run the command `sudo smbpasswd -a username` where `username` is that same FIRMM user and then enter the FIRMM user's password when prompted for it. Lastly, update your DICOM streaming shortcut on the scanner with this FIRMM username and password and you should be ready to DICOM stream once again.

## How do I check if the scanner computer can see the FIRMM computer's SAMBA share?

Use `net view IP_ADDRESS` on the scanner computer in a Command Prompt where IP_ADDRESS is your FIRMM computer's IP address on the network. To get a Command Prompt on the scanner computer, log into advanced user mode and run `cmd`. The `net view IP_ADDRESS` command should show you any shared SAMBA network directories on the FIRMM computer. Otherwise, authentication or networking problems are happening.
