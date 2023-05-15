# App Dependencies

The following table describes the Add-ons that are needed to utilize the full capabilities of the app. Please install and configure these apps prior to deploying this app.

!!! danger "[Danger, Will Robinson](https://cultural-phenomenons.fandom.com/wiki/Danger,_Will_Robinson)"
    Failure to install any of the below apps/add-ons will cause this app to not function as intended.

Splunkbase Add-on | Version | Description
----------------- | ------- | -----------
[OPNsense Add-on (TA-opnsense)](https://splunkbase.splunk.com/app/4538/) | >= 1.5.3 | Technical Add-on needed for Splunk to correctly parse the OPNsense firewall data.
[Splunk Common Information Model](https://splunkbase.splunk.com/app/1621/) | >= 5.0.0 | The Splunk CIM normalizes the data into datamodels which this app leverages for performance.
