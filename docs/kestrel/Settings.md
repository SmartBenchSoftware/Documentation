# Settings
The setup of Kestrel is important for it to function properly. It is strongly recommended to read through this entire guide before using Kestrel.


## Identifiers (File uniqueness)
For Kestrel to maintain it's database of migrated files and prevent duplicates, every file is required to have an identifier.
The uniqueness of a file is based on the combination of identifier field, configuration, and file type.
The uniqueness property may be a part number, part number + revision, or filename. If no identifier is provided, the full file path will be used.

When a file is migrated to Onshape, the file is checked for the uniqueness property, if a file with that uniquness already exists in the database, it will be skipped.
During the assembly creation process, the uniqueness properties of each component are used to build the assembly from already migrated parts.
If there is overlap in this property, the first file will be migrated, even if the two files are different.

## Property Mappings

In order to set file metadata in Onshape, each property needs to be mapped.
There are three settings pages for properties: Parts, Assemblies, Drawings.
You must create a mapping between the name of the property that appears in the original CAD files, and the property in Onshape.
Onshape properties are loaded from Onshape automatically. If the property does not appear in the list, ensure that it is active.

### Complex Mappings

Complex property mappings gives users the ability to manipulate metadata during migration. A complex mapping is identified automatically by containing the specific replacement sequences in the CAD property name.

The following keywords are available - assuming they were also included in the _MMD file.

{field:null}

{filename}

{configuration}

{title}

{subject}

{savedate}

{comment}

{keywords}

{author}

{field:<name>}

Any other CAD property in the _MMD file can be used with the {field:<name>} mapping. The value of the cad filed with the name <name> will be used. Note that the <> are not included but the {} are required.
Literal strings outside of the complex mappings will be kept.

A default value can be created by using the {field:null} option.

**Example:**

{field:partnumber}_{field:revision} -> 1000500_A

PN{field:partnumber} -> PN100500

### Property Value Mapping Tables

It may be required during migration to update or translate property values. For example, if the names of finishes changed from "Annodized - black" to just "Black".
Kestrel gives the ability thorugh a Mapping Table.
For a property mapping row, there is a "Table" button. Clicking opens that property's value mapping table.
The user must provide a 1 to 1 mapping of CAD values to Onshape values.
For list type properties in Onshape, these values must match a valid "value" in Onshape - not to be confused with Onshape display value.

## Additional Mappings

Kestrel requires 3 additional mappings for the File Uniquness, Onshape Document Name, and Version.
These property mappings are used to setup metadata in Onshape that might not exist in the desktop CAD environment.
By default, the file uniquness and document name are set to the file path.
It is not recommended to use File Path for the file uniqueness as it will not prevent duplicates across multiple Kestrel Users, or if there were issues with duplicate files in the legacy system.


Version Property is used to create the initial version in Onshape. Currently Kestrel does not support a "live updating" workflow where versions will be updated in Onshape after creation.

## Ignore Files
When selecting folder of files to upload to Onshape, it may be required to ignore or skip certain types of files.
This is done during the upload to Onshape and may not be done during metadata extraction depending on your method of extraction.

The ignore files mapping look at specific values in specifical CAD property fields.
If the match condition is met, the file is skipped during upload.

## Misc Options
Kestrel provides some additional settings that may either apply to the runfile generation or Onshape upload process

#### Create assembly groups
This option will group an entire assembly during creation process. Can be helpful as no mates are migrated.
  
#### Ignore missing components in Assemblies
If Kestrel is missing components in Assemblies, it will not be able to create them fully and report an error message.
This option suppresses that issue and warning and allows creation of assemblies with missing components.

#### Ignore toolbox components
Option set in the runfile for metadata processing.

#### Unsuppressed all assembly components
Option set in the runfile for metadata processing.

#### Create local folders in Onshape (set root directory)
Kestrel can replicate the folder structure from your local computer inside of Onshape.
When selected and a root directory is selected, the file structure is replicated inside the default Onshape folder.
Onshape documents are created in the correct folder when possible.

#### Default onshape folder
Default the Onshape upload destination. The root directory in Onshape to match the local folder root if the create local folders option is selected.

#### Company override
Only used when a user is having an issue with Onshape authenticate. This will force the login screen in Onshape for a specific company.

#### Mapped material density units
Mapped material units set in Onshape

# Non-CAD files
Drawing and non-CAD files can be associated to Part/Assembly files and uploaded to their document in Onshape.
Drawings and non-CAD files do not have accessible metadata and need to be associated by similar file names.
The options are to match either the whole file name (minus extension) or the first X characters.

This page also gives the option to set the export type for native drawings into either PDf or DXF file types for upload to Onshape.






