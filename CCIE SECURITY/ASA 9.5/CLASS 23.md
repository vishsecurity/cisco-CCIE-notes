### How ASA classifies packet in multiple mode:

1. Unique Interface
2. Unique MAC address 
3. Unique NAT configuration 

1. Unique Interface

   --> if an interface is shared with only one security context then
   that interface is unique for that context.

   --> In case if ASA recieves packet from that interface, it is simply
   forwarded to the context where it is allocated.

2. if interface is shared with more than one security context, then either unique MAC Address or
   Unique NAT configuration is used to classify packet.

   1. Unique MAC addres:
      1. --> if interface is shared then ASA will check the destination MAC address of the frame
         and compare it with any of the security context. if the MAC address is assigned only on one
         security context, then packet is forwarded to that security context.
      2. if we are sharing interface with more that one security context, each security context Uses the
         same MAC address
      3. There ave two ways to generate unique MAC address for each context
         a. Manual --> change the MAC address manually
         b. Automatic
      4. mac-address auto System Configuration firewall

3. Unique NAT Configuration

   --> if the interface is shared and MAC address is not unique, then ASA will check the Destination IP in the packet and it will compare that IP with mapped IP of any security context.

   - if destination IP matches with any of the mapped IP, then Packet is forwarded to that security context.
     inter-Context Routing

   --> Routing traftic between two security context within main ASA

   --> Inter context routing is possible only tf interface is shared between security context

   - inter-context Routing without NAT
   - inter-context Routing with NAT

### TASK: Configure ASA1 C1 and C2 so that R1 and R3 can communicate with each other

### TASK: Configure Dynamic PAT on C1 and C2 and make R1 and R3 can ping internet(R2).

- NOTE: Make sure it should not effect previous task.

