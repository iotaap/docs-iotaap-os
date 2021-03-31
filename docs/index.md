# IoTaaP OS Documentation

IoTaaP OS is a unique system built on top of FreeRTOS for ESP32 SoC which provides everything you need to successfully develop, deploy and manage your IoT devices.

## About

Most of the operations are handled by FreeRTOS tasks that are managing various modules (WiFi, MQTT, OTA, System, Filesystem...), data consistency is ensured by using RAM Queues for storing data temporary before handling.

All configuration files and security certificates are loaded from internal FAT filesystem. SD card is optional part of the whole system, used as temporary and backup storage and logs storage. 

## System Modules

* Configurator Module - Handles IoTaaP OS Web Configurator interface
* File System Module - Managing file system on internal filesystem and SD card
* HMI Module - Managing LED and Serial/MQTT configuration menu
* MQTT Module - Manages MQTTS connection with IoTaaP Cloud
* OTA Update Module - Periodically checking for updates and manages update process
* System Process Module - Manages various system processes for normal operation
* WiFi Module - Manages WiFi connection to the AP

## License
Apache License 2.0, see [LICENSE](./license.md)