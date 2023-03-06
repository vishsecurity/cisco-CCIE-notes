# Qos

- commands

  ```
  QoS is a very broad domain that cannot be covered in a single article. Cisco documentation about it is huge. It’s not enough to know the software features, but you need to know to which platforms are they applicable. Yes, the QoS features are very platform-dependent. Some features can be applied only to routers, some only to switches. And some can be different between members of the same family. For instance, not all QoS features available for Cisco 3560 are valid for Cisco 3550.
  
  The purpose of this article is to introduce you some of the platform-independent features. This will involve classification, congestion management, congestion avoidance, and policing.
  
  Check out this article for more information about QoS: Quality of Service: WAN.
  
  The topology used for this article and for simulation is below:
  
  The purpose of the lab is to show you how you can configure QoS and verify that it is applied correctly.
  
  You have been tasked to configure the following QoS policy:
  
      Assign to ICMP traffic the IP Precedence 1
      Assign to HTTP traffic the IP Precedence 3
      Assign to OSPF traffic the IP Precedence 7
      Police the ICMP traffic to maximum of 8Kbps
      Assign a bandwidth of 10Mbps for HTTP traffic
      Configure strict priority for OSPF traffic and allocate 1Mbps
      Leave all the other traffic in the default class-map
  
  At the beginning of the article, you will have a link from where you can download the GNS3 topology file and the devices configuration file.
  
  If you use these configuration files, make sure you adapt the path to the GNS3 files.
  
  Once the topology is loaded and all the devices are powered on, you will have to configure the three PCs with IP addresses and default gateway.
  
  There is one thing not shown on the diagram: R1, R2 and R3 are running OSPF protocol so that all the PCs can reach each other.
  
  This is the routing table of R2:
  
  R2#show ip route | begin Gateway
  Gateway of last resort is not set
  
       10.0.0.0/24 is subnetted, 5 subnets
  O       10.10.1.0 [110/3] via 10.10.23.3, 00:40:27, FastEthernet2/0
  C       10.10.2.0 is directly connected, FastEthernet0/0
  O       10.10.3.0 [110/2] via 10.10.23.3, 00:40:27, FastEthernet2/0
  O       10.10.13.0 [110/2] via 10.10.23.3, 00:40:27, FastEthernet2/0
  C       10.10.23.0 is directly connected, FastEthernet2/0
  R2#
  
  Once you start the hosts, you will need to configure the IP address on eth0 of each host and the default gateway pointing to the router to which they are connected, as shown on the diagram.
  
  Use “tc” as username to log in to the PCs without being asked for a password.
  
  This is needed on PC_2 to change the hostname, to add the right IP address on eth0, and to add the default route pointing to R2. Configure the other two PCs in a similar way:
  
  tc@box:~$ sudo hostname PC_2
  tc@PC_2:~$ sudo ifconfig eth0 10.10.2.100 netmask 255.255.255.0
  tc@PC_2:~$ sudo route add default gw 10.10.2.1 eth0
  
  You can paste this configuration on R1 to configure the class-maps, the access-lists, and the policy-maps and to apply them on the correct interfaces:
  
  R1#show running-config | section class-map
  class-map match-all OSPF
   match protocol ospf
  class-map match-all MATCH_HTTP
   match access-group 105
  class-map match-all ICMP_TO_CORE
   match  precedence 1
  class-map match-all HTTP_TO_CORE
   match  precedence 3
  class-map match-all MATCH_ICMP
   match access-group 101
  R1#show running-config | section policy-map
  policy-map FROM_HOST
   class MATCH_ICMP
    set precedence 1
   class MATCH_HTTP
    set precedence 3
  policy-map TO_CORE
   class ICMP_TO_CORE
    bandwidth 8
    police cir 8000
      conform-action transmit
      exceed-action drop
   class HTTP_TO_CORE
    bandwidth 10000
   class OSPF
    set precedence 7
    priority 1000
  R1#show  running-config | section access-list
  access-list 101 permit icmp any any
  access-list 101 remark "match icmp"
  access-list 105 remark "match http"
  access-list 105 permit tcp any any eq www
  R1#show running-config interface f0/0
  Building configuration...
  
  Current configuration : 126 bytes
  !
  interface FastEthernet0/0
   ip address 10.10.1.1 255.255.255.0
   duplex auto
   speed auto
   service-policy input FROM_HOST
  end
  
  R1#show running-config interface f2/0
  Building configuration...
  
  Current configuration : 126 bytes
  !
  interface FastEthernet2/0
   ip address 10.10.13.1 255.255.255.0
   duplex auto
   speed auto
   service-policy output TO_CORE
  end
  
  R1#
  
  The same access-lists, class-maps, and policy-maps have to be configured on R2 and R3. Just pay attention to the interfaces to which you assign the policy-maps and the direction.
  
  The TO_CORE policy-map should be applied on the output direction of an interface towards another router.
  
  The FROM_HOST policy-map should be applied on the input direction of an interface towards a PC.
  
  Let’s check if there were any ICMP or HTTP packets sent by PC_1. Observe that I’m checking the policy-map from f0/0, where the matching is done:
  
  R1#show policy-map interface f0/0
   FastEthernet0/0
  
    Service-policy input: FROM_HOST
  
      Class-map: MATCH_ICMP (match-all)
        0 packets, 0 bytes
        5 minute offered rate 0 bps, drop rate 0 bps
        Match: access-group 101
        QoS Set
          precedence 1
            Packets marked 0
  
      Class-map: MATCH_HTTP (match-all)
        0 packets, 0 bytes
        5 minute offered rate 0 bps, drop rate 0 bps
        Match: access-group 105
        QoS Set
          precedence 3
            Packets marked 0
  
      Class-map: class-default (match-any)
        3 packets, 981 bytes
        5 minute offered rate 0 bps, drop rate 0 bps
        Match: any
  R1#
  
  Let’s check the policy-map from interface f2/0 on R2. This policy-map should apply the bandwidth limits in case the traffic is go over the limit that we configured:
  
  R1#show policy-map interface f2/0
   FastEthernet2/0
  
    Service-policy output: TO_CORE
  
      Class-map: ICMP_TO_CORE (match-all)
        0 packets, 0 bytes
        5 minute offered rate 0 bps, drop rate 0 bps
        Match:  precedence 1
        Queueing
          Output Queue: Conversation 265
          Bandwidth 8 (kbps)Max Threshold 64 (packets)
          (pkts matched/bytes matched) 0/0
          (depth/total drops/no-buffer drops) 0/0/0
        police:
            cir 8000 bps, bc 1500 bytes
          conformed 0 packets, 0 bytes; actions:
            transmit
          exceeded 0 packets, 0 bytes; actions:
            drop
          conformed 0 bps, exceed 0 bps
  
      Class-map: HTTP_TO_CORE (match-all)
        0 packets, 0 bytes
        5 minute offered rate 0 bps, drop rate 0 bps
        Match:  precedence 3
        Queueing
          Output Queue: Conversation 266
          Bandwidth 10000 (kbps)Max Threshold 64 (packets)
          (pkts matched/bytes matched) 0/0
          (depth/total drops/no-buffer drops) 0/0/0
  
      Class-map: OSPF (match-all)
        16 packets, 1504 bytes
        5 minute offered rate 0 bps, drop rate 0 bps
        Match: protocol ospf
        QoS Set
          precedence 7
            Packets marked 16
        Queueing
          Strict Priority
          Output Queue: Conversation 264
          Bandwidth 1000 (kbps) Burst 25000 (Bytes)
          (pkts matched/bytes matched) 0/0
          (total drops/bytes drops) 0/0
  
      Class-map: class-default (match-any)
        20 packets, 2051 bytes
        5 minute offered rate 0 bps, drop rate 0 bps
        Match: any
  R1#
  
  As you can see, there were no ICMP or HTTP packets, but we matched the OSPF packets. Until now, there were 16 packets sent and we marked 16 with IP Precedence 7. As you can also see, “strict priority” was configured for OSPF traffic with a bandwidth of 1Mbps.
  
  Let’s simulate a HTTP request from R1 to R2. We will do a telnet on port 80 on R2. Because there is no actual HTTP server running on R2, the connection will be refused, but still the packet will be treated as a HTTP packet.
  
  tc@PC_1:~$ telnet 10.10.2.100 80
  telnet: can't connect to remote host (10.10.2.100): Connection refused
  tc@PC_1:~$
  
  Let’s check on R1 and see if we matched any HTTP packets and marked them with IP Precedence 3:
  
  R1#show policy-map interface f0/0 input class MATCH_HTTP
   FastEthernet0/0
  
    Service-policy input: FROM_HOST
  
      Class-map: MATCH_HTTP (match-all)
        1 packets, 74 bytes
        5 minute offered rate 0 bps, drop rate 0 bps
        Match: access-group 105
        QoS Set
          precedence 3
            Packets marked 1
  R1#
  
  As you can see, we matched one HTTP packet and we marked it with IP Precedence 3.
  
  We should see the same packet being matched and set by R3 on the out direction of interface f1/0:
  
  R3#show policy-map interface f1/0 output class HTTP_TO_CORE
   FastEthernet1/0
  
    Service-policy output: TO_CORE
  
      Class-map: HTTP_TO_CORE (match-all)
        1 packets, 74 bytes
        5 minute offered rate 0 bps, drop rate 0 bps
        Match:  precedence 3
        Queueing
          Output Queue: Conversation 266
          Bandwidth 10000 (kbps)Max Threshold 64 (packets)
          (pkts matched/bytes matched) 0/0
          (depth/total drops/no-buffer drops) 0/0/0
  R3#
  
  Because we are not sending at high rate and because there is no congestion, we will not reach the limit of 10Mbps assigned to HTTP traffic.
  
  We can test the policing using ICMP traffic and see how you can drop the packet when they reach the bandwidth limit assigned.
  
  Currently, ICMP traffic is policed at 8Kbps. Because the PCs cannot send more than one ICMP packet per second, we will not be able to hit the limit. However, we can use rapid ping from R1 and send ICMP packets with IP Precedence 1. We will get a reply only for few of the packets, because some of them will be dropped due to the police rate.
  
  Let’s start an extended ping from R1 towards R2 and see how many packets were dropped and how many were transmitted by R1 to R3 and then to R2.
  
  In the extended ping, you are asked to put the value of TOS for IP Precedence 1. This is 32(00100000).
  
  R1#ping
  Protocol [ip]:
  Target IP address: 10.10.23.2
  Repeat count [5]: 100
  Datagram size [100]: 1400
  Timeout in seconds [2]:
  Extended commands [n]: y
  Source address or interface: 10.10.13.1
  Type of service [0]: 32
  Set DF bit in IP header? [no]: yes
  Validate reply data? [no]:
  Data pattern [0xABCD]:
  Loose, Strict, Record, Timestamp, Verbose[none]:
  Sweep range of sizes [n]:
  Type escape sequence to abort.
  Sending 100, 1400-byte ICMP Echos to 10.10.23.2, timeout is 2 seconds:
  Packet sent with a source address of 10.10.13.1
  Packet sent with the DF bit set
  !.!.!.!.!.!.!.!.!.!.!.!.!.!.!.!.!.!.!.!.!.!.!.!.!.!.!.!.!.!.!.!.!.!.!.
  !.!.!.!.!.!.!.!.!.!.!.!.!.!.!.
  Success rate is 50 percent (50/100), round-trip min/avg/max = 60/111/284 ms
  R1#
  
  So let’s check what happened on R1:
  
  R1#show policy-map interface f2/0 output class ICMP_TO_CORE
   FastEthernet2/0
  
    Service-policy output: TO_CORE
  
      Class-map: ICMP_TO_CORE (match-all)
        100 packets, 141400 bytes
        5 minute offered rate 0 bps, drop rate 0 bps
        Match:  precedence 1
        Queueing
          Output Queue: Conversation 265
          Bandwidth 8 (kbps)Max Threshold 64 (packets)
          (pkts matched/bytes matched) 50/70700
          (depth/total drops/no-buffer drops) 0/0/0
        police:
            cir 8000 bps, bc 1500 bytes
          conformed 50 packets, 70700 bytes; actions:
            transmit
          exceeded 50 packets, 70700 bytes; actions:
            drop
          conformed 0 bps, exceed 0 bps
  R1#
  
  As you can see, 100 packets were supposed to be sent; 50 were conforming(meaning that they were transmitted) and 50 were exceeding. We configured this policy-map to drop any exceeding packets, hence the 50% packet loss. Half of the packets weren’t sent by R1 to R3.
  
  So let’s see how many packets R3 sent to R2:
  
  R3#show policy-map interface f2/0 output class ICMP_TO_CORE
   FastEthernet2/0
  
    Service-policy output: TO_CORE
  
      Class-map: ICMP_TO_CORE (match-all)
        50 packets, 70700 bytes
        5 minute offered rate 0 bps, drop rate 0 bps
        Match:  precedence 1
        Queueing
          Output Queue: Conversation 265
          Bandwidth 8 (kbps)Max Threshold 64 (packets)
          (pkts matched/bytes matched) 0/0
          (depth/total drops/no-buffer drops) 0/0/0
        police:
            cir 8000 bps, bc 1500 bytes
          conformed 50 packets, 70700 bytes; actions:
            transmit
          exceeded 0 packets, 0 bytes; actions:
            drop
          conformed 0 bps, exceed 0 bps
  R3#
  
  We fulfilled our goals: classify the ICMP, HTTP and OSPF traffic, assign a specific bandwidth to HTTP traffic, assign a strict priority bandwidth to OSPF, police the ICMP traffic.
  
  However, what you just saw is just a glimpse of what you can do on Cisco devices with regard to QoS.
  
  There are lot more features that you can configure, but this should be enough for you to prepare for CCNA exam.
  ```
  
  
