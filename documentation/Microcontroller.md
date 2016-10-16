# Microcontroller


# Espressig 8266

> ESP8266EX is among the most integrated Wi-Fi chips in the industry. Measuring just 5mm x 5mm, ESP8266EX requires minimal external circuitry and integrates a 32-bit Tensilica MCU, standard digital peripheral interfaces, antenna switches, RF balun, power amplifier, low noise receive amplifier, filters and power management modules - all in one small package. [Homepage](https://espressif.com/en/products/hardware/esp8266ex/overview)
> Low-power, highly-integrated Wi-Fi solution
> A minimal of 7 external components
> Wide temperature range: -40°C to +125°C
> ESP8285 - ESP8266 embeded with 8 Mbit flash


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