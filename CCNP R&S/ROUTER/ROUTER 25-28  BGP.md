- commans

  ```
  
  I. Configure Gig0/0 and Gig0/I interfaces with proper IP addresses for
  both routers
  
  2. Configure eBGP between two routers , announce 201.25.11.0/24 from
  customer router to ISP and 195.175.39.0/24 from ISP to Customer
  
  3. Run "show ip bgp summary" and "show ip bgp" commands and check
  the output
  
  Router#sh ip int bri
  Interface              IP-Address      OK? Method Status                Protocol 
  GigabitEthernet0/0/0   192.176.21.1    YES manual up                    down 
  GigabitEthernet0/0/1   201.25.11.1     YES manual up                    down 
  
  customer(config)#router bgp 6500
  customer(config-router)#neighbor 198.176.21.2 remote-as 65001
  customer(config-router)#network  201.25.11.0 mask 255.255.255.0 
  
  customer#sh ip bgp sum
  customer#sh ip bgp summary 
  BGP router identifier 201.25.11.1, local AS number 6500
  BGP table version is 1, main routing table version 6
  0 network entries using 0 bytes of memory
  0 path entries using 0 bytes of memory
  0/0 BGP path/bestpath attribute entries using 0 bytes of memory
  0 BGP AS-PATH entries using 0 bytes of memory
  0 BGP route-map cache entries using 0 bytes of memory
  0 BGP filter-list cache entries using 0 bytes of memory
  Bitfield cache entries: current 1 (at peak 1) using 32 bytes of memory
  BGP using 32 total bytes of memory
  BGP activity 0/0 prefixes, 0/0 paths, scan interval 60 secs
  
  Neighbor        V    AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
  198.176.21.2    4 65001       0       0        1    0    0 00:15:21        4
  
  
  ISP#sh ip int bri
  Interface              IP-Address      OK? Method Status                Protocol 
  GigabitEthernet0/0/0   192.176.21.2    YES manual up                    up 
  
  ISP(config)#router  bgp 65001
  ISP(config-router)#neighbor 198.176.21.1 remote-as 6500
  ISP(config-router)#network 195.175.39.0 mask 255.255.255.0
  
  ISP#sh ip bgp sum
  ISP#sh ip bgp summary 
  BGP router identifier 195.175.39.1, local AS number 65001
  BGP table version is 1, main routing table version 6
  0 network entries using 0 bytes of memory
  0 path entries using 0 bytes of memory
  0/0 BGP path/bestpath attribute entries using 0 bytes of memory
  0 BGP AS-PATH entries using 0 bytes of memory
  0 BGP route-map cache entries using 0 bytes of memory
  0 BGP filter-list cache entries using 0 bytes of memory
  Bitfield cache entries: current 1 (at peak 1) using 32 bytes of memory
  BGP using 32 total bytes of memory
  BGP activity 0/0 prefixes, 0/0 paths, scan interval 60 secs
  
  Neighbor        V    AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
  198.176.21.1    4  6500       0       0        1    0    0 00:15:33        4
  
  
  ```
  
  ```
  R1(config-if)#do sh ip int bri
  Interface              IP-Address      OK? Method Status                Protocol 
  GigabitEthernet0/0/0   10.1.12.1       YES manual up                    down 
  GigabitEthernet0/0/1   10.1.13.1       YES manual up                    down 
  GigabitEthernet0/0/2   unassigned      YES unset  administratively down down 
  Vlan1                  unassigned      YES unset  administratively down down
  Loopback1              1.1.1.1         YES manual up                    up 
  
  R1(config-if)#router bgp 5500 
  R1(config-router)#neighbor 4.4.4.4 remote-as 5500
  R1(config-router)#neighbor 4.4.4.4 remote-as update-source loopback 0
  
  R1(config-if)#router ospf 1
  R1(config-router)#router-id 1.1.1.1
  R1(config-router)#network 10.1.12.0 255.255.255.0 area 0
  R1(config-router)#network 10.1.13.0 255.255.255.0 area 0
  R1(config-router)#network 1.1.1.1 0.0.0.0 area 0
  
  R2(config-if)#do sh ip int bri
  Interface              IP-Address      OK? Method Status                Protocol 
  GigabitEthernet0/0/0   10.1.12.2       YES manual up                    up 
  GigabitEthernet0/0/1   10.1.24.2       YES manual up                    down 
  GigabitEthernet0/0/2   unassigned      YES unset  administratively down down 
  Vlan1                  unassigned      YES unset  administratively down down
  
  R2(config-if)#router ospf 1
  R2(config-router)#router-id 2.2.2.2
  R2(config-router)#network 10.1.12.0 255.255.255.0 area 0
  R2(config-router)#network 10.1.24.0 255.255.255.0 area 0
  
  R3(config)#do sh ip int bri
  Interface              IP-Address      OK? Method Status                Protocol 
  GigabitEthernet0/0/0   10.1.13.3       YES manual up                    up 
  GigabitEthernet0/0/1   10.1.34.3       YES manual up                    down 
  GigabitEthernet0/0/2   unassigned      YES unset  administratively down down 
  Vlan1                  unassigned      YES unset  administratively down down
  
  R3(config)#router ospf 1
  R3(config-router)#router-id 3.3.3.3
  R3(config-router)#network 10.1.13.0 255.255.255.0 area 0
  R3(config-router)#network 10.1.34.0 255.255.255.0 area 0
  
  r4(config)#do sh ip int bri
  Interface              IP-Address      OK? Method Status                Protocol 
  GigabitEthernet0/0/0   10.1.24.4       YES NVRAM  up                    up 
  GigabitEthernet0/0/1   10.1.34.4       YES NVRAM  up                    up 
  GigabitEthernet0/0/2   10.1.45.4       YES NVRAM  up                    down 
  Loopback0              4.4.4.4         YES manual up                    up 
  Vlan1                  unassigned      YES unset  administratively down down
  
  R4(config)#router ospf 1
  R4(config-router)#router-id 4.4.4.4
  R4(config-router)#network 10.1.24.0 255.255.255.0 area 0
  R4(config-router)#network 10.1.34.0 255.255.255.0 area 0
  R4(config-router)#network 10.1.45.0 255.255.255.0 area 0
  R4(config-router)#network 4.4.4.4 0.0.0.0 area 0
  R4(config-router)#neighbor 5.5.5.5 255.255.255.255 10.1.45.5
  
  R4(config-if)#router bgp 5500
  R1(config-router)#neighbor 1.1.1.1 remote-as 5500
  R1(config-router)#neighbor 1.1.1.1 remote-as update-source loopback 0
  
  R4(config-if)#router bgp 5500
  R4(config-router)#neighbor 10.45.1.5 remote-as 6500
  
  R4(config-if)#router bgp 5500
  R1(config-router)#neighbor 5.5.5.5 remote-as 6500
  R1(config-router)#neighbor 5.5.5.5 ebg-multihop 2
  
  r5(config)#do sh ip int bri
  Interface              IP-Address      OK? Method Status                Protocol 
  GigabitEthernet0/0/0   10.1.45.5       YES NVRAM  up                    up 
  
  
  R5(config-if)#router bgp 6500
  R5(config-router)#neighbor 10.1.45.4 remote-as 5500
  R4(config-router)#neighbor 4.4.4.4  255.255.255.255 10.1.45.4
  
  R5(config-if)#router bgp 6500
  R5(config-if)#neighbor 4.4.4.4  ebgp-multihop 2
  R5(config-if)#neighbor 4.4.4.4  remote-as 5500
  ```
  
  ```
  R3(config)#ip access-list standard  ROUTES_FOR_E3
  R3(config-router)#permit 150.1.50.0 0.0.0.255
  R3(config-router)#permit 150.2.50.0 0.0.0.255
  
  R3(config)#ip access-list standard  ROUTES_FOR_E2
  R3(config-router)#permit 200.0.0.0 0.0.0.255
  
  R3(config)# route-map LOCAL_PREF permit 10
  R3(config-route-map)#match ip address ROUTES_FOR_E3
  R3(config-route-map)#set local-prefrence 1000
  
  R3(config)# route-map LOCAL_PREF permit 20
  R3(config-route-map)#match ip address ROUTES_FOR_E2
  R3(config-route-map)#set local-prefrence 10
  
  R3(config-if)#router bgp 5500
  R3(config-router)#neighbor 10.1.36.6 remote-as 777
  R3(config-router)#neighbor 10.1.36.6 route-map LOCAL_PREF 
  ```
  
  
  
