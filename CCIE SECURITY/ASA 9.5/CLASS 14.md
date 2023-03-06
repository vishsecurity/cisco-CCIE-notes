- Object-Group

2. HTTPs Access of ASA

3. Packet-tracer command

- Object-Group

   --> it is a feature on ASA which can be used to easily manage access-list.

- There are two way of creating access-list
  a. Creating access-list without object-group (Management difficult)
  b. Creating access-list with object-group (Management Easy)
  access-list OUT permit icmp host 192.168.1.1 host 192.168.2.1 echo
  access-list OUT permit tcp host 192.168.1.1 host 192.168.2.1 eq telnet

- Steps to configure ACL with object-group
  a. create object-group
  b. Create acl and call the object-group

  Create object-group to define IP address:

  - object-group network <name>

  - subnet

  - host

- There ave total 6 type of object-group

  a. object-group network ~~? specify IP address

  b. object-group service --> Specify TCP/UDP port numbers

  c. object-group protocol ~--> Specify Protocol

  d. object-group icmp --> Specify ICMP service

  e. object-group user --> Specify username information with ASA joined with AD
  f. object-group security ~~? Specify a Security Group tag (ISE)

- object-group network SRC-IP
  network-object host 192.168.1.1
  object-group network DEST-IP
  network-object host 192.168.2.1
  object-group service TCP-PORTS tcp
  port-object eq telnet
  access-list IN extended permit tcp object-group SRC-IP object-group DEST-IP object-group TCP-PORTS

- We can create object-group service in two ways:

  a. object-group service TcP-PORTS (tcp)

  b. object-group service TCP-PORTS

  - We can call object-group service either at the place of protocol or at the end of ACL where we
    call port number

- in real time, ASA is configured mainly via GUI as it is easy to configure ASA via
  Gul. 

- Steps to access ASA via HTTPS:
  - a. Make sure ASDM image is available in flash of ASA
    You can copy the ASDM image from tftp in the flash
    b. Tell ASA where ASDM image is located
    asdm image Hash:/asdm-713.bin
    c. Enable HTTPs service on ASA
    Attp server enable
    d. Create username and enable aaa authentication
    username admin password cisco privilege 15
    aaa authentication http console LOCAL
    e. Tell which IP to allow
        http 0 0 inside