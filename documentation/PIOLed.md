# Led

## Code Writing

```sh
xe1gyq@jessie:~/nodemcu$ echo > src/main.ino
xe1gyq@jessie:~/nodemcu$ vi src/main.ino
```

```c
#include "Arduino.h"

void setup()
{
  pinMode(LED_BUILTIN, OUTPUT);
}

void loop()
{
  digitalWrite(LED_BUILTIN, HIGH);
  delay(500);
  digitalWrite(LED_BUILTIN, LOW);
  delay(500);
}
```

## Code Execution

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