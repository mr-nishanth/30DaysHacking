

#	Day 28

#### 10-02-2022

# TryHackMe Rank  26673 ( 62 Streak )

---
### Bounty Hunter
[TryHackMe Wonder Land](https://tryhackme.com/room/wonderland)

```
└─# nmap 10.10.91.194 -v -sC -sV -oN  nmap/initial                                                                                                       1 ⨯
Starting Nmap 7.92 ( https://nmap.org ) at 2022-02-10 10:43 EST
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 10:43
Completed NSE at 10:43, 0.00s elapsed
Initiating NSE at 10:43
Completed NSE at 10:43, 0.00s elapsed
Initiating NSE at 10:43
Completed NSE at 10:43, 0.00s elapsed
Initiating Ping Scan at 10:43
Scanning 10.10.91.194 [4 ports]
Completed Ping Scan at 10:43, 0.36s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 10:43
Completed Parallel DNS resolution of 1 host. at 10:43, 0.06s elapsed
Initiating SYN Stealth Scan at 10:43
Scanning 10.10.91.194 [1000 ports]
Discovered open port 80/tcp on 10.10.91.194
Discovered open port 22/tcp on 10.10.91.194
Completed SYN Stealth Scan at 10:43, 4.66s elapsed (1000 total ports)
Initiating Service scan at 10:43
Scanning 2 services on 10.10.91.194
Completed Service scan at 10:43, 14.02s elapsed (2 services on 1 host)
NSE: Script scanning 10.10.91.194.
Initiating NSE at 10:43
Completed NSE at 10:44, 7.19s elapsed
Initiating NSE at 10:44
Completed NSE at 10:44, 1.28s elapsed
Initiating NSE at 10:44
Completed NSE at 10:44, 0.00s elapsed
Nmap scan report for 10.10.91.194
Host is up (0.26s latency).
Not shown: 998 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey:
|   2048 8e:ee:fb:96:ce:ad:70:dd:05:a9:3b:0d:b0:71:b8:63 (RSA)
|   256 7a:92:79:44:16:4f:20:43:50:a9:a8:47:e2:c2:be:84 (ECDSA)
|_  256 00:0b:80:44:e6:3d:4b:69:47:92:2c:55:14:7e:2a:c9 (ED25519)
80/tcp open  http    Golang net/http server (Go-IPFS json-rpc or InfluxDB API
|_http-title: Follow the white rabbit.
| http-methods:
|_  Supported Methods: GET HEAD POST OPTIONS
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

NSE: Script Post-scanning.
Initiating NSE at 10:44
Completed NSE at 10:44, 0.01s elapsed
Initiating NSE at 10:44
Completed NSE at 10:44, 0.00s elapsed
Initiating NSE at 10:44
Completed NSE at 10:44, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://n
Nmap done: 1 IP address (1 host up) scanned in 29.74 seconds
           Raw packets sent: 1129 (49.652KB) | Rcvd: 1124 (44.956KB)


```
---

```


```

Obtain the flag in user.txt

```

```

Escalate your privileges, what is the flag in root.txt?

```

```
