# VRF

- commands

  ```
  R1(config)#hostname SULU
  SULU(config)#
  SULU(config)#
  SULU(config)#
  SULU(config)#
  SULU(config)#ip vrf SULU
  SULU(config-vrf)#int l0
  SULU(config-if)#ip vrf 
  *Mar  1 00:01:50.767: %LINEPROTO-5-UPDOWN: Line protocol on Interface Loopback0, changed state to up
  SULU(config-if)#ip vrf forwarding SULU
  SULU(config-if)#ip add 1.1.1.1 255.255.255.0
  SULU(config-if)#
  SULU(config-if)#int l1                      
  SULU(config-if)#ip vrf forwarding SULU      
  SULU(config-if)#ip add 1.1.1.1 255.255.255.0
  *Mar  1 00:02:24.355: %LINEPROTO-5-UPDOWN: Line protocol on Interface Loopback1, changed state to up
  SULU(config-if)#ip add 11.11.11.11 255.255.255.0
  
  SULU(config-if)#int tunnel 1
  SULU(config-if)#
  *Mar  1 00:16:40.403: %LINEPROTO-5-UPDOWN: Line protocol on Interface Tunnel1, changed state to down
  SULU(config-if)#tunnel source fastEthernet 0/0
  SULU(config-if)#tunnel destination 192.168.12.2
  SULU(config-if)#ip vrf forwarding SULU      
  SULU(config-if)#ip address 192.168.21.1 255.255.255.0 
  
  SULU(config)#router eigrp 12
  SULU(config-router)#no auto-summary
  SULU(config-router)#address-family ipv4 vrf SULU
  SULU(config-router-af)#network 1.1.1.0
  SULU(config-router-af)#network 11.11.11.0
  SULU(config-router-af)#network 192.168.21.0
  SULU(config-router-af)#autonomous-system 12
  
  R2(config)#hostname Checkov
  Checkov(config)#
  Checkov(config)#
  Checkov(config)#
  Checkov(config)#ip vrf CHECKOV
  Checkov(config-vrf)#int l0
  Checkov(config-if)#ip 
  *Mar  1 00:04:14.923: %LINEPROTO-5-UPDOWN: Line protocol on Interface Loopback0, changed state to up
  Checkov(config-if)#ip vrf forwarding CHECKOV
  Checkov(config-if)#ip add 2.2.2.2 255.255.255.0
  Checkov(config-if)#
  Checkov(config-if)#
  Checkov(config-if)#int l1                      
  Checkov(config-if)#ip vrf forwarding CHECKOV   
  *Mar  1 00:04:36.667: %LINEPROTO-5-UPDOWN: Line protocol on Interface Loopback1, changed state to up
  Checkov(config-if)#ip vrf forwarding CHECKOV
  Checkov(config-if)#
  Checkov(config-if)#ip add 22.22.22.22 255.255.255.0
  
  Checkov(config-if)#int tunnel 1
  *Mar  1 00:13:32.035: %LINEPROTO-5-UPDOWN: Line protocol on Interface Tunnel1, changed state to down   
  Checkov(config-if)#tunnel source fastethernet 0/0
  Checkov(config-if)#tunnel destination 192.168.12.1
  Checkov(config-if)#ip vrf forwarding CHECKOV
  SULU(config-if)#ip address 192.168.21.2 255.255.255.0 
  
  Checkov(config)#router eigrp 12
  Checkov(config-router)#no auto-summary
  Checkov(config-router)#address-family ipv4 vrf CHECKOV
  Checkov(config-router-af)#network 192.168.21.0
  Checkov(config-router-af)#network 2.2.2.0     
  Checkov(config-router-af)#network 22.22.22.0
  Checkov(config-router-af)#autonomous-system 12
  
  Checkov#ping vrf CHECKOV 11.11.11.11 source loopback 1
  
  Type escape sequence to abort.
  Sending 5, 100-byte ICMP Echos to 11.11.11.11, timeout is 2 seconds:
  Packet sent with a source address of 22.22.22.22 
  !!!!!
  Success rate is 100 percent (5/5), round-trip min/avg/max = 4/17/24 ms
  Checkov#ping vrf CHECKOV 11.11.11.11 source loopback 0
  
  Type escape sequence to abort.
  Sending 5, 100-byte ICMP Echos to 11.11.11.11, timeout is 2 seconds:
  Packet sent with a source address of 2.2.2.2 
  !!!!!
  Success rate is 100 percent (5/5), round-trip min/avg/max = 4/35/84 ms
  ```
  
  
  
  
