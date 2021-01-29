# IoTaaP OS Documentation

IoTaaP OS is a unique system built on top of FreeRTOS for ESP32 SoC which provides everything you need to successfully develop, deploy and manage your IoT devices.

## About

Most of the operations are handled by FreeRTOS tasks that are managing various modules (WiFi, MQTT, OTA, System, Filesystem...), data consistency is ensured by using RAM Queues for storing data temporary before handling.

All configuration files are loaded from SD card which must contain predefined file structure, certificate, configurations, etc. SD card is the vital part of the whole system, used as temporary storage, backup storage, long-term storage, operational storage, etc.

## System Modules

* WiFi Module - Manages WiFi connection to the AP
* MQTT Module - Manages MQTTS connection with IoTaaP Cloud
* OTA Update Module - Periodically checking for updates and manages update process
* HMI Module - Managing LED and Serial/MQTT configuration menu
* File System Module - Managing file system on SD card
* System Process Module - Manages various system processes for normal operation

## License
Apache License 2.0, see [LICENSE](./license.md)