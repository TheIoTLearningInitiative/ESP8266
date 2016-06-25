Projects
==

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
/*
 ESP8266 Blink by Simon Peter
 Blink the blue LED on the ESP-01 module
 This example code is in the public domain
 
 The blue LED on the ESP-01 module is connected to GPIO1 
 (which is also the TXD pin; so we cannot use Serial.print() at the same time)
 
 Note that this sketch uses LED_BUILTIN to find the pin with the internal LED
*/

void setup() {
  pinMode(LED_BUILTIN, OUTPUT);     // Initialize the LED_BUILTIN pin as an output
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(LED_BUILTIN, LOW);   // Turn the LED on (Note that LOW is the voltage level
                                    // but actually the LED is on; this is because 
                                    // it is acive low on the ESP-01)
  delay(1000);                      // Wait for a second
  digitalWrite(LED_BUILTIN, HIGH);  // Turn the LED off by making the voltage HIGH
  delay(2000);                      // Wait for two seconds (to demonstrate the active low LED)
}
```
