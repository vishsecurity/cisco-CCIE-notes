- unicast 

- commands

  ```
   CCNP-BSCI-v5.0 Lab 7-1: Implementing IGMP and IGMP Snooping
  - 5月 31, 2018
  
  本次練習是參考Cisco網路學院
  CCNP1 Building Scalable Internetworks v5.0
  Student Lab Manual
  我將它轉成Dynamips的設定檔 並寫下自己的實驗紀錄
  
  Dynamips的設定檔:
  ##################################################
  #
  # For CCNP1 Building Scalable Internetworks v5.0
  # Lab 7_1
  #
  ##################################################
  autostart=false
  [localhost:7200]
  workingdir = /opt/dynamips/dynagen-0.10.1/UTS/CCNP1/Week06/workingconfig/
  [[3640]]
  #  Specify 3640 IOS image on Windows here:
  #  image = C:\Program Files\Dynamips\images\c3640-jk9o3s-mz.123-S14.T7.extracted.bin
  #  Specify 3640 IOS image on Linux here:
   image = /opt/dynamips/images/c3640-jk.bin
   ram = 128
   disk0 = 0
   disk1 = 0
   # Choose an idlepc value from the below
   idlepc = 0x605ac7b8
   mmap = true
   ghostios = true
   confreg = 0x2102
  
  ###########################
  #
  # Define router instances 1
  #
  ###########################
    
   [[Router R1]]
    model = 3640
    console = 2001
    slot0 = NM-1FE-TX
   [[Router R2]]
    model = 3640
    console = 2002
    slot0 = NM-1FE-TX
   [[Router R3]]
    model = 3640
    console = 2003
    slot0 = NM-1FE-TX
   [[Router SW1]]
    model = 3640
    console = 2004
    slot0 = NM-16ESW
    F0/1 = R1 F0/0
    F0/3 = R2 F0/0
    F0/5 = R3 F0/0
  這Lab學習目標為
  • Configure IGMP to join interfaces to a multicast group
  • Verify the operation of IGMP at Layer 3
  • Analyze IGMP packets and packets sent to multicast groups
  • Enable PIM-DM
  • Verify the operation of IGMP snooping on a Catalyst switch
  場景:
  Configure IGMP to listen to the multicast group 229.7.7.7 on R2 and R3. Send
  multicast traffic from R1 to the LAN segment. Configure IGMP snooping to
  efficiently send multicast traffic through the switch.
  我的設定是
  1. Configure Hosts on a LAN
  R1:
  hostname R1
  !
  no ip routing
  !
  no ip domain lookup
  !
  interface Loopback1
   ip address 172.16.1.1 255.255.255.0
  !
  interface FastEthernet0/0
   ip address 192.168.1.1 255.255.255.0
   no shut
  !
  line con 0
   exec-timeout 0 0
   logging synchronous
  !
  end
  R2:
  hostname R2
  !
  no ip routing
  !
  no ip domain lookup
  !
  interface Loopback2
   ip address 172.16.2.1 255.255.255.0
  !
  interface FastEthernet0/0
   ip address 192.168.1.2 255.255.255.0
   no shut
  !
  line con 0
   exec-timeout 0 0
   logging synchronous
  !
  end
  R3:
  hostname R3
  !
  no ip routing
  !
  no ip domain lookup
  !
  interface Loopback3
   ip address 172.16.3.1 255.255.255.0
  !
  interface FastEthernet0/0
   ip address 192.168.1.3 255.255.255.0
   no shut
  !
  line con 0
   exec-timeout 0 0
   logging synchronous
  !
  end
  SW1:
  hostname SW1
  !
  no ip routing
  !
  no ip domain lookup
  !
  line con 0
   exec-timeout 0 0
   logging synchronous
  !
  end
  
  2. Subscribe Interfaces to Multicast Groups with IGMP
  R1 & R2 & R3:
  debug ip igmp
  debug ip packet
  R1:
  interface fastethernet 0/0
   ip igmp join-group 229.7.7.7
  !
  end
  !
  show ip igmp interface fastethernet 0/0
  !
  conf t
  !
  interface fastethernet 0/0
   no ip igmp join-group 229.7.7.7
  R2 & R3:
  interface fastethernet 0/0
   ip igmp join-group 229.7.7.7
  R2 & R3:
  show ip igmp groups
  show ip igmp membership
  R1 & R2 & R3:
  ping 229.7.7.7
  
  3. Verify IGMP Snooping on the Switch
  SW1:
  sh ip igmp snooping
  
  4. Configure a Multicast-Enabled Router on the VLAN
  R1:
  ip multicast-routing
  !
  interface fastethernet 0/0
   ip pim dense-mode
  
  5. Verify Multicast Operation at Layer 2
  R1:
  undebug all
  !
  show ip igmp groups
  !
  show ip igmp membership
  !
  show ip igmp interface
  
  6. Verify IGMP Snooping
  SW1:
  show mac address-table multicast
  Statically subscribe FastEthernet0/9 on SW1 to the multicast MAC group of 0100.5e07.07.07
  SW1:
  ip igmp snooping vlan 1 static 0100.5e07.0707 interface fastethernet 0/9
  
  7. Verify Multicast Operation at Layer 3
  R1:
  show ip mroute
  ping 229.7.7.7
  
  Final Configurations
  R1:
  hostname R1
  !
  no ip domain lookup
  !
  ip multicast-routing
  !        
  interface Loopback1
   ip address 172.16.1.1 255.255.255.0
  !
  interface FastEthernet0/0
   ip address 192.168.1.1 255.255.255.0
   ip pim dense-mode
   no shut
  !
  line con 0
   exec-timeout 0 0
   logging synchronous
  !
  end
  R2:
  hostname R2
  !
  no ip routing
  !
  no ip domain lookup
  !
  interface Loopback2
   ip address 172.16.2.1 255.255.255.0
  !
  interface FastEthernet0/0
   ip address 192.168.1.2 255.255.255.0
   ip igmp join-group 229.7.7.7
   no shut
  !
  line con 0
   exec-timeout 0 0
   logging synchronous
  !
  end 
  R3:
  hostname R3
  !
  no ip routing
  !
  no ip domain lookup
  !
  interface Loopback3
   ip address 172.16.3.1 255.255.255.0
  !
  interface FastEthernet0/0
   ip address 192.168.1.3 255.255.255.0
   ip igmp join-group 229.7.7.7
   no shut
  !
  line con 0
   exec-timeout 0 0
   logging synchronous
  !
  end
  SW1:
  hostname SW1
  !
  no ip routing
  !
  no ip domain lookup
  !
  ip igmp snooping vlan 1 static 0100.5e07.0707 interface Fa0/9
  !
  line con 0
   exec-timeout 0 0
   logging synchronous
  !
  end
  
  ```

  

- BROADCAST

- MULTICAST

- multicast address range - Class d- 224.0.0.0 239.255.255.255

- DIP

-  MRT

  - IGMP:- Internet Group Management Protocol
    L3 Protocol
    IP protocol No. 2
    Version 1,2 and 3
    By default version is running on all devices version 2.
    IGMP messages

  1. Query message:-
  preodic and triggered
  2. Report message:-
  226.1.1.1
  on multicast
  address 224.0.0.1
  2. Report message:-
  226.1.1.1

- CGMP- CISCO GROUP MANAGEMENT PROTOCOL

- PIM : PROTOCOL INDEPENDENT MULTICAST

  - Layer 3
    IP protocol no. 103
    Multicast address 224.0.0.13
    hello in every 30 seconds
    hold time 3.5 times of hello