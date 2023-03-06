## IPV6
- commands

  ```
  madrid(config)#int g0/0/0
  madrid(config-if)#ipv6 add 2001:db8:bcad::5/64
  madrid(config-if)#no sh
  
  madrid#sh cdp nei
  Capability Codes: R - Router, T - Trans Bridge, B - Source Route Bridge
                    S - Switch, H - Host, I - IGMP, r - Repeater, P - Phone
  Device ID    Local Intrfce   Holdtme    Capability   Platform    Port ID
  miami        Gig 0/0/0        157            R       ISR4300     Gig 0/0/0
  
  
  miami(config)#int g0/0/0
  miami(config-if)#ipv6 addre
  miami(config-if)#ipv6 address 2001:db8:bcad::5/64
  miami(config-if)#no sh
  miami(config-if)#
  %LINK-5-CHANGED: Interface GigabitEthernet0/0/0, changed state to up
  %LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/0, changed state to up
  
  miami#sh ipv6 int bri
  GigabitEthernet0/0/0       [up/up]
      FE80::240:BFF:FED0:5B01
      2001:DB8:BCAD::5
  GigabitEthernet0/0/1       [administratively down/down]
      unassigned
  GigabitEthernet0/0/2       [administratively down/down]
      unassigned
  Vlan1                      [administratively down/down]
      unassigned
  miami#
  
  ```

  

- 128 bit.

- hexadecimal.

- 8 fealds.

- every feald is 16 bits.

- every feald will seprate with :

- Broadcast is not available in IPV6.

- anycast is vailable in IPv6.

- 12A0:3298:6810:3802:1912:10D3:879C:1689/'
  
  - recistry/ 2 3
  - ISP Prefix / 32
  - Company / 48
  - subnet / 64
  
- Three types Unicast Addresses in IPV6

  1. Unique Local - (Private in IPV4)- FC00::/7
  2. Global Unicast - (Public in IPV4)- 2000::/3
  3. Link-Local - (as a APIPA in IPV4)- FE80::/10
  4. Multicast Address Range- ff00::/8
  5. Loopback- ::1
  
- ipv6 add autoconfig
  - RA-Router Advertisement
  - RS*Router Solicitation*
  - *NA’Neighbor Advertisement*
  - *NS*Neighbor Solicitation

In this post, we will touch base on the basic concepts of IPv6 addresses and networking.

## IPv6 Overview

IPv6 is intended as the replacement for the IPv4 network protocol. The major problem it solves is the exhaustion of IPv4 addresses by using a much larger network address space. It also provides a number of enhancements and new features for network conﬁguration management and support for future protocol changes.

The key reason IPv6 is not yet in wide deployment is that the core protocol does not have a simple way for systems that only have IPv6 addresses to communicate with systems that only have IPv4 addresses.

The best transition plan at present is to provide all hosts with both IPv4 and IPv6 addresses so that Internet resources only using one of the protocols can be reached from the host. This is called a dual-stack conﬁguration and is the approach on which this course will focus.

## Interpreting IPv6 Addresses

### IPv6 addresses

An IPv6 address is a 128-bit number, normally expressed as eight colon-separated groups of four hexadecimal nibbles (half-bytes). Each nibble represents four bits of the IPv6 address, so each group represents 16 bits of the IPv6 address.

\# 2001:0db8:0000:0010:0000:0000:0000:0001

To make it easier to write IPv6 addresses, leading zeros in a colon-separated group do not need to be written. However, at least one nibble must be written in each ﬁeld. Zeros which follow a nonzero nibble in the group do need to be written.

Since addresses with long strings of zeros are common, one or more groups of consecutive zeros may be combined with exactly one :: block.

Notice that under these rules, **2001:db8::0010:0:0:0:1** would be another less convenient way to write the example address. But it is a valid representation of the same address, and this can confuse administrators new to IPv6. Some tips for writing consistently readable addresses:

