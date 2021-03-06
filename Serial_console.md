# Serial console

To work with the bootloader (usually, U-Boot), you need access to a console. While some devices (e.g., Amlogic-based ones) may provide ways to interact with the bootloader over other means (e.g., USB A-A cable and a proprietary protocol), the most reliable way to interact with the bootloader may be a serial console.

For this you need:

* A host computer ("desktop", we are a using Linux system)
* A USB-to-serial converter (e.g.,  Prolific PL2303 based)

![](img/prolific.jpg)

To attach the serial converter, connect

* GND to GND
* RX to TX
* TX to RX
* __DO NOT__ connect VCC
* Power the device via its power supply

The connectors or test points for the serial console are usually on the PCB and not accessible from the outside of retail products. So you need to open your box. 

## Using Pogo Pins

Depending on the device, it may be necessary to use Pogo Pins to contact the tiny test points or solder points marked with TX, RX, GND.

![](img/pogo_housing.png)

A [3d printed pogo pin fixture](https://www.tinkercad.com/things/0eAaa5mslE4-mini-pogo-housing-for-x96-serial-amlogic) can used to access the tiny serial port test points using P50-B1 0.68mm pogo pins. This fixture can be contacted to the board using a "third hand" commonly used for soldering.

![](img/third_hand.jpg)

## Connecting with `screen`

To connect, do on the host computer:

```
sudo apt-get -y install screen
sudo screen -L -Logfile log.txt /dev/ttyUSB0 115200
```

You should now see and interact with the bootloader (U-Boot) output, as well as the boot log, and be able to interact with the booted system.

__Note:__ With flaky connections, it can happen that sending commands to the device may become impossible. At this point, only a reboot of the host computer seems to restore the communication. (To be verified.)

