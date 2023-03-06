Section 1 NAT --> Manual NAT
Section 2 NAT --> Auto NAT (object network NAT)

- Normal NAT --> Section 2 --> NAT order will be automatically maintained.
- Sectiont NAT --> Conditional NAT
                            If we want to priovitize a specific NAT rule
- In normal NAT, there are two IP address one is Real Source IP and One is Mapped Source IP

### task : remove default route from r1 and r3 if any .configure nat  on asa1 so that r1 can ping r3 or vice versa

-  Mapped Source 101,.4.4.24.
  Real Destination LO4..d.,4..4. Mapped Dest 192,168,411.

- object network REAL-SOURCE
  host 192.168.1.1

- object network MAPPED-SOURCE
  host 101.1.1.1

- object network REAL-DESTINATION
  host 101.1.1.1

- object network MAPPED-DESTINATION
  host 192.168.1.1

- nat (inside,outside) source static REAL-SOURCE MAPPED-SOURCE destination static MAPPED-DESTINATION REAL-DESTINATION

### TASK: Translate R14 IP into 101.1.1.11 if Rt tries to access R3 IP.

- Real Source --> 192.168.1.1
- Mapped Source --> 101.1.1.414
- Real Destination --> 101.1.1.1
- Mapped Destination --> 101.1.1.1

#### TASK USING MANUAL NAT

- a. Configure dynamic PAT on ASA. so that all inside users ave translated with outside interface ip address
- b. Translate IP 192.468.1.1 into 101.1.1.11 if destination IP is 101.1.1.1
- c. Do not perform translation if IP 192.168.1.1 access outside IP 102.1.1.4
