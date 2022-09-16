# Update Search Macros

!!! info "Recommended Step"

To ensure this App functions efficiently, it is important to update a few search macros. Change the following macros to their appropriate values. For more information on the search macros used in this app, see [Search Macros Reference](../../reference/reference-macros.md).

## How to Update Macros

1. Open the OPNsense app for Splunk.
1. Navigate to Settings > Advanced Search > Search macros.

    ??? question "Not seeing any results"
        If no results are found, be sure that the "App" context is set to the OPNsense app, owner is set to "Any", and choose "Created in the App" from the remaining drop-down.

1. Click the macro name to modify.

## Update Index Macros

Update the index specific macros to the indexes being used for the OPNsense data. Updating these to the correct values will increase performance of searches.

Macro | Default | Description | Example Value
----- | ------- | ----------- | -------------
opnsense_system_index | index=* | Update to the specific index being used for the opnsense:system sourcetype created from the System modular input. see [OPNsense Add-on: Modular Inputs](https://splunk-opnsense-ta-documentation.readthedocs.io/en/latest/getting-started/configure-inputs/configure-modinput/) | `index=netfwsystem`

## Update Search Related Macros

Update this search macro **only** if you are using DMA. see [Configure Data Model Acceleration](configure-dma.md) for more information.

!!! warning
    Updating this macro to "true" without first enabling data model acceleration will cause the searches in dashboards to fail or show no results.

Macro | Default | Description | Example Value
----- | ------- | ----------- | -------------
opnsense_summariesonly | summariesonly=false | Defaults to not using summarized data from the CIM. Set to "true" if using data model acceleration. | `summariesonly=true`

--8<-- "includes/abbreviations.md"
