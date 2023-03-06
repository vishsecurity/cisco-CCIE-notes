## Static Route Tracking --> Service Level Agreement (SLA)

--> if one ISP goes down, then we can forward trafic trom another ISP
--> We are taking lease line from two different ISP so that if our primary ISP goes down, then
automatically traffic should start passing through another ISP
--> We are not taking two lease lines to perform load balancing

1. We cannot add two route for same destination with same AD value.

2. if we add a static route, route will not be removed from routing table even if the next
  hop is not reachable.
  Static Route Tracking
  --> It is a feature in which we track a static voute based on a destination IP address.
  if the destination IP 1s reachable, then static route is added in the routing table
  if the destination IP is not reachable, then static route 1s automatically removed from routing table.
  if we want to track a particular IP, then we should specify that which protocol
  will be used to track
  on ASA, ICMP echo request is used to track the IP

  Step1: Create sla monitor (to specify IP which should be track and protocol) sla monitor 123 type echo protocol iplempEcho 101.1.4.1 interface outside

  Step2: Schedule SLA monitor sla monitor schedule 123 start-time now life forever
  frequency --> after how much second device should send icmp echo request by default frequency is + minute.
  Step3: Create a track (to bind SLA) track 2 vtr 123 reachability
  Step4: Add static route and bind track with it route outside 0.0.0.0 0.0.0.0 104,441 4 track 1

  ## TASK: Configure SLA monitor on ASA1 so that if primary ISP goes down then default route from
  secondary ISP should be added in routing table within 1 second.
  TCP ping