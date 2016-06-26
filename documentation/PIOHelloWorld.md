# Hello World

```
xe1gyq@jessie:~/nodemcu$ vi src/blink.ino
```

```c
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
  delay(500);
  // turn the LED off by making the voltage LOW
  digitalWrite(LED_BUILTIN, LOW);
   // wait for a second
  delay(500);
}
```

```sh
xe1gyq@jessie:~/nodemcu$ platformio run --target upload
...
...
espcomm_send_command: receiving 2 bytes of data
writing flash
..........................................................................................................................................................................................................................
starting app without reboot
espcomm_send_command: sending command header
espcomm_send_command: sending command payload
espcomm_send_command: receiving 2 bytes of data
closing bootloader
========================= [SUCCESS] Took 29.27 seconds =========================
xe1gyq@jessie:~/nodemcu$ 
```