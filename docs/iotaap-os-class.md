# IoTaaP_OS Class Reference

## Constructor

**IoTaaP_OS(const char *fwVersion)**  - Construct a new IoTaaP_OS object
#### Parameters

- **fwVersion** Current firmware version that will be used to trigger OTA update

## Functions

| **Function**            | **Type** | **Description**                                                                                          |
| ----------------------- | -------- | -------------------------------------------------------------------------------------------------------- |
| startWifi               | void     | Connects device to WiFi AP                                                                               |
| startMqtt               | void     | Starts MQTT thread and connects to MQTT broker                                                           |
| deviceCloudPublish      | int      | Publishes data to device topic (`/<username>/devices/<device-id>/<topic>`)                               |
| basicCloudPublish       | int      | Publishes data to the topic (`/<username>/<topic>`)                                                      |
| basicSubscribe          | int      | Subscribes to the topic                                                                                  |
| basicUnsubscribe        | int      | Unsubscribes from the topic                                                                              |
| deviceCloudPublishParam | int      | Creates structured parameter and publishes it to params topic (`/<username>/devices/<device-id>/params`) |
| writeToSystemLogs       | void     | Writes data to the system log                                                                            |
| getUserParameter        | bool     | Gets custom parameter from custom.cfg                                                                    |
| getSystemParameter      | bool     | Gets system parameter from default.cfg                                                                   |
| checkForUpdates         | void     | Triggers checking for updates                                                                            |