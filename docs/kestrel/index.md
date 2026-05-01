# Kestrel

Kestrel is an Onshape data migration tool. Kestrel allows users to manage the desktop to cloud migration process by simplifying file import, metadata management, and preventing file duplication.

Kestrel does not directly integrate into any desktop CAD Software. It requires use of other metadata preparation tools to facilitate the migration process.

Sign up for [Kestrel Here](https://kestrel.sbs)


## Quick Start Guide

### 1. Sign Up For Kestrel

Sign up for [Kestrel Here](https://kestrel.sbs).
You must sign up for Kestrel with the same email address as your Onshape account.
During the sign up process you will be required to log into Onshape in order to verify your account.
Data is managed at the Onshape company level. Your Onshape account must belong to a company. When you verify your account, you must log into the enterprise/company you will migrate to.

### 2. Download the Kestrel App

Go to the Desktop App page and download the Kestrel Desktop App.
The app is self updating and may require a whitelist from your company's IT department.
A non-self updating version is also available.

### 3. Configure Kestrel

Open the settings page and configure your options and parameters.

Be sure to configure a Unqiueness value for the database to use to prevent file duplicate.
Set all of your field mappings for part and assembly metadata.

[Learn more about the settings](kestrel/Settings.md)

### 4. Use Kestrel to Generate the Runfile

Kestrel uses a plain text file to manage file metadata extraction and uploads.
The format of this file can be found [Here](kestrel/Runfile.md)
The first screen of Kestrel will allow you to select files and generate a Runfile.

You may also create or modify this runfile with other applications in order to work with vaults, PDMs, ERPs, and more.

### 5. Generate Metadata

Kestrel is not able to directly open CAD files or read their metadata.
The migration process requires extracting metadata through other means. Read the "Runfile and _MMD files" page for more information.
A Solidworks macro example is provided on the downloads page that can aid in this process.

Run the provided macro while will generate _MMD files and update the status of items in the Runfile.

[Learn about the Metadata file format](kestrel/MetadataFiles.md)

### 6. Migrate to Onshape

Once data has been extracted and prepared for upload, use Kestrel to migrate files to Onshape.
The second tab in Kestrel is used to upload extracted metadata and files into Onshape.
Kestrel reads the runfile in order to determine which files to migrate to Onshape.
Files are directly imported into your Onshape, and the records of those files are added to the Kestrel database.

