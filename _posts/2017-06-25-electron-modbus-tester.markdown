---
layout: post
title: Modbus TCP Tester

---


I have recently been experimenting with the [electron](https://electron.atom.io/) project from Github. It uses web technologies to build desktop applications. As I work with industrial control systems, I decide to make a Modbus tester. In electron, web technologies are available (HTML, CSS and JavaScript), so I searched for a JavaScript Modbus library. I found [JSModbus](https://github.com/Cloud-Automation/node-modbus) which is hosted on Github.

<h4>Initial Testing</h4>
You can start two instances of my [Electron_Modbus](https://github.com/AnthonyMujic/electron_modbus) application and configure one as a server and the other as a client. Provided you get the address and port settings correct, you can have communication between the client and the server. At the moment, it isn't anything very exciting, is simply allows you to set and clear bits by clicking on them (when they are set they turn bold):

![Testing Client and Server](/assets/Modbus TCP Tester/1_testing_client_and_server.jpg)

To test the application can communicate with third party equipment, I set it up to communicate with a [Do-more Designer](http://support.automationdirect.com/products/domore.html) simulation PLC.
To configure the Modbus port on the simulation PLC, go to the PLC menu, and select 'System Configuration…' Check the 'Enable Modbus/TCP Server' check box and set the 'TCP Port Number' to match the port number of the Electron_Modbus client application (by default my application sets the port number 8502, as the default Modbus port of 502 can be blocked by default on some operating systems):

![PLC configuration](/assets/Modbus TCP Tester/2_domore_plc_configuration.jpg)

DoMore Designer has some of the most user friendly and comprehensive documentation I have seen for a PLC. In the help files there is a section of Memory Configuration and a sub section on Modbus Memory Blocks. It explains that to prevent malicious software from being able to control all memory on the PLC, it cordons off a section of memory only for Modbus communication. For instance, when my software sets bit one, rather than setting C1 in the PLC, it sets MC1. This bit can then be used in the PLC code, but it makes it explicit that it is a bit set by Modbus.

To try this example, download my electron_modbus application from Github. If you are running the application and the PLC simulator on the same machine, set the 'Server IP Address' to the loopback IP address (127.0.0.1, which is the default). Also ensure you set the port to the same number as the port number set on the PLC.

In the ladder logic, map a number of 'MC' bits to 'C' bits as shown below:

![PLC code](/assets/Modbus TCP Tester/3_plc_code.jpg)

Finally test it:

![successful simulation](/assets/Modbus TCP Tester/4_successful_simulation.jpg)
