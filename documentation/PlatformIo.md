PlatformIO
==

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

```sh
xe1gyq@jessie:~/nodemcu$ platformio lib install 6 
Installing library [ 6 ]:
Downloading  [####################################]  100%
Unpacking  [####################################]  100%
The library #6 'XBee' has been successfully installed!
xe1gyq@jessie:~/nodemcu$ platformio lib install 89
Installing library [ 89 ]:
Downloading  [####################################]  100%
Unpacking  [####################################]  100%
The library #89 'PubSubClient' has been successfully installed!
xe1gyq@jessie:~/nodemcu$ vi mqtt.ino
```

```c
/*
 Basic ESP8266 MQTT example
 This sketch demonstrates the capabilities of the pubsub library in combination
 with the ESP8266 board/library.

 It connects to an MQTT server then:
  - publishes "hello world" to the topic "outTopic" every two seconds
  - subscribes to the topic "inTopic", printing out any messages
    it receives. NB - it assumes the received payloads are strings not binary
  - If the first character of the topic "inTopic" is an 1, switch ON the ESP Led,
    else switch it off

 It will reconnect to the server if the connection is lost using a blocking
 reconnect function. See the 'mqtt_reconnect_nonblocking' example for how to
 achieve the same result without blocking the main loop.

 To install the ESP8266 board, (using Arduino 1.6.4+):
  - Add the following 3rd party board manager under "File -> Preferences -> Additional Boards Manager URLs":
       http://arduino.esp8266.com/stable/package_esp8266com_index.json
  - Open the "Tools -> Board -> Board Manager" and click install for the ESP8266"
  - Select your ESP8266 in "Tools -> Board"

*/

#include <ESP8266WiFi.h>
#include <PubSubClient.h>

// Update these with values suitable for your network.

const char* ssid = "........";
const char* password = "........";
const char* mqtt_server = "broker.mqtt-dashboard.com";

WiFiClient espClient;
PubSubClient client(espClient);
long lastMsg = 0;
char msg[50];
int value = 0;

void setup() {
  pinMode(BUILTIN_LED, OUTPUT);     // Initialize the BUILTIN_LED pin as an output
  Serial.begin(115200);
  setup_wifi();
  client.setServer(mqtt_server, 1883);
  client.setCallback(callback);
}

void setup_wifi() {

  delay(10);
  // We start by connecting to a WiFi network
  Serial.println();
  Serial.print("Connecting to ");
  Serial.println(ssid);

  WiFi.begin(ssid, password);

  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }

  Serial.println("");
  Serial.println("WiFi connected");
  Serial.println("IP address: ");
  Serial.println(WiFi.localIP());
}

void callback(char* topic, byte* payload, unsigned int length) {
  Serial.print("Message arrived [");
  Serial.print(topic);
  Serial.print("] ");
  for (int i = 0; i < length; i++) {
    Serial.print((char)payload[i]);
  }
  Serial.println();

  // Switch on the LED if an 1 was received as first character
  if ((char)payload[0] == '1') {
    digitalWrite(BUILTIN_LED, LOW);   // Turn the LED on (Note that LOW is the voltage level
    // but actually the LED is on; this is because
    // it is acive low on the ESP-01)
  } else {
    digitalWrite(BUILTIN_LED, HIGH);  // Turn the LED off by making the voltage HIGH
  }

}

void reconnect() {
  // Loop until we're reconnected
  while (!client.connected()) {
    Serial.print("Attempting MQTT connection...");
    // Attempt to connect
    if (client.connect("ESP8266Client")) {
      Serial.println("connected");
      // Once connected, publish an announcement...
      client.publish("outTopic", "hello world");
      // ... and resubscribe
      client.subscribe("inTopic");
    } else {
      Serial.print("failed, rc=");
      Serial.print(client.state());
      Serial.println(" try again in 5 seconds");
      // Wait 5 seconds before retrying
      delay(5000);
    }
  }
}
void loop() {

  if (!client.connected()) {
    reconnect();
  }
  client.loop();

  long now = millis();
  if (now - lastMsg > 2000) {
    lastMsg = now;
    ++value;
    snprintf (msg, 75, "hello world #%ld", value);
    Serial.print("Publish message: ");
    Serial.println(msg);
    client.publish("outTopic", msg);
  }
}
```

```sh
xe1gyq@jessie:~/nodemcu$ platformio run --target upload
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

- https://atom.io/packages/platomformio

