### Why do we need a firewall

### Cisco ASA features

### What are the primary requirement as per real time for an organisation:

- a. All inside users should be able to access internet

- b. Outside users should not be allowed to access inside network.
  
  ```
  ip access-list extended PAT
  permit ip any any
  
  int fa O/O
  ip nat inside
  
  int fa O/2
  ip nat outside
  
  ip nat inside source list PAT interface fO/1 overload
  
  ip access-list extended INBOUND
  deny ip any any
  
  int fa O/2
  ip access-group INBOUND in
  ```
  
- Stateful Inspection
  
  --> It is a feature by which all inside users can access internet and at the same if any
  unwanted packet comes trom outside is denied.
  
  --> Whenever any packet comes trom inside, device allows the packet and it will store the
  connection information( L3 , L4) in its connection table.

- b. Whenever any packet comes from outside, device will compare the packet information (I3, |4)
  with its connection table
  
  - --> packet matches with any of the connection entry in conn table, then the packet is
    allowed
  - --> if packet does not match with any of the conn entry in conn table, then packet is not
    allowed.