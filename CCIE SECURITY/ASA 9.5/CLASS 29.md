## Failover Health Monitoring
a. Unit Health Monitoring
b. Interface Health Monitoring
Unit Health Monitoring:
What if an ASA stops recieving hello message from LAN interface
4. if asa stops vecieving hello message trom LAN interface but it 1s receiving hello msg from data interface,
in that case failover will not trigger. Failover LAN interface will considered as failed
2. If asa stops recieving hello message from LAN interface as well as Data interface, then failover will trigger
Interface Health Monitoring:
--> Monitoring data interface by sending periodic hello message from monitored interface.
ASA sends hello messaae everu 5 seconds.
When a unit does not receive hello messages on a monitored
interface for half of the configured hold time, it runs the following
tests:
1. Line Protocol Status Check
--> ASA will check the line protocol status of its interface.
--> if the interface Is down, then that interface ’s considered as failed and same thing 1s informed to other
ASA from LAN interface. Test will stop
--> if the interface is up, ASA will perform 2nd test
2. Network Activity Test —) § SL
--> ASA will check whether any kind of packet recieved on that interface or not
--> if packet is recieved, then interface is considered healthy and test stops
--> if packet 's not recieved, then 3rd test ’s performed
3. ARP test:
> A reading of the unit ARP cache for the 2 most recently acquired
> entries
> The unit sends ARP requests to these machines
> After each request, the unit counts all received traffic for up to 5
> seconds. If traffic is received, the interface is considered
> operational
> If no traffic has been received, the ping test begins
4. Ping test:
>A ping test that consists of sending out a broadcast ping request.
>The unit then counts all received packets for up to 5 seconds
>If all network tests fail for an interface, but this interface on the
>other unit continues to successfully pass traffic, then the interface
>is considered to be failed