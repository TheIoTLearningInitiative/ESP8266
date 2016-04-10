Introduction
==



- [ESP8266 Wiki](https://github.com/esp8266/esp8266-wiki/wiki)
- https://www.gitbook.com/book/smartarduino/user-manual-for-esp-12e-devkit/details
- http://www.instructables.com/id/ESP8266-HTTP-IO-Server/
- Olimex IoT Firmware
- https://github.com/squix78/esp8266-projects/blob/master/arduino-ide/thingspeak-data-logger/thingspeak-data-logger.ino
- http://frightanic.com/computers/build-nodemcu-firmware-for-the-esp8266/

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

### NodeMCU Custom Builds

> You customize your NodeMCU firmware and we build it. Just for you. 

- [NodeMCU Custom Builds Homepage](http://nodemcu-build.com/)
- [Docker NodeMCU build](https://hub.docker.com/r/marcelstoer/nodemcu-build/)

```sh
xe1gyq@jessie:~$ git clone https://github.com/themadinventor/esptool.git
Cloning into 'esptool'...
remote: Counting objects: 385, done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 385 (delta 0), reused 0 (delta 0), pack-reused 382
Receiving objects: 100% (385/385), 152.05 KiB | 0 bytes/s, done.
Resolving deltas: 100% (211/211), done.
Checking connectivity... done.
xe1gyq@jessie:~$ cd esptool/
xe1gyq@jessie:~/esptool$ ls
esptool.py  LICENSE  MANIFEST.in  README.md  setup.py
xe1gyq@jessie:~/esptool$ 
root@jessie:/home/xe1gyq/esptool# sudo apt-get purge python-pkg-resources
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libc-ares-dev libjs-node-uuid libjs-underscore libv8-3.14-dev node-abbrev
  node-ansi node-ansi-color-table node-archy node-async node-block-stream
  node-combined-stream node-cookie-jar node-delayed-stream node-forever-agent
  node-form-data node-fstream node-fstream-ignore node-github-url-from-git
  node-glob node-graceful-fs node-inherits node-ini node-json-stringify-safe
  node-lockfile node-lru-cache node-mime node-minimatch node-mkdirp
  node-mute-stream node-node-uuid node-nopt node-normalize-package-data
  node-npmlog node-once node-osenv node-qs node-read node-read-package-json
  node-request node-retry node-rimraf node-semver node-sha node-sigmund
  node-slide node-tar node-tunnel-agent node-underscore node-which nodejs-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gyp* node-gyp* npm* python-cryptography* python-openssl*
  python-pkg-resources*
0 upgraded, 0 newly installed, 6 to remove and 3 not upgraded.
After this operation, 4,793 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 156395 files and directories currently installed.)
Removing npm (1.4.21+ds-2) ...
Purging configuration files for npm (1.4.21+ds-2) ...
Removing node-gyp (0.12.2+ds-1) ...
Removing gyp (0.1~svn1729-3) ...
Removing python-openssl (0.14-1) ...
Removing python-cryptography (0.6.1-1) ...
Removing python-pkg-resources (5.5.1-1) ...
Processing triggers for man-db (2.7.0.2-5) ...
root@jessie:/home/xe1gyq/esptool# sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libc-ares-dev libjs-node-uuid libjs-underscore libv8-3.14-dev node-abbrev
  node-ansi node-ansi-color-table node-archy node-async node-block-stream
  node-combined-stream node-cookie-jar node-delayed-stream node-forever-agent
  node-form-data node-fstream node-fstream-ignore node-github-url-from-git
  node-glob node-graceful-fs node-inherits node-ini node-json-stringify-safe
  node-lockfile node-lru-cache node-mime node-minimatch node-mkdirp
  node-mute-stream node-node-uuid node-nopt node-normalize-package-data
  node-npmlog node-once node-osenv node-qs node-read node-read-package-json
  node-request node-retry node-rimraf node-semver node-sha node-sigmund
  node-slide node-tar node-tunnel-agent node-underscore node-which nodejs-dev
  python-cffi python-ply python-pycparser python-six
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
root@jessie:/home/xe1gyq/esptool# /usr/local/bin/pip install pyserial
Collecting pyserial
  Using cached pyserial-3.0.1.tar.gz
Building wheels for collected packages: pyserial
  Running setup.py bdist_wheel for pyserial ... done
  Stored in directory: /root/.cache/pip/wheels/06/71/f1/d8c81329abcaf4c623daff8af76a7dbf00f055cb8205cec0ef
Successfully built pyserial
Installing collected packages: pyserial
Successfully installed pyserial-3.0.1
root@jessie:/home/xe1gyq/esptool# 
root@jessie:/home/xe1gyq/esptool# python esptool.py write_flash 0x2000 nodemcu-master-14-modules-2016-04-10-05-04-51-integer.bin 
Connecting...
Erasing flash...
Took 1.64s to erase flash block
Wrote 477184 bytes at 0x00002000 in 46.1 seconds (82.8 kbit/s)...

Leaving...
root@jessie:/home/xe1gyq/esptool# python esptool.py read_mac
Connecting...
MAC: 18:f0:14:da:27:2f
root@jessie:/home/xe1gyq/esptool# python esptool.py flash_id
Connecting...
Manufacturer: e0
Device: 4016
root@jessie:/home/xe1gyq/esptool# python esptool.py chip_id
Connecting...
Chip ID: 0x00dc273f

```

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
root@jessie:/home/xe1gyq/esptool# platformio init --board=nodemcu ^C
root@jessie:/home/xe1gyq/esptool# exit
exit
xe1gyq@jessie:~/esptool$ platformio init --board=nodemcu 

********************************************************************************
If you like PlatformIO, please:
- follow us on Twitter to stay up-to-date on the latest project news > https://twitter.com/PlatformIO_Org
- star it on GitHub > https://github.com/platformio/platformio
- try PlatformIO IDE for IoT development > http://platformio.org/platformio-ide
- donate to keep PlatformIO alive! > http://platformio.org/donate
********************************************************************************


The current working directory /home/xe1gyq/esptool will be used for project.
You can specify another project directory via
`platformio init -d %PATH_TO_THE_PROJECT_DIR%` command.

The next files/directories will be created in /home/xe1gyq/esptool
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
xe1gyq@jessie:~/esptool$ 
```

```sh
/**
 * Blink
 * Turns on an LED on for one second,
 * then off for one second, repeatedly.
 */
#include "Arduino.h"

void setup()
{
  // initialize LED digital pin as an output.
  pinMode(LED_BUILTIN, OUTPUT);
}

void loop()
{
  // turn the LED on (HIGH is the voltage level)
  digitalWrite(LED_BUILTIN, HIGH);
  // wait for a second
  delay(1000);
  // turn the LED off by making the voltage LOW
  digitalWrite(LED_BUILTIN, LOW);
   // wait for a second
  delay(1000);
}
```



- https://atom.io/packages/platomformio
- 

## MQTT

http://tuanpm.net/rock-solid-esp8266-wifi-mqtt-restful-client-for-arduino/
