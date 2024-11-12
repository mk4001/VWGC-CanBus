# VWGC-CanBus
VolksWagen Grand California Can Bus control

For all VW Grand California 600 and 680 owners, this project will help you understand how the Leisure compartment CanBus works, which is independent (or almost) from the Crafter's.

In this exercise I mapped the activation codes of the various devices: buttons, lights, control panel, etc.

I also created a portable extension (smartphone or tablet) of the Dometic control panel that the van is equipped with.

Hardware: I used a Raspberry PI 3B plus but the same thing can easily be done with a Raspberry PI Zero 2 W, smaller, more comfortable and more economical in power consumption.
The CAN-BUS plug-in board used for this project is a: "Waveshare RS485 CAN HAT for Raspberry Pi Zero/Zero W/Zero WH/2B/3B/3B, integrated CAN controller: MCP2515, 485 transceiver: SP3485", purchased on AliExpress.

Software: in addition to the basic "can-utils" module easily installable using the SUDO APT INSTALL command, I developed the graphical interface using Node-RED, convenient, practical, fast.
