# Clustering
etherChannel --> A feature by which we can bundle multiple physical Interfaces of a device to make a logical interface 

##  Why Etherchannel???

--> Throughput Increase
--> Load Balancing

--> Interface Redundancy

## How many interfaces can we bundle in EtherChannels:
--> Upto 16 interfaces
--> Upto 16 interfaces
Clustering
--> it is a feature by which we can bundle multiple physical ASAs together to make a single logical ASA
This feature provides:

a. Scalability (Throughput Inrcease, Loadbalancing)

b. High Availablity

--> It is mainly used in data centers

We can bundle upto 16 ASAs depending on the ASA model

## Performance Scaling Factor
When you combine multiple units into a cluster, you can expect a performance of approximately:

* 70% of the combined throughput
* 60% of maximum connections
+ 50% of connections per second
  For example, for throughput, the ASA 5585-X with SSP-40 can handle approximately 10 Gbps of real world
  firewall traffic when running alone. For a cluster of 8 units, the maximum combined throughput will be
  approximately 70% of 80 Gbps (8 units x 10 Gbps): 56 Gbps.

  If we bundle 5 ASAs, then how many ASA will be active to forward data traffic
  --> all & ASASs will be active
  There is no concept of active/standby, All the ASAs are active for data traffic
  Cluster Unit Roles:

1. Master --> Only one unit can be master. Master unit is elected to do centralized configuration
--> Configuration from Master unit is automatically replicated to all other slave unit

--> Master unit does not decide that data traftic should be forwarded trom which firewall

2. Slave

--> Any other ASA in cluster group other than Master unit Is slave.

--> We cannot do any configuration on Slave unit.

--> Configuration is replicated to slave unit from Master unit.

## Cluster Requirement

--> All ASAs must be identical
--> Same Software version and hardware mode
--> Same firewall type and Same Firewall Mode

## Cluster Control Link (CCL)
--> It is a dedicated interface by which all the ASAs are directly connected to each other and it 1s used for:
a. Master unit election
a 4. Configuration Replication
c. Connection Replication
a. Cluster Health Monitoring
e. Connection Ownership Query
Master Election Criteria

--> To elect Master unit, Cluster priority is configured on all the ASAs
==> ASA with Highest Cluster priority becomes Master Unit.

## Cluster Priovity

--> It is number ranging from 1 to 100.

--> Lower the number higher is the cluster priority.

--> by default, there 's no cluster priority, it is manually configured.
in a case if cluster priovity is same, then ASA with lowest Cluster —_ |unit name becomes Master

## Cluster unit name:
--> It is a logical name which is configured on each firewall as a part of Cluster configuration.
--> This name is used to represent ASA in cluster group

if same cluster unit name, then ASA with lowest serial number become:
the Master
There is no preemption in Clustering

1. ASA enabled with clustering sends Cluster hello message from it CCL every 3 seconds
Cluster hello message will include:

a. Cluster priority

b. Cluster unit name

c. Serial Number
2. If ASA does not recieve any cluster hello message with higher cluster priority within 45 seconds
then that ASA will become Master

3. If ASA with Higher cluster priority later joins the cluster group, it will join as Slave.

## In case if current Master fails, then this ASA will become Master

Cluster Deployment Modes:

a. Spanned EtherChannel Mode

b. Individual Interface Mode