# CCIE Security

- CCNA, CCNP, CCIE
  - ASA
  - VPN 
  - ISE
  - WSA
  - Firepower 
  - Wireless
  - Automation

### Router Security

- Types of traffic recieved by a router
  - To /from the device traffic
  - Through the device

### There can be two types of to the device traffic:

a. Traffic which is initiated by a user/admin
b. Traffic which is initiated by the device on its own

### Types of plane:

1) Management Plane
2) control Plane
3) Data Plane

1. Management Plane:

   --> Any traffic which is initiated by a user for management of a device for example:

   telnet, ssh, http , https

2. Control Plane:

   --> It includes any traffic  which is intiated by a device on its own without direct interaction
   with administrator

   --> for example: routing protocol!

3. Data Plane:

   --> it includes all the traffic which is passing through the device

### Network Foundation Protection: NFP

- All about breaking the infrastructure down into smaller components
- Systematically focus on how to secure each of those components
- Secure Management Plane
  1. Controlling Interactive Access
  2. Privilege level
  3. AAA
  4. Secure NTP
  5. Control who can access the device (IP)
  6. Enforce Password Policy

### what is interactive Access?

	--> It is a way by which we can take admin access of a device for its management purpose

2. Line con
   --> Only one user at a time can access the device

3. Line VTY

   --> Telnet and SSH

   --> it is  used to take remote access of the device

###  what is ARP

###  Explain Different types of ARP

### What commands do we need to run under line vty to enable any session:

​	a. Whether to accept the session or not under line vty
​	b. If session is accepted, then how to authenticate that session

​	a. Whether to accept the session or not under line vty

- transport input
  - transport input telnet
    -  only telnet session are accepted under line vty
 - transport input ssh
       -  only ssh sessions ave accepted under line vty

- transport input all 
- transport input telnet ssh
  - both telnet and ssh session accepeted under line vty 

- transport input noné 
  - no sessions accepted under line vty

- b. If session is accepted, then how to authenticate that session - Login

  - login --> device will always authenticate session using line vty password

  --> login local --> session 1s authenticated with local database
  --> no login --> no authentication at all
  --> no login related command --> authentication is done via AAA
