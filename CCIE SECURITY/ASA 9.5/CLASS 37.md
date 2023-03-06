# MPF

a. Protocol inspection
b. ttl decreament
c. tcp sequence number randomization disable
d. TCP option control

## Class-map can be of two types:

1. Match-Any

2. Match-All
- Match Any
  --> If class map has multiple match entry
  --> class map will be used if traffic matches with any of the entry

## class-map CMAP

a. TCP Match-all
b. UDP - --> Traffic must match with all the entries of class-map
c. ICMP --> normally, we have only one entry in this type of class-map

## TASK: Configure ASAZ so that only 2 concurrent telnet session are allowed through firewall from outside interface.

- class-map --> telnet
- policy-map --> 2 connection
- service-policy
- conn-max
- per-client-max
  x embroynic-max --> maximum half open connection
  x per-client-embryonic-max

## TASK: Configure TCP idle timeout on ASA to 30 minutes.

```
timeout conn 30
```

## TASK: Configure idle timeout of Telnet connection to be 30 minutes and make sure for any other TCP

- connection idle timeout is 4 hour
- class-map --> telnet
- policy-map
- set connection timeout idle 30