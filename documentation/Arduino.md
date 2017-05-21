# Arduino IDE

- [Getting Started with Arduino](http://www.arduino.cc/en/Guide/HomePage)
- [Unofficial list of 3rd party boards support urls](https://github.com/arduino/Arduino/wiki/Unofficial-list-of-3rd-party-boards-support-urls)
  - Generic ESP8266 modules
  - Olimex MOD-WIFI-ESP8266
  - NodeMCU 0.9 (ESP-12)
  - NodeMCU 1.0 (ESP-12E)
  - Adafruit HUZZAH ESP8266 (ESP-12)
  - SparkFun Thing
  - SweetPea ESP-210
  - WeMos D1
  - WeMos D1 mini

# Setup Steps

1. File > Preferences > Additional Boards Manager URLs
   - http://arduino.esp8266.com/stable/package_esp8266com_index.json
2. Tools > Board > Board Manager

# Linux Configuration

```sh
user@workstation:~/Downloads/arduino-1.8.2$ sudo usermod -a -G dialout xe1gyq
```

```sh
[  346.986871] usb 2-2.2: new full-speed USB device number 12 using xhci_hcd
[  347.137961] usb 2-2.2: New USB device found, idVendor=10c4, idProduct=ea60
[  347.137964] usb 2-2.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  347.137965] usb 2-2.2: Product: CP2102 USB to UART Bridge Controller
[  347.137966] usb 2-2.2: Manufacturer: Silicon Labs
[  347.137968] usb 2-2.2: SerialNumber: 0001
[  347.155481] usbcore: registered new interface driver cp210x
[  347.155501] usbserial: USB Serial support registered for cp210x
[  347.155536] cp210x 2-2.2:1.0: cp210x converter detected
[  347.156815] usb 2-2.2: cp210x converter now attached to ttyUSB0
```

# Arduino IDE Configuration

```
Board: NodeMCU 1.0
CPU Frequency: 80 MHz
Flash Size: 4M (3M SPIFFS)
Upload Speed: 115200
Port: /dev/ttyUSB0
```

Board Info

```sh
BN: Unknown board
VID: 10C4
PID: EA60
SN: Upload any sketch to obtain it
```

After uploading in Linux console:

```sh
Archiving built core (caching) in: /tmp/arduino_cache_802597/core/core_esp8266_esp8266_nodemcuv2_CpuFrequency_80,UploadSpeed_115200,FlashSize_4M3M_270be6ff9182869e36429f5bd365089d.a
Sketch uses 222129 bytes (21%) of program storage space. Maximum is 1044464 bytes.
Global variables use 31496 bytes (38%) of dynamic memory, leaving 50424 bytes for local variables. Maximum is 81920 bytes.
Uploading 226272 bytes from /tmp/arduino_build_658763/Blink.ino.bin to flash at 0x00000000
................................................................................ [ 36% ]
................................................................................ [ 72% ]
.............................................................                    [ 100% ]

```

