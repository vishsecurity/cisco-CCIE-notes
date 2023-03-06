## DHCP: Dynamic Host Configuration Protocol

- command

  - trusted

    - trunk

    - access dhcp

      ```
      Switch(config)#do sh his
      ip dhcp snooping
      ip dhcp snooping vlan 10
      ip dhcp snooping information option 
      int f0/2
      switchport mode trunk
      ip dhcp snooping trust
      int f0/1
      switchport mode access 
      switchport access  vlan 10
      ip dhcp snooping limit rate 10
      ```

- DORA
  D- Discover ,
  O- Offer
  R- Request
  A- Acknowledgment

- if you are not using Relay agent.

  - when your user and server both are in same network and in same
    vian.
  - then we need to disable option 82. in DHCP Snooping.
  - if you are not enabled DHCP Snooping then Option 82 will also not be
    used.
  - if you have enabled relay agent command on interface then no
    matter is the optiion 82 is enabled or disabled.

- VLAN ACL

  - Ip access list standard/estendard

  - access-list (no of acl) stan/ext _ Action Permit/Deny/ Network/IP/any_ Wildcard

  - acces-list 10 deny 10.1.1.0 0.0.0.255

  - ip access-list standard/extendard no/name

  - ip accesstist extended 101
    deny <protocol> Source ip/network Destination IP/ network

  - <service>
    telnet /23
    ssh/22

  - HTTPS
    TELNET
    SSH

  - tcp 

    - udp
    - ip
    - icmp

  - ip access-list standard 10
    permit 10.1.1.1 0.0.0.0
    exit
    vlan access-map cisco 10
    match Ip address 10
    action drop
    exit
    vlan access-map cisco 20
    action forward
    exit

    vian filter cisco vian-list 20

  - Private vian
    1. Primary vian
    2. Secondary Vian
    Primary vlan can communicate to all types of secondary vians.
    All Secondary vians can communicate to Primary vian but Secondary vian
    can not communicate to other secondary vian.

  ## Secondary vians are two types

  1. Community
  2. Isolated
     - Community users can communicate with eachother and can communicate to primary vian.
     - Isolated users can't communicate with each other but they can communicate with primary vian

  ## Modes of Ports in Private vlan

  1. Host (Secondary)
  2. Promiscous (Primary)

  

  ##  Switch port Securty

  - Firstly we need to use Static mode on my port where i want to configure Swithcport port-Security.
  - int f0/1
    Switchport mode Access (to chhange switchport mode)
    switchport port-security (To enable port security on port)
  - switchport port-security mac-address 0000.0000.000A (to define device identity) (this is static method)
    Or switchport port-security mac-address Sticky (This is dynamic method to learn device identity)
  - switchport port-security maximum 1
    switchport port-security violation
    - Protect | will block that mac address no message
    2. Restrict block and message will generate
    3. Shutdown block, message will generate and port will go in error-disable mode