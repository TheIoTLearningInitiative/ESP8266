Introduction
==



- [ESP8266 Wiki](https://github.com/esp8266/esp8266-wiki/wiki)
- https://www.gitbook.com/book/smartarduino/user-manual-for-esp-12e-devkit/details
- http://www.instructables.com/id/ESP8266-HTTP-IO-Server/
- Olimex IoT Firmware
- https://github.com/squix78/esp8266-projects/blob/master/arduino-ide/thingspeak-data-logger/thingspeak-data-logger.ino

# ESP8266

> ESP-12E

- http://www.esp8266.com/wiki/doku.php#getting_started
- https://learn.adafruit.com/adafruit-huzzah-esp8266-breakout/using-arduino-ide
- https://github.com/nodemcu
- http://hanneslehmann.github.io/2014/12/ESP8266Module/
- https://espressif.com/products/hardware/esp8266ex/overview/
- https://mcuoneclipse.com/2014/10/15/cheap-and-simple-wifi-with-esp8266-for-the-frdm-board/
- https://scargill.wordpress.com/?s=esp8266

## Linux Host Dmesg

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

## Build

### NodeMCU Custom Builds.

> You customize your NodeMCU firmware and we build it. Just for you. 

- [NodeMCU Custom Builds Homepage](http://nodemcu-build.com/)
- [Docker NodeMCU build](https://hub.docker.com/r/marcelstoer/nodemcu-build/)

## ESP Open SDK 

> Free and open (as much as possible) integrated SDK for ESP8266 chips

```sh
    root@host:~# apt-get install make unrar autoconf automake libtool gcc g++ gperf flex bison texinfo gawk ncurses-dev libexpat-dev python python-serial sed git
    root@host:~# apt-get install libtool-bin
    user@host:~$ git clone --recursive https://github.com/pfalcon/esp-open-sdk.git
    user@host:~$ cd esp-open-sdk
    user@host:~$ make
    user@host:~$ export PATH=/home/xe1gyq/Projects/esp-open-sdk/xtensa-lx106-elf/bin:$PATH
    
    $ make clean
    $ git pull
    $ git submodule sync
    $ git submodule update
    
    git clone --recursive https://github.com/pfalcon/esp-open-sdk.git /opt/esp-open-sdk
    cd /opt/esp-open-sdk
    make STANDALONE=y
    PATH=/opt/esp-open-sdk/xtensa-lx106-elf/bin:$PATH
     cd /opt/nodemcu-firmware
    make
    
```

- https://github.com/pfalcon/esp-open-sdk


## ESP8266 ROM Bootloader Utility

> A cute Python utility to communicate with the ROM bootloader in Espressif ESP8266. It is intended to be a simple, platform independent, open source replacement for XTCOM.

- https://github.com/themadinventor/esptool

## Node-MCU Firmware

> lua based interactive firmware for mcu like esp8266 http://nodemcu.com

- https://github.com/nodemcu/nodemcu-firmware
- https://github.com/nodemcu/nodemcu-firmware/releases/tag/0.9.6-dev_20150704
- https://learn.sparkfun.com/tutorials/esp8266-thing-hookup-guide

```sh
    user@host:~$ git clone --recursive https://github.com/pfalcon/esp-open-sdk.git /opt/esp-open-sdk
    user@host:~$ cd /opt/esp-open-sdk
    user@host:~$ make STANDALONE=y
    user@host:~$ PATH=/opt/esp-open-sdk/xtensa-lx106-elf/bin:$PATH
    user@host:~$ git clone https://github.com/nodemcu/nodemcu-firmware.git
    user@host:~$ cd /opt/nodemcu-firmware
    user@host:~$ make
```

## MicroPython

```sh
    root@host:~# apt-get install libffi-dev
    user@host:~$ git clone https://github.com/micropython/micropython.git
    user@host:~$ cd micropython/
    user@host:~$ cd unix/
    user@host:~$ make
    user@host:~$ make PORT=/dev/ttyUSB0 deploy
    Use make V=1 or set BUILD_VERBOSE in your environment to increase build verbosity.
    Writing build/firmware-combined.bin to the board
    #@esptool.py --port /dev/ttyUSB0 write_flash 0 build/firmware-combined.bin
    Connecting...
    Erasing flash...
    Took 0.87s to erase flash block
    Wrote 51200 bytes at 0x00000000 in 4.9 seconds (82.9 kbit/s)...
    Erasing flash...
    Took 1.58s to erase flash block
    Wrote 282624 bytes at 0x00010000 in 27.4 seconds (82.5 kbit/s)...
    
    Leaving...
    user@host:~$ su
    password
    root@host:~# minicom -D /dev/ttyUSB0
    
    <reset>
    
    >>> 
    MicroPython v1.5.2-51-g5b3f0b7 on 2016-01-10; ESP module with ESP8266
    Type "help()" for more information.
    >>> 

```

## Serial Monitor

- /dev/ttyUSB0
- 115200


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

- http://hanneslehmann.github.io/2015/01/ESP8266Module_LUA/

## Hardware Node-MCU Motor

- http://nodemcu-motor.doit.am/

## Services

> IoT platform for Makers

- http://jumpwire.io/
- https://github.com/knolleary/pubsubclient/blob/master/examples/mqtt_esp8266/mqtt_esp8266.ino
- 

### ESPlorer

```sh
    java –jar ESPlorer.jar
```

- https://github.com/4refr0nt/ESPlorer
- http://randomnerdtutorials.com/download/

## PlatformIO

> PlatformIO is an open source ecosystem for IoT development. Cross-platform build system. Continuous and IDE integration. Arduino and MBED compatible

- [PlatformIO](http://platformio.org/get-started)

## MQTT

http://tuanpm.net/rock-solid-esp8266-wifi-mqtt-restful-client-for-arduino/