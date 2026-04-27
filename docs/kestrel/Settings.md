# Settings



## Identifiers
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
A default value can be created by using teh {field:null} option.

Example:
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
Use property list and values to ignore files

## Misc Options
- Create assembly groups
- Ignore missing components in Assemblies
- Ignore toolbox components
- Unsuppressed all assembly components
- Create local folders in Onshape (set root directory)
- default onshape folder
- company override
- Mapped material density units

# Non-CAD files
extnesions, matching files
export drawings as PDF or DXF
upload drawings to new documetns vs upload drawings to associated document (by filename)




