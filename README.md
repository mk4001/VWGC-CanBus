# VWGC-CanBus
VolksWagen Grand California Can Bus control

For all VW Grand California 600 and 680 owners, this project will help you understand how the Leisure compartment CanBus works, which is independent (or almost) from the Crafter's one.

------------------------------------------------------------------------------------

**Disclaimer:**
This project is for educational and research purposes only. 
All intellectual property, trademarks, and copyrights related to the CAN-BUS codes and protocols belong to Volkswagen Group (Volkswagen AG). 
No part of this project is intended to infringe on Volkswagen’s rights or facilitate unauthorized access, modification, or misuse of their proprietary systems. 
The information provided here is shared solely for learning and understanding vehicle communication protocols. Any use of this data is at the user's own risk and responsibility.

------------------------------------------------------------------------------------

In this exercise I mapped the activation codes of the various devices: buttons, lights, control panel, etc.

I also created a portable version (smartphone or tablet) of the Dometic control panel that the van is equipped with.

<img width="355" alt="Screenshot 2024-11-12 at 10 03 32" src="https://github.com/user-attachments/assets/a5391275-344e-4d1b-9a47-f218824a07e9">

------------------------------------------------------------------------------------

**Hardware:** 
I used a Raspberry PI 3B plus but the same thing can easily be done with a Raspberry PI Zero 2 W, smaller, more comfortable and more economical in power consumption.

The CAN-BUS plug-in board used for this project is a: "Waveshare RS485 CAN HAT for Raspberry Pi Zero/Zero W/Zero WH/2B/3B/3B, integrated CAN controller: MCP2515, 485 transceiver: SP3485", purchased on AliExpress.

![71zU665C5QL](https://github.com/user-attachments/assets/69e259d7-0d23-4f9c-8c85-0adf21cbc9ba)
![712Thv4BfBL](https://github.com/user-attachments/assets/836959f0-23bf-4912-a74c-60e0c929d72c)
![RS485-CAN-HAT-size](https://github.com/user-attachments/assets/b488f949-a080-42d0-9930-93110be346e6)

------------------------------------------------------------------------------------

**Software:** 
in addition to the basic "can-utils" module easily installable using the "**SUDO APT INSTALL**" command, I developed the graphical interface using Node-RED, convenient, practical, fast.

The Flow used for this dashboard is: "node-red-contrib-socketcan", installable simply from console using the command:

![node-red-contrib-socketcan](https://github.com/user-attachments/assets/f5503e8e-380a-46b1-a069-a16e7245b6b6)

https://flows.nodered.org/node/node-red-contrib-socketcan

**npm install node-red-contrib-socketcan**

------------------------------------------------------------------------------------

**Software Installation:**

After having mounted the CAN HAT plug-in card on your Raspberry, you need to proceed as follows:

**sudo apt install can-utils**

**sudo ip link set can0 down**

**sudo ip link set can0 up type can bitrate 500000 loopback off listen-only off**

**sudo nano /etc/network/interfaces**

modifying as follows:

<img width="421" alt="Screenshot 2024-11-12 at 10 49 07" src="https://github.com/user-attachments/assets/813c13d5-f577-4c91-ae50-05b2e33ad62f">

------------------------------------------------------------------------------------

To be able to "sniff" the data coming from the CAN-BUS it is sufficient to use the command:

**cansniffer can0 -c -t0**

To send a command to a specific device, you must use the command:

**cansend can0 18EF70C9#00.40.00.00.00.00.00.00** (Example)

The complete list of messages & commands that I was able to collect:

https://github.com/mk4001/VWGC-CanBus/blob/main/Table.md

------------------------------------------------------------------------------------

To import the Flow Node-RED that generates the dashboard that can then be used via a browser, you need to import the attached Json Flow.

https://github.com/mk4001/VWGC-CanBus/blob/main/flows.json

------------------------------------------------------------------------------------

**Leisure CAN-Bus Connections:**

As you can see from the original wiring diagram of the manufacturer below, there are several points where you can connect to the "Convenience CAN-Bus" or Leisure CAN-Bus.

<img width="829" alt="MRS RGB Led2" src="https://github.com/user-attachments/assets/779b040c-39f3-4766-86ee-b8d85bd788e7">


I found it more convenient to connect to the R/G/B controller of the LED strip called: "7C4 947 022" more precisely to pins 9 and 10, as reported by the manufacturer's nomenclature.

<img width="953" alt="Screenshot 2024-11-13 at 09 49 07" src="https://github.com/user-attachments/assets/4735321d-cc62-4921-81b8-273e5689e8df">

The RGB controller is obviously located inside the technical cabinet exactly under the 230V electrical panel

![VW controller CAN-BUS](https://github.com/user-attachments/assets/c56e8efb-ccc1-46e1-bcbd-4c871873f29d)


------------------------------------------------------------------------------------

If you want to contribute to my research efforts on this and other reverse engineering projects of the VW Grand California, one of yours will be of great help.

[![Buy Me a Coffee](https://img.shields.io/badge/Buy%20Me%20a%20Coffee-donate-yellow)](https://www.buymeacoffee.com/mk4001)

