Inception
=========
Inception is a set of tools for auto configuring android devices. You can do the following:

- Generate all device settings
- Include any apps to be be (pre)installed
- Remove any stock apps
- Root the device
- Configure Wifi networks
- Patch APKs
- Replace Kernel, and/or ramdisk data in both boot and recovery imgs
- Place your adb keys

# Quick start:

```bash
incept bootstrap --base inception.device --variant myconfig
```

Edit ~/.inception/variants/inception/device/myconfig/myconfig.json

Override device settings, add wifi settings, or add some apps

For example:

```json
{
    "__extends__": "inception.device",
    "device": {
        "name": "custom"
    },
    "update": {
        "keys": null,
        "make": true,
        "network": {
            "aps": [
                {
                    "ssid": "Home network",
                    "security": "WPA-PSK",
                    "key": "CE3000FEED"
                }
            ]
        },
        "apps": {
            "com.whatsapp": {
                "apk": "myapps/whatsapp.apk"
            }
        }
    }
}

```
then:

```bash
incept make --variant inception.device.myconfig
```

This will generate:

 > ~/.inception/out/inception/device/myconfig/update.zip

Which is an OTA android update that you can install in several ways.

**Hint**
You will find the full config that generated the OTA package at:

 > ~/.inception/out/inception/device/myconfig/config.json

Inspect that file, override any properties in your own config, run make again and see your changes easily going through.


