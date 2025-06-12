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

CT scans can be acquired with unequal between-slice spacing.
However NIfTI assumes all 2D slices that form a 3D stack are equidistant.
These acquisitions can be resliced during conversion to obtain the same slice thickness.
The information of this reslising MUST be referenced in the `rec-` key (example: `rec-Resliced`).
In case of unequal between-slice spacing, NIfTI can be as raw data.

CT scans can also be acquired with gantry/detector tilt.
Titled acquisitions helps to focus acquisition on localization and reduce dose received.
In order to fit the 3D grid of NIfTI files tilted acquisition need [resample during conversion from DICOM](https://www.nitrc.org/plugins/mwiki/index.php/dcm2nii:MainPage#Computed_Tomography_.28CT.2C_CAT.29).
In case of gantry tilt, metadata `GantryTilt` is MANDATORY.
Information about resampled data can be stored in the `rec-` key as a free label (example : `rec-GTResampled`).

## CT recording data

{{ MACROS___make_filename_template(
   "raw",
   datatypes=["ct"],
   suffixes=["ct"])
}}

CT data MUST be stored in the `ct` directory.
NIfTI files with the `_ct` suffix.
In addition to the imaging data (*.nii) a _pet.json sidecar file MUST be provided.
The included metadata are divided into sections described below.

### CT metadata

#### Acquisition information

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
