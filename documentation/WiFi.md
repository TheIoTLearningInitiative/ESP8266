# WiFi

Taken from [Sabas1080 Github](https://github.com/sabas1080/OpenWiFiDetectorESP8266)

## Search

```sh
/*
 *MASLOW: an Open WiFi Detector with ESP8266 
 *based in Adafruit https://learn.adafruit.com/wifi-hotspot-finder-adafruit-pro-trinket-cc3000
 * by Andres Sabas
 * The Inventor's House Hackerspace
 * 19 sept 2015
 */
 
#include "ESP8266WiFi.h"

const int sleepTimeS = 30;

void sleep_now(){ 
  Serial.print(F("Sleeping..."));
  ESP.deepSleep(sleepTimeS * 1000000);
}

void setup() {
  Serial.begin(115200);
  WiFi.mode(WIFI_STA);
  WiFi.disconnect();
  delay(100);
  pinMode(BUILTIN_LED, OUTPUT);
  Serial.println("Setup done");
}
  
void loop() {
  uint8_t sec;
  analogWrite(BUILTIN_LED, 10);
  Serial.print(F("Scanning..."));
  int n = WiFi.scanNetworks(); // WiFi.scanNetworks will return the number of networks found
  Serial.println(F("scan done"));
  if (n == 0)
    Serial.println(F("no networks found"));
  else
  {
    Serial.print(n); Serial.print(F(" network"));
      if(n > 1) Serial.print('s');
      Serial.println(F(" found:"));
    for (int i = 0; i < n; ++i)
    {
      int sec = WiFi.encryptionType(i);
      
        // Print SSID and RSSI for each network found
        Serial.print(i + 1);
        Serial.print(": ");
        Serial.print(WiFi.SSID(i));
        Serial.print(" (");
        Serial.print(WiFi.RSSI(i));
        Serial.print(")");
        Serial.println(sec);
        delay(10);

        if((sec == ENC_TYPE_NONE || sec == ENC_TYPE_WEP) && (WiFi.RSSI(i) > -95)) {
            analogWrite(BUILTIN_LED, 1023);
            delay(1000);
            Serial.println("Not security");
            sleep_now();
        }
    }
  }

}
```

## Connect

```c
#include <ESP8266WiFi.h>
#include <ESP8266WiFiMulti.h>

ESP8266WiFiMulti WiFiMulti;

void setup() {
    Serial.begin(115200);
    delay(10);

    WiFiMulti.addAP("INFINITUMfdca", "1d8856da87");

    Serial.println();
    Serial.println();
    Serial.print("Wait for WiFi... ");

    while(WiFiMulti.run() != WL_CONNECTED) {
        Serial.print(".");
        delay(500);
    }

    Serial.println("");
    Serial.println("WiFi connected");
    Serial.println("IP address: ");
    Serial.println(WiFi.localIP());

    delay(500);
}


void loop() {
    const uint16_t port = 80;
    const char * host = "192.168.1.1";

    Serial.print("connecting to ");
    Serial.println(host);

    WiFiClient client;

    if (!client.connect(host, port)) {
        Serial.println("connection failed");
        Serial.println("wait 5 sec...");
        delay(5000);
        return;
    }

    client.print("Send this data to server");

    String line = client.readStringUntil('\r');
    client.println(line);

    Serial.println("closing connection");
    client.stop();
    
    Serial.println("wait 5 sec...");
    delay(5000);
}
```
