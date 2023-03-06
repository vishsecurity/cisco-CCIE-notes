# How ASA determines Egress Interface Traceroute

## How router determines Egress interface for a packet???

## How ASA determines Egress Interface???

a. Routing table
b. Xlate table (only in case of UN-NAT)
c. if there is connection table and packet is inspected, then there will be no check for egress interface (FAST PATH)


- is it possible to use routing table even if the packet is untranslated??
  --> yes, but only if the nat is identity nat

## TRACEROUTE

 ## what is traceroute???
  --> it specify the path followed by a packet from a source to a destination.

## TRACEROUTE uses:

- UDP port range 33434 to 33534 (100 ports)

- IP TTL field

- ICMP time-exceeded

- ICMP port unreachable

## scenario 1

  1. R1 will send 3 UDP packets with des port 33434, 33435, 33436
     with TTL 2 TTL 1

  2. R2 will drop the packet as TTL value is 2 and it will also tell the intiator
     about the same by sending ICMP time-exceeded message (TTL expire)

  3. R1 will add the IP of R2 in its traceroute output and then again send 3 UDP message with next 3
     ports with TTL value 2

  4. R3 will drop the packet as TTL is expired and it will tell the same to
     initiator by sending ICMP time exceeded Message.

  5. R1 will add the R3 ip in its traceroute output and then send 3 next UDP message with next 3
     UDP ports
     
     
## scenario 2

   1. R4. will process the packet and then drop the packet as
        the packet that can be recieved by R4 is with UDP port
        33434 to 33534
    
   2. R4 will also tell the initiator that packet is dropped
        because the requested port number is not reachable
        upon recieving ICMP port unreachable message, initiator will add the IP in traceroute output and stop the traceroute.
       Traceroute working for windows and unix device is different

##  UNIX device

a.  UDR With increamentea TTL
b.  ICMP time exceeded
c. ICMP port unreachable

## windows device

a. ICMP echo request with increamented TTL
b.  ICMP time exceeded
c. ICMP echo reply

## TASK: Configure ASA1 so that R1 can traceroute R4.

NOTE: Any ACL added should be host specific.

## TASK: Configure ASAZ so that any inside user can traceroute any outside IP address

```
access-list OUT permit icmp any any unreachable
access-list OUT permit icmp any any time-exceeded
```

## TASK: Configure ASAZ so that any windows user can traceroute any outside IP address.
MAke sure ICMP inspection is enabled