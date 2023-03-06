- commands

```
 int f0/1
 switchport mode access 
 switchport port-security maximum  4
 switchport port-security violation shutdown 
 storm-control broadcast level 10 
 spanning-tree portfast 
 spanning-tree bpduguard enable  
```



 ## SPAN

1. SPAN Stands for Switchport Analyzer.
2. It is also called port mirroring.
3. to analyz network traffic passing through port by using SPAN.
4. It will send a copy to the traffic to another port on the switch.
5. SPAN moniters received or sent (both) traffic on the one or more source port to a destinatio
   port for analysis. 
6. Only traffic that is entered or leaves source ports can be monitered.

## Source port characterstics
1. It can be any port type (ethernet, fastethernet, gigaethernet)
2. It can't be a destination port at same time.
3. each source port can be configured with a direction (ingress, egress, both)
4. for etherchannel source, the monitered direction would apply to all the physical port in the
group.
5. Source port can be in same or different vlan.
6. We can configure a trunk port as a source port, all vians active on the trunk are monitered.

## Desination Port charactersics
1. It can be any ethernet physical port.
2. It can't be a source port at same time.
3. It can't be an etherchannel group or a vian.
4. it can be physical port that is assign to an etherchanel group, the port will be removed from the group while it is
configured as a span destination port.
5. the port does not transmit any traffic except the required for SPAN session.
6. When it is a destination port, it does'nt participate in any of the layer2 protocols (STP, VTP, DTP, CDP, PAGP, LACP).
7. no address learning occurs on the destination port.

## LOCAL SPAN
- REMOTE SPAN
  - Remote SPAN/RSPAN
    If source and destination ports are on different switches in this scanario we use RSPAN.
- LOCAL SPAN
  - Source and Destination port are on a same single switch that is called local span.