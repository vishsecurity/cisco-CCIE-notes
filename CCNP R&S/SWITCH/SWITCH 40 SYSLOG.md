## SYSLOG 
- *Nov 18 20:15:49.067: - Timestamp / Seq
  %LINEPROTO Facility Code
  -5- Severity level
  UPDOWN:.- Mnemonic
  Line protocol on Interface Loopback1, changed state to up
- comm
  -   **Part 1:** Configure Syslog Service
  -   **Part 2:** Generate Logged Events
  -   **Part 3:** Manually Set Switch Clocks
  -   **Part 4:** Configure NTP Service
  -   **Part 5:** Verify Timestamped Logs

```

-   In this activity, you will enable and use the Syslog service and the NTP service so that the network administrator is able to monitor the network more effectively.
    
Part 1: Configure Syslog Service
## Step 1: Enable Syslog service.

1.  Click **Syslog**, then **Services** tab.
2.  **Turn** the Syslog service **on** and move the window so you can monitor activity.
		-   Configure **R1** to send log events to the Syslog server.
    R1(config)#logging 10.0.1.254
		-   Configure **S1** to send log events to the Syslog server.
    
    S1(config)#logging 10.0.1.254
		-   Configure **S2** to send log events to the Syslog server.
    S2(config)#logging 10.0.1.254

Part 2: Generate Logged Events
## Step 1: Change the status of interfaces to create event logs.

-   Configure a **Loopback 0** interface on **R1** then disable it.
    R1(config)#interface loopback 0
    R1(config-if)#shutdown
-   Turn off **PC1** and **PC2** . Turn them on again.
    

## Step 2: Examine the Syslog events.[](https://yaser-rahmati.gitbook.io/cisco-ccnp-r-s-300-115-switch/lab#step-2-examine-the-syslog-events)

1.  Look at the Syslog events. Note: All of the events have been recorded, however, the time stamps are incorrect.
    
2.  Clear the log before proceeding to the next part.
    

Part 3: Manually Set Switch Clocks
## Step 1: Manually set the clocks on the switches.[](https://yaser-rahmati.gitbook.io/cisco-ccnp-r-s-300-115-switch/lab#step-1-manually-set-the-clocks-on-the-switches)

-   Manually set the clock on **S1** and **S2** to the current date and approximate time.
    

S1#clock set 16:00:00 Apr 6 2018

S2#clock set 16:00:00 Apr 6 2018

## Step 2: Enable the logging timestamp service on the switches.[](https://yaser-rahmati.gitbook.io/cisco-ccnp-r-s-300-115-switch/lab#step-2-enable-the-logging-timestamp-service-on-the-switches)

-   Configure **S1** and **S2** to send its timestamp with logs it sends to the **Syslog** server.
    

S1(config)#service timestamps log datetime msec

S2(config)#service timestamps log datetime msec

Configure NTP Service
##  Step 1: Enable the NTP service.

In this activity, we are assuming that the NTP service is being hosted on a public internet server. If the NTP server was private, authentication could also be used.

1.  Open the **Services** tab of the **NTP** server.
    
2.  Turn the NTP service on and note the date and time that is displayed.
    

## Step 2: Automatically set the clock on the router[](https://yaser-rahmati.gitbook.io/cisco-ccnp-r-s-300-115-switch/lab#step-2-automatically-set-the-clock-on-the-router)

-   Set the clock on R1 to the date and time according to the NTP server.
    

R1(config)#ntp server 64.103.224.2

## Step 3: Enable the logging timestamp service of the router.[](https://yaser-rahmati.gitbook.io/cisco-ccnp-r-s-300-115-switch/lab#step-3-enable-the-logging-timestamp-service-of-the-router)

-   Configure **R1** to send its timestamp with the logs that it sends to the **Syslog** server.
    

R1(config)#service timestamps log datetime msec


Verify Timestamped Logs
## Step 1: Change the statuse of interface to create event logs.[](https://yaser-rahmati.gitbook.io/cisco-ccnp-r-s-300-115-switch/lab#step-1-change-the-statuse-of-interface-to-create-event-logs)

-   Re-enable and then disable the Loopback interface on R1.
    

R1(config)#interface loopback 0

R1(config-if)#shut

R1(config-if)#no shut

-   Turn off laptops **L1** and **L2**. Turn them on again.
    

## 

Step 2: Examine the Syslog events


```

