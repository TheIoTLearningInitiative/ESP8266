# Setup

https://raw.githubusercontent.com/platformio/platformio/develop/scripts/99-platformio-udev.rules

{% include "git+https://github.com/GitbookIO/documentation.git/README.md#0.0.1" %}

# Linux

# Serial Monitor

- Port: /dev/ttyUSB0
- Upload Speed: 115200

```sh
[12447.680034] usb 5-1: new full-speed USB device number 2 using uhci_hcd
[12448.052042] usb 5-1: New USB device found, idVendor=10c4, idProduct=ea60
[12448.052047] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[12448.052050] usb 5-1: Product: CP2102 USB to UART Bridge Controller
[12448.052053] usb 5-1: Manufacturer: Silicon Labs
[12448.052055] usb 5-1: SerialNumber: 0001
[12449.956079] usbcore: registered new interface driver usbserial
[12449.956099] usbcore: registered new interface driver usbserial_generic
[12449.956116] usbserial: USB Serial support registered for generic
[12449.965489] usbcore: registered new interface driver cp210x
[12449.965508] usbserial: USB Serial support registered for cp210x
[12449.965538] cp210x 5-1:1.0: cp210x converter detected
[12450.076028] usb 5-1: reset full-speed USB device number 2 using uhci_hcd
[12450.228219] usb 5-1: cp210x converter now attached to ttyUSB0
```

# PlatformIO IDE

- [Platform IO IDE](http://platformio.org/platformio-ide)

```sh
root@jessie:/home/xe1gyq/esptool# pip install -U platformio
Collecting platformio
  Downloading platformio-2.8.6-py27-none-any.whl (165kB)
    100% |████████████████████████████████| 174kB 1.0MB/s 
Collecting click<6,>=3.2 (from platformio)
  Downloading click-5.1-py2.py3-none-any.whl (65kB)
    100% |████████████████████████████████| 71kB 114kB/s 
Requirement already up-to-date: requests<3,>=2.4.0 in /usr/local/lib/python2.7/dist-packages (from platformio)
Requirement already up-to-date: pyserial<4 in /usr/local/lib/python2.7/dist-packages (from platformio)
Collecting colorama (from platformio)
  Downloading colorama-0.3.7-py2.py3-none-any.whl
Collecting bottle<0.13 (from platformio)
  Downloading bottle-0.12.9.tar.gz (69kB)
    100% |████████████████████████████████| 71kB 108kB/s 
Collecting lockfile<0.13,>=0.9.1 (from platformio)
  Downloading lockfile-0.12.2-py2.py3-none-any.whl
Building wheels for collected packages: bottle
  Running setup.py bdist_wheel for bottle ... done
  Stored in directory: /root/.cache/pip/wheels/0f/bd/f7/21e856551fa937e3c8a9d9592fd74a50714af336b8ee4f42c7
Successfully built bottle
Installing collected packages: click, colorama, bottle, lockfile, platformio
  Found existing installation: colorama 0.3.6
    Uninstalling colorama-0.3.6:
      Successfully uninstalled colorama-0.3.6
Successfully installed bottle-0.12.9 click-5.1 colorama-0.3.7 lockfile-0.12.2 platformio-2.8.6
```

```sh
xe1gyq@jessie:~$ mkdir nodemcu
xe1gyq@jessie:~$ cd nodemcu/
xe1gyq@jessie:~/nodemcu$ platformio init --board=nodemcu

The current working directory /home/xe1gyq/nodemcu will be used for project.
You can specify another project directory via
`platformio init -d %PATH_TO_THE_PROJECT_DIR%` command.

The next files/directories will be created in /home/xe1gyq/nodemcu
platformio.ini - Project Configuration File. |-> PLEASE EDIT ME <-|
src - Put your source files here
lib - Put here project specific (private) libraries
Do you want to continue? [y/N]: y

Project has been successfully initialized!
Useful commands:
`platformio run` - process/build project from the current directory
`platformio run --target upload` or `platformio run -t upload` - upload firmware to embedded board
`platformio run --target clean` - clean project (remove compiled files)
`platformio run --help` - additional information
```

### PlatformIO Lib

```sh
xe1gyq@jessie:~/nodemcu$ platformio lib 
Usage: platformio lib [OPTIONS] COMMAND [ARGS]...

Options:
  -h, --help  Show this message and exit.

Commands:
  install    Install library
  list       List installed libraries
  register   Register new library
  search     Search for library
  show       Show details about installed library
  uninstall  Uninstall libraries
  update     Update installed libraries
```

```sh
xe1gyq@jessie:~/nodemcu$ platformio lib search mqtt
Found 6 libraries:

[ ID  ] Name             Compatibility         "Authors": Description
--------------------------------------------------------------------------------
[ 89  ] PubSubClient     arduino, atmelavr, espressif "Nick O'Leary": A client library for MQTT messaging. MQTT is a lightweight messaging protocol ideal for small devices. This library allows you to send and receive MQTT messages. It supports the latest MQTT 3.1.1 protocol and can be configured to use the older MQTT 3.1 if
[1092 ] Adafruit-MQTT    arduino, atmelavr, espressif "Adafruit Industries": MQTT library that supports the CC3000, FONA, ESP8266, Yun, and generic Arduino Client hardware.
[ 537 ] espduino         arduino, atmelavr, atmelsam, teensy "Tuan PM": Wifi library (Chip ESP8266 Wifi SoC) using SLIP protocol via Serial port
[ 555 ] Homie            arduino, espressif    "Marvin Roger": ESP8266 framework for Homie, a lightweight MQTT convention for the IoT
[ 270 ] DimSwitch        arduino, atmelavr, atmelsam, espressif "Krzysztof": A library to control dimmable ballasts for fluorescent light tubes.
[ 227 ] Esp8266Configuration arduino, espressif    "Karsten Kukat": store and read configuration from SPIFFS (wifi ap, wifi station, mqtt ..)
```

```sh
xe1gyq@jessie:~/nodemcu$ platformio lib search -f mbed
Found 85 libraries:
...
xe1gyq@jessie:~/nodemcu$ platformio lib search -p espressif
Found 73 libraries:

[ ID  ] Name             Compatibility         "Authors": Description
--------------------------------------------------------------------------------
[ 257 ] Adafruit-PCD8544 arduino, espressif    "WereCatf": Espressif ESP8266 port of the Adafruit PCD8544 library

```

```sh
xe1gyq@jessie:~/nodemcu$ platformio lib install 6 
Installing library [ 6 ]:
Downloading  [####################################]  100%
Unpacking  [####################################]  100%
The library #6 'XBee' has been successfully installed!
```