- BGP Border Gateway Protocol

  - Scalability
  2. Flexibility
  3. Stability
  4. Reliability  - TCP
  4. single homed
  4. dual homed
  4. Single Multihomed
  - Dual Multihomed

  - BGP
    1. L-7 Protocol
    2. TCP Based Protocol
    3. Use TCP Port no. 179
    4. Class-less Routing protocol
    5. We are using BGP v4.
    6. It is PVRP Protocol (Path Vector Routing Protocol)
    7. It can select Best Path on the bases of NO. of AS.
    8. Inter AS Routing Protocol.
    9. In BGP we can use multiple Address Family Identifier (AFI)
    10. We can select unicast and multicast with IPV4 and IPV6 (SAFI) Subsequent Address Family Identifier.
    11. BGP is devided in two parts- IBGP , EBGP.
    12. IBGP (Same AS)
    13. EBGP (Different AS)

  - ASNo. Public AS and Private AS 65536(0- 65535)
    1. Reserved 0
    2. Public 1-64495
    3. Reserved 64496-64511
    4. Private 64512-65534
    5. Reserved 65535

  - BGP Messages
    1. OPEN
    2. UPDATE
    3. NOTIFICATION
    4. KEEPALIVE

  - BGP Neighbor States
    1. IDEL
    2. CONNECT
    3. ACTIVE
    4. OPEN SENT
    5. OPEN CONFIREM
    6. ESTABLISHED
       - ROTUER BGP 100 neighbor 12.1.1.2 remote-as 200
         ROTUER BGP 200 neighbor 12.1.1.1 remote-as 100
       - ACTIVE
       - PASSIVE
       - TCP
         - 3WAY HAND-SHAKE
           - SYN
           - SYN/ACK
           - ACK 
    
  -  Types of Path Manipulation

    1. Inbound Traffic Influence.
    2. Outbound Traffic Influence.
       1. Next-hop:
       for EBGP neighbor next-hop will modifed and for IBGP next-hop will not modified.
       2. Weight:- .
          1. Weight is CISCO Prepon Path Attribute.
          2. Weight is Locally Significarit.
          3. Weight is 0 for IBGP and EBGP learned routes.
          4. Weight is 32768 for locally injected routes.
          5. Weight is use for Outbound Traffic Influence.
          6. Weight is 16bit decimal value.
          7. (0-65535)
          8. Higher weight is always preffered.
       3. Local Preference:-
          1. This path attribute is forwarded in IBGP updates.
          2. Default Local Preference for IBGP route is 100.
          3. Higher is always preferred.
          4. Used to influence outbound traffic.
          5. Local Preference will not carry in EBGP updates.
          6. Mostly we will use it for EBGP neighbor.
       4. Locally Injected:-
          1. For a router its locally injected route are best compared to be learned from EBGP or IBGP neighbor.
          2. On CISCO platform Weight is doing same.
          3. We will never use this path attribute for path manipulation.
       5. AS- PATH:- , ,
          1. It is always used for inbound traffic influence.
          2. Least no. of AS are always preferred. &

          3. AS-PATH will check if LP is same. 3
       6. Origin Code:-
           How network is injected in BGP?
           With network command or with redistribution.
           if injected with network command origin code is "i"
           5 if injected with redistribution command origin code is "2" (Incomplete)
           "i" origin code will always preferred if any router is receiving same network with origin code "i" and "2".
       7. MED:-
         1. Multi Exit Discriminator.
         2. It is 32 bit value because IGP metric is also 32bit.
         3. It is carred in EBGP and IBGP updated.
         4. It is used for inbound traffic influence.
       
           ‘5. By default MED is "0" for all IBGP and EBGP routes.
           °6. Lower value is preferred.
         5. MED is actually inherited from routing table.
         6. If you are injecting network through network command or redistribution then MED is copied from routing table to BGP tabl
       
           directly connected routes MED is "0" No
       8. N -> Neighbor Type

       - ‘if router is : learning same route from EBGP   and IBGP neighbor
       
       9. IGP metric to reach on next-hop.
          -> if both neighbor are EBGP then will check Oldest neighbor Preferred.

