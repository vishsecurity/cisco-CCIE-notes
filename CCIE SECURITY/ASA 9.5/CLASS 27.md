# Stateful Failover:
--> Configuration as well as connection information is replicated

- Connection information such as :
  a. TCP connection

  b. UDP connection

  c. ICMP connection

  d. Xlate entries

  e. ARP table

  f. Http connection (if http replication is enabled)
  If we want to configure stateful failover, then we need one more interface which is known as Failover link interface
  Failover Link --> It is an interface which is used for connection replication
  a. We can either use Failover lan interface as failover link interface

  b. We can use a dedicated interface for failover link (stateful)

- Connection information which is not replicated:

a. HTTP connection (if http replication not enabled)
b. DHCP lease address
c. Multicast Routing

```
failover lan unit primary
failover lan interface Fover E2
failover interface ip Fover 7.7.400,100 255.255.255.0 st 7.7.400,4014
failover link Fover

failover lan unit primary
failover lan interface Fover E2
failover interface ip Fover 7.7.100.100 255.255.255.0 st 7.7.400.4014
Failover link STATEFUL EZ
fatlover interface ip STATEFUL 7.7.14014.100 255.255.255.0 St 7.7.404,4014

```

## TASK: Configure ASAZ in multiple mode as follows:

a. Create two security context C1 and C2

b. Allocate EO, E2 with C1 and E1,E3 with C2

c. configure IP address on C1 and C2 as per diagram.

d. Make sure Dynamic PAT and icmp inspection is enabled.

## TASK2: Configure Active/Standby Failover between ASA1 and ASA2 as follows:
a. Use E4 as Failover LAN-LINK Interface with nameif FOVER.
b. Use active IP 7.7.100.100 and standby IP 7.7.100.101 on E4. interface.

