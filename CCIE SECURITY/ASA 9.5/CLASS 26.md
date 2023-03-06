# Active/Standby Failover

Whenever we configure failover, there are two types of devices: one is active and other is standby.
Whenever we configure failover, there ave two IP addresses configured on each interface: one is active IP
and other is standby IP.

Which ever ASA becomes Active takes the active IP and standby Device takes the standby IP address
Standby IP is required for Failover Health Monitoring.

If we do not configure Standby IP, failover will work but failover health monitoring will not work.

No matter whether we configure a regular interface or failover lan interface, we shoula configure
standby IP address for each interface.

Configuring standby IP for data interface is optional, but for Lan interface is mandatory

## TASK: Configure active/standby failover between ASA1 and ASA3 as follows:

a. ASA1 should be Primary

b. Use E2 as failover lan interface with nameif "FOVER"

c. Active IP on E2 should be 7.7.100.100 and standby IP should be 7.7.100.101

- failover  lan unit --> Specify failover lan unit role --> primary or secondary

- failover lan interface ~~” Specity which interface should be used as failover lan interface
  --> as well as we specify the nameif of that interface

- failover interface ip --> specify IP address for failover lan interface

```
fallover lan unit primary  
failover lan interface FOVER Ethernet2 , 
failover interface jp FOVER 7.7.100,100 255.255.255.0 standby 7.7.400,4014

failover lan interface FOVER Ethernet2  
failover interface jp FOVER 7.7.100,100 255.255.255.0 standby 7.7.400,4024
```

failover --> to enable the failover

## TASK: Configure IP address on ASAZ as per diagram.
Make sure Dynamic PAT is configured and icmp inspection is enabled.

## TASK2: Configure failover between ASAL and ASA2 as follows:
a. Use E2 as failover lan interface with nameif "FOVER"

b. Active IP should be 7.7.100.400 and standby should be 7.7.400.1014

Stateless Failover --> Only configuration replication
Stateful Failover --> Configuration as well as connection replication