1.  Leading zeros in a group must always be suppressed.
2.  Use :: to shorten as much as possible. If two runs of zeros are equal in length, shorten the leftmost run of zeros by preference.
3.  Although it is allowed, do not use :: to shorten one group of zeros. Use :0: instead, and save :: for runs of zeros longer than a single group.
4.  Always use lowercase letters for hexadecimal numbers **a** through **f**.

**Note**: When including a TCP or UDP network port after an IPv6 address, always enclose the IPv6 address in square brackets so that the port does not look like it is part of the address-**\[2001:db8:0:10::1\]:80**

### IPv6 subnets

A normal unicast address is divided into two parts: the network preﬁx and interface ID. The network preﬁx identiﬁes the subnet. No two network interfaces on the same subnet can have the same interface ID; the interface ID identiﬁes a particular interface on the subnet.

Unlike IPv4, IPv6 has a standard subnet mask, which is used for almost all normal addresses, **/64**. In this case, half of the address is the network preﬁx and half of it is the interface ID. This means that a single subnet can hold as many hosts as necessary.

Typically, the network provider will allocate a shorter preﬁx to an organization, such as a **/48**. This leaves the rest of the network part for assigning subnets from that allocated preﬁx. For a /48 allocation, that leaves 16 bits for subnets (up to 65536 subnets).



IPV6 ADDRESS OR NETWORK

PURPOSE

DESCRIPTION

::1/128

localhost

The IPv6 equivalent to 127.0.0.1/8, set on the loopback interface.

::

The unspeciﬁed address

The IPv6 equivalent to 0.0.0.0. For a network service, this could indicate that it is listening on all conﬁgured IP addresses

::/0

The default route (the IPv6 Internet)

The IPv6 equivalent to 0.0.0.0/0. The default route in the routing table matches this network; the router for this network is where all trafﬁc is sent for which there is not a better route.

2000::/3

Global unicast addresses

Normal IPv6 addresses are currently being allocated from this space by IANA. This is equivalent to all the networks ranging from 2000::/16 through 3fff::/16.

fd00::/8

