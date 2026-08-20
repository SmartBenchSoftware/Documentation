# Quick Parse

The quick parse functionality allow Kestrel to quickly and easily directly read CAD files.
Quick Parse does not require any CAD system installed on your computer, and does not use any external programs or APIs to read the file.

Currently Solidworks 2012-2026 files are supported. Other files may be supported, but the status is currently unknown.

Note that this function is in beta and might have difficult to spot issues during the migration process.
Be sure to do a small test with the function first to ensure that it is working properly. Running a small test is helpful if you need to remove incorrect files from your Kestrel company database.

## Using Quick Parse

To use Quick Parse, start by adding files to your runfile as you normally would.
Before using another Metadata Extraction method (Such as the macro) - click the Quick Parse button to launch the process.
Click Start and wait for the process to complete.

Files that succeed quick parse will be marked as such in the runfile, and do not require further metadata extraction.
Not all files are supported. Some files will require further extraction.


## File Support

Quick Parse does not support files that contain configurations. All configured files need to be separately extracted.

Files with unexpected formats might also not be compatible.
If you have files that are not supported, and do not contain a configuration, email support@smartbenchsoftware.com. By sharing sample files with us, you can help increase the range of compatible files.

Drawings are not supported by Quick Parse.
