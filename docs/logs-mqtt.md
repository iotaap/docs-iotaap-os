# Logs via MQTT - BETA

Additionally to standard [logs](./logs.md) access, there is an option to access your logs remotely via special MQTT topics.

## Reading logs 
Most of the commands from standard [logs](./logs.md) access are supported via MQTT, but this feature is still in BETA version. 

### Sending command
User can connect to the MQTT broker using some client application (such as MQTT.fx) and same access parameters provided on IoTaaP Console. 

Special topic `/<username/devices/<device-id>/logs-req` is used for requesting a response from the device. Following JSON message should be used:

```json
{
	"device":"DEVICE_ID",
	"command":"CMD_STRING"
}
```

#### Parameters

 - **device** - Device ID (one provided by IoTaaP Console)
 - **command** - One of the supported commands

### Receiving response
After sending command to the above-mentioned topic, user will receive a response on the following topic: `/<username/devices/<device-id>/logs-resp`, response
message is predefined and it will look like this:

```json
{
	"device":"DEVICE_ID",
	"command":"CMD_STRING",
	"response":"RESPONSE_STRING",
	"time":"TIMESTAMP",
	"part":PART_ID,
	"data":
	[
		"DATA1_STRING",
		"DATA2_STRING",
		...
		"DATAN_STRING"
	]
}
```

#### Parameters

 - **device** - Device ID (one provided by IoTaaP Console)
 - **command** - Requested command
 - **response** - Command response - will not be included if there is no special comand response (e.g. "Unknown command", "Print 10 lines.")
 - **time** - Device time when response was sent (e.g. 2021-01-29 20:48:12)
 - **part** - Response index (if there are multiple responses)  
 - **data** - Log data

!!! danger "Topic usage"
    You should **NOT** use this special topics in any other application that will publish information to it, because this can cause 
    your application to break unexpectedly. Any information that is published to this topics may interfere with device operation.

## Currently supported commands

- **lines** - Number of lines to be displayed per page (in range: 1 to 100) (e.g. lines:20)
- **time** - Search for records on specific date and time (in `YYYY-MM-DD HH:MM:SS` format)
- **np** - Next page (displays next n (n is defined by `lines` command) records from current log location)
- **pp** - Previous page (displays previous n (n is defined by `lines` command) records from current log location)
- **clear_sys_logs** - Removes **ALL* system logs
- **stop** - Stops search after `time` command is used


!!! danger "clear_sys_logs command"
    Command `clear_sys_logs` will remove **ALL** system logs from SD card. This operation is irreversible and all system logs will be irretrievably removed. Use this command only if you know what you are doing.