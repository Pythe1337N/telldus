## Installation telldus-core
### Install prerequisites.
* ```sudo apt-get install libftdi1 libftdi-dev libconfuse1 libconfuse-dev cmake```

In the ```telldus-core``` directory run
* ```sudo cmake .```

If you get

— Could NOT find Doxygen (missing: DOXYGEN_EXECUTABLE)
run:
* ```sudo apt-get install doxygen```

After cmake is done run
* ```sudo make```
* ```sudo make install```

This will setup everything you need and create an epmty config file at ```/etc/tellstick.conf```
To this file you'll manually need to add the controller.
To find the serial of your tellstick run ```dmesg``` and look for:
```
[    1.394619] usb 1-6: New USB device found, idVendor=1781, idProduct=0c30
[    1.394622] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.394624] usb 1-6: Product: TellStick
[    1.394625] usb 1-6: Manufacturer: Telldus
[    1.394626] usb 1-6: SerialNumber: xxxxxxxx
```
Then use the SerialNumber above in the controller's serial field.
Type seems to be set tp `1` for original TellSticks and `2` for TellStick Duo. 
```
deviceNode = "/dev/tellstick"
controller {
  id = 1
  name = "TellStick"
  type = 1
  serial = "xxxxxxxx"
}
```
