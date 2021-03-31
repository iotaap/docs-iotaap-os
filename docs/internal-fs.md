# IoTaaP OS Internal filesystem

Starting from IoTaaP OS version 4, system uses internal FAT filesystem for storing configuration data and security certificates. 

## IoTaaP OS Web Configurator

All system configuration can be set-up using IoTaaP OS Web configurator. During initial boot (first boot) system will automatically
start web configurator. System parameters can be also adjusted by using [serial configurator](config-wizard.md).

## Custom partitions

IoTaaP OS requires custom partition table since it uses internal FAT filesystem. Partition configurations are available in the *partition* directory
that comes with the library, or simply in the [GitHub repository](https://github.com/iotaap/iotaap-os/tree/master/partitions).

#### Two partition configuration files are available under partitions directory

- default_16MB_fat.csv - to be used with recomended ESP32 modules with 16MB flash
- default_fat.csv - to be used with standard ESP32 modules with 4MB flash

## Selecting custom partition

When using PlatformIO, custom partition configuration file (.csv) can be defined in `platformio.ini` file in the following way:

`board_build.partitions = partitions/default_16MB_fat.csv`

 Please note that `partitions` directory should be on the same level as your `src` directory, for the above configuration to work properly.