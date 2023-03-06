# Spanned EtherChannel Mode

## Quest: How load balancing 1s done in this mode???

## Ques2: Which device performs load balancing in This mode???

## Ques3: Which one is the highest cluster priority ????

- Individual Interface Mode
- Connection roles
- Unsupported Feature
- Centralized Feature
- Individual Feature

## Individual Interface Mode
--> This mode 1s supported only in routed Firewall (Single/multiple).
--> AI ASA will have individual IP address on their interfaces
--> There will be not Etherchannel created between ASA and Switch
--> Load Balancing 1s perform by the connected Routers using ECMP, PBR

## TASK: Configure Cluster individual interface mode with ASAZ as Master unit.
Configure IP address on ASAs are per diagram

- we create a pool and in that pool we specify the ip address that should be assign to slave memeber
- we bond that pool while configuring ip address on material unit

## Connection Roles:

a. Connection Owner

--> Any ASA which recieves first packet of a connection becomes connection owner.

--> Connection owner calculates a hash based on sre ip, dest ip, sre port, dest port and based on that hash, @ connection director will chosen

--> All packets for a connection must pass through the same device (connection owner)

b. Connection Director

--> Connection director has a backup copy of connection

--> Connection forwarder queries about connection owner from connection director.