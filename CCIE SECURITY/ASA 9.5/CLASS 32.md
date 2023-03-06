## Cluster Deployment Mode:
a. Spanned EtherChannel Mode
b. Individual Interface Mode
a. Spanned EtherChannel Mode
--> This mode is supported in Routed/Transparent and Single/Multiple mode
--> In this mode Each ASA Interface is configured to make Etherchannel With Directly connected Switch.
--> Each ASA shares the Same IP addess on data interface
--> Load Balancing is Automatically Done by etherchannel (via switch)

## TASK: Configure Clustering between ASA1 and ASA2 as follows:

a. Use E2 as CCL with 7.7.100.100 IP on ASA and 7.7.100.101 IP on ASA2Z
b. ASA1 should become Master

c. Cluster unit name should be same as hostname.

Step1: Specify cluster interface mode
cluster interface-mode spanned
Step2: Create a cluster group (priority, interface, unit-name)
cluster group <name>  --> it can be anything, but it must be same on all the ASA
priority --> specify cluster priority
local-unit --> specify cluster unit name
cluster-interface --> specify cluster interface and IP
Step3: Enable cluster interface
Step4: Enable Cluster

## TASK: ON ASA, Make EO member of Port-channelt and Et member of Po2. Configure IP address on Pot and Po2 as per diagram.
Step1: Make Interfaces member of Portchannel Step2: Configure IP address and nameif on Portchanl

```
interface ethernet O
channel-group 4 mode on
no shutdown
interface ethernet 1
channel-group 2 mode on
no shutdown
```



## Cluster Connection Roles:
a. Owner
b. Director
c. Forwarder
Connection Owner
--> ASA which recieves the first packet of connection becomes the connection owner and will forward the
“ packet
--> All packets for a connection must pass through the same ASA
--> Connection owner will calculate a connection director and will forward copy of connection to the
connection director (director will acts as backup)

2. Connection Director
--> Device which recieves copy of connection
--> Connection forwarder queries about connection owner from connection director
3. Connection Forwarder
   --> Any ASA which recieves the packet from a connection for which it is not connection owner becomes
   the connection forwarder