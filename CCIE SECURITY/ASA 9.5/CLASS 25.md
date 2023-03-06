- what if HSRP --> backup
  Failover --> It is feature which is used to provide high availablity
  If one device goes down, then other device can take over its role.

- In Failover there will always two devices: one will act as primary and other will act as secondary
  One device will be active and other device will be standby
  Active --> The unit that passes the data traffic
  --> The unit which is active for data traffic
  Standby --> The unit that waits for active unit to fail and take over its role
  --> Data traffic never passes through standby unit

- Failover is of two types:
  a. Active/Standby
  b. Active/Active

- a. Active/Standby Failover

  --> In this one unit is active and other unit is standby

  --> Only one unit passes the data traftic (active unit)

  --> It is supported in single mode as well as in multiple mode
  --> Load Balancing 1s not supported in active/standby failover
  --> Preemption is not supported in active standby failover

  - Active/Active Failover

    --> In this both ASAs ave active for data traftic
    --> It is supported only in multiple mode

    --> Load Balancing is supported in this failover
    --> Preemption is supported

- Failover Requirement:

  --> Both ASA must be rdentical, Same model, Same RAM, Same number of interface

  --> Both ASAs must have same Software version, software version can be different only in case of Zero
  Downtime Upgrade.

  --> Both ASA must have same Mode (Single/Multiple) and Same Firewall type (Routed/Transparent)
  Failover Lan Interface

  It is a dedicated interface connected between both ASAs and is used for:

- This interface is used for:

  1. Active unit election
  2. Configuration Replication
  3.  Failover health monitoring
  4. Active IP and Active MAC replication

- To elect Active Unit, Both ASAs are configured with Failover LAN unit role

- Failover lan unit role:
  a. Primary
  b. Secondary

- No matter Whether we are configuring Active/Stanaby or
  Active/ active Failover, one ASA Is configured as Primary and
  Other ASA is configured as Secondary

- Failover lan unit vole --> Rrimary/Secondary
  Failover state --> Active/Standby

- During initial failover, both devices exchange failover lan unit role with each other, The ASA
  configured as Primary becomes Active 

- Configuration Replication
  --> Both ASAs must have identity configuration
  --> Configuration is replicated between both the ASAs via Failover LAN interface

- During initial failover (where active unit is not elected), All the configuration is replicated from
  primary unit to secondary unit.

- Once Active unit is elected, then configuration is replicated from active unit to standby unit.

-  Configuration is never replicated from standby to active, so we should never do any configuration

- Failover Health monitoring
  --> Both ASAs track each other's each by sending a hello/keepalive message periodically

- Active IP and Active MAC replication

