# VWGC-CanBus
VolksWagen Grand California Can Bus control

For all VW Grand California 600 and 680 owners, this project will help you understand how the Leisure compartment CanBus works, which is independent (or almost) from the Crafter's.

In this exercise I mapped the activation codes of the various devices: buttons, lights, control panel, etc.

I also created a portable extension (smartphone or tablet) of the Dometic control panel that the van is equipped with.

<img width="355" alt="Screenshot 2024-11-12 at 10 03 32" src="https://github.com/user-attachments/assets/a5391275-344e-4d1b-9a47-f218824a07e9">

Hardware: I used a Raspberry PI 3B plus but the same thing can easily be done with a Raspberry PI Zero 2 W, smaller, more comfortable and more economical in power consumption.
The CAN-BUS plug-in board used for this project is a: "Waveshare RS485 CAN HAT for Raspberry Pi Zero/Zero W/Zero WH/2B/3B/3B, integrated CAN controller: MCP2515, 485 transceiver: SP3485", purchased on AliExpress.

![71zU665C5QL](https://github.com/user-attachments/assets/69e259d7-0d23-4f9c-8c85-0adf21cbc9ba)
![712Thv4BfBL](https://github.com/user-attachments/assets/836959f0-23bf-4912-a74c-60e0c929d72c)
![RS485-CAN-HAT-size](https://github.com/user-attachments/assets/b488f949-a080-42d0-9930-93110be346e6)


Software: in addition to the basic "can-utils" module easily installable using the "**SUDO APT INSTALL**" command, I developed the graphical interface using Node-RED, convenient, practical, fast.

The Flow used for this dashboard is: "node-red-contrib-socketcan", installable simply from console using the command:

![node-red-contrib-socketcan](https://github.com/user-attachments/assets/f5503e8e-380a-46b1-a069-a16e7245b6b6)

https://flows.nodered.org/node/node-red-contrib-socketcan

**npm install node-red-contrib-socketcan**

Software Installation:

After having mounted the CAN HAT plug-in card on your Raspberry, you need to proceed as follows:

**sudo apt install can-utils**

**sudo ip link set can0 down**

**sudo ip link set can0 up type can bitrate 500000 loopback off listen-only off**

**sudo nano /etc/network/interfaces**

modifying as follows:

<img width="421" alt="Screenshot 2024-11-12 at 10 49 07" src="https://github.com/user-attachments/assets/813c13d5-f577-4c91-ae50-05b2e33ad62f">
