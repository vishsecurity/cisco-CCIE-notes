## IPsec

- commands

  ```
  R1(config)#hostname GODZILLA
  GODZILLA(config)#int f0/0
  GODZILLA(config-if)#ip add 192.168.12.1 255.255.255.0
  GODZILLA(config-if)#no sh
  GODZILLA(config-if)#int l0 
  GODZILLA(config-if)#ip add 1.1.1.1 255.255.255.0
  
  GODZILLA(config-if)#router ospf 1
  GODZILLA(config-router)#network 0.0.0.0 255.255.255.255 area 0
  
  GODZILLA(config)#crypto isakmp policy 10
  GODZILLA(config-isakmp)# authentication pre-share
  GODZILLA(config-isakmp)# encryption aes 256
  GODZILLA(config-isakmp)# hash sha
  GODZILLA(config-isakmp)# group 5
  GODZILLA(config-isakmp)# lifetime 3600
  
  GODZILLA(config)# crypto isakmp key 0 VAULT address 192.168.23.3 
  GODZILLA(config)# crypto ipsec transform-set MYTRANS esp-aes 256 esp-sha-hmac 
  GODZILLA(config)# crypto ipsec security-association  lifetime seconds 1880  
  
  GODZILLA(config)# access-list 100 permit ip 1.1.1.0 0.0.0.255 3.3.3.0 0.0.0.255
  
  GODZILLA(config)# crypto map MYMAP 10 ipsec-isakmp
  GODZILLA(config)# match address 100
  GODZILLA(config)# set peer 192.168.23.3
  GODZILLA(config)# set pfs group5
  GODZILLA(config)# set transform-set MYTRANS
  GODZILLA(config)# set security-association lifetime seconds 9 00
  GODZILLA(config)#crypto map MYMAP
  
  
  R2(config)#hostname KINGKONG
  KINGKONG(config)#int f0/0
  KINGKONG(config-if)#no sh
  *Mar  1 00:02:49.751: %LINK-3-UPDOWN: Interface FastEthernet0/0, changed state to up
  *Mar  1 00:02:50.751: %LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/0, changed state to up
  KINGKONG(config-if)#ip add 192.168.12.2 255.255.255.0   
  
  KINGKONG(config)#router ospf 1
  KINGKONG(config-router)#network 0.0.0.0 255.255.255.255 area 0
  
  R3(config)#hostname NESSIE  
  NESSIE(config)#int f0/0
  NESSIE(config-if)#ip add 192.168.23.2 255.255.255.0
  NESSIE(config-if)#no sh
  *Mar  1 00:03:51.611: %LINK-3-UPDOWN: Interface FastEthernet0/0, changed state to up
  *Mar  1 00:03:52.611: %LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/0, changed state to up
  NESSIE(config-if)#int l0
  *Mar  1 00:04:37.511: %LINEPROTO-5-UPDOWN: Line protocol on Interface Loopback0, changed state to up
  NESSIE(config-if)#ip add 3.3.3.3 255.255.255.0
  
  NESSIE(config)#router ospf 1
  NESSIE(config-router)#network 0.0.0.0 255.255.255.255 area 0
  
  NESSIE(config)#crypto isakmp policy 10
  NESSIE(config-isakmp)# authentication pre-share
  NESSIE(config-isakmp)# encryption aes 256
  NESSIE(config-isakmp)# hash sha
  NESSIE(config-isakmp)# group 5
  NESSIE(config-isakmp)# lifetime 3600
  
  NESSIE(config)# crypto isakmp key 0 VAULT address 192.168.12.1
  NESSIE(config)# crypto ipsec transform-set MYTRANS esp-aes 256 esp-sha-hmac 
  NESSIE(config)# crypto ipsec security-association  lifetime seconds 1880  
  
  NESSIE(config)# access-list 100 permit ip 3.3.3.3 0.0.0.255 1.1.1.0 0.0.255
  
  NESSIE(config)# crypto map MYMAP 10 ipsec-isakmp
  NESSIE(config-crypto-map)#match address 100
  NESSIE(config-crypto-map)#set peer 192.168.12.1
  NESSIE(config-crypto-map)# set pfs group5
  NESSIE(config-crypto-map)#set transform-set MYTRANS
  NESSIE(config-crypto-map)#set security-association lifetime seconds 1800
  NESSIE(config)#crypto map MYMAP
  
  NESSIE#show crypto isakmp sa
  NESSIE#ping 1.1.1.1 source 3.3.3.3
  NESSIE#show crypto ipsec transform-set
  NESSIE#show crypto map
  NESSIE#show crypto ipsec sa 
  ```

1. Authentication Pre-Shared Key (PSK)

2. Integrity MDS. Banged ‘Hash Dincetiten (SHA) 

3.  encription:- Confidentiality ‘Data Encription Standard (DES). (3DES), Advances

4. Anti-Replay

   1. Authentication:-
      To check user is valid or not.
   2. Integrity:-
      to set Bits order same.
   3. Confidentiality:-
       will forward my data in encrypted form.
   4. Anti-Replay

5. In IPsec there are multiple protocols.
   1. ESP- Encapsulation Security Payload (Provide Encription & Authentication)
   2. AH - Authentication Header (Provide Only Authentication)

6. ISAKMP (Internet Security Association Key Management Protocol)
   IKEv1

   Phase 1: - SA

   Phase 2:- Negotiate

7. Main mode

   - in main mode 6 messages are available.
     MM1:- Hash algoridtham: MD5 or SHA
     Encription Algo: AES
     Authentication: Pre-share Key
     Diffi-hellman Group :
     Lifetime

8. Quick Mode

  - in Quick mode 3 messages are available.

9. MM1:- This is the first message that the initiator sends to a responder One or multiple SA's Proposals are offered.
   MM2:- This message is sent from responder to initiator with the SA's parposal that matched.
   MN3:- In this message the initiator start the DH key exchange. this is based on DH group the responder matches in parposal.
   MM4:- The responder sends its own key to initiator. nf
   MM5:- The initiator start authentication by sending the peer router its IP address.
   MM6:- The responder send back a similar packet and authenticates the session.

10. ISAKMP
    Internet Security Association Key Management Protocol.
    It is actual implementation on IPsec.
    “ISAKMP policy 10

    