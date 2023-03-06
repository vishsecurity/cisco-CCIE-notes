- commands

  ```
   Switch(config-if)#do sh his
    int f0/1
    switchport mode access 
    switchport access  vlan 10
    int f0/2
    switchport mode access 
    switchport access  vlan 20
    int f0/3
    switchport mode access 
    switchport access  vlan 30
    int f0/4
    switchport mode trunk 
    pc1 > 10.41.40.2/10.41.40.1
    pc2 >  10.41.50.2/10.41.50.1
    pc3 > 10.41.60.2/10.41.60.1
    Router(config-subif)#do sh his
    int gi0/0.10  
    encapsulation dot1q 10
    ip add 10.41.40.1 255.255.255.0
    int gi0/0.20
    encapsulation dot1q 20
    ip add 10.41.50.1 255.255.255.0
    int gi0/0.30
    encapsulation dot1q 30
    ip add 10.41.60.1 255.255.255.0
    do sh his
  ```
  
  
  
  ```
  Switch(config)#int f0/1
  Switch(config-if)#switchport mode ac
  Switch(config-if)#switchport mode access 
  Switch(config-if)#switchport acc
  Switch(config-if)#switchport access vlan 10
  % Access VLAN does not exist. Creating vlan 10
  Switch(config-if)#
  Switch(config-if)#int f0/2
  Switch(config-if)#switchport mode access 
  Switch(config-if)#switchport access vlan 20
  % Access VLAN does not exist. Creating vlan 20
  Switch(config-if)#
  Switch(config-if)#int f0/3
  Switch(config-if)#switchport mode access vlan 30
  Switch(config)#ip
  Switch(config-if)#do sh his
    int vlan 10
    ip add 10.41.40.1 255.255.255.0
    int vlan 20
    ip add 10.41.50.1 255.255.255.0
    int vlan 30
    ip add 10.41.60.1 255.255.255.0
    do sh his
  ```
  
  
  
- Inter Vian Communication

  - ROS (Router On Stick)
  - Use SVI (Switch Virtual Inteface)

- router

  1. Check L2 information.
  2. Remove L2 information
  3. Check L3 information.
  4. Check R.T
  5. Find Exit Interface
  6. Add L2 Information
  7. Check ARP Table

  