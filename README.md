# usbinfo

search and display of USB device connection marks left in the Windows SYSTEM registry


### regdump

> from https://github.com/adoxa/regdump

download raw [regdump.c](https://raw.githubusercontent.com/patatetom/usbinfo/master/regdump.c) and compile it with `gcc` :

```bash
$ gcc regdump.c -o ~/.local/bin/regdump
```

dump a SYSTEM registry :

```bash
$ regdump -t /mnt/sda2/Windows/System32/config/SYSTEM > /tmp/SYSTEM.dump
```


### usbinfo

download raw [usbinfo](https://raw.githubusercontent.com/patatetom/usbinfo/master/usbinfo) bash script and make it executable :

```bash
$ curl https://raw.githubusercontent.com/patatetom/usbinfo/master/usbinfo > ~/.local/bin/usbinfo
$ chmod +x ~/.local/bin/usbinfo
```

parse the dump :

```bash
usbinfo /tmp/SYSTEM.dump
```
