# IoTaaP OS functions

### void start()
Starts IoTaaP OS. Has to be called before any other function


### void startWifi()
Connects device to WiFi AP 

### void startMqtt()

#### Parameters

 - **MQTT_CALLBACK_SIGNATURE** - Pointer to MQTT callback function


!!! info "MQTT_CALLBACK_SIGNATURE"
    MQTT_CALLBACK_SIGNATURE is predefined MQTT callback function signature. Parameter should point to the void function.
    ```cpp
    void callback(char *topic, byte *message, unsigned int length)
    {
    }   
    
    ```

### int deviceCloudPublish()
Publishes data to device topic (`/<username>/devices/<device-id>/<topic>`)

#### Parameters

 - **payload** - JSON formatted payload to be sent to the cloud
 - **uTopic** - Topic name where payload should be sent

#### Returns
- `(int)` Returns 0 if successfull

!!! warning "JSON formatted"
    Payload should be JSON formatted in order to be properly received by cloud

!!! info "Queuing used"
    To provide optimal performance system uses Queuing for publishing data. In most cases data will be published
    immediately, but if multiple publishing functions are called without delay between your data could be added 
    to the queue. Queued data will be automatically published as fast as possible. 

### int basicCloudPublish()
Publishes data to the topic (`/<username>/<topic>`)

#### Parameters

 - **payload** - JSON formatted payload to be sent to the cloud
 - **uTopic** - Topic name where payload should be sent

#### Returns
- `(int)` Returns 0 if successfull

!!! warning "JSON formatted"
    Payload should be JSON formatted in order to be properly received by cloud

!!! info "Queuing used"
    To provide optimal performance system uses Queuing for publishing data. In most cases data will be published
    immediately, but if multiple publishing functions are called without delay between your data could be added 
    to the queue. Queued data will be automatically published as fast as possible. 

### int basicSubscribe()
Subscribes to the topic

#### Parameters

- **uTopic** - Topic name to subscribe to

#### Returns
- `(int)` Returns 0 if successfull

!!! warning "Username added automatically"
    Your MQTT username will be added automatically as a root topic. (`/<username>/<uTopic>`)

!!! info "Queuing used"
    To provide optimal performance system uses Queuing for subscribing to topics. In most cases system will subscribe to the topic
    immediately, but if multiple subscribing functions are called without delay between your subscription request could be added 
    to the queue. Queued subscription requests will be automatically handled as fast as possible. 

### int basicUnsubscribe()
Unsubscribes from the topic

#### Parameters

- **uTopic** - Topic name to unsubscribe from

#### Returns
- `(int)` Returns 0 if successfull

!!! warning "Username added automatically"
    Your MQTT username will be added automatically as a root topic. (`/<username>/<uTopic>`)

!!! info "Queuing used"
    To provide optimal performance system uses Queuing for unsubscribing from topics. In most cases system will unsubscribe from the topic
    immediately, but if multiple unsubscribing functions are called without delay between your unsubscribe request could be added 
    to the queue. Queued unsubscribe requests will be automatically handled as fast as possible. 

### int deviceCloudPublishParam()
Creates structured parameter and publishes it to params topic (`/<username>/devices/<device-id>/params`)

#### Parameters

- **name** - Parameter name
- **value** - Parameter value (can be numeric or textual)

#### Returns
- `(int)` Returns 0 if successfull

#### Structured parameter sample

```json
{
  "device_id" : "5e4ecaae0ed7ef47c0e0ede3",
  "name": "myParam",
  "value": 98,
  "time": "2020-08-19 01:50:48",
  "unix_ms": 1597787448349
}

```

#### Structured parameter keys

- **device_id** - Device ID
- **name** - Your parameter name (string type)
- **value** - Your parameter value (can be any JSON valid data type)
- **time** - Current system time
- **unix_ms** - Current unix time in milliseconds

!!! info "Queuing used"
    To provide optimal performance system uses Queuing for publishing data. In most cases data will be published
    immediately, but if multiple publishing functions are called without delay between your data could be added 
    to the queue. Queued data will be automatically published as fast as possible. 

### void writeToSystemLogs()
Writes data to the system log with `USER` tag

#### Parameters

- **data** - Data to be logged

### bool getSystemParameter()
Gets system parameter from default.cfg on internal filesystem

#### Parameters

- **element** - Parameter name
- **output** - Destination (can be `char`, `int` or `bool` type)

#### Returns
- `(bool)` Returns `true` if parameter exists or `false` if not

### void checkForUpdates()
Triggers checking for updates. Calling this function will schedule checking for updates. Updates will be usually checked within a
few milliseconds. 

This function is pretty handy if `auto_update` parameter in `default.cfg` is set to false (automatic updates disabled), since it can trigger
updates check manually from the main code.

#### Example 
If your application is time critical automatic updates can cause unexpected delays in communication during checking and during update process and 
restart. 

`checkForUpdates()` function can be called from main code when it is safe for your application to run update check. Usual aproach would
be placing this function in MQTT callback function to be triggered when data is published to specific MQTT topic to which device is subscribed.

