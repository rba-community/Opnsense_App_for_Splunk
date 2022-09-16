# Data Model Acceleration

!!! info "Optional"

Enabling Data model acceleration (DMA) will allow the searches to perform much more efficiently for larger datasets. If you run into issues with dashboards taking too long to load, data model acceleration will increase performance with a slight increase to resource usage. To learn more about data model acceleration see [Splunk Docs: Accelerate data models](https://docs.splunk.com/Documentation/Splunk/latest/Knowledge/Acceleratedatamodels).

## Enable Acceleration

Before enabling Data model acceleration, ensure the index being used for the OPNsense data has been allowed on the CIM add-on list of indexes.

1. In Splunk web, Navigate to Apps > Manage Apps.
1. Find the App "Splunk Common Information Model" and click `set up` on the right side.
1. For each of the models being used, whitelist the appropriate indexes. For more information on the data models used by this app/add-on see [OPNsense Add-on sourcetype reference](https://splunk-opnsense-ta-documentation.readthedocs.io/en/latest/reference/reference-sourcetypes/).

    * This will allow only the indexes listed to be accelerated. If you are ingesting data into other indexes and also want them to be included in the acceleration, list them here as well.

    ???+ tip
        To identify which indexes are being used by the CIM, the following query can be run:

        ```shell
        | multisearch
            [| tstats summariesonly=f prestats=t count from datamodel=Authentication by index
            | eval datamodel="Authentication"]
            [| tstats summariesonly=f prestats=t count from datamodel=Web by index
            | eval datamodel="Web"]
            [| tstats summariesonly=f prestats=t count from datamodel=Network_Sessions by index
            | eval datamodel="Network_Sessions"]
            [| tstats summariesonly=f prestats=t count from datamodel=Network_Resolution by index
            | eval datamodel="Network_Resolution"]
            [| tstats summariesonly=f prestats=t count from datamodel=Intrusion_Detection by index
            | eval datamodel="Intrusion_Detection"]
            [| tstats summariesonly=f prestats=t count from datamodel=Network_Traffic by index
            | eval datamodel="Network_Traffic"]
        | stats count by index datamodel
        | stats values(index) as indexes by datamodel
        | eval indexes=mvjoin(indexes, ",")
        ```

        **Notice** that this data searches for all data and not just the OPNsense data. Modify the search as needed.

1. Once the appropriate indexes are listed, check the "Accelerate" box at the top and save.
1. The data model will begin to build. This may take some time depending on the size.
1. Update the `opnsense_summariesonly` macro to `summariesonly=true`. Setting this will force the dashboards to use accelerated data only, optimizing the searches. see [Update Macros](../configure-macros/#update-search-related-macros) in this documentation for more information.

--8<-- "includes/abbreviations.md"
