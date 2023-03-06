###  Can we use Dynamic NAT to allow outside user to access any inside server???
--> no

- Static PAT 
- Static NAT 
- Identity NAT

- Static NAT and Static PAT are mainly used to allow internet users to access any inside server.
  Because in static NAT and Static PAT, xlate entry is automatically created.

- Static NAT
  --> It is bidirectional in nature
  --> translation 1s automatically created as we configure nat rule and it is permanent.
  --> It Is one to one NAT
  --> There is fixed mapped IP for a Real IP
  --> Only Layer 3 information is stored in translation table.

  ###  TASK: Configure Static NAT to translate DMZ IP 192.168.2.1 into outside IP 101.1.1.1
  or

  ###  TASK: Configure NAT on ASAZ. so that outside users can access DMZ server with outside IP 101.1.1.1

  - Ingress --> DMZ      real IP --> 192.168.2.1
    eqvess --> outside    mapped |P--> 101.1.1.1

  - object network DMZ
    host 192.168.2.1
    nat (dmz,outside) static 101.1.1.1

  - All the services of Real IP is mapped with services of Mapped IP.
    Static PAT:
    --> Translation entry 1s permanent
    --> /t can be many to one
    --> One service of Mapped IP is binded with one service of Real IP
    --> Layer 3 and layer 4 information is used to configure static PAT.

    ###  TASK: Configure NAT on ASA so that telnet services of outside interface is mapped with telnet services of DMZ server.

    - Real IP :  192.168.21
      real Port : telnet
      mapped IP  : interface
      mapped port : telnet

    - object network DMZ
      host 192.168.2.1
      nat (dmz,outside) static interface service tcp telnet telnet

      

      ### TASK: Configure NAT on ASA so that telnet services of outside interface is mapped with R2 and SSH services of outside interface is mapped with R2.

      - TO Verify task make sure you can successfully telnet R2 and SSH R1 from R3:

        ### TASK: Configure NAT on ASAZ so that You can telnet R1 as well R2 using outside interface
    
    - Identity NAT
          --> Translating Real IP into its own IP
          --> Identity NAT is also known as NAT Bypass
    - NAT-Exemption --> before 2.3 
      - Identity NAT is mainly used in case of VPN 
