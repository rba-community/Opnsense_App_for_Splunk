# OPNsense App for Splunk

![GitHub](https://img.shields.io/github/license/ZachChristensen28/Opnsense_App_for_Splunk)

The OPNsense App for Splunk helps make your firewall data meaningful. Visualize system or security related events recorded by the [OPNsense Firewall](https://opnsense.org/). This app requires the [OPNsense Add-on for Splunk](https://splunkbase.splunk.com/app/4538/).

 Info | Description
------|----------
Version | 1.0.1 - See on [Splunkbase](https://splunkbase.splunk.com/app/5372/)
Vendor Product Version | [OPNsense 20.7](https://opnsense.org/)
APP has a web UI | Yes, this app contains views.

```TEXT
Version 1.0.1

New
- Added System Dashboard. This is powered by the modular input from the Add-on. 
```

## Requirements

- Install [TA-opnsense](https://github.com/ZachChristensen28/TA-opnsense) (version 1.3.3 or higher) also located on [Splunkbase](https://splunkbase.splunk.com/app/4538/)
- Install [Splunk Common Information Model](https://splunkbase.splunk.com/app/1621/) (version 4.x)

### Where to Install

Splunk platform Instance type | Supported | Required | Actions required/ Comments
----------------------------- | --------- | -------- | --------------------------
Search Heads | Yes | Yes | Install on search heads
Indexers | no | no | Not supported
Heavy Forwarders | no | no | Not supported

## Setup

(Recommended) Update the following search macros to their appropriate values:

Macro | Default | Description
----- | ------- | -----------
`opnsense_summariesonly` | summariesonly=false | Controls Data Model Acceleration. Update to "true" if utilizing Data model acceration, otherwise, leave default.
`opnsense_system_index` | index=* | If using the modular input from Add-on, update this setting to the correct index for better performance.

## Bugs/Feature requests

Please open an issue or submit a feature request at [github.com](https://github.com/ZachChristensen28/Opnsense_App_for_Splunk)

### Feature Requests

- OPNsense netflow logs to Splunk walkthrough

## Versions

```TEXT
Version 1.0.0
- Initial Creation
```
