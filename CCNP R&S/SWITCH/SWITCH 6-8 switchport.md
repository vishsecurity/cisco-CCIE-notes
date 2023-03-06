# Switchport mode trunk

1. Access Mode:- This interface will be member of only a single VLAN.
2. Trunk:- switch will use tagging on Trunk interface.

## TRUNK ENCAPSULATION PROTOCOLS

1. ISL (Inteer Switch Link)
2. Dotig (IEEE 802.1Q Standard)

## ISL
1. It is a CISCO Protocol.

2. It is only available in CISCO devices.

3. ISL header size is 30 bytes. 

4. 26 header and 4 byte trailer

## Dot1q

5. itis open standard.
6. Dot1q header size 4 bytes

## VLAN-HOPING

## SWITCHPORT MODES

- Administrative Mode
  - Static Access
    - Switchport mode access
  - Static Trunk
    - Dynamic Desirable
    - Dynamic Auto
- Opprational Mode
      - access
     - Trunk

## DTP 

- It is Cisco Proprietary Protocol.
- It is a Layer 2 Protocol.
3. It is use to create Trunk Port and Access Port Dynamically.
- By default DTP is enabled on all Cisco Switch.
- It send message Priodically in every 30 sec.
6. It uses Multicast MAC address 0100.0ccc.cccc.

# MODES 

- DA DA  Access dynamic
- DD DA Trunk Dynamic
- DA DD Trunk Dynamic
- DD DD Trunk Dynamic
