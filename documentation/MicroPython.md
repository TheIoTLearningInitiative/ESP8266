# MicroPython

> MicroPython - a lean and efficient Python implementation for microcontrollers and constrained systems [MicroPython Github](https://github.com/micropython/micropython)

- [MicroPython Documentation ESP8266](http://docs.micropython.org/en/v1.8/esp8266/index.html)
- [MicroPython tutorial for ESP8266](https://docs.micropython.org/en/latest/esp8266/esp8266/tutorial/index.html)

```sh
root@host:~# apt-get install libffi-dev pkg-config
```

```sh
user@host:~$ git clone https://github.com/micropython/micropython.git
user@host:~$ cd micropython/
```

```sh
user@host:~$ ls
ACKNOWLEDGEMENTS    docs      lib        pic16bit   teensy   zephyr
bare-arm            drivers   LICENSE    py         tests
cc3200              esp8266   logo       qemu-arm   tools
CODECONVENTIONS.md  examples  minimal    README.md  unix
CONTRIBUTING.md     extmod    mpy-cross  stmhal     windows
```

```sh
user@host:~$ cd unix/
user@host:~$ make axtls
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
user@host:~$ su
password
root@host:~# minicom -D /dev/ttyUSB0
    
<reset>
    
>>> 
MicroPython v1.5.2-51-g5b3f0b7 on 2016-01-10; ESP module with ESP8266
Type "help()" for more information.
>>> 
```

