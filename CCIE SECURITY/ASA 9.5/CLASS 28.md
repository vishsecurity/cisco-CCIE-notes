# Active/Standby Failover in Multiple Mode
Active/Active Failover

--> Both the ASAs ave active.

--> Failover works mainly on security context level on Physical ASA level
--> Preemption is supported, ana fey cate Toa)

--> Load Balancing ts supported as both ASAs forward the data trakhic

- TO compiguire active/active Failover, Failover groups are Used,
  We bind security context with failover group as per requirement

--> There can be two failover group --> Group and Group2

--> one group is configured as primary and other group is configured as
secondary

--> Group configured as primary will be active on primary unit

--> Group configured as secondary will be active on secondary unit



## Step: Configuring failover group as primary and secondary
fallover group 4
primary

failover group 2
secondary

## Step2: Bind failover group with security context

```
 context c1
Join-failover-group 4
context c2
Join-failover-group 2
```

In active/active failover, both failover groups become active on Primary Unit at initial failover

1. Monitored Interface
--> by default, all the interfaces configured on ASA are monitored
--> Uf that interface fails, it can trigger failover
--> Sub-interfaces are not monitored by default
In Real time, which interfaces of ASA should be monitored???
--> all interface should be monitored

If We know that a particular interface of ASA is flapping, then We can remove that
interface From monitoring

2. Interface-Policy

--> At least how many monitored interface should fail on an ASA to trigger failover

by default interface policy is 1, which means even if one monitored interface fails, then failover will trigger
Failover Health Monitoring

a. Unit Health Monitoring --> Sending hello msgs from failover LAN interface

b. Interface HEalth Monitoring --> Sending hello msgs from Data interface

Running failover command on mate
Failover IPsec

## Unit Health Monitoring

--> Sending hello message trom Failover Lan INTERFACE to track health of other ASA
--> Hello message is periodically send and hello timer is 2 seconds and hold timer is 15 seconds
fatlover polltime unit
What if an ASA stops recieving hello message from LAN interface

2. if asa stops recieving hello message trom LAN interface but it 1s receiving hello msg trom data interface,
in that case failover will not trigger. Failover LAN interface will considered as failed
2. Uf asa stops recieving hello message from LAN interface as well as Data interface, then failover will trigger