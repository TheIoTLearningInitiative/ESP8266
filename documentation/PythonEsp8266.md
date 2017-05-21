# Micro Python ESP8266


```sh
user@host:~$ export PATH=/home/xe1gyq/NodeMcu/esp-open-sdk/xtensa-lx106-elf/bin:$PATH
```

```sh
user@host:~$ cd micropython/esp8266
user@host:~$ make
```

```sh
...
LINK build/firmware.elf
   text	   data	    bss	    dec	    hex	filename
 572052	   1096	  64360	 637508	  9ba44	build/firmware.elf
Create build/firmware-combined.bin
esptool.py v1.2
('flash    ', 36256)
('padding  ', 608)
('irom0text', 536940)
('total    ', 573804)
('md5      ', '9c0e81ca947e91beae3e3b7cec9df97f')
```

```sh
user@host:~$ cd unix/
user@host:~$ make axtls
```

# Micro Python Deploy

```sh
user@host:~$ export PATH=/home/xe1gyq/NodeMcu/esp-open-sdk/xtensa-lx106-elf/bin:$PATH
```

```sh
user@host:~$ make PORT=/dev/ttyUSB0 deploy
Use make V=1 or set BUILD_VERBOSE in your environment to increase build verbosity.
Writing build/firmware-combined.bin to the board
#@esptool.py --port /dev/ttyUSB0 write_flash 0 build/firmware-combined.bin
Connecting...
Erasing flash...
Took 0.87s to erase flash block
Wrote 51200 bytes at 0x00000000 in 4.9 seconds (82.9 kbit/s)...
Erasing flash...
Took 1.58s to erase flash block
Wrote 282624 bytes at 0x00010000 in 27.4 seconds (82.5 kbit/s)...

Leaving...
```

```sh
user@host:~$ su
password
root@host:~# minicom -D /dev/ttyUSB0
    
<reset>

MicroPython v1.8.7-781-g299c0a39 on 2017-05-21; ESP module with ESP8266
Type "help()" for more information.
>>> print("hi")
hi
>>> 
```

# Micro Python Execution

```python
MicroPython v1.8.7-781-g299c0a39 on 2017-05-21; ESP module with ESP8266
Type "help()" for more information.
>>> import machine
>>> machine.freq()
80000000
>>> machine.freq(160000000)
>>> import esp
>>> esp.osdebug(None)
>>> esp.osdebug(0)
```

```python
>>> wlan = network.WLAN(network.STA_IF)                                         
>>> wlan.active(True)                                                           
mode : sta(5c:cf:7f:dc:41:fa) + softAP(5e:cf:7f:dc:41:fa)                       
#5 ets_task(4020ed88, 28, 3fff9eb0, 10)                                         
add if0                                                                         
>>> wlan.scan()                                                                 
scandone                                                                        
[(b'INFINITUM09E845', b'0\x91\x8f\t\xe8E', 1, -75, 3, 0), (b'INFINITUMfjph', b']
>>> wlan.isconnected()
False
>>> wlan.connect('INFINITUMfjph', '1c2899dfda')
>>> scandone
state: 0 -> 2 (b0)
state: 2 -> 3 (0)
state: 3 -> 5 (10)
add 0
aid 2
cnt

connected with INFINITUMfjph, channel 2
dhcp client start...
ip:192.168.1.71,mask:255.255.255.0,gw:192.168.1.254                         

>>> wlan.ifconfig()                                                             
('192.168.1.71', '255.255.255.0', '192.168.1.254', '8.8.8.8')                   
>>> 
```

# Micro Python Pip

```sh
>>> import upip                                                                 
>>> upip.install("micropython-struct")                                          
Installing to: /lib/                                                            
Installing to: /lib/                                                            
Warning: pypi.python.org SSL certificate is not validated                       
Installing micropython-struct 0.1.1 from https://pypi.python.org/packages/5d/eez            
>>> upip.install("micropython-pystone")                                         
Installing to: /lib/                                                            
Installing micropython-pystone 3.4.2-2 from https://pypi.python.org/packages/13z
```
