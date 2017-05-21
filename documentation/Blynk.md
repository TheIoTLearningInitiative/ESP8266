# Blynk

> Create an app for any connected project or product based on Arduino, Raspberry Pi, ESP8266, SparkFun, and other hardware.

- [Blynk Homepage](http://www.blynk.cc/)
- [Blynk Getting Started](http://www.blynk.cc/getting-started/)
- [Blynk Community](http://community.blynk.cc/)

## Library Installation

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
```

## Code Writing

```sh
xe1gyq@jessie:~/nodemcu$ echo > src/main.ino
xe1gyq@jessie:~/nodemcu$ vi src/main.ino
```

```c
#define BLYNK_PRINT Serial
#include <ESP8266WiFi.h>
#include <BlynkSimpleEsp8266.h>

char auth[] = "80c754ba45644ec4b4b402eb8ae10163";

void setup()
{
  Serial.begin(9600);
  Blynk.begin(auth, "INFINITUMfjph", "1c3889dfdb");
}

void loop()
{
  Blynk.run();
}
```

## Code Execution

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