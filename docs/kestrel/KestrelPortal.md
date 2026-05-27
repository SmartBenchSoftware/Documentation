# Kestrel Portal

Kestrel provides an online portal for managing the migration database and logs.
This online database allows for multiple users to migrate files with Kestrel.

## Files

The Files database contains records for all items uploaded to Onshape.
The files database in Kestrel is managed at an Onshape company level. Users in the same Onshape company will be using the same database.

### Add items
Items can be manually added to the files database. This can be used to include already uploaded items, or Onshape native parts to replace imported files during assembly construction.

### Import CSV

Users may import existing items into the Kestrel database through a CSV file. This may be used for files that were already migrated manually, or in order to use Onshape native parts in place of imported parts in assemblies.

To import a CSV, first download the CSV template.
Fill out all the required fields, and re-import the file into Kestrel.
Please note that editing with Excel may cause unexpected issues, as excel is known to corrupt CSV files or save with unsupported format changes.

### Deleting Items

Items that were uploaded to the Kestrel database can be removed with the "Delete Selected" button.
Please note that this does not remove them from your Onshape.

## Logs

All file upload attempts, and database changes are recorded in the logs.
The logs give the ability to easily audit migrations, and understand potential issues (such as files being skipped).

## Desktop App

This page contains the download links for the Kestrel desktop app, along with any provided macros to aid in the metadata preparation process.
It is recommended to use the Kestrel launcher as it will automatically update Kestrel upon launch. Older versions of the Kestrel desktop app cannot be used once an update has been released.

## Changing User Company
Your account and Kestrel data is all managed by your verified Onshape Company ID.
In the case where a sandbox environment is used and a move to production is required, the user will need to switch Onshape Company.
This can be done by clicking the user email in the top right of the Kestrel web portal.
This will bring you to the user profile page. On the user profile page is a button for "Switch Company". This will require authenticating with Onshape. During this process, be sure to select the correct company in the Onshape auth page. If no company selection was available, make sure to log out of Onshape before initiating the switch company process.
If the auto-updating nature of the application causes network or IT issues, you may directly download the Kestrel desktop app. But note, that updates will need to be manually downloaded.

The Kestrel app requires Windows 7 or later, or windows server 2012 R2 or later.
Kestrel requires an internet connection to Onshape.
