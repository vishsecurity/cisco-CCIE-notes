## What is use of class-map???

## Can we call multiple class-map in a single policy-map??? why???

- Hash --> It is used for authentication purpose
  It is used for Integrity purpose as well
- hash is one way function or we can say that it cannot be reserved. whenever we caculate hash of data , any mathematical formula(algorithm) is us

##  What is encryption --> To encrypt the data, To hide the data, Converting plain text data into unreadable format

##  what is decryption --> Converting unreadable data into readable format

- The hash output of same data will always be same, but if we change even one character the output will be totally different.
- The size of hash output is always same irresepective of input size

## TASK: Configure ASA2 so that if R2 traceroute R1, then ASA should be seen in the traceroute output

- access-list --> UDP --> 1.1 to 101.1.1.1 eq range 35434 33554
- class-map --> acl
- policy-map --> decreament-ttl
- service-policy --> inside

```
access-list TRACEROUTE permit udp host 492.168.4.4 host 104.1.1.4 vange 35434 53534
class-map TRACEROUTE
match access-list TRACEROUTE
```

```
policy-map PMAP
class TRACEROUTE
set connection decrement-ttl
service-policy PMAP interface inside
```

## TASK: Configure ASAZ so that, if any inside IP traceroute any outside IP ASA should be seen in the traceroute output
- class-map -->
- policy-map --> decreament-ttl
- sevvice-policy --> inside

## TASK: Configure R14 and R2 as EBGP neighbors

- Make sure BGP neighborship is authenticated with password "cisco"
  BGP hash is sent with TCP option 19.
  This option is not availble in TCP header by default
  ASA removes any extra TCP header option if available
  1. Create a tcp-map to allow tcp option 19

  2. create acl

  3. create class-map

  4. call class-map in policy-map and apply tcp-map

- Whenever BGP calculates hash, it calculate hash of BGP password + TCP sequence number