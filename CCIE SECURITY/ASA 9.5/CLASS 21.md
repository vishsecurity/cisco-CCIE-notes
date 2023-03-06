### what are Security Context

- --> It is a feature by which we can create multiple logical ASAs within a single physical ASA
  --> We can virtualize the ASA with this feature 
  --> Each Logical ASA is known as Security context 
  --> Each logical ASA will acts as a standalone device with its own interfaces,
  own security policies, own routing

### what are type of context ?

- There are two types of context on ASA:
  - a. Admin context
  - b. Regular context
- why security context ?
  - if you ave a ISP and providing firewall services to different clients 
  - if you need more than one firewall in your network but you cannot afford more than one firewall
  - if you need to place firewall in your internal network as well  

- If we want to create security context, ASA must in multiple mode   
    a. Single mode --> default mode of ASA, ASA acts as a single device       
    b. multiple mode --> USe to create multiple logical ASAs

  - show mode              

  ### How to create security context 

  -  context <name>                                    

  ### How to change ASA mode from single to multiple

  - mode multiple

    --> This command will change the behavior of ASA
    --> It will intiate a reboot

  ### what will happend to the configuration of single mode???

  ​	--> Configuration of single mode will be saved at the two locations:
  ​	         a. In flash: with file name "old_running.clg”

  ​			 b. multiple mode 

  ​		There ave two types of console which we can get:
  ​          a. Main firewall Console --> System Configuration Firewall
  ​           b. Security context Console

  - We cannot use main firewall to configure any interface or any kind of policy.
  - It is only used to manage security context (create, interface, cfg-url, delete, modify)
    --> Main firewall is also used to configure failover

### what things should be configured for a security context from main firewall console (System configuration firewall)
a. Allocate-interface  --> logical ASA does not have its own interface, so interfaces
from physical ASA is allocated to context
								 --> we can allocate all the interface of main firewall to security
contexts
b. Config-url --> we specity the path where configuration of context will be saved
					--> configuration can be saved at two locations
		            a. LOCAL --> Flash of ASA
                    b. Remote --> FTP, TFTP, HTTP

c. Resource allocation --> we can even share same interface with multiple context

- there  are two types of context of asa
  - admin context
  - regular context

### what is admin context ?

-  Admin Context

  ​	--> It Is Just like a regular security context with an extra privilege
  ​	 --> We can remotely manage System configuration firewall using admin context.

### how to create admin context ?

- admin-context <name>
- For admin context --> config-url is flash:

### How to take console of logical ASA

- changeto context 01

### How to take console of main firewall from context

- changeto system
- changeto context system
- exit --> exit -—> exit