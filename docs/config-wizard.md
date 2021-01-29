# Configuration Wizard

Configuration Wizard is advanced feature used for parameter configuration via Serial interface. All parameters from default.cfg and custom.cfg can be configured by using
one of this commands:

  - **set-system** - wizard to set all parameters from system configuration data
  - **set-user** - wizard to set all parameters from user configuration data


## Using commands
Simply type `set-system` or `set-user` command into your serial interface. Wizard will start with the following output:

```
Parameter wizard (leave empty for unchanged):

 String "device_id":5e4ecffe0ed7ef34c0e0ede3
    New "device_id":

```

you can use your serial interface to change the parameter or press **ENTER** to keep the current value. If you want to update a specific parameter,
just enter new value into your serial interface and press **ENTER**, after that you should get the following output (e.g. for auto_update parameter):

```
Boolean "auto_update":true
    New "auto_update":false
--> New "auto_update":false

```

at the end, wizard will automatically exit with the following message:

```
Leaving parameter wizard (data is saved)

```