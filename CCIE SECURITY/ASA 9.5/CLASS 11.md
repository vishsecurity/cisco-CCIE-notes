### What is access-list???

  --> It is a list of permit or deny statement
What is the use of ACL??
	--> Control Data trattic (Permit or deny)
	--> Control Interactive Access
	--> NAT/PAT use on IOS
	--> Policy Based routing
	--> Route Filtering
	--> VPN

### Types of Access-list:

a. Standard Access-list
b. Extended Access-list
c. EtherType access-list
d. WebType Access-list
e. Time Based Access-list

- There is no concept of Numbered ACL on ASA, Only named ACL
  is supported. With name of ACL, ASA connot determine the
  type of ACL. We can use number as a name of ACL

1. Extended ACL:
      --> It is the main type of ACL on ASA because only extended ACL can be applied on an
   interface of ASA to filter data trattic.

2. Standard ACL
--> it can be used to filter trattic based on source IP.
--> it can be used for routing filtering
4. Standard ACLs

- Supported in routed and transparent mode
  Cannot be applied to an interface
  Can be used in route filtering and redistribution

2. Ethertype ACL:

- Can be used in transparent mode
  Can be used permit or drop traffic based on the Ethertype value
  in the layer-2 packet

3. Webtype ACLs

- Webtype ACLs are used for filtering clientless SSL VPN traffic
  Supported in routed mode only

 4 . time based ACL


- How to create Access-list  How to apply ACL

  - access-list                aCCESS-Group

    - access-list <name> <type> permit <sprotocol> <sre-ip> <src-p ort> <dest-ip> <dest-prt>
                                                    deny tcp 
                                    													 udp

      ​														iCMP

    -   access-list <name> standard permit <src-ip>
                                                      deny host
                                                               any
                                                               subnet

    -  access-group <name> <direction> interface <nameif>
                                              in
                                             out

    - Specifying the type of ACL is not mandatory in case of standard or extended

    -  ASA can automatically determine the type of ACL

    -   TASK: Configure Access-list on ASA1 so that R21 can ping R3
