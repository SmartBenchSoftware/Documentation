# Solidworks Metadata Extraction 

To aid in the metadata extraction process for Solidworks files, a macro has been provided.

## Download the macro

The macro file can be download on the [Kestrel site](https://kestrel.sbs/DesktopApp) under the Download Macro section

## Requirements

The macro file requires a version of Solidworks 2020 or newer.
The macro may work with older versions, but potentially unintended results.
The macro will not work with Solidworks Connected or any version of Solidworks that does not allow for saving files locally.
Any addins or automations that are set to run automatically when a file is opened should be disabled.

## Running the macro

Before running the macro, be sure to close all open Solidworks files.

In the Solidworks menu go to Tools > Macro > Run, and select the provided macro file.

The macro will read your runfile contents and extract metadata for all included parts, and any required assembly components.

## Notes

As the macro does not have the option to stop or pause during running, it is possible that the extraction process could take a long period of time.
It is recommended to test with a small number of files (1-10), and to work with smaller subsets of migration data (~100 files at a time).
