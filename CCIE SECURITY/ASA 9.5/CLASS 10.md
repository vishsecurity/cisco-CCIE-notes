- Remote Management of ASA:

  - Telnet
    b. SSH
    c. Static Route
    d. Connecting EVE router with PC
    e. HTTPs

  - Accessing ASA using Telnet

### TASK: Configure ASAZL so that R1 can telnet ASAL

1. Enable Telnet services on ASA
2. Tell which IP can access ASA via Telnet

1. enable Telnet service:

--> Set telnet password       How to set telnet password??

- passwa <telnet-pswd>
  password <telnet-pswd>

- by default, telnet password is set to "cisco"

2. Tell which IP can access ASA via Telnet

  - telnet <p> <mask> <nameif>

  - telnet 192.1468.4.4 255.255.255.255 inside

### Task2: Enable Telnet on ASAL and make sure any IP from any interface can telnet.
    telnet 0.0.0.0 0.0.0.0 inside
    telnet 0.0.0.0 0.0.0.0 dmz
    telnet 0.0.0.0 0.0.0.0 outside

- limitation:
  1. If more than one security level is configured, then telnet is not allowed from lowest security
     level
  2. if only one security level is confiqured, then it must be 100

### TASK. Make sure telnet sessions are authenticated via LOCAL database.

- aaa authentication telnet console LOCAL
  username cisco password cisco

### How to locally check telnet sessions on ASA

- who

### How to terminate telnet sessions locally:
  - kill
  - By default, idle timeout for telnet session is 5 minutes.
        -  If we want to change telnet idle timeout --> telnet timeout < >
      
### TASK: Enable SSH on ASA1  and make sure any user from inside network can SSH.

1. Enable SSH service on ASA
2. Tell which IP can SSH
3. Enable SSH service on ASA
  1. Generate crypto key --> by default, a crypto key is generated on ASA
  2.  username/password
  3. aaa authentication list for SSH

    - aaa authentication ssh console LOCAL
      ssh O O inside

### TASK: Create a loopback on R1 with IP 1.1.1.1/32 and make sure this IP is reachable from ASA

### TASK: Add a default route on ASA pointing towards outside interface

- route outside O O 192.168.3.4
- ASA supports all routing protocol, but with limited and required features of routing protocol

