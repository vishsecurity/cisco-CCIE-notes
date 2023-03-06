- command

  ```
  Switch(config)#do  sh his
    int range fa0/1-2
    switchport mode  trunk 
   
    channel-group 1 mode  active 
    Switch(config)#do sh his
    int range fa0/1-2
    switchport mode  trunk 
    channel-group 1 mode passive 
    
    Switch#sh etherchannel su
  Switch#sh etherchannel summary 
  Flags:  D - down        P - in port-channel
          I - stand-alone s - suspended
          H - Hot-standby (LACP only)
          R - Layer3      S - Layer2
          U - in use      f - failed to allocate aggregator
          u - unsuitable for bundling
          w - waiting to be aggregated
          d - default port
  
  
  Number of channel-groups in use: 1
  Number of aggregators:           1
  
  Group  Port-channel  Protocol    Ports
  ------+-------------+-----------+----------------------------------------------
  
  1      Po1(SU)           LACP   Fa0/1(P) Fa0/2(P) 
  
  Switch#sh etherchannel s
  Switch#sh etherchannel summary 
  Flags:  D - down        P - in port-channel
          I - stand-alone s - suspended
          H - Hot-standby (LACP only)
          R - Layer3      S - Layer2
          U - in use      f - failed to allocate aggregator
          u - unsuitable for bundling
          w - waiting to be aggregated
          d - default port
  
  
  Number of channel-groups in use: 1
  Number of aggregators:           1
  
  Group  Port-channel  Protocol    Ports
  ------+-------------+-----------+----------------------------------------------
  
  1      Po1(SU)           LACP   Fa0/1(P) Fa0/2(P) 
  ```
  
  ```
  Switch(config)#do sh his
    int range fa0/1-2
    no switchport 
    channel-group 1 mode passive 
    int port-channel 1
    ip add 10.42.20.1 255.255.255.0
    
    Switch#sh etherchannel summary 
  Flags:  D - down        P - in port-channel
          I - stand-alone s - suspended
          H - Hot-standby (LACP only)
          R - Layer3      S - Layer2
          U - in use      f - failed to allocate aggregator
          u - unsuitable for bundling
          w - waiting to be aggregated
          d - default port
  
  
  Number of channel-groups in use: 1
  Number of aggregators:           1
  
  Group  Port-channel  Protocol    Ports
  ------+-------------+-----------+----------------------------------------------
  
  1      Po1(RU)           LACP   Fa0/1(P) Fa0/2(P) 
  ```
  
  

## REQUIRNMENTS OF ETHERCHANNEL

1. We can aggrigate normal ports and uplink ports.
2. Speed must match of all ports of aggrigated etherchannel ports.
3. Duplex must match.
4. Ethernet Standard must match. (Fastethernet, GIG, Ethernet)
5. Trunk Encapsulation Protocol must match.
6. Trunk allowed vlan list must match.
7. Native vian must match.
8. Prunning eligibility list must match.

## ETHERCHANNEL Loadbalancing Algoridtham

1. Src Mac Address (By Default)
2. Dst Mac Address
3. Src and Dst MAC Address
4. Src IP Address
5. Dst IP Address
6. Src and Dst IP Address
7. Src Port No.
8. Dst Port No.
9. Src and Dst Port No.

## Types of Etherchannel

1, Static:-

- ->We can aggrigate maximum 8 links.
- -> Mode is = ON
- channel-group 10 mode on

2. Dynamic:-
	a. PAGP 
	b. LACP 

## PAGP:-
1. It Stand for Port Aggregation Protocol.
2. Both devices need of CISCO.
3. Maximum we can Aggregate 8 links.
4. Types pf Modes=1. Desirable 2. Auto

## LACP:-
1. It stands for Link- Aggregation Control Protocol.
2. It is Open Standard Protocol.
3. We can aggregate maximum 16 Links, but 8 links will participate Actively and remaining 8 links will remain in Standby State.
4. Modes =1. Active 2. Passive

##  Layer 3 Switching

- Types of Layer 3 Switching

1. Process Switching
2. Fast Switching
3. CEF Switching

## Types of Adjacency Table
- Null Adjacency:- Null Adj table will be responsible to handle all those packet which are forwarded toward null interface.
- Drop Adjacency:- This table is basically responsible to handle all those packet which encountered with mismatch of encapsulation or crc error.
- Discard Adjacency:- This table is responsible to handle all those packet which are discarded by an ACL.
- Glean Adjacency:- This table is responsible to have information about all directly connected network and whenever a packet will move to any directly connected networkthen all those packet will be handled by glean adjancecy.
- Punt Adjacency:- This table is responsible to handle those packet which is not processed by cef and forwarded to control plane to process these packet.