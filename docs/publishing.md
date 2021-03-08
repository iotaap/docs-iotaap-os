# Publishing IoTaaP OS Library
Since this library was built using PlatformIO we are using `pio` for publishing this library to the PlatformIO registry.

## Versioning
This library uses semantic versioning. Before building procedure library version in `library.json` must be updated. 

CHANGELOG.md must be also updated by describing changes. 

Finally, in `iotaap_os\src\system\definitions.h` parameter `LIB_VERSION` has to be updated.

## Publishing library to the PlatformIO registry
1. Position your terminal to `iotaap_os` directory (where *library.json* is located)
2. Login to the PlatformIO account using the following command: `pio account login` 
3. Use your PlatformIO credentials to login
4. Execute the following command: `pio package publish --owner=iotaap`

!!! warning "Organisation member"
    Please note that only **IoTaaP** organisation member can publish to the registry. Repository owner 
    can add you to the organisation if needed. 

## CI/CD
CI and CD are handled by internally hosted Jenkins instance. Based on the `Jenkinsfile` new Jenkins Job will be started
on any Pull request (and all checks have to pass before it can be merged with `master` branch) and on every push to any
branch. 