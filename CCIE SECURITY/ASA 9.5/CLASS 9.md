### what is DMZ 

### Default Behavior

### How to set enable password

### Show commands and clear commands

- De-Militivized Zone: --> it s a zone where inside servers are placed which are accessible from internet.
  We put Public server in a different zone so that if there is any kind of attack on the server, tt would not
  impact the inside network

- Default Behavior of ASA:

  - Higher security level to lower security level --> all traffic allowed

  - Lower Security Level to higher security level --> all traffic denied

  - Same Security level --> all traffic denied by default

  - TCP and UDP traffic --> inspected by default, There is an excemption for TCP and UDP reply traffic

  - we can allow same security level traffic by using these commands:

  - same-security-traffic permit inter-interface
    --> if two different physical interface have same security level

  - same-security-traffic permit intra-interface
    --> if two sub-interface of same physical interface

    ### How to set enable password on ASA?

    - enable password cisco123
    - By default, enable password is not set.
      ASA always asks for enable password 

   ### How to remove enable password?

    - a. no enable password
    - enable password
    -  clear configure enable

  - You can run any privilege exec command from global configuration mode without using
    "do" keyword

### How to check ip address on asa interface  

    - show interface ip brief

### How to check nameif and security level 

    - Show nameif

- complete running-clg : show run
- check run cfg only for interface : show run interface
- check run cfg for nameif of interface : show run interface
- check run cfg for a Particular interface : show run interface gi0/o

### How to clear Configuration

- to clear all configuration : clear configure all
- to clear run clg of all interfaces : clear configure interface
- to clear run cl of a particular interface : clear configure interface gi 0/0
- clear namerf from run cg :  inter Gi O/O / no nameif

- Remote management of ASA
  - There are two things we need to configure to enable any remote
    management service:
    a. Enable the service
    b. Tell which IP can access that service

