# Device Status 

IoTaaP OS will publish it's current system status to a specific MQTTS topic. This functionality is implemented as a part of MQTTS service running in the background.

## Publishing device state

IoTaaP OS will periodically publish its state to the following topic:

`/<username>/devices/<device-id>/status`

!!! danger "Topic usage"
    You should **NOT** use this topic in any other application that will publish information to it, because this can cause 
    your application to break unexpectedly. Any information that is published to this topic will be ignored by the device, except
    when this kind of implementation is done manually.

### Message format

Our system uses JSON as the default format for published messages. Status message is predefinded and looks like this:

```json
{
    "battery": 100,
    "uptime": 5482,
    "core_version": "1.0.2",
    "fw_version": "1.5.2"
}
```

**Message parameters**

- battery `(number)`: current battery percentage (%)
- uptime `(number)`: time since power-up in seconds
- core_version `(string)`: IoTaaP OS version
- fw_version `(string)`: your firmware version