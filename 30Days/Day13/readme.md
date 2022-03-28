# Day 13

#### 26-01-2022

[The Trusted Source for IP Address Data](https://ipinfo.io/)



# TryHackMe Rank 54799

## TryHackMe Basic Pentesting

[TryHackMe](https://tryhackme.com/room/basicpentestingjt)

IP : `10.10.192.42`

## Scanning

```
					Open port

# Nmap 7.92 scan initiated Wed Jan 26 09:55:54 2022 as: nmap -sC -sV -oN initial 10.10.192.42
Nmap scan report for 10.10.192.42
Host is up (0.36s latency).
Not shown: 994 closed tcp ports (reset)
PORT     STATE SERVICE     VERSION
22/tcp   open  ssh         OpenSSH 7.2p2 Ubuntu 4ubuntu2.4 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey:
|   2048 db:45:cb:be:4a:8b:71:f8:e9:31:42:ae:ff:f8:45:e4 (RSA)
|   256 09:b9:b9:1c:e0:bf:0e:1c:6f:7f:fe:8e:5f:20:1b:ce (ECDSA)
|_  256 a5:68:2b:22:5f:98:4a:62:21:3d:a2:e2:c5:a9:f7:c2 (ED25519)
80/tcp   open  http        Apache httpd 2.4.18 ((Ubuntu))
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Site doesn't have a title (text/html).
139/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp  open  netbios-ssn Samba smbd 4.3.11-Ubuntu (workgroup: WORKGROUP)
8009/tcp open  ajp13       Apache Jserv (Protocol v1.3)
| ajp-methods:
|_  Supported methods: GET HEAD POST OPTIONS
8080/tcp open  http        Apache Tomcat 9.0.7
|_http-title: Apache Tomcat/9.0.7
|_http-favicon: Apache Tomcat
Service Info: Host: BASIC2; OS: Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
|_clock-skew: mean: 1h40m01s, deviation: 2h53m12s, median: 0s
| smb-os-discovery:
|   OS: Windows 6.1 (Samba 4.3.11-Ubuntu)
|   Computer name: basic2
|   NetBIOS computer name: BASIC2\x00
|   Domain name: \x00
|   FQDN: basic2
|_  System time: 2022-01-26T09:58:42-05:00
|_nbstat: NetBIOS name: BASIC2, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
| smb2-time:
|   date: 2022-01-26T14:58:42
|_  start_date: N/A
| smb2-security-mode:
|   3.1.1:
|_    Message signing enabled but not required
| smb-security-mode:
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Wed Jan 26 09:58:49 2022 -- 1 IP address (1 host up) scanned in 175.26 seconds


```


# Questions and Answers

* Hidden directory on the webserver ( `development` , found via Gobuster )
* Username ( `jan` and `kay` found via enum4linux )
* Password ( `jan:armando` found via Hydra with SSH )

# Found Credentials

`jan:armando`

# SSH
```
ssh jan@<IP>

yes

enter password

```
[Privilege Escalation Awesome Scripts SUITE](https://github.com/Tib3rius/privilege-escalation-awesome-scripts-suite)
