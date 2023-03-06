- commands

  - redistribute E1 increase their matrix
  - redistribute E2 does not increase their matrix

  ```
  1- Configure OSPF for the network above. Router 1 should be a ASBR which redistributes the static routes. These routes shouldn’t
  increase their metrics while they are passing over the network and should have a beginning OSPF cost of 200. All routers should have
  a router — id that is similar to their names.
  
  2- After configuring first step, which router is DR and which router is BDR in Area 0 ?
  
  3- Define Router 1 DR in Area 0 and Router 2 and Router 3 won’t be a DR or a BDR. After this configuration, which kind of
  neighborship established between Router 1 — Router 2 and Router 2 — Router 3 ?
  
  4- Configure summarization on ABR routers.
  
  5- Configure summarization on ASBR router.
  
  - R1(config-if)#do sh ip int bri
  
    Interface              IP-Address      OK? Method Status                Protocol 
  
    GigabitEthernet0/0/0   172.30.0.1      YES manual up                    up 
  
  - R1#sh ip int bri
    Interface                  IP-Address      OK? Method Status                Protocol
    FastEthernet0/0            172.30.0.1      YES manual up                    up    
  
  - R2#sh ip int br
    *Mar  1 00:01:21.823: %SYS-5-CONFIG_I: Configured from console by console
    R2#sh ip int bri
    Interface                  IP-Address      OK? Method Status                Protocol
    FastEthernet0/0            172.30.0.2      YES manual up                    up      
    FastEthernet0/1            172.30.10.2     YES manual up                    up      
  
  - R3#sh ip int bri
    Interface                  IP-Address      OK? Method Status                Protocol
    FastEthernet0/0            172.30.20.4     YES manual up                    up      
    FastEthernet0/1            unassigned      YES unset  administratively down down    
    Loopback1                  10.20.0.1       YES manual up                    up      
    Loopback2                  10.20.1.1       YES manual up                    up      
    Loopback3                  10.20.2.1       YES manual up                    up      
    Loopback4                  10.20.3.1       YES manual up                    up    
  
  - R1(config)#do sh his
    router ospf 1
    router-id 1.1.1.1
    network 172.30.0.0 255.255.255.0 area 0
    redistribute static subnets metric 200 metric-type 2
    do sh his
  
  - R2(config)#drouter ospf 1
    router-id 2.2.2.2
    network 172.30.0.0 255.255.255.0 area 0
    network 172.30.10.0 255.255.255.0 area 10
  
    - sh ip ospf nei 
  
    - int f0/0
      - ip ospf priority 0
    - router ospf 1 ABR
      - area 10 range 10.1.0.0 255.255.255.0
  
  - R3(config)#router ospf 1
    R3(config-router)#router 
    R3(config-router)#router-id 3.3.3.3
    R3(config-router)#network 172.30.20.0 255.255.255.0 area 10
  
    - int f0/0
      - ip ospf priority 0
    - router ospf 2 ASBR
      - summary-address 172.30.0.0 255.255.255.0
  ```

  ```
  1) Configure OSPF for the topology above. Redistribute the static routes on R1 as type E11 to inject the external routes into OSPF domain.
  2) OSPF adjacency mustn’t established if there is no OSPF router.
  
  3) Routers in Area 0 must be configured with MDS , Routers in Area 23 must be configured with clear-text authentication ( Keys : cisco )
  4) Routers in Area 45 should not receive the external routes out of OSPF domain.
  
  5) Routers in Area 23 mustn’t receive Type 3-4-5 LSAs. These routers must reach the external network via default route which has a cost
  of 100.
  
  6) All routers must ping together. 
  
  
  R2#sh ip int bri
  Interface              IP-Address      OK? Method Status                Protocol 
  FastEthernet0/0        10.100.1.2      YES manual up                    up 
  FastEthernet0/1        unassigned      YES unset  administratively down down 
  Serial0/0              10.23.1.2       YES manual down                  down 
  Serial0/1              unassigned      YES unset  administratively down down 
  Serial0/2              unassigned      YES unset  administratively down down 
  Serial0/3              unassigned      YES unset  administratively down down 
  FastEthernet1/0        unassigned      YES unset  administratively down down 
  FastEthernet1/1        unassigned      YES unset  administratively down down
  
  R2(config)#router ospf 1
  Router(config-router)#router-id 2.2.2.2
  Router(config-router)#network 10.100.1.0 0.0.0.255 area 0
  Router(config-router)#network 10.23.1.0 0.0.0.255 area 0
  Router(config-router)#network 10.23.1.0 0.0.0.255 area 23
  
  R2(config)#int s0/0
  R2(config-if)#ip ospf authentication 
  R2(config-if)#ip ospf authentication-key cisco
  
  R2(config)#int s0/0
  R2(config-if)#ip ospf authentication message-digest 
  R2(config-if)#ip ospf message-digest-key 1 md5 cisco
  
  R2(config)#router ospf 1
  R2(config)#area 23 stub no-summary 
  
  R4#sh ip int bri
  Interface              IP-Address      OK? Method Status                Protocol 
  FastEthernet0/0        10.45.1.4       YES manual up                    up 
  FastEthernet0/1        unassigned      YES unset  administratively down down 
  Serial0/0              10.100.1.4      YES manual down                  down 
  Serial0/1              unassigned      YES unset  administratively down down 
  Serial0/2              unassigned      YES unset  administratively down down 
  Serial0/3              unassigned      YES unset  administratively down down 
  FastEthernet1/0        unassigned      YES unset  administratively down down 
  FastEthernet1/1        unassigned      YES unset  administratively down down
  
  R4(config)#router ospf 1
  R4(config-router)#router-id  4.4.4.4
  R4(config-router)#network 10.100.1.0 0.0.0.255 area 0
  R4(config-router)#network 10.45.1.0 0.0.0.255 area 45
  
  R4(config)#int f0/0
  R4(config-if)#ip ospf authe
  R4(config-if)#ip ospf authentication mess
  R4(config-if)#ip ospf authentication message-digest 
  R4(config-if)#ip ospf me
  R4(config-if)#ip ospf message-digest-key 1 md5 cisco
  
  R4(config)#router ospf 1
  R4(config-router)#area 45 stub
  
  R1(config-if)#do sh ip int bri
  Interface              IP-Address      OK? Method Status                Protocol 
  FastEthernet0/0        10.100.1.1      YES manual up                    up 
  
  R1(config)#router ospf 1
  R1(config-router)#router-id 1.1.1.1
  R1(config-router)#network 10.100.1.0 255.255.255.0 area 0
  R1(config-router)#redistribute static subnets  metric 50 metric-type 1
  
  R1(config)#int f0/0
  R1(config-if)#ip ospf  authentication message-digest 
  R1(config-if)#ip ospf  message-digest-key 1 md5 cisco
  
  R6r#sh ip int bri
  Interface              IP-Address      OK? Method Status                Protocol 
  FastEthernet0/0        10.100.1.6      YES manual up                    up 
  FastEthernet0/1        unassigned      YES unset  administratively down down 
  Serial0/0              10.67.1.6       YES manual down                  down 
  
  
  R6(config)#router ospf 1
  R6(config-router)#network 10.100.1.0 255.255.255.0 area 0
  R6(config-router)#network 10.67.1.0 255.255.255.0 area 67
  R6(config-router)#router-id 6.6.6.6
  R6#clear ip ospf process 
  
  R6(config)#int s0/0
  R6(config-if)#ip ospf authentication message-digest 
  R6(config-if)#ip ospf message-digest-key 1 md5 cisco
  01:20:22: %OSPF-5-ADJCHG: Process 1, Nbr 7.7.7.7 on Serial0/0 from FULL to DOWN, Neighbor Down: Dead timer expired
  
  R2(config)#router ospf 1
  R6(config-router)# area 67 virtual-link 7.7.7.7
  
  
  01:20:22: %OSPF-5-ADJCHG: Process 1, Nbr 7.7.7.7 on Serial0/0 from FULL to DOWN, Neighbor Down: Interface down or detached
  
  
  Router#sh ip int bri
  Interface              IP-Address      OK? Method Status                Protocol 
  FastEthernet0/0        unassigned      YES unset  administratively down down 
  FastEthernet0/1        unassigned      YES unset  administratively down down 
  Serial0/0              10.45.1.5       YES manual up                    down 
  
  Router(config)#router ospf 1
  Router(config-router)#router-id 5.5.5.5
  Router(config-router)#network 10.45.1.0 0.0.0.255 area 45
   
  Router(config)#router  ospf 1
  Router(config-router)#passive-interface default 
  
  R5(config)#router ospf 1
  R5(config-router)#area 45 stub 
  
  R3(config)#int s0/0
  R3config-if)#ip add 10.23.1.3 255.255.255.0
  R3(config-if)#no sh
  
  R3(config-if)#do sh ip int bri
  Interface              IP-Address      OK? Method Status                Protocol 
  Serial0/0              10.23.1.3       YES manual up                    up 
  Loopback0              172.30.0.1      YES manual up                    up 
  Loopback1              172.30.1.1      YES manual up                    up 
  Loopback2              172.30.2.1      YES manual up                    up 
  Loopback3              172.30.3.1      YES manual up                    up
  
  R3(config)#router ospf 1
  R3(config-router)#router-id 3.3.3.3
  R3(config-router)#network 10.23.1.0 255.255.255.0 area 23
  00:43:21: %OSPF-5-ADJCHG: Process 1, Nbr 2.2.2.2 on Serial0/0 from LOADING to FULL, Loading Done
  R3(config-router)#network 10.30.1.0 255.255.255.0 area 23
  R3(config-router)#network 10.30.2.0 255.255.255.0 area 23
  R3(config-router)#network 10.30.3.0 255.255.255.0 area 23
  
  R3(config)#int s0/0
  R3(config-if)#ip ospf authentication-key cisco
  
  R7#sh ip int bri
  Interface              IP-Address      OK? Method Status                Protocol 
  Serial0/0              10.67.1.7       YES manual up                    up 
  Serial0/1              10.78.1.7       YES manual administratively down down 
  
  R7(config)#router ospf 1
  R7(config-router)#router-id 7.7.7.7
  R7(config-router)#network 10.78.1.0 255.255.255.0 arae 78
  R7(config-router)#network 10.67.1.0 255.255.255.0 area 67
  R6(config-router)# area 67 virtual-lin 6.6.6.6
  
  R8#sh ip int bri
  Interface              IP-Address      OK? Method Status                Protocol 
  FastEthernet0/0        unassigned      YES unset  administratively down down 
  FastEthernet0/1        unassigned      YES unset  administratively down down 
  Serial0/0              10.78.1.8       YES manual down                  down 
  
  R8(config)#router ospf 1
  R8(config-router)#network 10.78.1.0 255.255.255.0 area 78
  R8(config-router)#router-id 8.8.8.8
  
  
  ```

  ```
  ospf v3
  
  R1(config)#ipv6 unicast-routing
  R2(config)#ipv6 unicast-routing
  R3(config)#ipv6 unicast-routing
  
  R1(config)#int g0/0/0
  R1(config-if)#ipv6 add 2001:DB8:CAFE:1::1/64
  R1(config-if)#int g0/0/1
  R1(config-if)#ipv6 add 2001:DB8:CBED:1::1/64
  R1(config)#ipv6 router ospf 10
  %OSPFv3-4-NORTRID: OSPFv3 process 10 could not pick a router-id,please configure manually
  R1(config-rtr)#router-id 1.1.1.1
  
  
  R2(config)#int g0/0/0
  R2(config-if)#ipv6 address 2001:DB8:CAFE:1::2/64
  R2(config-if)#int g0/0/1
  R2(config-if)#ipv6 address 2001:DB8:ABCD:1::1/64
  R2(config)#ipv6  router ospf 10
  %OSPFv3-4-NORTRID: OSPFv3 process 10 could not pick a router-id,please configure manually
  R2(config-rtr)#router
  R2(config-rtr)#router-id 2.2.2.2
  
  
  R3(config)#int g0/0/0
  R3(config-if)#ipv6 add 2001:DB8:ABCD:1::2/64
  R3(config-if)#int g0/0/1
  R3(config-if)#ipv6 add 2001:DB8:CBED:1::2/64
  R3(config)#ipv6 router ospf 10
  %OSPFv3-4-NORTRID: OSPFv3 process 10 could not pick a router-id,please configure manually
  R3(config-rtr)#router
  R3(config-rtr)#router-id 3.3.3.3
  
  
  R1(config)#int g0/0/0
  R1(config-if)#ipv6 ospf 10 area 0
  R1(config-if)#
  R1(config-if)#int g0/0/1
  R1(config-if)#ipv6 ospf 10 area 0
  
  R2(config-rtr)#int g0/0/0	
  R2(config-if)#ipv6 ospf 10 area 0
  R2(config-if)#int g0/0/1
  00:21:23: %OSPFv3-5-ADJCHG: Process 10, Nbr 1.1.1.1 on GigabitEthernet0/0/0 from LOADING to FULL, Loading Done
  R2(config-if)#ipv6 ospf 10 area 0
  
  R3(config-rtr)#int g0/0/0
  R3(config-if)#ipv6 ospf 10 area 0
  R3(config-if)#int g0/0/1
  R3(config-if)#ipv6 ospf 10 area 0
  00:22:07: %OSPFv3-5-ADJCHG: Process 10, Nbr 1.1.1.1 on GigabitEthernet0/0/0 from LOADING to FULL, Loading Done
  
  R3(config-if)#do sh ipv6 ospf nei
  
  Neighbor ID     Pri   State           Dead Time   Interface ID    Interface
  1.1.1.1           1   FULL/DR         00:00:30    2               GigabitEthernet0/0/0
  2.2.2.2           1   FULL/DR         00:00:37    2               GigabitEthernet0/0/1
  ```

  

