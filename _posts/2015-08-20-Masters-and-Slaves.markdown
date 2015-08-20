---
layout: post
title: Masters and Slaves
---

Modbus is a simple communication protocol used to transfer information between PLCs and other smart devices. Many modern devices support the protocol and with Modbus TCP operating on standard Ethernet networks, Modbus is easier than ever to use. There are countless great resources on the Internet explaining what Modbus is and how it works.
As you get more confident with the concepts and are thinking about using Modbus in your next project there are a few thing you should keep in mind:

1. Terminology – In Modbus the 'master' is the device that makes the requests, and the 'slave' is the device that answers the requests. For example you may have a SCADA computer which is the 'master', it can get values from the 'slave' PLC. Some manufactures, however, may not stick to the convention and instead use 'client'/'server' terminology. A 'client' requests information from the 'server' which serves the 'client' by sending the information back. 'master' = 'client' and 'slave' = 'server'. You have to be careful, your PLC manufacturer may claim that your PLC acts as a Modbus TCP 'server'. And your device manufacture will assure you that their device supports Modbus TCP, but if it is a 'server' as well you will run into trouble. Both devices will be sitting on the network, waiting for a request, but neither will be able to initiate a request so no communication will occur.

2. Flexibility – In Modbus TCP it may be possible to write to addresses you should not write to. For instance, say you have a device which is a Modbus 'master'. You configure it to write to a certain address in the PLC 'slave'. If you are not careful, you may write to the wrong address. As with all things make sure you test it before you implement it in production.

3. Documentation – It is possible to write to addresses on the 'slave' without explicitly stating it in the 'slave' device's configuration. In some older devices, this can provide a fault finding nightmare. Say the system is accidentally writing to a certain address, turning an alarm on. There may be no clues in the code as to what is writing to that address. My advice is to document your code thoroughly in order to avoid this situation. Newer PLCs will set aside certain memory regions which allow Modbus communication. This is useful in that it clearly demarcates areas of memory that may be written to by other Modbus devices.

Aside from these considerations, I think Modbus TCP is a highly flexible and easy to use communications protocol, and valuable in any system integrator's tool box.