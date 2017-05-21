# Setup

{% include "git+https://github.com/GitbookIO/documentation.git/README.md#0.0.1" %}

# PlatformIO IDE Command Line Installation

> The next-generation integrated development environment for IoT

- [Platform IO IDE](http://platformio.org/platformio-ide)
- [PlatformIo-Udev](https://raw.githubusercontent.com/platformio/platformio/develop/scripts/99-platformio-udev.rules)

```sh
root@workstation:~# pip install -U platformio
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
user@workstation:~$ mkdir nodemcu
user@workstation:~$ cd nodemcu/
user@workstation:~/nodemcu$ platformio init --board=nodemcu

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

### PlatformIO Libraries

```sh
user@workstation:~/nodemcu$ platformio lib 
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
user@workstation:~/nodemcu$ platformio lib search mqtt
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
[ 415 ] Blynk            arduino, energia, mbed, wiringpi, atmelavr, atmelsam, timsp430, titiva, nordicnrf51, espressif, native "Volodymyr Shymanskyy": Build a smartphone app for your project in minutes. Works with Arduino, ESP8266, Raspberry Pi, Intel Edison/Galileo, LinkIt ONE, Particle Core/Photon, Banana Pro, LeMaker Guitar, Energia, MBED, LightBlue Bean, ...
[ 444 ] Buttons          arduino, atmelavr, atmelsam, timsp430, titiva, teensy, freescalekinetis, ststm32, nordicnrf51, nxplpc, espressif, siliconlabsefm32 "Richard Miles": Handle different types of buttons and button events easily (touch, capacitive, push)
[ 548 ] MySensors        arduino, atmelavr, atmelsam, timsp430, titiva, teensy, freescalekinetis, ststm32, nordicnrf51, nxplpc, espressif, siliconlabsefm32 "MySensors": Home Automation Framework. Create your own wireless sensor mesh using NRF24L01+ and RFM69 radios running on Arduino or ESP8266. Over-the-air updates and MySensors support in 16+ home automation controllers.
[ 550 ] ThingSpeak       arduino, atmelavr, atmelsam, timsp430, titiva, teensy, freescalekinetis, ststm32, nordicnrf51, nxplpc, espressif, siliconlabsefm32 "MathWorks": ThingSpeak Communication Library for Arduino & ESP8266
[ 554 ] AnalogInput      arduino, atmelavr, atmelsam, timsp430, titiva, teensy, freescalekinetis, ststm32, nordicnrf51, nxplpc, espressif, siliconlabsefm32 "John Ogle": Provides an easy way to automatically calibrate an analog input on an Arduino board.
[ 555 ] Homie            arduino, espressif    "Marvin Roger": ESP8266 framework for Homie, a lightweight MQTT convention for the IoT
[ 573 ] microcoap        arduino, atmelavr, atmelsam, timsp430, titiva, teensy, freescalekinetis, ststm32, nordicnrf51, nxplpc, espressif, siliconlabsefm32 "Toby Jaffey": A small CoAP implementation for microcontrollers
[ 563 ] WeatherStation   arduino, espressif    "Daniel Eichhorn": A wifi connected information display
[ 561 ] JsonStreamingParser arduino, atmelavr, atmelsam, timsp430, titiva, teensy, freescalekinetis, ststm32, nordicnrf51, nxplpc, espressif, siliconlabsefm32 "Daniel Eichhorn": A very memory efficient library to parse (large) JSON objects on embedded devices
[1092 ] Adafruit-MQTT    arduino, atmelavr, espressif "Adafruit Industries": MQTT library that supports the CC3000, FONA, ESP8266, Yun, and generic Arduino Client hardware.
[ 578 ] Sensors          arduino, mbed, wiringpi, atmelavr, teensy, espressif, linux_arm "James Smith": Use I2C-connected sensors like accelerometers, gyroscopes, and barometers in your projects, without knowing the intimate details about the actual device connected.
[ 579 ] ArduRPC          arduino, atmelavr, espressif "DinoTools": ArduRPC brings remote procedure calls to microcontrollers. The protocol has been designed to be simple and flexible.
[ 575 ] tiny-http        arduino, energia, mbed, libopencm3, spl, wiringpi, atmelavr, atmelsam, timsp430, titiva, teensy, freescalekinetis, ststm32, nordicnrf51, nxplpc, espressif, siliconlabsefm32, linux_arm "Celci.us Labs": A Tiny HTTP Server
[ 429 ] aREST            arduino, atmelavr, atmelsam, teensy, espressif "marcoschwartz": RESTful API for Arduino using HTTP or Serial communications
[ 124 ] RadioHead        arduino, energia, atmelavr, atmelsam, timsp430, titiva, teensy, freescalekinetis, ststm32, nordicnrf51, nxplpc, espressif, siliconlabsefm32, linux_arm, native "Mike McCauley": The RadioHead Packet Radio library which provides a complete object-oriented library for sending and receiving packetized messages via RF22/24/26/27/69, Si4460/4461/4463/4464, nRF24/nRF905, SX1276/77/78, RFM95/96/97/98 and etc.
```

```sh
user@workstation:~/nodemcu$ platformio lib search -f mbed
Found 85 libraries:
...
user@workstation:~/nodemcu$ platformio lib search -p espressif
Found 73 libraries:

[ ID  ] Name             Compatibility         "Authors": Description
--------------------------------------------------------------------------------
[ 257 ] Adafruit-PCD8544 arduino, espressif    "WereCatf": Espressif ESP8266 port of the Adafruit PCD8544 library

```

```sh
user@workstation:~/nodemcu$ platformio lib install 6 
Installing library [ 6 ]:
Downloading  [####################################]  100%
Unpacking  [####################################]  100%
The library #6 'XBee' has been successfully installed!
```
