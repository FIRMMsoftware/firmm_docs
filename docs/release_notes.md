![Logo](img/FirmmLogo.png)

## v3.2.13 (2020-06-06)
* **BUGFIX:** FIRMM filtered FD numbers applied incorrect scaling for rotations about L-R axis resulting in a small discrepancy.  Note: the impacts before and after the fix have been evaluated and determined to be inconsequential.

## v3.2.12 (2020-01-21)
* **BUGFIX:** The FIRMM GUI would crash if "Filtered FD" was selected, and zero filtered frames were available for a given series. This is now fixed.

## v3.2.11 (2020-01-17)
* **BUGFIX:** The GE transfer script firmm_rsync.sh should now properly handle BOLD runs that are stopped before completion of the run.

## v3.2.10 (2020-01-14)
* **MINOR UPDATE:** Better log messages in the terminal.
* **MINOR UPDATE:** Debug logging information outputs to a log file, which can be located at /home/firmmproc/FIRMM/v3.2.10/code/FIRMM_processing.log.
* **BUGFIX:** FIRMM could get stuck reading GE DICOM data if data for several frames were arriving all at once (like during the beginning of an 800ms TR multi-band sequence while the reconstruction is catching up). This is now fixed.

## v3.2.9 (2019-12-01)
* **NEW FEATURE:** FIRMM is now compatible with GE! [Click here](https://firmm.readthedocs.io/en/3.2/ge_dicom_streaming/) for more info about DICOM transfer.
* **NEW FEATURE:** CSV output can be found in /home/firmmproc/FIRMM/v3.2.9/sessions/FIRMM_logs
* **NEW FEATURE:** FIRMM is now compatible with [Singularity](https://sylabs.io/singularity/)! The installer will ask if you want to use Docker or Singularity. This has been tested using Singularity 2.6.3 on a Neurodebian system, and on a system running Singularity 3.2.0.
* **MINOR UPDATE:** [Printable quick start page for Siemens](https://github.com/FIRMMsoftware/firmm_docs/raw/3.2/docs/FIRMM_Operator_Instructions_SIEMENS.pdf). Print it, put it up on the wall in the control room, stop answering questions about how to run FIRMM!
* **MINOR UPDATE:** The DICOM transfer script for Siemens has been improved to more clearly report if the scanner->FIRMM connection has been made.
* **BUGFIX:** Previously, FIRMM would use only the first TR encountered to make time calculations, and the calculations would then be wrong for subsequent series with a different TR. This is now fixed, sessions with multiple TRs should report summaries/progress/predictions correctly.

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
