# Pebble Notes

Probably most of this is documented somewhere already but I always like to have a look at how it works first before trying to dig though the various forums and online documentation.

One of the primary reasons I got a Pebble is so I could write some of my own apps that could display on the device. At this point there is no SDK available. I decided to try and figure out how the Pebble works. Here is what I have seen thus far.

Related Source Projects
* https://github.com/aleksandyr/pbw-tools
* https://github.com/PebbleDev/pebble-tools
* https://github.com/Hexxeh/libpebble

## Firmware Updates
iPhone app launches and makes this request:

### Latest Version Request
https://pebblefw.s3.amazonaws.com/pebble/ev2_4/release/latest.json

```
GET /pebble/ev2_4/release/latest.json HTTP/1.1
Host: pebblefw.s3.amazonaws.com
Proxy-Connection: keep-alive
Accept-Encoding: gzip, deflate
Accept: */*
Accept-Language: en-us
Connection: keep-alive
User-Agent: PebbleApp/1.0.4 CFNetwork/609.1.4 Darwin/13.0.0
Pragma: no-cache
Cache-Control: no-cache


```

### Latest Version Response
```JSON
{
    "recovery": {
        "url": "https://pebblefw.s3.amazonaws.com/pebble/ev2_4/release/pbz/recovery_ev2_4_v1.5.2.pbz",
        "timestamp": 1356919500,
        "notes": "Official Recovery Firmware",
        "friendlyVersion": "v1.5.2",
        "sha-256": "1ca285d65d80b48b90bab85c5f9e54c907414adffa6f1168beec8aac5d6f32a2"
    },
    "normal": {
        "url": "https://pebblefw.s3.amazonaws.com/pebble/ev2_4/release/pbz/normal_ev2_4_v1.8.1.pbz",
        "timestamp": 1360275561,
        "notes": "Improved backlight control; Notification popups now time out after 3 minutes; Bug fixes",
        "friendlyVersion": "v1.8.1",
        "sha-256": "f3908e60f72122cc97a0ee8eca88605e071211c74bbee08bf3a08e8d54480327"
    }
}
```


## PBZ Info

### File Format

The PBZ file is a zipped file which contains the following:
- manifest.json
- system_resources.pbpack
- tintin_fw.bin

#### manifest.json

