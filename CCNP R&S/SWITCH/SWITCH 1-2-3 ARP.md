#  SWITCH

1. it is Layer 2 device.
2. It is Full duplex Device.
3. Bydefault Single broadcast domain.
4.  Per-port collision Domain device.
5. Switch packet in the same network. (L2)
6. It is also known as Plug and Play,
7. We use ASIC chip on Switch.
8. It is also a centeral device.
9.  Switch can Flood traffic as Unicast, Multicast and Broadcast.
10. Switch first time do broadcast and after that always performe Unicasting.

## Switching is Three types

1. Layer 2 Switching

2. Layer 3 Switching

3. MPLS

## Process of Ethernet Switch

1. Address Learning
2. Filterning & Forwarding
3. Loop Avoidance
   1. Switch will check Source Mac address.
   2. Switch will check CAM table.
      *if information is available then it will refresh.
      *if it is not then it will creat entry in CAM
   3. Switch will check D-mac in L2 header.

4. Switch will check CAM table.
 5. Switch will find Exit Interface.