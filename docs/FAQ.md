![Logo](img/FirmmLogo.png)

## Does FIRMM store DICOMs?

Any DICOMs used by FIRMM will be automatically deleted from the FIRMM computer after two days. Therefore, it is **very important** that users never count on FIRMM for long term data storage.

## How do I get data from my scanner to FIRMM?

To use FIRMM effectively, DICOMs need to be transferred as fast as possible to the incoming DICOM directory on the FIRMM host computer.

- **SIEMENS:** Set up and run `ideacmdtool` or the FIRMM start/stop shortcuts on your scanner.  Instructions for this are available in our ideacmdtool README or shortcuts README, respectively.
- **GE:** Please [email us](mailto:info@firmm.io) for help.
- **PHILIPS:** Please [email us](mailto:info@firmm.io) for help.

When the FIRMM installation script is run, it makes two Windows batch files on the FIRMM machine. They are called `FIRMM_session_start.bat` and `FIRMM_session_stop.bat`. Getting these to the scanner from the FIRMM host PC will allow SIEMENS users to use DICOM streaming start/stop shortcuts.  Read our shortcuts documentation for more information.

## Does FIRMM work with GE or PHILIPS scanners?

FIRMM is designed to work with any scanner as long as DICOM data can be sent to a Samba shared network directory on the FIRMM host computer.

## How do I test FIRMM?

After connecting to the FIRMM host computer via `ssh -X firmm_host` (where `firmm_host` is your FIRMM Linux system's name), run `FIRMM -t`. This will start FIRMM on the `firmm_host` computer and copy a few test DICOM series to the incoming DICOM directory specified in the settings. Remember to click **Start FIRMM** in the browser window.  FIRMM will close automatically a little after the test is finished.

## How do I change the FD thresholds?

The FD thresholds can be adjusted **before beginning a session* by using the settings tab in the FIRMM GUI. See our Usage documentation for more information for more information.

## Can I revert to a previously installed version of FIRMM if needed?

Users can revert to a previous version of FIRMM if the minor version is the same (e.g. reverting from 2.1.1 to 2.1.0). This would normally occur only if a bugfix that was introduced within the minor version caused problems running FIRMM on the user's system.

To revert to a previous version, find the previous version of the `run.sh` file that was created by the FIRMM automatic updater. It will be stored in the same directory as your current `run.sh` and its name will contain the previous version number (e.g. `run.sh.2.1.0`). Re-save that previous file under the name `run.sh`, replacing or removing your current file. Then you can run FIRMM commands as normal and the desired version will be used.

## Does FIRMM work with structural data?

Not currently, but we plan to add this capability in an upcoming release.

## Where has FIRMM been tested?

As of the creation date of this document, FIRMM has been tested on the following systems/scanners:

- Intel Xeon E5-2640v3 (16GB RAM, HDD) with Siemens Prisma scanner
- Dell Optiplex with i5 processor (4GB RAM, HDD) with Siemens Skyra scanner
- Core i7-4790K (16GB RAM, SSD) with Siemens Prisma scanner
