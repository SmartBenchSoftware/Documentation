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

### Property Tables



## Associated Files


