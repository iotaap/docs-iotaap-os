# SD Card Filesystem

!!! warning "Warning"
    SD Card is the vital part of IoTaaP OS and device will not be able to boot if SD card with preloaded filesystem structure is
    not present in the SD card slot.

All configuration files are loaded from SD card which must contain predefined file structure, certificate, configurations, etc. 
SD card is the vital part of the whole system, used as temporary storage, backup storage, long-term storage, operational storage, etc. 

## IoTaaP OS File system structure
IoTaaP OS file system structure must be burned to the SD card before usage. 

```
├── etc
│   ├── device
│   │   ├── custom.cfg 
│   │   └── default.cfg
│   └── ssl
│       └── certs       
│           └── ca.crt 
├── home
│   └── iotaap
│       └── data.log    
└── var
    └── log
        └── SYS00000.LOG
```


- **etc/device/default.cfg** should be edited to match parameters given on IoTaaP console
- **etc/device/custom.cfg** can optionally contain custom JSON formatted data to be used from main program
- **etc/ssl/certs/ca.crt** is the ROOT certificate used for secure communication between device and IoTaaP Cloud
- **home/iotaap/data.log** is temporary file that will contain dropped data (e.g. if connection was lost) that will be removed after being successfully published
- **var/log/SYS#####.log** will contain system logs in multiple files limited to 50MB per file, oldest file will be dropped when total log size is greather than 2GB

!!! warning "SD Card Size"
    In order for your system to work properly micro SD card size should not be less then 4GB