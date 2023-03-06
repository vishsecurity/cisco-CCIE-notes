# Transparent firewall

1. How to configure interfaces in transparent firewall
2. Routing protocol neighborship through the firewall
3. Remote management of transparent firewall

4. Static MAC address, how to enable arp-inspection
why/where transparent firewall
--> transparent firewall is not used as edge device as some
of the feature are not supported for example:
a. VPN for data traffic
4. Any kind of NAT with ASA IP as mapped IP
a. It is used for testing purpose
5. it is deployed before any critical server in the inside network

## TASK: Deploy ASA2 as transparent firewall between R1 and R2 with management IP address 192.168.1.10
Configure nameif on interfaces as per diagram  

Step1: Change firewall type to transparent firewall transparent all the configuration of routed firewall will be
deleted

Step2: Create a BVI

```
interface bvi 4
lp address 192.168.4140
```

Step3: Bind interface with BVI and assign nameif
interface ethernet O

```
no sh
namelf inside
bridge-group 4
interface ethernet 1
no sh
namelf outside
bridge-group 4
```

TASK2: Make R21 and R2 EIGRP neighbors