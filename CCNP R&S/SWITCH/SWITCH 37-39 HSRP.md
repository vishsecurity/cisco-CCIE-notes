- commands

  ```
  Router(config)#int g0/0/0
  Router(config-if)#ip add 172.30.10.2 255.255.255.0
  Router(config-if)#no sh
  
  Router(config)#int g0/0/0
  Router(config-if)#ip add 172.30.10.3 255.255.255.0
  Router(config-if)#no sh
  
  - pc > 172.30.10.100 /172.30.10.1
  
  - int g0/0/0
    standby 1 ip 172.30.10.1 255.255.255.0 
  
  - int g0/0/0
    standby 1 ip 172.30.10.1 
    standby 1 priority 200 
    standby 1 preempt 
  - R1#sh standby 
  	  GigabitEthernet0/0/0 - Group 1
      	State is Active
    ​    5 state changes, last state change 00:12:11
  	    Virtual IP address is 172.30.10.1
  	   
  
  ```

  ​	

## Gateway High Availaibility

1. HSRP:- Hot Standby Router Protocol
2. VRRP:- Virtual Router Redundancy Protocol
3. GLBP:- Gateway Loadbalancing Protocol

## HSRP :

1. It is CISCO Proprietry protocol.
2. hello interval is 3sec.
3. hold interval is 10sec.
4. It is uses udp port no. 1985
5. It uses multicast address to send its message 224.0.0.2
6. by default its priority is 100.
7. It has built-in track command.
8. Default decerement in priority is 10 with using track command.
9. It support authentication 1. plain text , 2. MDS.
10. It support maximum 256 groups, group range is (0-255).
11. It uses virtual mac address 0000.0c07.acxx
12. By default preemption is disable in HSRP for active router election.

## HSRP States
1. Disabled
2. Init
3. Speaking
4. Listning
5. Standby
6. Active

## Active Router election Process
 1. Higher Priority
2. Higher ip address

## HSRP

- Gr.1 Pr. 192.168.1.100
  R1 120 “Active
  R2 110 Standby
  R3 100 _Listning

- Gr.2 Pr. 192.168.1.110
  R1 100 = Listning

  R2 120 Active

  R3 110 Standby

 - Gr.3 Pr. 192.168.1.120
    R1 100 Listning
    R2 110 Standby
    R3 120 Active

## Active Router election Process —
	1. Higher Priority
	2. Higher ip address (Condition) if Preemption is enabled

## Standby Router Election Process

	1. Higher Priority
	2. Higher IP Address

## GLBP en
1. Gateway Lodbalancing Protocol
2. Hello interval 3 sec, Hold interval 10 sec.
3. It uses udp port no. 3222. 
4. it uses multicast address 224.0.0.12
5. Default priority is 100. 
6. Default Weight is 100.
7. bydefault preemption is disabled. es
8. It support loadbalancing. 
9. It uses mac address 0007.B400.xxxx

## Components of GLBP
1. AVG
2. AVF
AVG:- Active Virtual Gateway 

## AVG:- Active Virtual Gateway
1. AVG election s same as hsrp.
2. It is responsible to provide arp responce for all request which are coming from lan users based on loadbalancing algorithem.
3. AVF:- Active Virtual Forwarder
   1. It is responsible to forward data.