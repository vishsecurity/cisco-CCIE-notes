##  VTP
1. Itis a Cisco Protocol.
2. It is L2 Protocol.
3. It Stands for Vian Trunking Protocol.
4. It is use for centerlized VLAN information.
5. By default VTP is enabled on all Cisco Switches.
6. It uses multicast MAC Address 0100,.0ccc.cccc

## Requirment of VTP
1. Trunking Must be enabled between Switches.
2. VTP Domain Name Must Match (It can be up to 32 characters long)
3. VTP Password must match (optional)

### Types of VTP MODES
1. VIP MODE SERVER
2. VIP MODE CLIENT
3. VIP MODE TRANSPARENT
4. VTP OFF MOD

## VTP MODE SERVER:-
1. It can add, remove and edit vlans information.
2. It can generate VTP update.
3. Itis Default Mode in some of plateform.
4. it store its vlan database into flash memory in vian.dat file.
5. We can create only normal range of vlan.

## CLIENT MODE:-
1. We can't create vlan, delete vian or can't modify any vian in VTP Client mode.
2. It can receive vian information from server mode switch learn it and can relay it further.
3. It will work as Relay Agent.
4. It can have only normal range of VLAN.
5. It store its vlan information in flash memory vian.dat file.

## VTP Transparent Mode:-
1. We can create vlan, delete vian and edit it.
2. Itis also a default mode in some plateform of switches.
3. We can create normal range of vian as well as Extended range of vlan.
4, It can also called standalone switch.
5. It can't generate VTP Update.
6. It can receive vian update from server switch and relay it further without modify itself.
7. It store its vian database in flash memory as well as in Running- Config.
8. We can set Different Password in VTP transparent Mode
8. We can set Different Password in VTP transparent Mode.

## VTP Messages

1. Summary Advertisement
2. Subset Request
3. Join Message

##  VTP Summary advertisement

1. VTP Domain Server send Preiodically after every 300sec.
2. Triggered Whenever any vlan Database change will occur.

## Contant of Summary Advertisement
1. VTP DOMAIN
2. CR NUMBER
3. VERSION
4. MDS Digest value

## CR Number

1. CR Stands for Configuration Revision Number.
2. Itis a 32bit value.
3. Represent in the form of decimal.
4. By default CR number will be 0 on all switches.
5. It will increment by 1 whwnever any vian database change will occur.
6. On Transparent Mode switch CR number will be always set 0. No increment apply.
7. The VTP revision Number is stored in NVRAM.
8. It will not altered by a power cycle of switch.

## How to reset CR Number
1. Change VIP mode 
2. Change VTP domain name

## VTP Messages

1. Summary Advertisement
2. Subset Request

3. Join Message

## VTP v3 .
1. Extendend VLAN range we can use.
2. Private vian Configuration Sync.
3. Rspan vlan
4. MsT