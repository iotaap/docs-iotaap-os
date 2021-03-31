# SD Card Filesystem

!!! warning "Notice"
    From IoTaaP OS version 4, SD card is only optional component of the system. Although we recommend using SD card to enable features
    such as data backup and system logs, you device will boot without SD card by loading configuration and security certificates
    from [internal filesystem](internal-fs.md).

## IoTaaP OS File system structure
FS structure will be automatically created on first boot

```
├── home
│   └── iotaap
│       └── data.log    
└── var
    └── log
        └── SYS00000.LOG
```

- home/iotaap/data.log is temporary file that will contain dropped data (e.g. if connection was lost) that will be removed after being successfully published
- var/log/SYS*****.log will contain system logs in multiple files limited to 50MB per file, oldest file will be dropped when total log size is greather than 2GB
