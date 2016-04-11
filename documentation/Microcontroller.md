# Microcontroller

## ESP8266

The ESP8266 is a low-cost Wi-Fi chip with full TCP/IP stack and microcontroller capability produced by Shanghai-based Chinese manufacturer, Espressif. [Wikipedia](https://en.wikipedia.org/wiki/ESP8266)

- [ESP8266 Community Forum](http://www.esp8266.com/)
- [ESP8266 Github Community Forum](https://github.com/esp8266)
- [ESP8266 Wiki](https://github.com/esp8266/esp8266-wiki/wiki)
- [ESP8266EX Datasheet](https://www.adafruit.com/images/product-files/2471/0A-ESP8266__Datasheet__EN_v4.3.pdf)
- [ESP8266 Datasheet](https://www.adafruit.com/datasheets/ESP8266_Specifications_English.pdf)
- [ESP8266 Graphical Datasheet](https://cdn.sparkfun.com/datasheets/Wireless/WiFi/ESP8266ModuleV1.pdf)
- [Nurdspace ESP8266](https://nurdspace.nl/ESP8266)
- [ESP8266 Projects](http://benlo.com/esp8266/esp8266Projects.html)

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