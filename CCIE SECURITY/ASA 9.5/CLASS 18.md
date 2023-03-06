- Dynamic NAT : There ave three ways be which we can configure NAT on ASA
- Dynamic PAT :  NAT on ASA is divided in three sections:
- Static NAT  : a. Section2. --> Manual NAT
- Static PAT : b. Section2 --> Auto NAT (object network NAT)
- Identity NAT : c. Section3 --> Manual NAT with "after-auto"

### conditional nat 

- translating source ip address based on a condition(destination ip)

- Auto NAT (object network NAT)
  -> NAT Is always configured under real IP object without "source" keyword
  --> NAT order is automatically maintained by ASA (static rule ave preferred over dynamic)
  --> Conditional NAT is not supported
- Manual NAT
  --> NAT is configured from global configuration mode
  --> NAT is always configured with "source" keyword
  --> Nat order is not automatically maintained, Admin must must the nat order manually
  --> Conditional NAT is supported

### TASK: Configure Dynamic NAT on ASA2. to translate all inside users with outside IP vange (101.1.1.11 to 101.1,1.13).

- if real ip is "any" ip,then creating object for real ip is optional
- if mapped ip is "interface" ip ,  only in that case we cannot use object .for any other mapped ip creating object is mandatory

### TASK: Configure Dynamic PAT on ASA to translate all inside users with outside interface IP address

- Real ip --> any
- Mapped IP --> interface

### TASK : configure dynamic pat on asa1 to translate all  inside and dmz ip with outside interface ip. 

- note : you are allowed to configure only one rule 

### TASK: Configure NAT on ASAZ so that Telnet services of R2 is statically port mapped with telnet services of outside interface.

- Real IP --> 192.168.2.4
- Real Port ~~? telnet
- Mapped IP ~~” interface
- Mapped Port ~~? telnet