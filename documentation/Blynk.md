Blynk
==

> Create an app for any connected project or product based on Arduino, Raspberry Pi, ESP8266, SparkFun, and other hardware.

- [Blynk Homepage](http://www.blynk.cc/)
- [Blynk Getting Started](http://www.blynk.cc/getting-started/)

```sh
xe1gyq@jessie:~/nodemcu$ platformio lib search *blynk*
Found 1 libraries:

[ ID  ] Name             Compatibility         "Authors": Description
--------------------------------------------------------------------------------------------------------------------------
[ 415 ] Blynk            arduino, energia, mbed, wiringpi, atmelavr, atmelsam, timsp430, titiva, nordicnrf51, espressif, native "Volodymyr Shymanskyy": Build a smartphone app for your project in minutes. Works with Arduino, ESP8266, Raspberry Pi, Intel Edison/Galileo, LinkIt ONE, Particle Core/Photon, Banana Pro, LeMaker Guitar, Energia, MBED, LightBlue Bean, ...
xe1gyq@jessie:~/nodemcu$ platformio lib install 415
Installing library [ 415 ]:
Downloading  [####################################]  100%
Unpacking  [####################################]  100%
The library #415 'Blynk' has been successfully installed!
xe1gyq@jessie:~/nodemcu$ vi src/blynk.ino
```

```sh
xe1gyq@jessie:~/nodemcu$ platformio run --target upload
espcomm_send_command: receiving 2 bytes of data
writing flash
..............................................................................................................................................................................................................................................
starting app without reboot
espcomm_send_command: sending command header
espcomm_send_command: sending command payload
espcomm_send_command: receiving 2 bytes of data
closing bootloader
============================================== [SUCCESS] Took 34.32 seconds ==============================================
xe1gyq@jessie:~/nodemcu$ 
```