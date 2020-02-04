# usbinfo

search and display of USB device connection marks left in the Windows SYSTEM registry


### regdump

> from https://github.com/adoxa/regdump

download raw [regdump.c](https://raw.githubusercontent.com/patatetom/usbinfo/master/regdump.c), check it and compile it with `gcc` :

```bash
$ gcc regdump.c -o ~/.local/bin/regdump
```

dump a SYSTEM registry :

```bash
$ # -t switch is important !
$ regdump -t /mnt/sda2/Windows/System32/config/SYSTEM > /tmp/SYSTEM.dump
```


### usbinfo

download raw [usbinfo](https://raw.githubusercontent.com/patatetom/usbinfo/master/usbinfo) bash script, check it and make it executable :

```bash
$ curl https://raw.githubusercontent.com/patatetom/usbinfo/master/usbinfo > ~/.local/bin/usbinfo
$ chmod +x ~/.local/bin/usbinfo
```

edit his `ids` variable :

```bash
$ # Ctrl-O to save changes and Ctrl-X to quit nano editor
$ nano ~/.local/bin/usbinfo
…
#ids=/var/lib/usbutils/usb.ids	# on Debian, provided by package "usb.ids"
#ids=/usr/share/hwdata/usb.ids	# on Arch, provided by package "hwids"
…
```

parse the dump :

```bash
$ # fields are last time, title, serial number, first time, device description and friendly name
$ # fields are separated by one tab \t character
$ usbinfo /tmp/SYSTEM.dump | sort -r | grep ^2020-
2020-01-21 16:19:47	---- End -----
2020-01-21 16:19:27	VendorId 46F4 - ProductId 0001	1-0000:00:03.0-2	2020-01-21 16:07:12	USB Mass Storage Device
2020-01-21 16:07:12	Disk QEMU QEMU_HARDDISK	1-0000:00:03.0-2&0	2020-01-21 16:07:12	Disk drive	QEMU QEMU HARDDISK USB Device
2020-01-21 16:04:55	Adomax Technology Co., Ltd - ProductId 0001	28754-0000:00:03.0-1	2020-01-21 15:02:00	USB Input Device
```
