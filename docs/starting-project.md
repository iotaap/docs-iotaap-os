# Starting a new IoTaaP OS project using PlatformIO

We recommend you go through the example project that is available in the examples folder, and in IoTaaP OS [tutorial](https://docs.iotaap.io/docs-tutorials/iotaap-os/).

## Installing IoTaaP OS using PlatformIO

You have to declare library dependencies in your `platformio.ini` file, by using [lib_deps](https://docs.platformio.org/page/projectconf/section_env_library.html) option. You can define the specific library version, although we recommend using the newest version in your projects.

#### Example project configuration

```
[env:myenv]
platform = espressif32
board = iotaap_magnolia
framework = arduino

lib_deps =

     # RECOMMENDED
     # Accept new functionality in a backwards compatible manner and patches
     iotaap/IoTaaP OS @ ^4.0.0

     # Accept only backwards compatible bug fixes
     # (any version with the same major and minor versions, and an equal or greater patch version)
     iotaap/IoTaaP OS @ ~4.0.0

     # The exact version
     iotaap/IoTaaP OS @ 4.0.0

```

More info about Library installation using PlatformIO can be found [here](https://platformio.org/lib/show/11733/IoTaaP/installation).