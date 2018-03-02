![Logo](img/FirmmLogo.png)

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
* **FEATURE:** predict how much scan time it will take to collect a sqecified amount of low-motion data
