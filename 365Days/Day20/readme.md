
#	Day 20

#### 02-02-2022

# TryHackMe Rank  43636

## TryHackMe Nmap
[TryHackMe](https://tryhackme.com/room/furthernmap)


Notes:
- Task 6

	- SYN scans are sometimes referred to as "Half-open" scans, or "Stealth" scans.
	- SYN scans are significantly faster than a standard TCP Connect scan.
	- SYN scans are the default scans used by Nmap if run with sudo permissions. If run without sudo permissions, Nmap defaults to the TCP Connect scan
	- If a port is closed then the server responds with a RST TCP packet. If the port is filtered by a firewall then the TCP SYN packet is either 	dropped, or spoofed with a TCP reset.

- Task 7

	- TCP, UDP connections are stateless
	-  If it gets a UDP response (which is very unusual), then the port is marked as open. More commonly there is no response, in which case the request is sent a second time as a double-check. If there is still no response then the port is marked open|filtered and Nmap moves on.
	- When a packet is sent to a closed UDP port, the target should respond with an ICMP (ping) packet containing a message that the port is unreachable. This clearly identifies closed ports, which Nmap marks as such and moves on.

- Task 8

	- That said, the goal here is, of course, firewall evasion. Many firewalls are configured to drop incoming TCP packets to blocked ports which have the SYN flag set (thus blocking new connection initiation requests). By sending requests which do not contain the SYN flag, we effectively bypass this kind of firewall. Whilst this is good in theory, most modern IDS solutions are savvy to these scan types, so don't rely on them to be 100% effective when dealing with modern systems.
