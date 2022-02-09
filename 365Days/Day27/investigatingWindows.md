



```

C:\Users\Administrator>systeminfo

Host Name:                 EC2AMAZ-I8UHO76
OS Name:                   Microsoft Windows Server 2016 Datacenter
OS Version:                10.0.14393 N/A Build 14393
OS Manufacturer:           Microsoft Corporation
OS Configuration:          Standalone Server
OS Build Type:             Multiprocessor Free
Registered Owner:          EC2
Registered Organization:   Amazon.com
Product ID:                00376-40000-00000-AA753
Original Install Date:     3/2/2019, 4:06:35 PM
System Boot Time:          2/9/2022, 12:56:41 PM
System Manufacturer:       Amazon EC2
System Model:              t3.small
System Type:               x64-based PC
Processor(s):              1 Processor(s) Installed.
                           [01]: Intel64 Family 6 Model 85 Stepping 7 GenuineIntel ~2500 Mhz
BIOS Version:              Amazon EC2 1.0, 10/16/2017
Windows Directory:         C:\Windows
System Directory:          C:\Windows\system32
Boot Device:               \Device\HarddiskVolume1
System Locale:             en-us;English (United States)
Input Locale:              en-us;English (United States)
Time Zone:                 (UTC) Coordinated Universal Time
Total Physical Memory:     2,010 MB
Available Physical Memory: 1,069 MB
Virtual Memory: Max Size:  2,394 MB
Virtual Memory: Available: 1,414 MB
Virtual Memory: In Use:    980 MB
Page File Location(s):     C:\pagefile.sys
Domain:                    WORKGROUP
Logon Server:              \\EC2AMAZ-I8UHO76
Hotfix(s):                 16 Hotfix(s) Installed.
                           [01]: KB3176936
                           [02]: KB3186568
                           [03]: KB3192137
                           [04]: KB3199209
                           [05]: KB3199986
                           [06]: KB4013418
                           [07]: KB4023834
                           [08]: KB4035631
                           [09]: KB4049065
                           [10]: KB4089510
                           [11]: KB4091664
                           [12]: KB4093137
                           [13]: KB4132216
                           [14]: KB4465659
                           [15]: KB4485447
                           [16]: KB4487026
Network Card(s):           1 NIC(s) Installed.
                           [01]: Amazon Elastic Network Adapter
                                 Connection Name: Ethernet 2
                                 DHCP Enabled:    Yes
                                 DHCP Server:     10.10.0.1
                                 IP address(es)
                                 [01]: 10.10.101.42
                                 [02]: fe80::5854:552a:8269:a060
Hyper-V Requirements:      A hypervisor has been detected. Features required for Hyper-V will not be displayed.




```

```
C:\Users\Administrator>net user

 User accounts for \\EC2AMAZ-I8UHO76                                                                                                                                                         -------------------------------------------------------------------------------               Administrator            DefaultAccount           Guest                                       Jenny                    John                                                                 The command completed successfully.

                                                                                                                                                                                                                                              C:\Users\Administrator>net user Administrator                                                 User name                    Administrator                                                    Full Name                                                                                     Comment                      Built-in account for administering the computer/domain           User's comment                                                                                Country/region code          000 (System Default)                                             Account active               Yes                                                              Account expires              Never                                                                                                                                                          Password last set            3/2/2019 5:46:03 PM                                              Password expires             Never                                                            Password changeable          3/2/2019 5:46:03 PM                                              Password required            Yes                                                              User may change password     Yes                                                                                                                                                            Workstations allowed         All                                                              Logon script                                                                                  User profile                                                                                  Home directory                                                                                Last logon                   2/9/2022 12:57:54 PM                                                                                                                                           Logon hours allowed          All                                                                                                                                                            Local Group Memberships      *Administrators                                                  Global Group memberships     *None                                                            The command completed successfully.                                                                                                                                                                                                                                                       C:\Users\Administrator>net user John                                                          User name                    John                                                             Full Name                    John                                                             Comment                                                                                       User's comment                                                                                Country/region code          000 (System Default)                                             Account active               Yes                                                              Account expires              Never                                                                                                                                                          Password last set            3/2/2019 5:48:19 PM                                              Password expires             Never                                                            Password changeable          3/2/2019 5:48:19 PM                                              Password required            Yes                                                              User may change password     Yes                                                                                                                                                            Workstations allowed         All                                                              Logon script                                                                                  User profile                                                                                  Home directory                                                                                Last logon                   3/2/2019 5:48:32 PM                                                                                                                                            Logon hours allowed          All                                                                                                                                                            Local Group Memberships      *Users                                                           Global Group memberships     *None                                                            The command completed successfully.                                                                                                                                                                                                                                                       C:\Users\Administrator>net user Jenny                                                         User name                    Jenny                                                            Full Name                    Jenny                                                            Comment                                                                                       User's comment                                                                                Country/region code          000 (System Default)                                             Account active               Yes                                                              Account expires              Never                                                                                                                                                          Password last set            3/2/2019 4:52:25 PM                                              Password expires             Never                                                            Password changeable          3/2/2019 4:52:25 PM                                              Password required            Yes                                                              User may change password     Yes                                                                                                                                                            Workstations allowed         All                                                              Logon script                                                                                  User profile                                                                                  Home directory                                                                                Last logon                   Never                                                                                                                                                          Logon hours allowed          All                                                                                                                                                            Local Group Memberships      *Administrators       *Users                                     Global Group memberships     *None                                                            The command completed successfully.

```

```
lusrmgr.msc

Group --> Admin --> right click properties
See those who are admin

```

```
event viewer

Filter all log related log using 4624 id

Filter timestamp using 4672

```

###	Q1.	Whats the version and year of the windows machine?
```


```
---
###	Q2.	Which user logged in last?
```


```
---

###	Q3.	When did John log onto the system last?
Answer format: MM/DD/YYYY H:MM:SS AM/PM

```


```
---


###	Q4.	What IP does the system connect to when it first starts?
```


```

###	Q4.What two accounts had administrative privileges (other than the Administrator user)?

Answer format: username1, username2

```


```

###	Q5.	Whats the name of the scheduled task that is malicous.

```


```

###	Q6.	What file was the task trying to run daily?

```


```

###	Q7.	What port did this file listen locally for?

```



```

###	Q8.	When did Jenny last logon?

```


```

###	Q9.	At what date did the compromise take place?

Answer format: MM/DD/YYYY

```


```

###	Q10.	At what time did Windows first assign special privileges to a new logon?

Answer format: MM/DD/YYYY HH:MM:SS AM/PM

```


```

###	Q11.	What tool was used to get Windows passwords?

```


```

###	Q12.	What was the attackers external control and command servers IP?

```


```

###	Q13.	What was the extension name of the shell uploaded via the servers website?

```


```

###	Q14.	What was the last port the attacker opened?

```


```

###	Q15.	Check for DNS poisoning, what site was targeted?

```

```
