### TASK DISCUSSION 

- NAT-RPF
- Packet Flow
- How Egress Interface is determined on ASA
- Symmetric Routing and Asymmetric routing

  - Symmetric routing --> Same path followed by a packet for forward and reverse flow

  - Asymmetric routing --> different path followed by a packet for forward and reverse flow
- NAT-RPF (Reverse Path Failure)
       --> It is a feature on ASA which gets enabled automatically as we configure any NAT on ASA.
       --> NAT-RPF feature makes sure that for a packet same NAT rule is used for translation and    untranslation
      --> if for a packet different nat rules are used for translation and untranslation, ASA will simply drop that packet

1. Conn table

2. Un-translation (NAT Rule) 2.4 --> route lookup

3. ACL

4. NAT

5. Inspection


- Whenever packet is recieved on an interface of ASA, these checks are peformed:
  a. ASA will check its connection table
    --> if packet matches with connection table, packet is forwarded without any further inspection. Interface
- ACL and Security Level check 1s bypassed.
   --> If packet does not match with the connection table, state of packet is verified, if rt 1s TCP syn packet, packet is processed for next check, otherwise packet i's dropped and log message is generated.
  --> if packet matches with connection, ASA does not perform route lookup for destination
  b. ASA will check whether to un-translate the packet or not by checking its Xlate table. If the
  destination IP and destination port (if any) matches with any of the mapped IP and mapped port(if
  any) for that interface, ASA will perform untranslation

- if access-list is configured on interface, packet must match with any of the permit statement, if packet
   does not match with any of the permit statement packet is dropped.
- if access-list is not configured on interface, then packet is processed as per default behavior of ASA.
-  ASA will check its NAT rule to confirm whether to translate the packet or not.
    if packet matches with any of the NAT rule, packet must be translated
    if packet does not match with any of the NAT rule, packet is simply processed without any translation.