Unique local addresses (RFC 4193

IPv6 has no direct equivalent of RFC 1918 private address space, although this is close. A site can use these to self-allocate a private routable IP address space inside the organization, but these networks cannot be used on the global Internet. The site must randomly select a /48 from this space, but it can subnet the allocation into /64 networks normally.

fe80::/10

Link-local addresses

Every IPv6 interface automatically conﬁgures a link-local unicast address that only works on the local link on the fe80::/64 network. However, the entire fe80::/10 range is reserved for future use by the local link. This will be discussed in more detail later.

ff00::/8

Multicast

The IPv6 equivalent to 224.0.0.0/4. Multicast is used to transmit to multiple hosts at the same time, and is particularly important in IPv6 because it has no broadcast addresses

**Note**: The table above lists network address allocations that are reserved for speciﬁc purposes. These allocations may consist of many different networks. Remember that IPv6 networks allocated from the global unicast and link-local unicast spaces have a standard /64 subnet mask

### Link-local addresses

A link-local address in IPv6 is an unroutable address which is used only to talk to hosts on a speciﬁc network link. Every network interface on the system is automatically conﬁgured with a link-local address on the **fe80::/64** network. To ensure that it is unique, the interface ID of the linklocal address is constructed from the network interface’s Ethernet hardware address. The usual procedure to convert the 48-bit MAC address to a 64-bit interface ID is to invert bit 7 of the MAC address and insert ff:fe between its two middle bytes.

-   Network preﬁx: **fe80::/64**
-   MAC address: **00:11:22:aa:bb:cc**
-   Link-local address: **fe80::211:22ff:feaa:bbcc/64**

The link-local addresses of other machines can be used like normal addresses by other hosts on the same link. Since every link has a **fe80::/64** network on it, the routing table cannot be used to select the outbound interface correctly. The link to use when talking to a link-local address must be speciﬁed with a scope identiﬁer at the end of the address. The scope identiﬁer consists of % followed by the name of the network interface.  
For example, to use **ping6** to ping the link-local address **fe80::211:22ff:feaa:bbcc** using the link connected to the **eth0** network interface, the correct command would be:

$ ping6 fe80::211:22ff:feaa:bbcc%eth0

**Note**: Scope identiﬁers are only needed when contacting addresses that have “link” scope. Normal global addresses are used just like they are in IPv4, and select their outbound interfaces from the routing table.

### Multicast

Multicast plays a larger role in IPv6 than in IPv4 because there is no broadcast address in IPv6. One key multicast address in IPv6 is **ff02::1**, the all-nodes link-local address. Pinging this address will send trafﬁc to all nodes on the link. Link-scope multicast addresses (starting **ff02::/8**) need to be speciﬁed with a scope identiﬁer, just like a link-local address

$ ping6 ff02::1%eth0 
PING ff02::1%eth0(ff02::1) 56 data bytes 
64 bytes from fe80::211:22ff:feaa:bbcc: icmp\_seq=1 ttl=64 time=0.072 ms
64 bytes from fe80::200:aaff:fe33:2211: icmp\_seq=1 ttl=64 time=102 ms (DUP!)
64 bytes from fe80::bcd:efff:fea1:b2c3: icmp\_seq=1 ttl=64 time=103 ms (DUP!) 
64 bytes from fe80::211:22ff:feaa:bbcc: icmp\_seq=2 ttl=64 time=0.079 ms 

## IPv6 Address Configuration

IPv4 has two ways in which addresses get conﬁgured on network interfaces. Network addresses may be conﬁgured on interfaces manually by the administrator, or dynamically from the network using DHCP. IPv6 also supports manual conﬁguration, and two methods of dynamic conﬁguration, one of which is DHCPv6.

### Static addressing

Interface IDs for static IPv6 addresses can be selected at will, just like IPv4. In IPv4, there were two addresses on a network that could not be used, the lowest address in the subnet and the highest address in the subnet. In IPv6, the following interface IDs are reserved and cannot be used for a normal network address on a host.

-   The all-zeros identiﬁer 0000:0000:0000:0000 (“subnet router anycast”) used by all routers on the link. (For the 2001:db8::/64 network, this would be the address 2001:db8::.)
-   The identiﬁers fdff:ffff:ffff:ff80 through fdff:ffff:ffff:ffff

### DHCPv6 conﬁguration

DHCPv6 works a little differently than DHCP for IPv4, because there is no broadcast address. Essentially, a host sends a DHCPv6 request from its link-local address to port 547/UDP on **ff02::1:2,** the all-dhcp-servers link-local multicast group. The DHCPv6 server then usually sends a reply with appropriate information to port 546/UDP on the client’s link-local address.

### SLAAC Configuration

In addition to DHCPv6, IPv6 also supports a second dynamic conﬁguration method, called **Stateless Address Autoconﬁguration** (SLAAC). Using SLAAC, the host brings up its interface with a link-local **fe80::/64** address normally. It then sends a “router solicitation” to **ff02::2,** the all-routers linklocal multicast group. An IPv6 router on the local link responds to the host’s link-local address with a network preﬁx and possibly other information. The host then uses that network preﬁx with an interface ID that it normally constructs in the same way that link-local addresses are constructed. The router periodically sends multicast updates (“router advertisements”) to conﬁrm or update the information it provided.

**IMPORTANT** A typical Linux machine conﬁgured to get IPv4 addresses through DHCP is usually also conﬁgured to use SLAAC to get IPv6 addresses. This can result in machines unexpectedly obtaining IPv6 addresses when an IPv6 router is added to the network. Some IPv6 deployments combine SLAAC and DHCPv6, using SLAAC to only provide network address information and DHCPv6 to provide other information, such as which DNS servers and search domains to conﬁgure.
