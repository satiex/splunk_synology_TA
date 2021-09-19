# splunk_synology_TA
This repo contains a Synology Technical Add-On for Splunk.

```
.
└──TA_synology
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
- I used [TA-qnap](https://github.com/diogofgm/TA-qnap) by @diogofgm as a starting point.
- ITWhisperer from the [Splunk Community Forums](https://community.splunk.com/) provided assistance with file size conversions.

# Synology DSM Technical Add-on for Splunk

## System requirements
- Tested on Synology DSM v7.0-41890
- Tested with Splunk 8.1.1

## Installation
Install the add-on on: 
Search Heads - The add-on contains search time extractions 

## Configuration
### Splunk
- Configure a new index and give it a name (synology).

#### Receiving syslogs on Splunk
NOTE: We recommend that you forward logs from Synology to a dedicated Syslog server (rsyslog, syslog-ng) which will then forward the logs to Splunk.
- Configure a new Data Input using a UDP/TCP port such as 514 pointing to the new index using the "synology" sourcetype.

### Synology DSM
- Install the Log Center package from the Package Center.
- Configure the Log Sending settings.
  - Server: IP or hostname of Splunk Indexer, Splunk Heavy Forwarder, or your Syslog server which then forwards logs to Splunk.
  - Port: Listening port (514)
  - Transfer Protocol: UDP or TCP
  - Log format: BSD (RFC 3164)

![image](https://user-images.githubusercontent.com/22540060/133915040-7bb8b20f-cea8-4096-8784-b12ed310aaa1.png)

- Configure the Log Filters settings.
  - For the most verbose logs, configure as per image below.
  
![image](https://user-images.githubusercontent.com/22540060/133915532-cb0c0240-b993-4cfa-bcb8-906917e1a669.png)

- Configure the File Transfer logs.
  - Go to Control Panel > File Services
  - For SMB, click Enable Tranfer Log and then configure the Log Settings.
    - For the most verbose logs, configure as per image below.

![image](https://user-images.githubusercontent.com/22540060/133915733-e38f3427-d9ba-4fd3-9149-46de92e36e94.png)
   
   - For AFP, click Enable transfer log.
![image](https://user-images.githubusercontent.com/22540060/133917124-bb856f98-6180-404a-9794-b313b1218662.png)
 


For more information please refer to the [Synology documentation](https://kb.synology.com/en-global/DSM/help/LogCenter/logcenter_client?version=7).

## Support
Please file bug reports to our [GitHub issue tracker](https://github.com/satiex/splunk_synology_TA/issues) and they will be addressed as soon as possible.

## TODO
- Synology DSM has a lot of featuers and functionality. I have not yet explored which actions or events generate a log. If you would like to contribute, please test as much of the different features of your Synology DSM and work on the field extractions for each event.
- I'm currently attempting to get file sizes into a consistant format (Bytes). I've started a post in the Splunk Community forums here: https://community.splunk.com/t5/Splunk-Search/Converting-variable-File-Size-Units-with-dot-points-to-bytes/m-p/567504
- The regular expressions for much of the field extractions needs tightening up.
