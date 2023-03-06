- Resource Management in multiple Mode
- Hiding interface number in security context
- Remote Management of Security Context and System Configuration Firewall
- Packet Capture (ASA Troubleshooting)

- There ave some limited resources on ASA:

  - a. Maximum Connection

    b. Connection per second
    c. Xlate entry

    d. Inspection per second

    e. Routing table

    f. MAC address

    g. Telnet, SSH, ASDM

- By default, a security context can utilize all the resources of main
  firewall, thus leaving no resource for any other security context,
  Some of the resources as limited:
  a. telnet
  b. ssh
  ¢. ASDM

### TASK1: Create a security context with name "c1" on ASAL and make sure these resources are allocated with that context
- a. Maximum connection --> LOK
  b. xlate entries --> 10K

  c. Telnet, SSH, ASDM ---> 10
  d. MAC-ADDRESS --> SK

- Step1: Create a class
  Step2: Bind class with security context

### TASK: Create a context with name C2 and bind these resource with C2
- 	a. maximum connection --> 20K
-	b. CONNECTION PER SECOND --> 1000/SEC
-	c. Inspection per second --> 1000/sec
-	d. Telnet, ssh, --> 5

- what will happen to the resources which are not allocated???
  whether security context will be able to utilize those resources or not???
- By default, there is class configured on Cisco ASA and in that class, all the resources are unlimited except four resource --> telnet, ssh, asdm and MAC-ADDRESS
- C1 context is configured and you have to manage C1 context remotely from inside interface
- How do we manage main firewall remotely???

### How do we manage main firewall remotely???
- Packet-tracer
  --> It is a way by which we can logically check that if a particular packet 's recieved by ASA, then what
  action will be taken on that packet 
- PACKET CAPTURE
  --> It 1s a feature by which we can capture packet on an interface and check whether
  packet 's actually vecieved by ASA or not
- Create a capture
  capture <name> interface <nameif>
- as we create and apply capture all the packets received and transmitted will be
  captured until we remove or clear the capture