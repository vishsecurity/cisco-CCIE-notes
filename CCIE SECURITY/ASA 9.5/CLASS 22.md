### TASK: Configure ASA2 in multiple as follows:

- a. Create two security context C1 and C2
  --> Allocate EO and E1 to C1, E2 and E3 to C2
  --> Config-url for C1 should be "c1.cfg" and for C2 should be "c2.cfg"
  --> Configure ip address on C1 and C2. as per diagram.
  --> Configure dynamic PAT and enable ICMP inspection.

- As we change the firewall mode, admin context is automatically created
  configuration is saved at two locations:
  a. in flash
  b. in admin-context
  inter-context routing is not possible without shared interface
  enabling interface is always done from system configuration firewall