- LSRP

  1. in LSRP behaviour all router will share identical database.

  2. OSPF is LSRP protocol, it is not fullu true.

  3. OSPF use SPF algo to calculate COST.

  4. OSPF use AD viaue 110. 

  5. ospf use multicast address 224.0.0.5 and 224.0.0.6

  6. hello time of OSPF is 10 sec and hold time is 40 sec.

  7. ospf use ip protocol no. 89.

  8. OSPF is classles routing protocol. e

  9. cost algo refB/W / Link B/W mbps.

  10. ospf support equal-cost load-balancing.

  11. in ospf there are three types of tables

      1. RT
      2. Database Table

      3. Neighbor Table
      
  12. OSPF routers share links information.

  13. OSPF AUTHENTICATION

      1. Type -0 null 
      2. Type -1 plain text

      3. Type - 2 MD5

- ROUTER OSPF 1
  1. Router will elect a router ID
      network 12.1.1.0 0.0.0.3

 - OSPF States

    - Disable
    - init
    - Two
    - Ex-Start 
    - Exchange
    - Loading
    - Full

- link number- 1

  link type- loopback
  link network 1.1.1.1
  link ip 1.1.1.1

  link subnet mask /32
  link neighbor- stub
  link cost-

- hello message a
  1. router id 1.1.1.1 
  2. area id 0.0.0.0 ‘need to match
  3. timers- hello 10sec = Match

  ​                    hold 40sec = match 
  4. Authentication match
  5. subnetmask - match

- lsa 1

  - DR and BDR state is full

    DR- DROTHER FULL

    BDR - DROTHER FULL
    DROTHER - DROTHER TWO WAY

  - Internal Routers
    Backbone routers
    ABR (Area Border Router)

- lsa 2

- T-NSSA Area
  STUB AREA:-

  1. you can use only on Non- backbone area
  2. In Stub area LSA-5 will filter.
  3. In Stub Area LSA-4 Automatically filter.

- T-STUB AREA:-

  1. You will enable it only on ABR.
  2. filter LSA-5
  3. filter LSA-4
  4. filter LSA-3
  5. Only advertise Default Route in form of LSA-3.

- STUB

- T-STUB

- NSSA

- T-NSSA

- NSSA

  1. LSA filter
  2. LSA filter
  3. LSA 7 will add

- T- NSSA

  - LSA 5 filter
  - LSA 4 filter
  - LSA 3 filter
  4. Default Router in form of LSA- 3
