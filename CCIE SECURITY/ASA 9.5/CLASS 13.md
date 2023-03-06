## questionsCan we ping the opposite interface of ASA 

### Can we ACL to control telnet traffic to the device 

### Can we inspect icmp protocol or not 

### ASA maintains connection table only for TCP and UDP or what?? 

### Can we delete connection table manually?? 

### If firewall maintains connection table, is there any idle timeout, if yes???

- Connecting EVE router with PC
- HTTPs access of ASA.

- We cannot ping opposite interface of ASA as it is denied by default. It is denied because of security reasons.

- Is there any way by which we can ping opposite interface of ASA???
  --> yes, if we configure a site to site VPN to secure ICMP traffic

- Can we use ACL to control telnet traffic to the device.

  - Whenever we apply any ACL on interface of ASA, that ACL will work for data traffic.
    ACL applied on the interface of ASA will not work for to the device traffic.

    - if we want to control to the device icmp traffic, we can use ICMP keyword
      ar to control the icmp traffic.

    - There is an implicit deny at the end of icmp statement same as of ACL.

### TASK: configure ASA so that R1 should not be able to ping ASA, Every other ICMP traffic should be   allowed.

- Can we apply ACL for to the dev ice on ASA??
  - --> yes we can apply, by using "control-plane"
  -  Telnet
  - ssh
  -   IcmP
  - we can inspect icmp traffic on the ASA
    - ASA maintains connection table only for TCP and UDP or what??
      - ASA maintain connection table for every packet no matter whether it is TCP,UDP, ICMP,GRE, OSPF, EIGRP or any IP protocol
      - No matter whether packet is for to the device ov through the device, ASA maintains connection table
      - it does not mean that all the packets are inspected. Only TCP and UDP traffic is inspected

