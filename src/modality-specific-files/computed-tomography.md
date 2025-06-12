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

### Time

### Reconstruction

{{ MACROS___make_sidecar_table("ct.CTReconstruction") }}

### Hardware information

### Institution information

### Tissue description

### Deidentification information

#### Example (`*_ct.json`)

### Recommended patient data
