# Tools

# ESP Tool

```sh
xe1gyq@jessie:~$ sudo pip install setuptools
xe1gyq@jessie:~$ sudo pip install esptool
```

```sh
xe1gyq@jessie:~$ git clone https://github.com/themadinventor/esptool.git
Cloning into 'esptool'...
remote: Counting objects: 385, done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 385 (delta 0), reused 0 (delta 0), pack-reused 382
Receiving objects: 100% (385/385), 152.05 KiB | 0 bytes/s, done.
Resolving deltas: 100% (211/211), done.
Checking connectivity... done.
```

```sh
xe1gyq@jessie:~$ cd esptool/
xe1gyq@jessie:~/esptool$ ls
esptool.py  LICENSE  MANIFEST.in  README.md  setup.py
xe1gyq@jessie:~/esptool$ 
```

```sh
root@jessie:/home/xe1gyq/esptool# sudo apt-get purge python-pkg-resources
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libc-ares-dev libjs-node-uuid libjs-underscore libv8-3.14-dev node-abbrev
  node-ansi node-ansi-color-table node-archy node-async node-block-stream
  node-combined-stream node-cookie-jar node-delayed-stream node-forever-agent
  node-form-data node-fstream node-fstream-ignore node-github-url-from-git
  node-glob node-graceful-fs node-inherits node-ini node-json-stringify-safe
  node-lockfile node-lru-cache node-mime node-minimatch node-mkdirp
  node-mute-stream node-node-uuid node-nopt node-normalize-package-data
  node-npmlog node-once node-osenv node-qs node-read node-read-package-json
  node-request node-retry node-rimraf node-semver node-sha node-sigmund
  node-slide node-tar node-tunnel-agent node-underscore node-which nodejs-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gyp* node-gyp* npm* python-cryptography* python-openssl*
  python-pkg-resources*
0 upgraded, 0 newly installed, 6 to remove and 3 not upgraded.
After this operation, 4,793 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 156395 files and directories currently installed.)
Removing npm (1.4.21+ds-2) ...
Purging configuration files for npm (1.4.21+ds-2) ...
Removing node-gyp (0.12.2+ds-1) ...
Removing gyp (0.1~svn1729-3) ...
Removing python-openssl (0.14-1) ...
Removing python-cryptography (0.6.1-1) ...
Removing python-pkg-resources (5.5.1-1) ...
Processing triggers for man-db (2.7.0.2-5) ...
```

```sh
root@jessie:/home/xe1gyq/esptool# sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libc-ares-dev libjs-node-uuid libjs-underscore libv8-3.14-dev node-abbrev
  node-ansi node-ansi-color-table node-archy node-async node-block-stream
  node-combined-stream node-cookie-jar node-delayed-stream node-forever-agent
  node-form-data node-fstream node-fstream-ignore node-github-url-from-git
  node-glob node-graceful-fs node-inherits node-ini node-json-stringify-safe
  node-lockfile node-lru-cache node-mime node-minimatch node-mkdirp
  node-mute-stream node-node-uuid node-nopt node-normalize-package-data
  node-npmlog node-once node-osenv node-qs node-read node-read-package-json
  node-request node-retry node-rimraf node-semver node-sha node-sigmund
  node-slide node-tar node-tunnel-agent node-underscore node-which nodejs-dev
  python-cffi python-ply python-pycparser python-six
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
root@jessie:/home/xe1gyq/esptool# pip install pyserial
Collecting pyserial
  Using cached pyserial-3.0.1.tar.gz
Building wheels for collected packages: pyserial
  Running setup.py bdist_wheel for pyserial ... done
  Stored in directory: /root/.cache/pip/wheels/06/71/f1/d8c81329abcaf4c623daff8af76a7dbf00f055cb8205cec0ef
Successfully built pyserial
Installing collected packages: pyserial
Successfully installed pyserial-3.0.1
root@jessie:/home/xe1gyq/esptool# 
```

```sh
root@jessie:/home/xe1gyq/esptool# python esptool.py write_flash 0x2000 nodemcu-master-14-modules-2016-04-10-05-04-51-integer.bin 
Connecting...
Erasing flash...
Took 1.64s to erase flash block
Wrote 477184 bytes at 0x00002000 in 46.1 seconds (82.8 kbit/s)...

Leaving...
```

```sh
root@jessie:/home/xe1gyq/esptool# python esptool.py read_mac
Connecting...
MAC: 18:f0:14:da:27:2f
root@jessie:/home/xe1gyq/esptool# python esptool.py flash_id
Connecting...
Manufacturer: e0
Device: 4016
root@jessie:/home/xe1gyq/esptool# python esptool.py chip_id
Connecting...
Chip ID: 0x00dc273f
```