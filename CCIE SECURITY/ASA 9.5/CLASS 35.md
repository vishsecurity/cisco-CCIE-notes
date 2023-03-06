# Modular Policy Framework

--> It is a feature by which we can take advanced action other than permit or deny on a packet.

a. inspection of any protocol which is not inspected by default
b. Decreament TTL in IP packet
  -  by default ASA does not decreament TTL for any packet passing through it becuase of security reasons
c.  ASA randomizes the TCP sequence number for any TCP packet passing through It.
  - To prevent TCP Sequence number based attack
d.  Can take action based on connections
--> Maximum connection 
--> Max Half Open connection 
--> MAX connections per second
e. Quality of Service
f. inspection of protocol that changes the port dynamically
g. Application inspection (not recommended)


## whenever we create an ACL, there are three thing which we specify:

a. Identify the traffic
b. what action to be take
c. Where/when to take action
```
access-list OUT permit icmp any any
access-group OUT in interface outside

```

## Components of MPF:

a. Class-map --> identify the traffic
b. Policy-map --> Take action on Class-map
c. Service-Policy --> Apply policy-map on interface or globally

## Class-map
--> it s used only for traffic identification
--> 1t cannot be used to take action

## Class-map can of two types:

a. LB Class-map
--> Can identify trattic based on L3 and L4 information
```
class-map <name>
```

b. L7 Class-map
--> To fdentify traffic based on Layer 7

```
class-map type inspect http <name>
```

2. Policy-map

--> It is used to take action on class-map
--> We can call multiple class-map in a single policy-map
```
policy-map <name>
```

## TASK: Configure ASA to inspect icmp protocol on inside interface
Class-map --> icmp
policy-map --> inspect
service-policy --> interface inside

### 1st way

1. create acl and call icmp traffic
2. Create class-map and call acl

```
access-list ICMP-ACL permit icmp any any
class-map ICMP
match access-list CMP-ACL
```

3. Create policy-map and call class-map
4. Apply policy-map on interface
```
policy-map PMAP
class (CMP
inspect icmp
service-policy PMAP interface inside
```

### 1st way

1. create acl and call icmp traffic
2. Create class-map and call acl


```
access-list ICMP-ACL permit icmp any any
class-map ICMP
match access-list ICMP-ACL
```

### 2 way

```
class-map ICMP
match any
```
### third way

```
class-map ICMP
match default-inspection-trattic
```

### TASK2: Configure ICMP inspection on ASA if R14 pings R3.