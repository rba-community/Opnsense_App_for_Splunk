# Search Macro Reference

Macro | Default | Description
----- | ------- | -----------
`opnsense_comment(1)` | "" | Ability to set comments within the App. This is no longer required as of Splunk 8.1 and three back ticks may be used. See [Splunk Docs: Adding Comments](https://docs.splunk.com/Documentation/Splunk/latest/Search/Comments) for more information.
`opnsense_summariesonly` | summariesonly=false | Defaults to not using summarized data from the CIM. Set to "true" if using data model acceleration.
`opnsense_system_index` | index=* | Update to the specific index being used for the opnsense:system sourcetype created from the System modular input. see [OPNsense Add-on: Modular Inputs](https://splunk-opnsense-ta-documentation.readthedocs.io/en/latest/getting-started/configure-inputs/configure-modinput/)
`opnsense_tstats` | tstats \`opnsense_summariesonly\` prestats=true | Used by dashboards within this app. Modifying this macro will impact dashboards from loading searches properly.
`opnsense_local_ip(1)` | $ip_field$ IN(10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16, 224.0.0.0/4) | Used by dashboards within this app to find local IPs.
`opnsense_trunk(2)` | eval $t_field$=if(mvcount($t_field$)>$t_num$, mvappend(mvindex($t_field$, 0, $t_num$-1), "..Truncated.."), $t_field$) | Truncates multivalued fields based off the integer passed to the macro.
`opnsense_ctime(1)` | convert timeformat="%F %T %Z" ctime($utime$) | Converts unix timestamp into human readable format.
