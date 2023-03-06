### TASK: Configure R2 to accept telnet session under line VTY and make sure authentication is done using line vty password "cisco"

```
line vty O 4
login
password cisco
transport input telnet
```

###  TASK: Configure R2 to accept telnet session only from IP 192.168.1.1

```
- access-list 40 permit host 192.168.1.1
- line vty O 4
- access-class 10 in
```

### TASK: Configure R2 to terminate telnet sessions if it is idle for 1 minute
```
 line vty O 4
exec-timeout 1
```


### TASK: Configure R2 to terminate telnet session after 1 minute no matter whether it is

  - line vty O 4
    
    - absolute-timeout

- How to enable SSH on a router
  a. Hostname

  b. Domain name

  c. Crypto key

  d. Username/password

  e. login local under line vty

- Whenever we generate a crypto keya name must be specified for the key.
  - show crypto key mypubkey rsa

- We can generate a crypto key without specifying hostname and domain name, if we specify the name of crypto key in the command
  - crypto key generate rsa label SSH-KEYS