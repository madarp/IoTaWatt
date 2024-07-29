# My Recent Updates

This is my fork of the [IoTaWatt](https://github.com/boblemaire/IoTaWatt) project.  
I am attempting to keep it up-to-date with recent changes to the Crypto libraries, and also make it more Linux-friendly.

I use WSL2 Ubuntu in Windows.  To achieve the PlatformIO connectivity to flash and do serial monitoring, I had to map the windows COM port over to WSL.
- Install the [usbipd](https://github.com/dorssel/usbipd-win/releases) utility into Windows.  This will forward USB traffic over the IP connection between Windows and WSL.

In a PowerShell __admin__ window, note the usb busid of Silicon Labs CP210x.  
> `usbipd list`

Share the Silicon Labs CP210x USB to UART Bridge device over to WSL
> `usbipd bind --busid <busid>`

Attach the Silicon Labs Bridge device into WSL.  It will become unavailable in Windows
>    `usbipd attach --wsl busid <busid>`

What it should look like when done:

 
```
PS C:\Windows\system32> usbipd list
Connected:
BUSID  VID:PID    DEVICE                                                        STATE
1-2    0764:0501  USB Input Device                                              Not shared
1-6    03f0:0b92  HyperX Virtual Surround Sound, USB Input Device               Not shared
2-5    1462:7c37  USB Input Device                                              Not shared
7-1    048d:1336  USB Mass Storage Device                                       Not shared
7-3    10c4:ea60  Silicon Labs CP210x USB to UART Bridge (COM7)                 Attached
8-4    0451:ca01  USB Input Device                                              Not shared
9-1    046d:0825  Logi C270 HD WebCam                                           Not shared
9-2    046d:c52b  Logitech USB Input Device, USB Input Device                   Not shared
```
In Ubuntu:
```
~ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 10c4:ea60 Silicon Labs CP210x UART Bridge
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

-------
# IoTaWatt WiFi Electricity Monitor Project

IoTaWatt is an open-source, open hardware project to produce an accurate, inexpensive, and easy-to-use energy monitor.  
It can use any of dozens of common current transformers and will report the data locally via an integrated web server, or upload to any of several third-party energy websites/databases. Configuration and administration are through an easy-to-use browser-based utility running on a computer, tablet, or smartphone.

![IoTaWatt USA Bundle](Docs/pics/readmepic.jpg)
*IoTaWatt North America Bundle with two CTs for Mains*

IoTaWatt is a full-function standalone energy monitor with the capability to store and serve up to 15 years (or more) of comprehensive usage data and has an integrated web-server with visualization apps. At the same time, it can upload data to any and all of several (and counting) web-based database and reporting systems.

Hardware is open and uses an ESP8266 nodeMCU, MCP3208 12-bit ADCs, an RTC, and an SD card. The commercially manufactured unit is tested and certified to UL standards in the US and Canada, CE compliant, and FCC compliant and comes with a custom enclosure and wall mount.

Metrics accumulated to 5-second resolution are Voltage (V), Power (Watts), Energy (kWh), VA, and PF. While not certified to a standard, users typically report accuracy within 1% of their revenue meters.

With over 1,000 units sold worldwide over the past year, it's now starting to get the attention of energy professionals.

The software project is not commercial; however, it was necessary to establish a legal entity (IoTaWatt, Inc.) in order to manufacture, certify, and sell the hardware worldwide. There is an investment in that infrastructure that needs to be recovered through sales. You can visit the [IoTaWatt Stuff Store](https://stuff.iotawatt.com) to get one.

The unit is manufactured in the USA.

*   [Documentation](https://iotawatt.readthedocs.io)
*   [Project Website](https://iotawatt.com)
*   [User Forum](https://community.iotawatt.com)

![Inputs/Outputs Display](Docs/pics/status/inputsOutputsDisplay.png)
![Multichannel Graph](Docs/pics/graphMultichannel.jpg)
![Total Power Output](Docs/pics/outputs/totalPowerOutput.png)
![PV Output Display](Docs/pics/PVoutput/PVoutputDisplay.png)
![InfluxDB Grafana](Docs/pics/influxDBGrafana.png)
