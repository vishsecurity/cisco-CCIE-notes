1. Default behavior of ASA
2. Packet flow of ASA with ACL
3. Packet flow of ASA with ACL and NAT
4.  How ASA determines egress interface

### Packet Flow:

- Whenever ASA recieves packet from any interface.
  ASA tries to match packet with its connection table.

1. if packet matches with connection table, then Security Level and ACL check is bypassed for the packet.
    Packet is directly forwarded out of its egress interface.

2. If packet does not match with connection table, then state of packet is verified in case if it is TCP.
    If it is TCP syn packet then packet is processed for next check.
    if it is not a syn packet, then packet is dropped.
    ASA will check packet as per ACL configured on the interface.

3. If Access-list is configured, then packet must match with any of the permit statement. Otherwise
    packet will be dropped.

4. If access-list is not configured, then packet is processed as per default behavior

  ###  Global Access-list

  ​      --> It is a way by which we can apply an ACL on all the interfaces of ASA in inbound direction.
  this global ACL concept is not mainly used on ASA, this concept is used on Firepower
  what if interface ACL and global ACL both ave applied

  - THERE WILL NO IMPLICIT DENY AT THE END OF INTERFACE ACL 
  - If both ACLs are applied then interface ACL will be checked.
  - If packet matches with any statement, then action will be taken and global will not be checked.
  - If packet does not match with any of the interface acl statement, then global ACL will be checked. 