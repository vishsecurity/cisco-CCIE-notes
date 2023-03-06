QOS Quality of Service

Converged Networks
- Single Network for Voice, Data and Video (before it was all on different networks)

Quality issues in Converged Network
1) Lack of bandwidth
- Maximum bandwidth = the lowest link in the network
- Forward the most important packets first (voice over ftp)
2) End-to-end delay
- A-to-B delay
- Propagation delay - time it takes to transit a packet
- Processing delay - time it takes to process a packet from its input, decision, then onto its output
- Queuing delay (can be prioritized) - when a packet waits in the output queue of a router
- Serialization delay - times it takes to physically transfer bits on the wire
3) Variation of delay (jitter)
ex. Traffic (A)(B)(C) is a lot smoother than (A)(B)---(C), the latter is jitter. Cisco has dejitter functions to resolve this. Similar to how videos are prebuffered
4) Packet loss
- Tail drops: packets may be lost when output queue is full
- WRED Weighted Random Early Detection: X [MAX] Y [MIN] Z, if it gets to X amount of traffic, low priority traffic are randomly dropped

Ways to reduce delay:
- Upgrade links
- Forward important packets first
- Compress payload / IP packet headers
- Guarantee enough bandwidth to sensitive traffic

QOS requirements
Voice/Video latency <= 150ms
Jitter <= 30ms
Loss <= 1%
Video bandwidth +20% (ex. 384kbps + 20% requires 460kbps)

QOS requirements classes/priority
Mission-critical apps > Transactional (chats, client-to-server transactions) > Best-Effort (internet, e-mail) > Less-than-best-effort (scavenger - facebook, youtube, bit torrent)

Implement QOS
1) CLI - no templates
2) Modular QoS CLI (MQC) - can create templates
3) AutoQoS - can create templates 
3a) AutoQoS VoIP (voice ONLY) 
- DOES NOT looks at traffic
- Router & Switches
3b) AutoQoS Enterprise (voice, video and data) 
- looks at traffic and also offer suggestions
- Routers ONLY
4) QoS Policy Manager (QPM)
- Centralized QoS Management platform, enables network wide QoS

3 models of QoS
1) Best effort 
- no QoS is applied to packets
- does scale, no gurantee delivery
2) IntServ 
- applications signal to network that they require special QoS
- does not scale, gurantee delivery (ex. "you bought First Class ticket, you will be guranteed a seat in First Class")
3) DiffServ 
- disregard application, network recognize classes that require special QoS
- does scale, no gurantee delivery (ex. "just because you want to be treated like First Class, does not gurantee you will be treated like First Class")
**Real world, IntServ (mission-control) and DiffServ (QoS) work together
**Real world, Best Effort is used on the Internet