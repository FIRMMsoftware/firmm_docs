![Logo](img/FirmmLogo.png)

## v3.0.0 (COMING SOON!)
* **NEW FEATURE:** Filtered FD: choose between displaying "raw" FD and "filtered" FD to account for artifactually-produced motion
* **NEW FEATURE:** Ignore specific BOLD series from summary statistics and plot (user-selectable)
* **NEW FEATURE:** Select which DICOM folder to start processing. This allows one FIRMM computer to be used with two scanners simultaneously, and allows a user to start processing an "old" session.

## v2.1.3 (2017-10-19)
* **BUGFIX:** fixed incorrect FD for second frame of each series

## v2.1.2 (2017-08-24)
* **BUGFIX:** fixed temporary file cleanup in motion correction script
* **BUGFIX:** fixed install script not being able to find "release" version files

## v2.1.1b (2017-06-26)
* **FEATURE:** display framewise displacement (FD) of BOLD data during acquisition
* **FEATURE:** display summary table of BOLD series with how much low-motion data has been collected for each series
* **FEATURE:** predict how much scan time it will take to collect a sqecified amount of low-motion data
