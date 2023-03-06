### Why Dynamic is unidirectional 

### Why static is bidirectional Is if Wo mapped 
### Why NAT is one to one
### Why PAT is many to one 

- If NAT value is configured for any Ie) then ASA must translate that
  - IP, if no  avaiiavle then packer will be dropped
  - if NAT rule is not configured, ASA will simply process the packer Without translation
  
- Dynamic PAT 

- Static NAT

- For NAT, ASA maintains two tables:
  - a. NAT table (Nat configuration) --> show nat
  - b. Xlate table (Translation table) --> show xlate 
  
- ASA translate packet by checking NAT table
  ASA Un-transiates packet by checking Xlate table

  ### Why NAT is one to one??

  ###  Dynamic PAT

  ​	--> It is unidirectional in nature

  ​    --> Translation entry is maintained for 30 seconds

  ​	--> It is many to one (translation 1s mainly done on the basis of Layer#)

  

  ###  TASK: Configure Dynamic PAT on ASA to translate all inside users with outside IP 101.1.1.41

  - Ingress inside : Real IP = any
    Egress outside : Mapped IP 104.1.4.41

  - Creatiing object for real ip is mandatory

  - Creating object for Mapped ip
    - a, It the mapped IP is intertace Ip, then we cannot create any ovject for mapped Ip
      We must use "interface! keyword available in NAT statement,
    - b. if mapped IP is any other IP, then creating object is optional
      ---> We can directly call the IP in nat statement or we can create object and then call the object.
  - How ICMP packet is translated??
    - ICMP identifier field --> this field is used by ASA to translate icmp packet

