- transport input none |  How to delete a crypto key on a router
  - Generate crypto key with name
  - Key modulus --> It is the size of crypto key
  - Move the key size more secure crypto key is
  - crypto key generate rsa label SSH modulus 1024
  - Delete a specific crypto key

### Privilege level

​	--> It is a feature by which we can limit the number of commands entered by a user

- why 

  --> It is a number ranging from 0 to 15.

  --> Three privilege levels are by default enabled (0, 1, and 15)

  --> Some commands are already available in these privilege level 

  --> 2 to 14 are disabled by default, but can be enabled if required. 

- there are three mode:

  a. user exec mode

  b. privilege exec mode

  c. Global configuration mode

- No matter whether we are into which mode of router, there is always a privilege level assigned

- User should only be able to shut/no shut interface and assign IP address to interface.

- If we want to give limited access of global configuration mode to a user, then we can enable
  any of the privilege level from 2 to 14.

- Points to remember:

  a. Higher privilege level will always inherit lower privilege level commands.

  b. We can add command to any privilege level (exception is level 15)

  ¢. We cannot remove any pre-defined command from default enabled privilege level.

  ### How to add command to any privilege level

  - what command to be added:
  -  which mode do we run that command
  - For which privilege level do we want to add command
  - What cmd should be already available in that privilege mode in order to run cmd that we want to add
  - User should only be able to shut/no shut interface and assign IP address to interface.

- How to enable level 2

  - privilege <mode> level spriv-level> <emd to be added>