```JSON
{
  "manifestVersion": 1,
  "firmware": {
    "name": "tintin_fw.bin",
    "timestamp": 1360275561,
    "crc": 766002693,
    "hwrev": "ev2_4",
    "type": "normal",
    "size": 444643
  },
  "generatedBy": "zulak-air",
  "generatedAt": 1360609232,
  "debug": {
    "resourceMap": {
      "media": [
        {
          "defName": "PUG",
          "type": "png",
          "file": "images\/pug.png"
        },
        {
          "defName": "DIALOG_HELLO",
          "type": "png",
          "file": "images\/hello.png"
        },
        {
          "defName": "MENU_ICON_EYE",
          "type": "png",
          "file": "images\/menu_icon_eye.png"
        },
        {
          "defName": "MENU_ICON_TEXT_WATCH",
          "type": "png",
          "file": "images\/menu_icon_text_watch.png"
        },
        {
          "defName": "MENU_ICON_CLASSIC_WATCH",
          "type": "png",
          "file": "images\/menu_icon_classic_watch.png"
        },
        {
          "defName": "MENU_ICON_FUZZY_WATCH",
          "type": "png",
          "file": "images\/menu_icon_fuzzy_watch.png"
        },
        {
          "defName": "MENU_ICON_TRASH",
          "type": "png",
          "file": "images\/menu_icon_trash.png"
        },
        {
          "defName": "SETTINGS_ICON_RESET",
          "type": "png",
          "file": "images\/settings_icon_reset.png"
        },
        {
          "defName": "SETTINGS_ICON_BLUETOOTH_ALT",
          "type": "png",
          "file": "images\/settings_icon_bluetooth_alt.png"
        },
        {
          "defName": "SETTINGS_ICON_BLUETOOTH",
          "type": "png",
          "file": "images\/settings_icon_bluetooth.png"
        },
        {
          "defName": "SETTINGS_ICON_AIRPLANE",
          "type": "png",
          "file": "images\/settings_icon_airplane.png"
        },
        {
          "defName": "SETTINGS_ICON_ABOUT",
          "type": "png",
          "file": "images\/settings_icon_about.png"
        },
        {
          "defName": "LAUNCHER_ICON_PACKAGE",
          "type": "png",
          "file": "images\/launcher_icon_package.png"
        },
        {
          "defName": "LAUNCHER_ICON_CLOCK",
          "type": "png",
          "file": "images\/launcher_icon_clock.png"
        },
        {
          "defName": "LAUNCHER_ICON_ALARM",
          "type": "png",
          "file": "images\/launcher_icon_alarm.png"
        },
        {
          "defName": "LAUNCHER_ICON_SHUTDOWN",
          "type": "png",
          "file": "images\/launcher_icon_shutdown.png"
        },
        {
          "defName": "LAUNCHER_ICON_RUNKEEPER",
          "type": "png",
          "file": "images\/launcher_icon_runkeeper.png"
        },
        {
          "defName": "LAUNCHER_ICON_SETTINGS",
          "type": "png",
          "file": "images\/launcher_icon_settings.png"
        },
        {
          "defName": "LAUNCHER_ICON_MUSIC",
          "type": "png",
          "file": "images\/launcher_icon_music.png"
        },
        {
          "defName": "GENERIC_ICON",
          "type": "png",
          "file": "images\/generic_icon.png"
        },
        {
          "defName": "FIRST_BOOT",
          "type": "png",
          "file": "images\/first_boot.png"
        },
        {
          "defName": "SIMPLE_MINUTE",
          "type": "png-trans",
          "file": "images\/simple_minute.png"
        },
        {
          "defName": "SIMPLE_HOUR",
          "type": "png-trans",
          "file": "images\/simple_hour.png"
        },
        {
          "defName": "CHECKMARK",
          "type": "png",
          "file": "images\/checkmark.png"
        },
        {
          "defName": "SIMPLE_BG",
          "type": "png",
          "file": "images\/simple_bg.png"
        },
        {
          "defName": "FONT_FALLBACK",
          "type": "font",
          "file": "ttf\/RasterGothic14Cond.ttf"
        },
        {
          "defName": "GOTHIC_14",
          "type": "font",
          "file": "ttf\/RasterGothic14Cond.ttf"
        },
        {
          "defName": "GOTHIC_14_BOLD",
          "type": "font",
          "file": "ttf\/RasterGothic14CondBold.ttf"
        },
        {
          "defName": "GOTHIC_18",
          "type": "font",
          "file": "ttf\/RasterGothic18Cond.ttf"
        },
        {
          "defName": "GOTHIC_18_BOLD",
          "type": "font",
          "file": "ttf\/RasterGothic18CondBold.ttf"
        },
        {
          "defName": "GOTHIC_24",
          "type": "font",
          "file": "ttf\/RasterGothic24Cond.ttf"
        },
        {
          "defName": "GOTHIC_24_BOLD",
          "type": "font",
          "file": "ttf\/RasterGothic24CondBold.ttf"
        },
        {
          "defName": "GOTHIC_28",
          "type": "font",
          "file": "ttf\/RasterGothic28Cond.ttf"
        },
        {
          "defName": "GOTHIC_28_BOLD",
          "type": "font",
          "file": "ttf\/RasterGothic28CondBold.ttf"
        },
        {
          "defName": "GOTHAM_30_BLACK",
          "type": "font",
          "file": "ttf\/GothamBlack30.ttf"
        },
        {
          "trackingAdjust": -2,
          "defName": "GOTHAM_42_BOLD",
          "type": "font",
          "file": "ttf\/Gotham-Bold.otf"
        },
        {
          "trackingAdjust": -3,
          "defName": "GOTHAM_42_LIGHT",
          "type": "font",
          "file": "ttf\/Gotham-Light.otf"
        },
        {
          "trackingAdjust": -3,
          "characterRegex": "[0-9:-]",
          "defName": "GOTHAM_42_MEDIUM_NUMBERS",
          "type": "font",
          "file": "ttf\/Gotham-Medium.otf"
        },
        {
          "trackingAdjust": -2,
          "characterRegex": "[0-9:\\.-]",
          "defName": "GOTHAM_34_MEDIUM_NUMBERS",
          "type": "font",
          "file": "ttf\/Gotham-Medium.otf"
        },
        {
          "trackingAdjust": -2,
          "characterRegex": "[mikm-]",
          "defName": "GOTHAM_34_LIGHT_SUBSET",
          "type": "font",
          "file": "ttf\/Gotham-Light.otf"
        },
        {
          "trackingAdjust": -1,
          "characterRegex": "[minkm\/-]",
          "defName": "GOTHAM_18_LIGHT_SUBSET",
          "type": "font",
          "file": "ttf\/Gotham-Light.otf"
        },
        {
          "defName": "DROID_SERIF_28_BOLD",
          "type": "font",
          "file": "ttf\/DroidSerif28Bold.ttf"
        }
      ],
      "friendlyVersion": "v1.8-HM",
      "versionDefName": "SYSTEM_RESOURCE_VERSION"
    }
  },
  "type": "firmware",
  "resources": {
    "timestamp": 1360275561,
    "crc": 264127307,
    "friendlyVersion": "v1.8-HM",
    "name": "system_resources.pbpack",
    "size": 144662
  }
}
```


