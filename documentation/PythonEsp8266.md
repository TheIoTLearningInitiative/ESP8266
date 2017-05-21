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

# Deploy

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


