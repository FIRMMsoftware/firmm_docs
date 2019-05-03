![Logo](img/FirmmLogo.png)

## v3.0.14 (2018-10-17)
* **MINOR UPDATE:** Added "For investigational use only" note.

## v3.0.13 (2018-09-25)
* **BUGFIX:** Fixed a bug where FIRMM would crash if given a BOLD image that had a non-square slice matrix.
* **BUGFIX:** Ignore CMRR BOLD single-band reference image (SBRef).

## v3.0.12 (2018-04-10)
* **NEW FEATURE:** Multi-echo BOLD: FIRMM will use the first echo volume of each BOLD frame to calculate motion and ignore all other echo volumes
* **BUGFIX:** Fixed a bug where processed image data was not properly cleaned up. The ~firmmproc/FIRMM/v3*/sessions/ directory should be much smaller now.

## v3.0.10 (2018-03-26)
* **BUGFIX:** fixed a bug where DICOMs couldn't be written to the incoming DICOM folder because the samba user connecting was different from the local FIRMM user

## v3.0.9 (2018-03-02)
* **BUGFIX:** settings will now be applied automatically when clicking "Save Profile"

## v3.0.8 (2018-02-28)
* **BUGFIX:** fixed error due to spaces or other special characters in "Patient Name" or "Patient ID" DICOM header fields

## v3.0.7 (2018-02-23)
* **NEW FEATURE:** Filtered FD: choose between displaying "raw" FD and "filtered" FD to account for artifactually-produced motion (for more information on the FIRMM FD filter, [see the FAQ entry](FAQ.md#what-is-the-firmm-fd-filter)
* **NEW FEATURE:** Ignore specific BOLD series from summary statistics and plot (user-selectable)
* **NEW FEATURE:** Select which DICOM folder to start processing
* **NEW FEATURE:** Change settings with the new Settings Tab in the FIRMM GUI

## v2.1.3 (2017-10-19) [Click here for FIRMM Version 2 Documentation](http://firmm.readthedocs.io/en/2.1.3/)
* **BUGFIX:** fixed incorrect FD for second frame of each series

## v2.1.2 (2017-08-24)
* **BUGFIX:** fixed temporary file cleanup in motion correction script
* **BUGFIX:** fixed install script not being able to find "release" version files

## v2.1.1b (2017-06-26)
* **FEATURE:** display framewise displacement (FD) of BOLD data during acquisition
* **FEATURE:** display summary table of BOLD series with how much low-motion data has been collected for each series
* **FEATURE:** predict how much scan time it will take to collect a specified amount of low-motion data
