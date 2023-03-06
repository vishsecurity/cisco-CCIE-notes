# DNS Doctoving
## TASK:

1. Configure NAT on ASAZ so that any outside user can access DMZ server with 101.1.1.11 IP.

2. Make sure Outside users can access DMZ server with name "google.com". Use RB as DNS server.

3. Make sure inside users can also access the DMZ server with name with R3 as DNS server

  ```
  Real IP --> 192.1628.2.4
  Mapped IP --> 101.1.1.11
  ```

  

  ## DNS Doctoring

  --> It is a feature by which ASA can inspect DNS packets and look every DNS reply packet.

  --> IPASA finds that DNS reply packet contains any of the mapped IP, then ASA will replace mapped IP
  with (ts Real (P and send the packet as rt ts.

  Step1: Enable DNS Doctoring for NAT rule with "dns" keyword in
  nat statement

  ```
  object network R2
  nat (dmz,outside) static OLL,4.44 dns
  ```

  Step2: Enable DNS inspection
  by default dns inspection is enabled
  ASA

1. Routed Firewall --> L3 device in the network
2. Transparent Firewall
3. Single Mode --> Act as a single device
4. Multiple Mode --> We can create security context
  Transparent Firewall
  --> In this ASA acts as a Layer2 device in the network
  --> ASA will forward packets based on the MAC address.
  --> ASA maintains MAC address table.
  --> ASA is transparent for adjacent devices,
  --> ASA can take action from layer 2 to layer 7.
  --> we can configure one IP address on ASA 1-2. management (P
  address. It must be of same subnet as of directly connected
  network
  --> ASA maintains routing table as well as MAC address table.
  Routing table is used only for management traftic.
  Ranyting table fe nover weed far data teal fn tranepnrent Lrowsl/
  --> by default layer2 traffic is allowed through firewall irvesepective of security level, but action
  can be take by configuring ethertype access-list

  --> Statice route for management traftic is supported, Routing protocol cannot be configured
  --> routing protocol through the device 1s allowed

  --> by default multicast IP traftic is not allowed irrepective of security level