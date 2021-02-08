# IoTaaP OS Required Hardware

!!! info "ESP32 SoC"
    IoTaaP OS is currently fully optimized and developed to work with ESP32 SoC by [Espressif](https://www.espressif.com/en/products/socs/esp32/overview). 
    Although, there is a possibility for porting IoTaaP OS to other sillicons we strongly recommend using it on ESP32.

## Supported ESP32 modules

IoTaaP OS supports various versions of ESP32 SoC, but most widely used module is **ESP32-WROOM-32D**, limited testing has also been done on the new, improved ESP32 module **ESP32­-WROOM­-32E**.

Minimum required Flash memory is **4MB**, but we recommend using **16MB** of Flash memory for best performance

## IoTaaP OS - Peripherals

IoTaaP OS uses predefined peripheral configuration, and we strongly recommend to stick to it. Have in mind during your hardware desing to implement the following configuration. 

 | **Pin** | **Functionality** | **Note**                                |
 | ------- | ----------------- | --------------------------------------- |
 | IO23    | MOSI              | 3.3V level                              |
 | IO19    | MISO              | 3.3V level                              |
 | IO18    | CLK               | 3.3V level                              |
 | IO5     | CS                | 3.3V level                              |
 | IO36    | BATTERY SENS.     | Use voltage divider and Li-Ion battery* |
 | IO2     | LED               | Use 330R resistor and green LED*        |
 | TXD0    | Serial TX         | Standard 3.3V level serial interface    |
 | RXD0    | Serial RX         | Standard 3.3V level serial interface    |

!!! warning "Note"
    **Battery sensing** circuit should have a dividing coefficient of ***Vin/2***, we recommend using 4k7 resistors. Battery should have max voltage of 4.2V,
    as system is configured to work with standard Li-Ion discharging curve. *Please note that battery percentage is only approximal*. Usage of the battery sensing is
    optional (connect pin to ground if not used).
    **LED** can be any LED with resistor and it is used for system status indication (**Fast blinking** - Connecting, **Slow blinking** - Reconnecting, **Periodic blinking** - Normal operation)

![alt text](https://files.iotaap.io/assets/iotaap-os/assets/esp32-sd-card-wiring.jpg "SD Card wiring")