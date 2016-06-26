# WiFi

Taken from [Sabas1080 github](https://github.com/sabas1080/OpenWiFiDetectorESP8266)

## Search

```sh
#include "ESP8266WiFi.h"


const int sleepTimeS = 30;

void setup() {
  Serial.begin(115200);

  // Set WiFi to station mode and disconnect from an AP if it was previously connected
  WiFi.mode(WIFI_STA);
  WiFi.disconnect();
  delay(100);
  pinMode(4, OUTPUT);
  Serial.println("Setup done");

}
  
void loop() {
  uint8_t sec;
  
  analogWrite(4, 10);

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

        if((sec == ENC_TYPE_NONE || sec == ENC_TYPE_WEP) && (WiFi.RSSI(i) > -95)) { // If open network and good signal...
            // Switch LED to conspicuous 'open networks' flash immediately
            analogWrite(4, 1023); // 1 sec
            delay(1000);
            // "Open hotspot" is as good as the indicator gets and the scan
            // can stop now, get into power-saving sleep mode ASAP.
            // If you're using the Serial console and want to see all
            // networks displayed, comment out this line:
            //Serial.println("Not security");
            //Mode Sleep for ESP8266 Version 12 or model with pin16 avaible
            //Necesary jump RST and GPIO16
            
            sleep_now(); // Function Sleep 30 seconds
        }
    }
  }

}

//Mode Sleep for ESP8266 Version 12 or model with pin16 avaible

void sleep_now(){
 
  Serial.print(F("Sleeping..."));
  // deepSleep time is defined in microseconds. Multiply
  // seconds by 1e6 
  ESP.deepSleep(sleepTimeS * 1000000);
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