## Watch Face Download

I assume the PBW files are generated with pbw-tools.

### Watch Face Request

```BASH
curl -O http://pebble-static.s3.amazonaws.com/watchfaces/apps/brains.pbw
```

```
GET /watchfaces/apps/brains.pbw HTTP/1.1
Host: pebble-static.s3.amazonaws.com
Referer: http://pebble-static.s3.amazonaws.com/watchfaces/index.html
Accept-Encoding: gzip, deflate
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us
Connection: keep-alive
User-Agent: Mozilla/5.0 (iPhone; CPU iPhone OS 6_1_2 like Mac OS X) AppleWebKit/536.26 (KHTML, like Gecko) Mobile/10B146
Pragma: no-cache
Cache-Control: no-cache
```

### Watch Face Response



#### manifest.json

```JSON
{
  "manifestVersion": 1,
  "generatedBy": "Tiny.local",
  "generatedAt": 1358384585,
  "application": {
    "reqFwVer": 1,
    "timestamp": 1358384584,
    "crc": 3860292302,
    "name": "pebble-app.bin",
    "size": 3196
  },
  "debug": {
    "resourceMap": {
      "media": [
        {
          "defName": "IMAGE_MENU_ICON",
          "type": "png",
          "file": "images\/menu_icon_herr_rams_watch.png"
        },
        {
          "defName": "IMAGE_BACKGROUND",
          "type": "png",
          "file": "images\/brains_watch_background.png"
        },
        {
          "defName": "IMAGE_HOUR_HAND",
          "type": "png",
          "file": "images\/brains_watch_hour_hand.png"
        },
        {
          "defName": "IMAGE_MINUTE_HAND",
          "type": "png",
          "file": "images\/brains_watch_minute_hand.png"
        },
        {
          "defName": "IMAGE_SECOND_HAND",
          "type": "png",
          "file": "images\/brains_watch_second_hand.png"
        },
        {
          "defName": "IMAGE_CENTER_CIRCLE",
          "type": "png-trans",
          "file": "images\/brains_watch_center.png"
        }
      ],
      "friendlyVersion": "dev_0.0",
      "versionDefName": "APP_RESOURCES"
    }
  },
  "type": "application",
  "resources": {
    "timestamp": 1358384584,
    "crc": 1532877025,
    "friendlyVersion": "dev_0.0",
    "name": "app_resources.pbpack",
    "size": 8548
  }
}

```

