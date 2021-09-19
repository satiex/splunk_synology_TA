# splunk_synology_TA
This repo contains a Synology Technical Add-On for Splunk.

```
.
└──splunk_synology_TA
  ├── default
  │   └── app.conf
  │   └── eventypes.conf
  │   └── props.conf
  │   └── tags.conf
  │   └── transforms.conf
  └── lookups
  │   └── transforms.conf
  └── lookups
  │   └── default.meta
  └── static
    └── appIcon.png
    └── appIcon_2x.png
```

This app is currently in development. Contributions are welcome.

## Credits
I used [TA-qnap](https://github.com/diogofgm/TA-qnap) by @diogofgm as a starting point.

# Synology DSM Technical Add-on for Splunk

## System requirements
- Tested on Synology DSM v7.0-41890
- Tested with Splunk 8.1.1

## Installation
Install the add-on on: 
Search Heads - The add-on contains search time extractions 

## Configuration
### Splunk
- Configure a new index (e.g. storage) for the new logs

#### Receiving syslogs on Splunk
NOTE: Its recommended to use a separate and dedicated syslog solution (e.g. rsyslog, syslog-ng, etc)
- Configure new TCP port (e.g. 514) pointing to the new index using the "synology:syslog" sourcetype

#### Monitoring log files
- Configure a new file monitor input pointing to the new index using the "synology:syslog" sourcetype

### Synology DSM
- Configure syslog outputs
For more information please refer to the [Synology documentation](https://kb.synology.com/en-global/DSM/help/LogCenter/logcenter_client?version=7).

![image](https://user-images.githubusercontent.com/22540060/133915040-7bb8b20f-cea8-4096-8784-b12ed310aaa1.png)

## Support
Please file bug reports to our [GitHub issue tracker](https://github.com/satiex/splunk_synology_TA/issues) and they will be addressed as soon as possible.
