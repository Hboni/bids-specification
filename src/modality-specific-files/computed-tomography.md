# Computed Tomography

Support for Computed Tomography (CT) was developed as a
[BIDS Extension Proposal](../extensions.md#bids-extension-proposals).
Please see [Citing BIDS](../introduction.md#citing-bids)
on how to appropriately credit this extension when referring to it in the
context of the academic literature.

!!! example "Example datasets"

    Several [example CT datasets](https://bids-standard.github.io/bids-examples/#ct)
    have been formatted using this specification
    and can be used for practical guidance when curating a new dataset.

    Further CT datasets are available from [OpenNeuro](https://openneuro.org).

## Terminology and conventions

## CT recording data

{{ MACROS___make_filename_template(
   "raw",
   datatypes=["ct"],
   suffixes=["ct"])
}}

CT data MUST be stored in the `ct` directory.
NIfTI files with the `_ct` suffix.

### CT metadata

#### Acquisition informations

{{ MACROS___make_sidecar_table("ct.CTAcquisition") }}

#### Indexes

CT scan is an important source of dose experienced by patients.
To quantify radiation dose, multiple indexes are used to estimate dose from scanner perspective (CTDIvol) or from patient perspective (SSDE).
These indexes are used to control safety for patients and optimize scan parameters.

{{ MACROS___make_sidecar_table("ct.CTIndexes") }}

### Time

### Reconstruction

{{ MACROS___make_sidecar_table("ct.CTReconstruction") }}

### Hardware information

### Institution information

### Tissue description

### Deidentification information

Describes the mechanism or method used to modify or remove metadata
and/or pixel data to protect the patient or participant's identity.

<!-- This block generates a metadata table.
These tables are defined in
  src/schema/rules/sidecars
The definitions of the fields specified in these tables may be found in
  src/schema/objects/metadata.yaml
A guide for using macros can be found at
 https://github.com/bids-standard/bids-specification/blob/master/macros_doc.md
-->
{{ MACROS___make_sidecar_table("mri.DeidentificationMethod") }}

Each object in the `DeidentificationMethodCodeSequence` array includes the following RECOMMENDED keys:

<!-- This block generates a table describing subfields within a metadata field.
The definitions of these fields can be found in
  src/schema/objects/metadata.yaml
and a guide for using macros can be found at
 https://github.com/bids-standard/bids-specification/blob/master/macros_doc.md
-->
{{ MACROS___make_subobject_table("metadata.DeidentificationMethodCodeSequence.items") }}

#### Example (`*_ct.json`)

### Recommended patient data
