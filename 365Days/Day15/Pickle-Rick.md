# Pickle Rick

IP :  `10.10.252.236 `


# namp

```
# Nmap 7.92 scan initiated Fri Jan 28 07:51:08 2022 as: nmap -sC -sV -oN initial 10.10.252.236
Nmap scan report for 10.10.252.236
Host is up (0.28s latency).
Not shown: 998 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.6 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 35:a0:a4:56:c6:23:4e:37:3e:37:4c:b7:ff:4b:b0:3d (RSA)
|   256 e5:c4:74:f0:bf:73:9f:d3:6c:c0:62:f4:84:c0:20:5f (ECDSA)
|_  256 da:a5:2f:31:6e:6f:ec:a3:e0:6a:de:06:03:97:30:98 (ED25519)
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
|_http-title: Rick is sup4r cool
|_http-server-header: Apache/2.4.18 (Ubuntu)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Fri Jan 28 07:51:29 2022 -- 1 IP address (1 host up) scanned in 20.94 seconds


```

# nikto

```

 Nikto v2.1.6
---------------------------------------------------------------------------
+ Target IP:          10.10.252.236
+ Target Hostname:    10.10.252.236
+ Target Port:        80
+ Start Time:         2022-01-28 07:55:51 (GMT-5)
---------------------------------------------------------------------------
+ Server: Apache/2.4.18 (Ubuntu)
+ The anti-clickjacking X-Frame-Options header is not present.
+ The X-XSS-Protection header is not defined. This header can hint to the user agent to protect against some forms of XSS
+ The X-Content-Type-Options header is not set. This could allow the user agent to render the content of the site in a different fashion to the MIME type

+ No CGI Directories found (use '-C all' to force check all possible dirs)

+ Server may leak inodes via ETags, header found with file /, inode: 426, size: 5818ccf125686, mtime: gzip
+ Apache/2.4.18 appears to be outdated (current is at least Apache/2.4.37). Apache 2.2.34 is the EOL for the 2.x branch.
+ Cookie PHPSESSID created without the httponly flag
+ Allowed HTTP Methods: GET, HEAD, POST, OPTIONS 



```

```
	
	View page -> Username: R1ckRul3s
	robots.txt --> Wubbalubbadubdub	

```

# gobuster
```

	http://10.10.252.236/login.php


```
# Task 1

What is the first ingredient Rick needs?

	mr. meeseek hair

# Task 2

What is the second ingredient Rick needs?

	1 jerry tear
	
# Task 3

What is the final ingredient Rick needs?

	fleeb juice
