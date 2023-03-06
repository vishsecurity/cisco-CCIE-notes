- commands

  ```
  SW4(config)#do sh his
    spanning-tree mode rapid-pvst 
    spanning-tree  vlan 1 priority 4096
  SW3(config)#do sh his
    spanning-tree mode rapid-pvst 
    spanning-tree  vlan 1 root primary   
  ```
  
  
  
- STP
  
  - Root Bridge Election Criteria:-
  - Lowest Bridge-Priority (32768 By default)
  
- BPDU : 
  - Bridge Protocol Data Unit.
  - Root Bridge always generate a hello message after every 2 sec. that message is called BPDU message.
  - It is use to elect Root-Bridge.
  
- BPDUS are two types:- 
  
    1. C BPDU (Configuration BPDU) 
    2. TCN BPDU (Topology Change Notification BPDU)
    
- C-BPDU:-

    1. It will generated for Root-bridge election.
    2. First time all switches will sent this BPDU. 
    3. After election Only Root-Bridge will Generate it and relay it on all interfaces toward all connected Switches.

- Content of Cnf guration BPDU

    1. ProtocolID (2 Bytes)

    2. Version (1 Byte)
    3. Type (1 Byte)
    4. Flag (1 Byte) 
    5. Root-Bridge-ID (8 Bytes)
    6. Cost (4 Bytes)
    7. Designated Bridge -ID (8 Bytes)
    8. Designated Port-ID (2 Bytes)
    9. Max-Age Timer (2 Bytes)
    10. Frward Delay Time (2 Bytes)
    11. Message Age Time (2 Bytes)
    12. Hello Time (2 Bytes) 

    1. Protocol-ID:-
       It is always set 0. It is use to identify that which protocol is encapsulated in
       Ethernet Header. So for STP Identification is 0.
    2. Version:- 
       It is use to identify that which version of STP is using as like CST-0, PVST,PVST+ -1, RSTP -2, MST -3

    3. Type: It is use to identify that the BPDU are which type as if we use C-BPDU =0X00 , TCN-BPDU = 0X80

    4. FLAG:-

    - flag bits are identification that in C-BPDU is there any other encapsulation of information as like te-bit =1 (this bit is for the infromation of received TCN BPDU) 

    - tc Ack bit = 1 (this bit is for the information of Acknowledgment of received TCN - BPDU)

    5. COST:- Path costs are defined as a 1 byte value. Cost is predefined link by link according IEEE. Root-Bridge always
    generate cost 0. Every receiver Switch will add Own link cost in the received BPDU. Cost will be calculated inreceiving side.

    6. Bridge- ID (8byte)-
       1. It is 8 byte identity.
       2. Bridge ID is the combination of Priority + Base MAC Address.
       3. Priority is 2:byte identity and MAC is 6 byte.
       4. Priority is the combination of Priority + VLAN ID.
       5. Priority is 4 bits + VLAN ID is 12 bits.
    7. Designated Bridge-1D:-
       It is the Bridge ID of Sender Switch.

    8. STP PORT-ID:-
       1. It is the combination of Port Priority and interface ID.
       2. Port Priority is by default -128. 
       3. We can change it by +/- 16.
       4.  Interface ID is the number of Interface.
       5. In BPDU always sender (Designated) Port-ID will be add.
    9. STP PORT ROLES:-
       1. Designated Port (DP)
       2. Non Designated Port (NDP)
         1. DP:
            1. A port which transmit superior BPDU will become DP.
            2. Root-Bridge all ports will become always DP.
            3. On a single sengment both ports can not be DP or RP.
         2. NDP:-
            1. It is a port of NRB switch.
            2. It is a port where NRB will receive C-BPDU.
            3. NDP are two types.
               1.  RP (Root Port)
               2. ALT (Alternate Port)

- RP:-

    1. A port which receive superior BPDU will become Root Port.

    2. There can only a single Root Port on a Single Non-Root Bridge.

- Alt : -
  1 . It is a Backup Port of Non Root Bridge which is receiving C-BPDU and this configuration BPDU is Inferior.

  2. If my single RP port will go down then my Alt Port will become Next RP.

### How switch will identify that which BPDU is superior BPDU

1. Lowest Root-Bridge ID

### RP Port Election Process.

- Lowest Root-Bridge ID
2. Lowest Cost BPDU
3. Lowest Designated BridgeID
- Lowest Designated Port ID
  1. Designated Port Priority,
  2. Designated Port -ID(No.)

| STP PORT STATE |      | BPDU SEND | BPDU RECEIVE | MAC  | DATA |                                                            |
| -------------- | ---- | --------- | ------------ | ---- | ---- | ---------------------------------------------------------- |
| DISABLE        |      | NO        | NO           | NO   | NO   | Port shut down                                             |
| BLOCKING       |      | NO        | YES          | NO   | NO   | port will move from blocking to listning state immediately |
| LISTNING       |      | YES       | YES          | NO   | NO   | port will move in next state in 15 sec                     |
| LEARNING       |      | YES       | YES          | YES  | NO   | port will move in next state in 15 sec                     |
| FORWARDING     |      | YES       | YES          | YES  | YES  |                                                            |

- Hello Time:- 2sec
- Max age Time:- 20sec
- Forward Delay :- 15sec h
- Message Age Time:- 7
