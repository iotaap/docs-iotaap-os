# Logs

IoTaaP OS will save system logs to SD card by default to the **var/log/SYS#####.log** file. Directory could contain multiple log files with maximum size of 50MB per file or 2GB in total. If maximum nuber of log files is reached, system will automatically delete oldest log file.

!!! warning "Notice"
    Please note that system logs will be disabled if SD card is not present. Your system will work, but you will not be able to 
    retreive system logs.


## Log tags
System can write multiple log types, categorized by tags

- **INFO** - Low priority event, usually describing standard system events
- **SYSTEM** - System related messages, usually boot messages or system information
- **WARNING** - Medium priority event, usually describing some system issue from which system can autonomously recover
- **ERROR** - High priority event, usually describing some fatal error that disables system from normal operation
- **USER** - Special priority tag, created from the main code using `writeToSystemLogs()` function

## Reading logs 
System logs can be checked by plugging SD card to the SD card reader and checking logs using log explorer (e.g. glogg), however this approach will cause downtime, since SD card has to be removed from the device.

Another way of reading logs is by using Serial Interface. Serial Interface dongle should be connected with PC usign mini USB cable and then connected with the board (otherwise it will cause device to reboot). Standard serial terminal (e.g. Termite) can be used to communicate with the device. 

By default real time logging is disabled (log messages will not be printed to the serial interface, but will be saved to the SD card if present).A few simple commands can be used in order to read and manage logs in real time.

Additionally, logs can be accessed via special MQTT topics, check [Logs via MQTT](./logs-mqtt.md)

## Real time log reading commands
System supports some simple commands to be used in real time. Standard serial configuration is; baud: `115200`, data bits: `8`, stop bits: `1`, parity: `none`, flow control: `none` and every command should be followed by CR and LF characters. 

- **debug_on** - Turn on real time logging
- **debug_off** - Turn off real time logging 
- **lines** - Number of lines to be displayed per page (in range: 1 to 100) (e.g. lines:20)
- **time** - Search for records on specific date and time (in `YYYY-MM-DD HH:MM:SS` format)
- **np** - Next page (displays next n (n is defined by `lines` command) records from current log location)
- **pp** - Previous page (displays previous n (n is defined by `lines` command) records from current log location)
- **clear_sys_logs** - Removes **ALL* system logs
- **stop** - Stops search after `time` command is used


!!! danger "clear_sys_logs command"
    Command `clear_sys_logs` will remove **ALL** system logs from SD card. This operation is irreversible and all system logs will be irretrievably removed. Use this command only if you know what you are doing.