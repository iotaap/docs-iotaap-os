# Custom config file

Custom configuration file is located on the SD Card, under **etc/device/custom.cfg**. This file defines custom device settings 
that can be accessed from main code using `getUserParameter()` function.


## Custom configuration file
Custom configuration file is JSON formatted and does **not** support arrays or similar complex data types

### custom.cfg example

```json
{
  "section": "Production-1",
  "serial": "AE5441QQ",
  "description": "Products counter"
}
```

!!! warning "What if custom config file is not used?"
    If custom configuration file will not be used it should contain empty JSON `{}`.