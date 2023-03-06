## Routing

- commands

  ```
  
  
  1- Route the traffic of PC-1 to ISP-2, if ISP-2 is down make sure PC-1 can not go to WAN.
  2- Route Telnet and https traffic of PC-2 to ISP-1, and the rest to ISP-2.
  3- Route all other PCs to ISP-2.
  
  - Router(config)#ip access-list  extended CLIENT1
  
    Router(config-ext-nacl)#permit ip host 192.168.1.20 any 
  
    Router(config-ext-nacl)#exit
  
    Router(config)#route-map policy permit 10 
  
     Router(config)#match ip address CLIENT1
  
    Router(config)#set ip next-hop 201.1.1.2
  
  - Router(config)#ip access-list  extended CLIENT2
  
    Router(config-ext-nacl)#permit ip host 192.168.1.21 any eq 443
  
    Router(config)#route-map policy permit 20
  
    Router(config)#match ip address CLIENT2
  
    Router(config)#set ip next-hop 20.1.1.2
  
  - Router(config)#route-map policy permit 30
  
    Router(config)#set ip next-hop 20.1.1.2
  
  - int f0/0 (LAN)
  
    - ip policy router-map policy
  ```
  
  ```
  
  1) Configure EIGRP and OSPF with no summarization.
  
  2) Activate full mutual redistribution between OSPF and EIGRP networks. All routers must see all routes on the routing tables.
  Implement all metrics, pay attention that OSPF external routes shouldn’t increase their metrics.
  
  3) Implement distribute-list filter so that just the “odd” loopbacks of the Router 1 is seen on OSPF domain. All “even” subnets
  (including physical networks) shouldn’t be seen from OSPF domain side.
  
  4) Implement route-map filter so that just /24 routes are seen at EIGRP domain.
  policy making
  
  Router(config-if)#do sh ip int bri
  Interface              IP-Address      OK? Method Status                Protocol 
  GigabitEthernet0/0/0   10.1.12.1       YES manual administratively down down 
  GigabitEthernet0/0/1   unassigned      YES unset  administratively down down 
  GigabitEthernet0/0/2   unassigned      YES unset  administratively down down 
  Loopback0              10.1.0.1        YES manual up                    up 
  Loopback1              10.1.1.1        YES manual up                    up 
  Loopback2              10.1.2.1        YES manual up                    up 
  Loopback3              10.1.3.1        YES manual up                    up 
  Loopback4              10.1.4.1        YES manual up                    up 
  Loopback5              10.1.5.1        YES manual up                    up 
  Loopback6              10.1.6.1        YES manual up                    up 
  Vlan1                  unassigned      YES unset  administratively down down
  
  Router(config-if)#router eigrp 100
  Router(config-router)#no auto
  Router(config-router)#network 10.1.12.0 0.0.0.255
  Router(config-router)#network 10.1.0.0 0.0.0.255
  Router(config-router)#network 10.1.1.0 0.0.0.255
  Router(config-router)#network 10.1.2.0 0.0.0.255
  Router(config-router)#network 10.1.3.0 0.0.0.255
  Router(config-router)#network 10.1.4.0 0.0.0.255
  Router(config-router)#network 10.1.5.0 0.0.0.255
  Router(config-router)#network 10.1.6.0 0.0.0.255
  Router(config-if)#router ospf 1
  Router(config-router)#redistribute eigrp 100  subnet  metric-type 2
  Router(config-if)#router eigrp 100
  Router(config-router)#redistribute ospf metric 10111
  Router(config-router)#access-list 1 permit 10.1.1.0 0.0.0.255
  Router(config-router)#access-list 1 permit 10.1.3.0 0.0.0.255
  Router(config-router)#access-list 1 permit 10.1.5.0 0.0.0.255
  Router(config-router)#ip prefix-list networkel permit 10.0.0.0/8 le 24
  Router(config-router)#route-map filter_ospf_to_eigrp permit 10
  Router(config-router)#match ip prefix-list networkel
  Router(config-router)#router eigrp 100
  Router(config-router)#redistribute ospf 1 met 10111 route-map filter_ospf_to_eigrp
  
   Router(config-if)#do sh ip int bri
  Interface              IP-Address      OK? Method Status                Protocol 
  GigabitEthernet0/0/0   10.1.23.3       YES manual up                    down 
  GigabitEthernet0/0/1   unassigned      YES unset  administratively down down 
  GigabitEthernet0/0/2   unassigned      YES unset  administratively down down 
  Loopback0              10.1.7.1        YES manual up                    up 
  Loopback1              10.1.8.1        YES manual up                    up 
  Loopback2              10.1.9.1        YES manual up                    up 
  Loopback3              10.1.10.1       YES manual up                    up 
  Loopback4              10.1.11.1       YES manual up                    up 
  Loopback5              10.1.12.1       YES manual up                    up 
  Loopback6              10.1.13.1       YES manual up                    up 
  Vlan1                  unassigned      YES unset  administratively down down
  
  Router(config)#router ospf 1
  Router(config-router)#netw
  Router(config-router)#network 10.1.23.0 0.0.0.255
  Router(config-router)#network 10.1.23.0 0.0.0.255 area 0
  Router(config-router)#network 10.1.7.0 0.0.0.255 area 0
  Router(config-router)#network 10.1.8.0 0.0.0.255 area 0
  Router(config-router)#network 10.1.9.0 0.0.0.255 area 0
  Router(config-router)#network 10.1.10.0 0.0.0.255 area 0
  Router(config-router)#network 10.1.11.0 0.0.0.255 area 0
  Router(config-router)#network 10.1.12.0 0.0.0.255 area 0
  Router(config-router)#network 10.1.13.0 0.0.0.255 area 0
  
  Router(config-if)#do sh ip int bri
  Interface              IP-Address      OK? Method Status                Protocol 
  GigabitEthernet0/0/0   10.1.12.2       YES manual up                    up 
  GigabitEthernet0/0/1   10.1.23.2       YES manual up                    up 
  GigabitEthernet0/0/2   unassigned      YES unset  administratively down down 
  Vlan1                  unassigned      YES unset  administratively down down
  
  
  ```
  
  ```
  1) Configure EIGRP and OSPF for the network above and advertise all the networks for every router. Don’t use summarization.
  
  2) Implement full, mutual redistribution between OSPF and EIGRP for router 2 and router 3. 10.4.0.0/24 and 10.4.1.0/24 must have a
  seed metric 100 and OSPF tag 10, 10.4.2.0/24 and 10.4.3.0/24 must have a seed metric 200 and OSPF tag 20. All other subnets
  advertised to OSPF domain must have a seed metric 300, OSPF tag 30. OSPF routes advertised to EIGRP domain must have a
  BW=400, DLY=20,RGL=55,LD=1,MTU=1500,TAG=40 .External OSPF routes shouldn’t increase their metrics.
  
  3) 10.4.4.0/24 network shouldn’t reach to OSPF routing domain. 
  
  R1#sh ip int bri
  Interface                  IP-Address      OK? Method Status                Protocol
  FastEthernet0/0            10.1.13.1       YES manual up                    up      
  FastEthernet0/1            10.1.12.1       YES manual up                    up      
  Loopback0                  10.1.0.1        YES manual up                    up      
  R1(config)#router eigrp 100
  R1(config-router)#no auto
  R1(config-router)#network 10.1.13.0 0.0.0.255
  R1(config-router)#network 10.1.12.0 0.0.0.255
  R1(config-router)#network 10.1.0.0 0.0.0.255 
  
  
  R4#sh ip int bri
  Interface                  IP-Address      OK? Method Status                Protocol
  FastEthernet0/0            10.1.24.4       YES manual up                    up      
  FastEthernet0/1            unassigned      YES unset  administratively down down    
  Loopback0                  10.4.0.1        YES manual up                    up      
  Loopback1                  10.4.1.1        YES manual up                    up      
  Loopback2                  10.4.2.1        YES manual up                    up      
  Loopback3                  10.4.3.1        YES manual up                    up      
  Loopback4                  10.4.4.1        YES manual up                    up
  
  R4(config)#router ospf 1
  R4(config-router)#network 10.1.24.0 0.0.0.255
  % Incomplete command.
  
  R4(config-router)#network 10.1.24.0 0.0.0.255 area 0
  R4(config-router)#network 10.4.1.0 0.0.0.255 area 0   
  R4(config-router)#network 10.4.0.0 0.0.0.255 area 0
  R4(config-router)#network 10.4.2.0 0.0.0.255 area 0
  R4(config-router)#network 10.4.3.0 0.0.0.255 area 0
  R4(config-router)#network 10.4.4.0 0.0.0.255 area 0
  R4(config-router)#
  
  R2#sh ip int bri
  Interface                  IP-Address      OK? Method Status                Protocol
  FastEthernet0/0            10.1.24.2       YES NVRAM  up                    up      
  FastEthernet0/1            10.1.12.2       YES NVRAM  up                    up      
  FastEthernet1/0            10.1.23.2       YES manual up                    up
  
  R2(config)#router ospf 1
  R2(config-router)#router
  R2(config-router)#router-id 2.2.2.2
  R2(config-router)#network 10.1.24.0 0.0.0.255
  R2(config-router)#network 10.1.24.0 0.0.0.255 area 0
  R2(config-router)# 
  *Mar  1 00:01:50.731: %OSPF-5-ADJCHG: Process 1, Nbr 10.4.4.1 on FastEthernet0/0 from LOADING to FULL, Loading Done
  R2(config-router)#network 10.1.23.0 0.0.0.255 area 0
  
  R2(config)#router eigrp 100 
  R2(config-router)#no auto           
  R2(config-router)#network 10.1.12.0 0.0.0.255        
  R2(config-router)#
  
  R2(config)#access-list 1 permit 10.4.0.0 0.0.0.255
  R2(config)#access-list 1 permit 10.4.1.0 0.0.0.255
  R2(config)#access-list 2 permit 10.4.2.0 0.0.0.255   
  R2(config)#access-list 2 permit 10.4.3.0 0.0.0.255
  R2(config)#access-list 3 permit 10.4.4.0 0.0.0.255
  
  R2(config)#route-map EIGRP_TO_OSPF permit 10
  R2(config-route-map)#match ip address 1 
  R2(config-route-map)#set metric 100
  R2(config-route-map)#set tag 10
  
  R2(config-route-map)#route-map EIGRP_TO_OSPF permit 20
  R2(config-route-map)#match ip address 2               
  R2(config-route-map)#set metric 200                   
  R2(config-route-map)#set tag 20        
  
  R2(config)#route-map EIGRP_TO_OSPF deny 30     
  R2(config-route-map)#match ip address 3      
  
  R2(config-route-map)#route-map EIGRP_TO_OSPF permit 40
  R2(config-route-map)#set metric 300                      
  R2(config-route-map)#set tag 30 
  
  R2(config-route-map)#router ospf 1
  *Mar  1 00:09:07.011: %DUAL-5-NBRCHANGE: IP-EIGRP(0) 100: Neighbor 10.1.12.1 (FastEthernet0/1) is down: Interface Goodbye received
  *Mar  1 00:09:07.495: %DUAL-5-NBRCHANGE: IP-EIGRP(0) 100: Neighbor 10.1.12.1 (FastEthernet0/1) is up: new adjacency
  
  R2(config-router)#redistribute eigrp 100 sub
  R2(config-router)#redistribute eigrp 100 subnets rou
  R2(config-router)#redistribute eigrp 100 subnets route-map  EIGRP_TO_OSPF
  
  R2(config-router)#route-map OSPF_TO_EIGRP
  R2(config-route-map)#det metric 400 20 255 1 1500
  R2(config-route-map)#set tag 40
  R2(config-route-map)#set metric-type type-2
  
  R2(config)#router eigrp 100
  R2(config-router)#redistribute ospf 1 route-map OSPF_TO_EIGRP
  
  
  R3#sh ip int bri
  Interface                  IP-Address      OK? Method Status                Protocol
  FastEthernet0/0            10.1.13.3       YES manual up                    up   
  FastEthernet0/1            10.1.23.3       YES manual up                    up   
  FastEthernet1/0            unassigned      YES unset  administratively down down
  
  R3(config)#router ospf 1
  R3(config-router)#netw
  R3(config-router)#router  
  R3(config-router)#router-id 3.3.3.3
  R3(config-router)#netw
  R3(config-router)#network 10.1.23.0 0.0.0.255
  % Incomplete command.
  R3(config-router)#network 10.1.23.0 0.0.0.255 area 0
  
  R3(config-router)#router eigrp 100
  R3(config-router)#network 10.1.13.0 0.0.0.255 
  R3(config-router)#no auto
  R3(config-router)#
  
  ```
  
  
  
- static
  - static default
  - static manual
    - ip route <Secondary network> <Subnet mask of Secondary network> <next-hop/exit int>
  
- dynamic
  - IGP
    - DVRP/RIP
    - ADVRP/EIGRP
    - LSRP/OSPF
  - EGP
    - BGP
    - PVRP