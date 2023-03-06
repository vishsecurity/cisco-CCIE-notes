# ASA 8.4

```
interface Vlan1

 nameif inside
 security-level 100
 ip address 192.168.10.1 255.255.255.0
!
interface Vlan2
 nameif outside
 security-level 2
 ip address 209.165.200.253 255.255.255.0
!
interface Vlan3
 no forward interface Vlan 1
 nameif dmz
 security-level 70
 ip address 192.168.20.1 255.255.255.0

HQ-ASA(config)#int e0/1
HQ-ASA(config-if)#sw
HQ-ASA(config-if)#switchport acc
HQ-ASA(config-if)#switchport access vlan 1
HQ-ASA(config-if)#
HQ-ASA(config-if)#int e0/0
HQ-ASA(config-if)#sw
HQ-ASA(config-if)#switchport acc
HQ-ASA(config-if)#switchport access vlan 2


HQ-ASA(config)#dhcp  address 192.168.10.25-192.168.10.25 inside
HQ-ASA(config)#dhcp   dns 192.168.10.10 
HQ-ASA(config)#dhcp option 3 ip 192.168.10.1
HQ-ASA(config)#dhcp enable inside


ciscoasa(config)#ntp authentication-key 1 md5 corpkey
ciscoasa(config)#ntp server 192.168.10.10 key 1


HQ-ASA(config)#aaa authentication ssh console local
HQ-ASA(config)#crypto key generate rsa modulus 1024
WARNING: You have a RSA keypair already defined named <Default-RSA-Key>.
Do you really want to replace them? [yes/no]: yes
Keypair generation process begin. Please wait...

HQ-ASA(config)#ssh 192.168.10.5 255.255.255.255 inside
HQ-ASA(config)#ssh timeout 20


HQ-ASA(config)#object network inside-nat
HQ-ASA(config-network-object)#subnet 192.168.10.0 255.255.255.0
HQ-ASA(config-network-object)#nat (inside,outside) dynamic interface 


HQ-ASA(config-network-object)#object network dmz-dns-server
HQ-ASA(config-network-object)#host 192.168.20.5
HQ-ASA(config-network-object)#nat (dmz,outside) static 209.165.200.242

HQ-ASA(config-network-object)#object network dmz-web-server
HQ-ASA(config-network-object)#host 192.168.20.2
HQ-ASA(config-network-object)#nat (dmz,outside) static 209.165.200.241


HQ-ASA#sh nat
Auto NAT Policies (Section 2)
1 (dmz) to (outside) source static dmz-dns-server 209.165.200.242
    translate_hits = 0, untranslate_hits = 0
2 (dmz) to (outside) source static dmz-web-server 209.165.200.241
    translate_hits = 0, untranslate_hits = 0
3 (inside) to (outside) source dynamic inside-nat interface
    translate_hits = 0, untranslate_hits = 0

HQ-ASA(config)#class-map inspection_default
HQ-ASA(config-cmap)#match default-inspection-traffic
HQ-ASA(config-cmap)#policy-map globla_policy
HQ-ASA(config-pmap)#class inspection_default
HQ-ASA(config-pmap-c)#inspect dns
HQ-ASA(config-pmap-c)#inspect ftp
HQ-ASA(config-pmap-c)#inspect http
HQ-ASA(config-pmap-c)#inspect icmp


HQ-ASA(config)#service-policy globla_policy global

HQ-ASA(config)#access-list OUTSIDE-TO-DMZ extended permit tcp any host 209.165.200.241 eq 80
HQ-ASA(config)#access-list OUTSIDE-TO-DMZ extended permit tcp any host 209.165.200.242 eq 53
HQ-ASA(config)#access-list OUTSIDE-TO-DMZ extended permit tcp  host  172.16.40.10 host 209.165.200.241 eq 21 
HQ-ASA(config)#access-group OUTSIDE-TO-DMZ in interface outside



HQ(config)#access-list 110 permit ip 209.165.200.240 0.0.0.15 172.16.40.0 0.0.0.255

HQ(config)#crypto isakmp  policy 10
HQ(config-isakmp)#encryption aes 256
HQ(config-isakmp)#hash sha
HQ(config-isakmp)#authentication pre-share
HQ(config-isakmp)#authentication pre-share
HQ(config-isakmp)#group 5
HQ(config-isakmp)#lifetime 86400


HQ(config)#crypto isakmp key cisco address 172.16.20.2
HQ(config)#crypto ipsec transform-set VPN-SET esp-aes 256 esp-sha-hmac
HQ(config)#crypto map VPN-MAP 10 ipsec-isakmp
HQ(config-crypto-map)#set peer  172.16.20.2
HQ(config-crypto-map)#set pfs group5
HQ(config-crypto-map)#set security-association lifetime seconds 86400
HQ(config-crypto-map)#set transform-set VPN-SET
HQ(config-crypto-map)#match address 110


HQ(config)#int s0/0/0
HQ(config-if)#cr
HQ(config-if)#crypto map VPN-MAP

Branch(config)#access-list 110 permit ip 172.16.40.0 0.0.0.255 209.165.200.240 0.0.0.15
Branch(config)#crypto isakmp policy 10
Branch(config-isakmp)#encryption aes

Branch(config)#crypto isakmp policy 10
Branch(config-isakmp)#encryption aes 256
Branch(config-isakmp)#hash sha
Branch(config-isakmp)#authentication pre-share
Branch(config-isakmp)#group 5
Branch(config-isakmp)#lifetime 86400

Branch(config)#crypto isakmp key cisco address 10.1.1.1
Branch(config)#crypto ipsec transform-set VPN_SET esp-aes 256 esp-sha-hm

Branch(config)#crypto map VPN-MAP 10 ipsec-isakmp 
% NOTE: This new crypto map will remain disabled until a peer
        and a valid access list have been configured.
Branch(config-crypto-map)#set peer 10.1.1.1
Branch(config-crypto-map)#set pfs group5
Branch(config-crypto-map)#set security-association lifetime seconds 86400


Branch(config-crypto-map)#set transform-set VPN-SET
Branch(config-crypto-map)#match address 110

Branch(config)#int s0/0/0
Branch(config-if)#crypto map VPN-MAP

```

