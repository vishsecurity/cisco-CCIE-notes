- commands
  
  ```
  1- Configure the network above with EIGRP using Autonomous system number 50. Additionally EIGRP shouldn’t work as a classful
  routing protocol.
  
  2- EIGRP neighborhood shouldn’t be established on any interface if there are no EIGRP routers.
  
  3- BB router should summarize networks between 172.30.0.0 / 172.30.7.255 as a single network.
  
  4- BB router should use unequal load balance to reach 10.1.2.0 / 24 network.
  
  - R2#sh ip int bri
    Interface                  IP-Address      OK? Method Status                Protocol
    FastEthernet0/0            10.1.2.2        YES manual up                    up      
    FastEthernet0/1            10.1.24.2       YES manual up                    up      
    FastEthernet1/0            10.1.25.2       YES manual up                    up      
  
  - BB#sh ip int bri
    Interface                  IP-Address      OK? Method Status                Protocol
    FastEthernet0/0            10.1.34.1       YES manual up                    up      
    FastEthernet0/1            10.1.24.1       YES manual up                    up      
    Loopback1                  172.30.0.1      YES manual up                    up      
    Loopback2                  172.30.1.1      YES manual up                    up      
    Loopback3                  172.30.2.1      YES manual up                    up      
    Loopback4                  172.30.3.1      YES manual up                    up      
    Loopback5                  172.30.4.1      YES manual up                    up      
    Loopback6                  172.30.6.1      YES manual up                    up      
    Loopback7                  172.30.7.1      YES manual up                    up      
    Loopback8                  172.30.8.1      YES manual up                    up      
  
  - BB(config-if)#do sh ip route 
    Codes: C - connected, S - static, R - RIP, M - mobile, B - BGP
           D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area 
           N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
           E1 - OSPF external type 1, E2 - OSPF external type 2
           i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
           ia - IS-IS inter area, * - candidate default, U - per-user static route
           o - ODR, P - periodic downloaded static route
  
    Gateway of last resort is not set
  
     172.30.0.0/24 is subnetted, 8 subnets
  
    C       172.30.2.0 is directly connected, Loopback3
    C       172.30.3.0 is directly connected, Loopback4
    C       **172.30.0.0 is directly connected, Loopback1**
    C       172.30.1.0 is directly connected, Loopback2
    C       172.30.6.0 is directly connected, Loopback6
    C       172.30.7.0 is directly connected, Loopback7
    C       172.30.4.0 is directly connected, Loopback5
    C       172.30.8.0 is directly connected, Loopback8
         10.0.0.0/24 is subnetted, 2 subnets
    C       10.1.24.0 is directly connected, FastEthernet0/1
    C       10.1.34.0 is directly connected, FastEthernet0/0
  
  - R3#sh ip int bri
    Interface                  IP-Address      OK? Method Status                Protocol
    FastEthernet0/0            10.1.2.3        YES manual up                    up      
    FastEthernet0/1            10.1.34.2       YES manual administratively down down    
  
  - BB(config)#router eigrp 50
  
    BB(config-router)#no auto
  
    BB(config-router)#network 10.1.0.0 255.255.255.0
    BB(config-router)#network 172.30.0.0 255.255.255.0
  
    - int f0/0
      - ip summary-address eigrp 50 172.30.0.0 255.255.255.0
  
    - router eigrp 50
      - variance 2 
  
  - sh ip eigrp neighbor
  
  - R2(config)#router eigrp 50
  
    BB(config-router)#no auto
  
    R2(config-router)#network 10.1.2.2  255.255.255.0   
    R2(config-router)#network 10.1.24.2  255.255.255.0 
    R2(config-router)#network 10.1.25.2  255.255.255.0 
  
  - R3(config)#router eigrp 50
    R3(config-router)#no auto 
    R3(config-router)#network 10.1.2.3 255.255.255.0   
    R3(config-router)#network 10.1.34.2 255.255.255.0  
  ```

- Dynamic Routing
  
  - ADVRP
    - EIGRP
      - DUAL
        K Values 5 k values
        K1- Bandwidth
        K2- Load
        K3- Delay
        K4- Relaibility
        K5- MTU
    - It is L3 Protocol.
    - EIGRP use multicast address 224.0.0.10 to share all messages.
  - EIGRP create three types of tables
    a.Routing Table
    b.Neighbor Table
    c.Topology Table
  - It is CISCO Protocol.
  - To create multiple domain of EIGRP we use AS# (Autonomous System Number).
  - It is Class-less Routing Protocol.
  - In EIGRP Updates are preodic And Triggered.
  - In EIGRP we can perform Equal and Unequal Cost loadbalancing.
  - EIGRP use DUAL algoridtham to select best route.
  - We have 5 K values in EIGRP.
  - 11. In EIGRP AD viaues are 90, 170, 5

- ROUTER ID
  
  1. Static
  2. Highest Loopback IP
  3. Highest IP of physical interface

- DUAL
  
  1. FD
  2. RD/AD
  3. S
  4. FS

- eigrp messages
  
  1. Hello
  2. Update
  3. Acknowledgment

- Split Horizan
  Route Poision
  Poision Revirus

- summarization
  
  | 192.168.97.0/24  | 128 | 64  | 32  | 16  | 8   | 4   | 2   | 1   |
  | ---------------- | --- | --- | --- | --- | --- | --- | --- | --- |
  | 192.168.98.0/24  | 0   | 1   | 1   | 1   | 0   | 0   | 0   | 1   |
  | 192.168.99.0/24  | 0   | 1   | 1   | 0   | 0   | 0   | 1   | 0   |
  | 192.168.100.0/24 | 0   | 1   | 1   | 1   | 0   | 0   | 1   | 0   |
  | 192.168.101.0/24 | 0   | 1   | 1   | 0   | 0   | 1   | 0   | 0   |
  | 192.168.102.0/24 | 0   | 1   | 1   | 1   | 0   | 1   | 0   | 1   |
  | 192.168.103.0/24 | 0   | 1   | 1   | 0   | 0   | 1   | 1   | 0   |
  | 192.168.104.0/24 | 0   | 1   | 0   | 0   | 1   | 1   | 1   | 1   |
  
  - Route-Filtring
    eigrp tool= Distribute-list ACL prefix-list
    10.1.1.0/29
    10.1.2.0/26
    10.1.3.0/27
    10.1.4.0/28
    10.1.5.0/30
    10.1.6.0/24
  - ip prefix-list <name> <Action> <network> ge 28 le 30
  - ROUTE-MAP
    - EIGRP 100
      EIGRP 200
      OSPF 1|
    - metric
    - next-hop
    - interface
    - route-type
    5. source-protocol
  - redistrtibution