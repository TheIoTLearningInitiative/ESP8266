# Micro Python x86

```sh
user@host:~$ cd micropython/
user@host:~$ ls
```

```sh
user@host:~$ cd unix/
user@host:~$ make axtls
user@host:~$ make
```

```sh
user@host:~$ ./micropython
```

```python
>>> 
MicroPython v1.8.7-781-g299c0a39 on 2017-05-21; linux version
Use Ctrl-D to exit, Ctrl-E for paste mode
>>> print("hi")
hi
>>> 
```

# Micro Python Pip

```sh
user@host:~$ ./micropython -m upip install micropython-pystone
Installing to: /home/xe1gyq/.micropython/lib/
Warning: pypi.python.org SSL certificate is not validated
Installing micropython-pystone 3.4.2-2 from https://pypi.python.org/packages/13/00/8f7c7ab316e8850ea3273956e1370d008cfd36697dec2492388d3b000335/micropython-pystone-3.4.2-2.tar.gz
xe1gyq@kali:~/NodeMcu/micropython/unix$ 
```
