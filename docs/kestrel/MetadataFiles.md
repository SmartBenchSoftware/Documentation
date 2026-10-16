# `_MMD.txt` File Schema

This document defines the text format for `_MMD` metadata files.
Kestrel is not able to directly integrate into other CAD platforms.
In order to migrate files with metadata into Onshape, temporary plain text metadata files need to be generated.
The files need to be created in "%appdata%/SmartBench Software/" path.
Kestral will read the runfile to find files, and the metadata files in order to upload to Onshape.

Users may either use the provided macro to generate _MMD files, or use their own methods.

## File naming

Use this naming pattern:

`<original-file-name-with-dots-replaced-by-underscores>_MMD.txt`
Files must be place in the "%appdata%/SmartBench Software/" path.

Example:

- Original CAD file: `Gearbox.sldasm`
- Metadata file: `Gearbox_sldasm_MMD.txt`

Note that the extension remains within the filename.

## Format rules

- Plain text file
- One record per line
- Records are identified by fixed prefixes
- Values are unquoted
- Windows paths should be written as full paths when applicable

## Line types

### 1) File path record

```text
---FILEPATH---<source file full path>
```

Use once to identify the source file.

---

### 2) Property record

```text
---PROPERTY===<property name>---VALUE===<property value>
```

Use for metadata properties not specific to a configuration (ie custom properties).
If a property is not found in the configured properties, Kestrel will default to these non-configured properties.

---

### 3) End-of-properties marker

```text
---ENDPROPERTIES---
```

Marks the end of normal property records.

---

### 4) Configuration file path record (optional)

```text
---CONFIGURATION===<configuration name>---PATH===<configuration-specific file path>
```

Use for files that have multiple configurations.
Configured files must have each configuration as a separate file. Each file needs to have the target configuration saved as the active configuration.
Onshape uploads will only look at the active configuration.

---

### 5) Configuration property record (optional)

```text
---CONFIGUREDPROP===<configuration name>---PROPERTY===<property name>---VALUE===<property value>
```

Use when a property value is specific to one configuration.

---

### 6) Configuration-specific component record (optional)

```text
---CONFIGUREDCOMP===<parent configuration name>---COMPONENT===<component name>---PATH===<component file path>---COMPCONFIG===<component configuration>---TRANSFORM===<16 comma-separated transform values>
```

All component lists are defined by configuration - including a default configuration.
All files are uploaded to Onshape with a configuration included.

---

### 7) Drawing PDF path record (optional, drawing files)

```text
---PDF===<exported PDF full path>
```

Use for drawing metadata when a PDF export path is available.


### 8) Material records (optional, part files only)

Material metadata lets Kestrel apply the CAD material to the uploaded Onshape part. The material **name** is emitted as a normal property record using the reserved `{swmaterial}` property name; the material **database id** and **density** are emitted as their own record types.

```plaintext
---PROPERTY==={swmaterial}---VALUE===<material display name>
---MATERIALID===<material database>|<material name>
---MATERIALDENSITY===<density in kg/m^3>

```

- `---PROPERTY==={swmaterial}---VALUE===` — the applied material name (e.g. `1023 Carbon Steel Sheet (SS)`). This is a standard property record and must appear before `---ENDPROPERTIES---`.
- `---MATERIALID===` — the material database file and internal material name, separated by a pipe (`|`)
- `---MATERIALDENSITY===` — the material density in `kg/m^3`. Omit this line (or use `0`) when density is unavailable; Kestrel will skip the density update.

A material is only applied in Onshape when a material name is present. The density is ignored unless a material is also mapped.

---

### 9) Configured material records (optional, part files)

Use these when a material differs per configuration. Values are keyed by configuration name and take precedence over the part-level material records above; configurations without their own material fall back to the part-level values.

```plaintext
---CONFIGUREDMATERIAL===<configuration name>---VALUE===<material display name>
---CONFIGUREDMATERIALID===<configuration name>---VALUE===<material database>|<material name>
---CONFIGUREDMATERIALDENSITY===<configuration name>---VALUE===<density in kg/m^3>

```

---

### Material example (part)

```plaintext
---FILEPATH---C:\CAD\Bracket.sldprt
---PROPERTY==={filename}---VALUE===Bracket.sldprt
---PROPERTY==={swmaterial}---VALUE===1023 Carbon Steel Sheet (SS)
---MATERIALID===1023 Carbon Steel Sheet (SS)
---MATERIALDENSITY===7858.000032
---ENDPROPERTIES---

```

---


## Minimal valid `_MMD` examples

### Part (minimal)

```text
---FILEPATH---C:\CAD\Bracket.sldprt
---PROPERTY==={filename}---VALUE===Bracket.sldprt
---ENDPROPERTIES---
```

### Drawing with PDF

```text
---FILEPATH---C:\CAD\Bracket.slddrw
---PROPERTY==={filename}---VALUE===Bracket.slddrw
---ENDPROPERTIES---
---PDF===C:\CAD\Bracket.pdf
```

### Assembly with one component

```text
---FILEPATH---C:\CAD\TopLevel.sldasm
---PROPERTY==={filename}---VALUE===TopLevel.sldasm
---ENDPROPERTIES---
---CONFIGUREDCOMP===default---COMPONENT===PartA-1---PATH===C:\CAD\PartA.sldprt---COMPCONFIG===Default---TRANSFORM===1,0,0,0,0,1,0,0,0,0,1,0,0,0,0,1

```
