- What is AAA?
- Why AAA??
- How to configure AAA??

1. Device Administration:
--> connecting to a device for its management purpose such as telnet to a firewall

2. Network Access:

   --> Connecting to a device to access a network

### TASK1: Enable AAA on R2 and make sure line vty session is authenticated via LOCAL database.

- Step1: Enable AAA
- Step2: Create AAA authentication list

- Step1: Enable AAA
  aaa new-mode
- As we enable AAA on a router, all the lines (line con and line vty) get authenticated and authorized via AAA
  --> If we enable aaa on a router, then we must have any AAA list for
  authentication as well as authorization

- Step2: Create aaa authentication list
  aaa authentication login default local

- aaa authentication <method> <name of list>
- name of list : Whenever we create any AAA ist, each list is given a name 
- Whenever we specify name of the list, there ave two options available:
  - a. Custom --> we can define any custom name for example: ABC , XYZ
  - b. default --> It is a pre-defined name available
    - aaa authentication login ABC
    - aaa authentication login default
- if we create AAA list with Custom name, then we must apply that list on line VTY or line
  console
- if we create default AAA list, then there is not need to apply the list on line vty or line
  console, because default list is by default applied on line vty as well as line console.
- aaa authentication login defualt <database>
  - which database to use for authentication

### TASK: Enable AAA on R2 to authentication line vty session using LOCAL database:

- default

  ```
  aaa new-mode
  aaa authentication login default local
  username praveen password cisco
  ```

- custom

  ```
  aaa new-mode
  aaa authentication login VTY local
  username praveen password cisco
  line vty O 4
  login authentication VTY
  ```

  