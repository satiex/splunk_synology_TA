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
- Install the Log Center package from the Package Center.
- Configure the Log Sending settings.
  - Server: IP or hostname of Splunk Indexer or Splunk Heavy Forwarder
  - Port: listening port (514)
  - Transfer Protocol: UDP or TCP
  - Log format: BSD (RFC 3164)

![image](https://user-images.githubusercontent.com/22540060/133915040-7bb8b20f-cea8-4096-8784-b12ed310aaa1.png)

- Configure the Log Filters settings.
  - For the most verbose logs, configure as per image below.
  
![image](https://user-images.githubusercontent.com/22540060/133915532-cb0c0240-b993-4cfa-bcb8-906917e1a669.png)

For more information please refer to the [Synology documentation](https://kb.synology.com/en-global/DSM/help/LogCenter/logcenter_client?version=7).

- Configure the File Transfer logs.
  - Go to Control Panel > File Services > SMB and click Enable Tranfer Log and then configure the Log Settings.
  - For the most verbose logs, confige as per image below.

![image](https://user-images.githubusercontent.com/22540060/133915733-e38f3427-d9ba-4fd3-9149-46de92e36e94.png)


## Support
Please file bug reports to our [GitHub issue tracker](https://github.com/satiex/splunk_synology_TA/issues) and they will be addressed as soon as possible.
