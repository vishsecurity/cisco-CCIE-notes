# NAT/PAT

## commands

- ASA 1

  - ASA(config)# clear config  interface gigabitethernet 1/2

  - ASA(config)#int gi1/2

  - ASA1(config-if)# no sh

  - ASA1(config-if)#nameif outisde

  - ASA1(config-if)#ip add 101.1.1.10 255.255.255.0

  - ASA1(config-if)#wr memory

  - ASA1(config-if)#fixup protocol icmp

    - this command allow to the asa traffic .

  - ASA1(config-if)#int g1/1

  - ASA1(config-if)#no sh

  - ASA1(config-if)#nameif inside

  - ASA1(config-if)#ip add 192.168.1.10 255.255.255.0

  - ! object group

    - !ASA1(config)#object-group network abc
    - !ASA1(config-network-object-group)#network object host 1.1.1.1
    - !ASA1(config-network-object-group)#network object host 2.2.2.2
    - !ASA1(config-network-object-group)#exit
    - !ASA1(config)#clear configuration object-group

  - ASA1(config)#object network abc

    ASA1(config-network-object)#host 1.1.1.1

    ASA1(config-network-object)#host 2.2.2.2

    ASA1(config-network-object)#subnet 192.168.1.0 255.255.255.0
    
  - ASA1(config)#object network real-ip

  - ASA1(config-network-object)#subnet 192.168.1.0 255.255.255.0

  - ASA1(config)#object network mapped-ip

  - ASA1(config-network-object)#range 101.1.1.11 101.1.1.13

  - ASA1(config)#object network real-ip

  - ASA1(config-network-object)#nat (inside,outside) dynamic mapped-ip

- R1

  - R1(config)#int g0/0
  - R1(config-if)#ip add 192.168.1.1 255.255.255.0
  - R1(config-if)#no sh
  - R3(config)#ping 101.1.1.1

- R3

  - R3(config)#int g0/0
  - R3(config-if)#ip add 101.1.1.1 255.255.255.0
  - R3(config-if)#no sh
  - R3(config)# do bebug ip icmp

## Debug

- ASA1#sh int ip bri

  Interface              IP-Address           OK? Method      Status                Protocol

  Virtual0                      127.1.0.1          YES unset            up                    up

  GigabitEthernet1/1     192.168.1.10    YES manual     up                    up

  GigabitEthernet1/2     101.1.1.10      YES manual      up                    up

- ASA1(config)#sh run object-group

- ASA1(config-network-object)#sh run object

  ```
  0
  object network abc
  host 1.1.1.1
  ```

- ASA1(config-network-object)#sh run object

  ```
  0
  object network abc
  host 2.2.2.2
  ```

- ASA1(config-network-object)#sh run object

  ```
  0
  object network abc
  subnet 192.168.1.0 255.255.255.0
  ```

- ASA1(config-network-object)#sh xlate

  ```
  0 in use, 0 most used
  ```

- ASA1#sh run nat

  ```
  object network real-ip
  nat (inside,outside) dynamic mapped-ip
  ```

## wiresshark

## scenario

1. if r1 does not have route of r3, will r1 ping r3 ?
   1. it will go through asa since it is inspected but r3 does not have root so packet will not come back.
2. TASK: Configure Dynamic NAT on ASA1 to translate inside subnet 192.168.1.0/24 into pool of mapped
   IP (101,1.1.11 to 101.1.14.13) on outside interface. 
   - Ingress --> inside
   - Egress ==> outside
   - Real IP --> 192.168.1.0/24
   - Mapped IP --> 104.1.4.44 - 101.1.1.143
   - Step1: Create object for Real IP and Mapped IP
   - Step2: Configure NAT under Real IP object

##  questions

#### communication is success full 

-  when packet go and come back.
- when packet  go it will  translate 1.1 to 10.1 (translated)
- when packet return  10.1 to 1.1 (n translate)

### what is NAT?

- Translating an IP address into another IP which is routable on the destination network.

- NAT can be:

  a. Private to Public  : To provide internet access to inside user (LAN)
  b. Private to Private  : VPN with NAT
  c. Public to Private :
  d. Public to Public  :

- Types of NAT

  a. Dynamic NAT

  - Translation is not permanent
  - Translation entry is removed after some time
  - Entry in Xlate is added only when packet is translated. Entry 's not
    automatically added in Xlate after NAT configuration
  - Translation entry is not permanent. Default timeout is 3 hours. timeout xlate 
  - It is one to one 
  - Translation is mainly done on the basis of Layer3 information 
  -  Translation is done on the basis of first come first server. 
  - ln this, we always have a pool of mapped ip
  - it is unidirectional (only NAT)
    - if connection initiated, then only NAT will work 
    - If connection initiated from outside, UN-NAT will not work
  - where connection is initiated from inside.

  b. Dynamic PAT

  - --> Translation is mainly done on the basis of Layer 4
    --> Layer 3 and Layer 4 information is maintained in translation table.
    --> Many to One

  ¢. Static NAT 

  - Translation entry in Xlate 1s permanent which means, as we configure NAT, entry is automatically
    updated in the translation table.
  - It is bi-directional .
  - where connection is initiated from outside.
  - it is one to one

  d. Static PAT 

  - --> Translation is mainly done on the basis of Layer 4
    --> Layer 3 and Layer 4 information is maintained in translation table.
    --> Many to One

  e. Identity NAT
  f. Condition NAT

- Whenever we perform translation, there are two IP addresses:
  - Real IP address --> It is the actual IP of the device/user
  - Mapped IP address --> the IP address in which real IP is translated.
  - Translation --> Translating Real IP into Mapped IP   (policy applied) [NAT]
  - Un-Translation --> Translating Mapped IP into Real IP  [UN NAT]

- Why to use NAT ?

  1. To access internet from private network 
  2. To hide the real IP address 
  3. Resolve IP routing problems, such as overlapping subnets.
     1. same subnet means overlapping subnet.

  

- what is difference between  object and object-group ?

 - object-group 
     - we can have multiple match statements 
     - It is used to simplify Access-list
 - object
    - we can have only one match statement and one NAT statement . 
    - It is used to configure NAT
    - There ave only two types of object
      - layer 3
      - layer 4

