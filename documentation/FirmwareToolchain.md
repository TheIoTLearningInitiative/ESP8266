# Toolchain

# Esp8266 SDK

- [Building the toolchain](https://github.com/esp8266/esp8266-wiki/wiki/Toolchain)

# ESP Open SDK

> Free and open (as much as possible) integrated SDK for ESP8266/ESP8285 chips

- [Free and open (as much as possible) integrated SDK for ESP8266/ESP8285 chips](https://github.com/pfalcon/esp-open-sdk)

```sh
root@host:~# sudo apt-get install make unrar-free autoconf automake libtool gcc g++ gperf \
    flex bison texinfo gawk ncurses-dev libexpat-dev python-dev python python-serial \
    sed git unzip bash help2man wget bzip2
```

```sh
root@host:~# sudo apt-get install libtool-bin
```

```sh
root@host:~$ git clone --recursive https://github.com/pfalcon/esp-open-sdk.git
root@host:~$ cd esp-open-sdk/
root@host:~$ make
```

```sh
root@host:~$ export PATH=/home/xe1gyq/NodeMcu/esp-open-sdk/xtensa-lx106-elf/bin:$PATH
```