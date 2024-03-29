## TCN- Topology Change Notification
1. Insignificant Topology Change
2.  Direct Topology Change
3. Indirect Topology Change

### TCN BPDU

1. Protocol ID
2. Version
3. Type 

### TCN
- TCN BPDU will give an information that a change is in topology.
- TCN BPDU always generated by Non Root bridge from Root Port , toward Root Bridge.
- It  will use Portfast Feature on All Access Ports.
- If i will use it then TCN will not generate when my Access port willicome up or go down.
- If i will use Portfast on Access port then it will not wait 15 sec in Listning and also not 15 sec in learning state, It mean it will come direct in Forwarding State.

## Types of STP:-
1. CST= COMMAN SPANNING TREE

2. PVST= PER VLAN SPANNING TREE

3. PVST+= PER VLAN SPANNING TREE PLUS
   1. CST
      1. CST is open Spandard Protocol.
      2. 802.1d IEEE Standard.
      3. It operate a single instance of STP for all VLAN.
      4. Doesn't Support Load-balancing.
      5. CPU utilization is low.
   2. PVST, PVST+ :-
      1. It is CISCO proprietary.
      2. It operates seprate instance for each VLAN.
      3. It support Load-balancing.
      4. CPU utilization is high.
      5. No of BPDU will generate same as no, of instance (VLAN).
      6. PVST is not compatibal with CST.
      7. PVST is not more use in CISCO.
      8. PVST+ is compatibal with CST.

   - ROOT GUARD:-

   1. It is use to secure ROOTB RIDGE from attack.
   2. Root Guard we can enable only on Trunk DP not on Access DP.
   3. If we will enable ROOTGUARD on RP Port then RP port will stop to receive superior BPDU and whensuperior BPDU will come on it then this port will go in ROOT INCONSISTANT (errordisable state Blocking) state.
   4. If superior BPDU will receive on ROOT GUARD applied port then port will go in ROOTINCONSISTANT state.
   5. Port will go in blocking state for 20 sec if superior BPDU will receive on ROOT GUARD port and when attack will off then port will try to come out from error disable state, it mean it will recover automatically after (max age) 20 sec.

   - LOOP GUARD:-
     1. It is use to secure ROOT PORT.
     2. It is use to secure topology from Loop.
     3. We will use LOOPGUARD on all RP Trunk.
     4. If DP port of ROOTBRIDGE will not send any BPDU for any reason as for IOS bug then LOOPGUARD enabled ROOT PORT will go in LOOPINCONSICTANT state (errordisable) (blocking state) after (max age) 20sec. AND RP not will move role RP to DP.
     5. RP port will come out automatically from loop inconsistant state when DP port of ROOT BRIDGE will again start to send BPDU.

   - BPDU GUARD:-
     1. It will enble on all access port.
     2. BPDU GUARD enabled port will not receive any BPDU from PC.
     3. It is use to secure switch topology from Parrot PC Operating System.
     4. lf BPDU GUARD enabled port will receive any BPDU from attacker PC then
     this port will go in error disable state. And data will block from thish blocking port. Now to come-out port from error disable state we will manual shut and no shut down this port.

   - BPDU FILTER

     1. Both are used on Access Port only.

     2. BPDU FILTER enabled port will not send BPDU and nor receive BPDU.
     3. If any one will send BPDU on BPDU FILTER enabled port then port will never go in error disable state it will discard BPDU only.

   - UDLD :- UniDirectional Link Detection
     1. It is used to detect Undirectional Link.
     2. It is CISCO proprietary Protocol.
     3. It is Layer 2 Protocol.
     4. It use multicst address 0100.0ccc.cccc

   - THERE ARE TWO MODES OF UDLD
     1. Normal Mode :- If unidirectional link is detected then normally log message will generate.
     2. Aggressive Mode:- If unidirectional link is detected then log message will generate and port will go in error disable state.

   - RSTP/RPVST+
     1, Rapid Spanning Tree Protocol
     2. It is Open Standard Protocol.
     3. IEEE Standard 802.1w
     4.  It has fast convergen.
     5. Root Bridge, Root Port and Designated Port election criteria is same as STP.
     6. Portfast is required on all Access ports.
     7. In RSTP TCN BPDU is not available.
     8. There NONROOT BRIDGE can also send C-BPDU.

- CONFIGURATION BPDU

  1. Protocol ID
  2. Protocol Version
  3. Type
  4. Flag
  5. Root Bridge ID
  6. Cost
  7. Designated Bridge ID
  8. Designated Port ID
  9. Max Age  (If continually 3 message will not receive then BPDU will be expire. It mean after 6 seconds.) 
  10. Forward Delay Time (15)
  11. Message Age Time (7)
  12. Hello Time (2sec)

- PORT STATE STP

  - DISABLE
    BLOCKING
    LISTNINGG
    LEARNING
    FORWARDING
  - PORT STATE RSTP
    1. DISCARDING =15 Sec
    2. LEARNING =15 Sec
    3. FORWARDING

- STP-FLAG (8bit)
  7-TCAck
  6- unused
  5- unused
  4-unused
  3- unused
  2- unused
  1- unused 
  0-TC

- RSTP - FLAG
  7-TCAck
  6- Agreement
  5- State Forwarding
  4- State Learning
  3- Port Role
  2- Port Role
  1- Proposal
  0-TC

- Port Role:-

  00 Reserved
  01 Alt/Backup
  10 RP
  11 DP

- MST
  1. Multi Spanning Tree protocol
  2. Open Standard Protocol.
  3. IEEE Standard is 802.1s
  4. Bydefault is works same as CST.
  5. Bydefault instnce 0 exist and all VLAN will mapped into that instance.
  6. Instance 0 is called CIST (Common Internal Spanning Tree)
  7. We can create multiple instances according to our requirement.
  8. Its convergence is same as RSTP.
  9. Root Bridge, Root Port and DP port election criteria is same as STP.

- MST ATTRIBUTES

  1. NAME= (NULL)
  2. ie REVISION NO = {0} if we will create any another instance then we need to increment by 1,
     ‘Manually in REVISION NO. This work will no be performed by automatically as VTP.

  3. INSTANCE = {MAPED VLAN} 
     1. NAME- NEET TO MATCH 
        REVISION NO.
        INSTANCE NO.
        MAPPED VALN