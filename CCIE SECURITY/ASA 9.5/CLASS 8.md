- Firewall:
  - --> The main purpose of firewall is to allow all inside users to access internet while deny
    any unwanted packet coming from outside.
  - --> It is used to control which traffic can go outside and which traffic can come from
    outside

- Cisco ASA: Adaptive Security Appliance
  - ASA feature:

  a. Static Packet Filtering using ACL

  b. Stateful inspection

  c. NAT/PAT

  d. VPN is supported

  e. Routing (static as well as dynamic)

  F. Routed and transparent mode of ASA

  g. Single vs multiple mode

  h. High availability (Failover)

  i. Cluster (Etherchannel)

  j. DHCP (DHCP server, DHCP client, DHCP relay agent)
  k. Application inspection (we can take action based on L7) (not done on asa)
  I. AAA

  m. MPF (advanced action)

- Configuring an interface on ASA
  - a. Enable interface 
  - b. IP address   
  - c. Nameif .
  - d. Security-Level
  - Nameif:
    --> it is specify a name for the interface
    --> it can be any logical name
    --> Most commonly used names are inside, outside, and DMZ
    --> namerf must be unique for each interface
    --> It is used to apply any kind of policy on the interface.
    - ASA never checks name to forward any data trafic
- Security Level
  --> it is number ranging trom 0 to 100
  --> Based on this number, ASA decides whether to allow the packet or not
                     interface gi0/O
                     security-level 100
  
  - for nameif inside, security level is automatically configured to 100
  - for any other nameif, security level is O which can be changed
  
- if we do not specity subnet mask then automatically it will take classful subnet
  mask
  Default behavior of ASA
  a. Higher Security Level to Lower Security Level, all traffic is allowed.
  b. Lower Security Level to Higher Security Level, all traffic is denied. You may use ACL to
  permit traffic.
  c. Same Security Level Traffic is by default denied.
  d. TCP and UDP is inspected by default. ASA stateful behavior is only for TCP and UDP by
  default.
- TCP and UDP reply traffic is always allowed