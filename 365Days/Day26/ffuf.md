
#	Day 27

#### 07-02-2022

# TryHackMe Rank  33559 ( 60 Streak )


# FFUF
[TryHackMe ffuf](https://tryhackme.com/room/ffuf)


-	ffuf stands for Fuzz Faster U Fool. It's a tool used for web enumeration, fuzzing, and directory brute forcing.


       At a minimum we're required to supply two options: -u to specify an URL and -w to specify a wordlist. The default keyword FUZZ is used to tell ffuf where the wordlist entries will be injected

---

## Task 2
###    Q1.	What is the first file you found with a 200 status code?
```
ffuf -u http://10.10.96.250/FUZZ -w SecLists/Discovery/Web-Content/big.txt                                                                           1 ⨯

        /'___\  /'___\           /'___\
       /\ \__/ /\ \__/  __  __  /\ \__/
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/
         \ \_\   \ \_\  \ \____/  \ \_\
          \/_/    \/_/   \/___/    \/_/

       v1.3.1-dev
________________________________________________

 :: Method           : GET
 :: URL              : http://10.10.96.250/FUZZ
 :: Wordlist         : FUZZ: SecLists/Discovery/Web-Content/big.txt
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405
________________________________________________

.htaccess               [Status: 403, Size: 288, Words: 21, Lines: 11]
.htpasswd               [Status: 403, Size: 288, Words: 21, Lines: 11]
config                  [Status: 301, Size: 312, Words: 20, Lines: 10]
docs                    [Status: 301, Size: 310, Words: 20, Lines: 10]
external                [Status: 301, Size: 314, Words: 20, Lines: 10]
favicon.ico             [Status: 200, Size: 1406, Words: 5, Lines: 2]
robots.txt              [Status: 200, Size: 26, Words: 3, Lines: 2]
server-status           [Status: 403, Size: 292, Words: 21, Lines: 11]
:: Progress: [20476/20476] :: Job [1/1] :: 180 req/sec :: Duration: [0:01:59] :: Errors: 0 ::

```


Ans:	favicon.ico
---


## Task 3

-	One approach you could take would be to start enumerating with a generic list of files such as raft-medium-files-lowercase.txt.

###    Q1.    What text file did you find?

```
ffuf -u http://10.10.96.250/FUZZ -w SecLists/Discovery/Web-Content/raft-medium-files-lowercase.txt                                                 130 ⨯

        /'___\  /'___\           /'___\
       /\ \__/ /\ \__/  __  __  /\ \__/
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/
         \ \_\   \ \_\  \ \____/  \ \_\
          \/_/    \/_/   \/___/    \/_/

       v1.3.1-dev
________________________________________________

 :: Method           : GET
 :: URL              : http://10.10.96.250/FUZZ
 :: Wordlist         : FUZZ: SecLists/Discovery/Web-Content/raft-medium-files-lowercase.txt
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405
________________________________________________

favicon.ico             [Status: 200, Size: 1406, Words: 5, Lines: 2]
.htaccess               [Status: 403, Size: 288, Words: 21, Lines: 11]
logout.php              [Status: 302, Size: 0, Words: 1, Lines: 1]
index.php               [Status: 302, Size: 0, Words: 1, Lines: 1]
login.php               [Status: 200, Size: 1523, Words: 89, Lines: 77]
robots.txt              [Status: 200, Size: 26, Words: 3, Lines: 2]
phpinfo.php             [Status: 302, Size: 0, Words: 1, Lines: 1]
.                       [Status: 302, Size: 0, Words: 1, Lines: 1]
php.ini                 [Status: 200, Size: 148, Words: 17, Lines: 5]
about.php               [Status: 200, Size: 4840, Words: 331, Lines: 109]
.html                   [Status: 403, Size: 284, Words: 21, Lines: 11]
.php                    [Status: 403, Size: 283, Words: 21, Lines: 11]
setup.php               [Status: 200, Size: 4066, Words: 308, Lines: 123]
.htpasswd               [Status: 403, Size: 288, Words: 21, Lines: 11]
security.php            [Status: 302, Size: 0, Words: 1, Lines: 1]
.htm                    [Status: 403, Size: 283, Words: 21, Lines: 11]
.htpasswds              [Status: 403, Size: 289, Words: 21, Lines: 11]
.htgroup                [Status: 403, Size: 287, Words: 21, Lines: 11]
wp-forum.phps           [Status: 403, Size: 292, Words: 21, Lines: 11]
.htaccess.bak           [Status: 403, Size: 292, Words: 21, Lines: 11]
.htuser                 [Status: 403, Size: 286, Words: 21, Lines: 11]
.ht                     [Status: 403, Size: 282, Words: 21, Lines: 11]
.htc                    [Status: 403, Size: 283, Words: 21, Lines: 11]
:: Progress: [16244/16244] :: Job [1/1] :: 188 req/sec :: Duration: [0:01:40] :: Errors: 0 ::

```
---
###    Q2.    What two file extensions were found for the index page?

```
ffuf -u http://10.10.96.250/indexFUZZ -w SecLists/Discovery/Web-Content/web-extensions.txt

        /'___\  /'___\           /'___\
       /\ \__/ /\ \__/  __  __  /\ \__/
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/
         \ \_\   \ \_\  \ \____/  \ \_\
          \/_/    \/_/   \/___/    \/_/

       v1.3.1-dev
________________________________________________

 :: Method           : GET
 :: URL              : http://10.10.96.250/indexFUZZ
 :: Wordlist         : FUZZ: SecLists/Discovery/Web-Content/web-extensions.txt
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405
________________________________________________

.php                    [Status: 302, Size: 0, Words: 1, Lines: 1]
.phps                   [Status: 403, Size: 289, Words: 21, Lines: 11]
:: Progress: [39/39] :: Job [1/1] :: 13 req/sec :: Duration: [0:00:04] :: Errors: 0 ::

```
---
###    Q3.    What page has a size of 4840?

```
ffuf -u http://10.10.96.250/FUZZ -w SecLists/Discovery/Web-Content/raft-medium-words-lowercase.txt -e .php , .txt

        /'___\  /'___\           /'___\
       /\ \__/ /\ \__/  __  __  /\ \__/
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/
         \ \_\   \ \_\  \ \____/  \ \_\
          \/_/    \/_/   \/___/    \/_/

       v1.3.1-dev
________________________________________________

 :: Method           : GET
 :: URL              : http://10.10.96.250/FUZZ
 :: Wordlist         : FUZZ: SecLists/Discovery/Web-Content/raft-medium-words-lowercase.txt
 :: Extensions       : .php
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405
________________________________________________

.php                    [Status: 403, Size: 283, Words: 21, Lines: 11]
.htm                    [Status: 403, Size: 283, Words: 21, Lines: 11]
.htm.php                [Status: 403, Size: 287, Words: 21, Lines: 11]
logout.php              [Status: 302, Size: 0, Words: 1, Lines: 1]
config                  [Status: 301, Size: 312, Words: 20, Lines: 10]
.html                   [Status: 403, Size: 284, Words: 21, Lines: 11]
.html.php               [Status: 403, Size: 288, Words: 21, Lines: 11]
docs                    [Status: 301, Size: 310, Words: 20, Lines: 10]
index.php               [Status: 302, Size: 0, Words: 1, Lines: 1]
login.php               [Status: 200, Size: 1523, Words: 89, Lines: 77]
about.php               [Status: 200, Size: 4840, Words: 331, Lines: 109]
.                       [Status: 302, Size: 0, Words: 1, Lines: 1]
external                [Status: 301, Size: 314, Words: 20, Lines: 10]
.htaccess               [Status: 403, Size: 288, Words: 21, Lines: 11]
.htaccess.php           [Status: 403, Size: 292, Words: 21, Lines: 11]
setup.php               [Status: 200, Size: 4066, Words: 308, Lines: 123]
security.php            [Status: 302, Size: 0, Words: 1, Lines: 1]
phpinfo.php             [Status: 302, Size: 0, Words: 1, Lines: 1]
.php3                   [Status: 403, Size: 284, Words: 21, Lines: 11]
.phtml                  [Status: 403, Size: 285, Words: 21, Lines: 11]
.htc.php                [Status: 403, Size: 287, Words: 21, Lines: 11]
.htc                    [Status: 403, Size: 283, Words: 21, Lines: 11]
instructions.php        [Status: 200, Size: 14014, Words: 1484, Lines: 263]
.php5                   [Status: 403, Size: 284, Words: 21, Lines: 11]
.html_var_de.php        [Status: 403, Size: 295, Words: 21, Lines: 11]
.html_var_de            [Status: 403, Size: 291, Words: 21, Lines: 11]
.php4                   [Status: 403, Size: 284, Words: 21, Lines: 11]
server-status           [Status: 403, Size: 292, Words: 21, Lines: 11]
.htpasswd.php           [Status: 403, Size: 292, Words: 21, Lines: 11]
.htpasswd               [Status: 403, Size: 288, Words: 21, Lines: 11]
.html..php              [Status: 403, Size: 289, Words: 21, Lines: 11]
.html.                  [Status: 403, Size: 285, Words: 21, Lines: 11]
.html.html              [Status: 403, Size: 289, Words: 21, Lines: 11]
.html.html.php          [Status: 403, Size: 293, Words: 21, Lines: 11]
.htpasswds              [Status: 403, Size: 289, Words: 21, Lines: 11]
.htpasswds.php          [Status: 403, Size: 293, Words: 21, Lines: 11]
[WARN] Caught keyboard interrupt (Ctrl-C)


```
---

###    Q4.    How many directories are there?
```
 ffuf -u http://10.10.96.250/FUZZ -w SecLists/Discovery/Web-Content/raft-medium-directories-lowercase.txt

        /'___\  /'___\           /'___\
       /\ \__/ /\ \__/  __  __  /\ \__/
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/
         \ \_\   \ \_\  \ \____/  \ \_\
          \/_/    \/_/   \/___/    \/_/

       v1.3.1-dev
________________________________________________

 :: Method           : GET
 :: URL              : http://10.10.96.250/FUZZ
 :: Wordlist         : FUZZ: SecLists/Discovery/Web-Content/raft-medium-directories-lowercase.txt
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405
________________________________________________

config                  [Status: 301, Size: 312, Words: 20, Lines: 10]
docs                    [Status: 301, Size: 310, Words: 20, Lines: 10]
external                [Status: 301, Size: 314, Words: 20, Lines: 10]
server-status           [Status: 403, Size: 292, Words: 21, Lines: 11]
                        [Status: 302, Size: 0, Words: 1, Lines: 1]
:: Progress: [26584/26584] :: Job [1/1] :: 177 req/sec :: Duration: [0:02:41] :: Errors: 2 ::

```


---
## Task 4

###    Q1.    After applying the fc filter, how many results were returned?

```
  ffuf -u http://10.10.96.250/FUZZ -w SecLists/Discovery/Web-Content/raft-medium-files-lowercase.txt -fc 403

        /'___\  /'___\           /'___\
       /\ \__/ /\ \__/  __  __  /\ \__/
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/
         \ \_\   \ \_\  \ \____/  \ \_\
          \/_/    \/_/   \/___/    \/_/

       v1.3.1-dev
________________________________________________

 :: Method           : GET
 :: URL              : http://10.10.96.250/FUZZ
 :: Wordlist         : FUZZ: SecLists/Discovery/Web-Content/raft-medium-files-lowercase.txt
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405
 :: Filter           : Response status: 403
________________________________________________

index.php               [Status: 302, Size: 0, Words: 1, Lines: 1]
login.php               [Status: 200, Size: 1523, Words: 89, Lines: 77]
favicon.ico             [Status: 200, Size: 1406, Words: 5, Lines: 2]
logout.php              [Status: 302, Size: 0, Words: 1, Lines: 1]
robots.txt              [Status: 200, Size: 26, Words: 3, Lines: 2]
phpinfo.php             [Status: 302, Size: 0, Words: 1, Lines: 1]
.                       [Status: 302, Size: 0, Words: 1, Lines: 1]
php.ini                 [Status: 200, Size: 148, Words: 17, Lines: 5]
about.php               [Status: 200, Size: 4840, Words: 331, Lines: 109]
setup.php               [Status: 200, Size: 4066, Words: 308, Lines: 123]
security.php            [Status: 302, Size: 0, Words: 1, Lines: 1]
:: Progress: [16244/16244] :: Job [1/1] :: 124 req/sec :: Duration: [0:01:44] :: Errors: 0 ::

```
---
###    Q2.    After applying the mc filter, how many results were returned?

```
	ffuf -u http://10.10.96.250/FUZZ -w SecLists/Discovery/Web-Content/raft-medium-files-lowercase.txt -mc 200

        /'___\  /'___\           /'___\
       /\ \__/ /\ \__/  __  __  /\ \__/
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/
         \ \_\   \ \_\  \ \____/  \ \_\
          \/_/    \/_/   \/___/    \/_/

       v1.3.1-dev
________________________________________________

 :: Method           : GET
 :: URL              : http://10.10.96.250/FUZZ
 :: Wordlist         : FUZZ: SecLists/Discovery/Web-Content/raft-medium-files-lowercase.txt
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200
________________________________________________

favicon.ico             [Status: 200, Size: 1406, Words: 5, Lines: 2]
login.php               [Status: 200, Size: 1523, Words: 89, Lines: 77]
robots.txt              [Status: 200, Size: 26, Words: 3, Lines: 2]
php.ini                 [Status: 200, Size: 148, Words: 17, Lines: 5]
about.php               [Status: 200, Size: 4840, Words: 331, Lines: 109]
setup.php               [Status: 200, Size: 4066, Words: 308, Lines: 123]
:: Progress: [16244/16244] :: Job [1/1] :: 170 req/sec :: Duration: [0:01:50] :: Errors: 0 ::

```
---

###    Q3.    Which valuable file would have been hidden if you used -fc 403 instead of -fr?

```
 ffuf -u http://10.10.96.250/FUZZ -w SecLists/Discovery/Web-Content/raft-medium-files-lowercase.txt  -fr  '/\..*'

        /'___\  /'___\           /'___\
       /\ \__/ /\ \__/  __  __  /\ \__/
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/
         \ \_\   \ \_\  \ \____/  \ \_\
          \/_/    \/_/   \/___/    \/_/

       v1.3.1-dev
________________________________________________

 :: Method           : GET
 :: URL              : http://10.10.96.250/FUZZ
 :: Wordlist         : FUZZ: SecLists/Discovery/Web-Content/raft-medium-files-lowercase.txt
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405
 :: Filter           : Regexp: /\..*
________________________________________________

favicon.ico             [Status: 200, Size: 1406, Words: 5, Lines: 2]
logout.php              [Status: 302, Size: 0, Words: 1, Lines: 1]
robots.txt              [Status: 200, Size: 26, Words: 3, Lines: 2]
phpinfo.php             [Status: 302, Size: 0, Words: 1, Lines: 1]
index.php               [Status: 302, Size: 0, Words: 1, Lines: 1]
login.php               [Status: 200, Size: 1523, Words: 89, Lines: 77]
.                       [Status: 302, Size: 0, Words: 1, Lines: 1]
php.ini                 [Status: 200, Size: 148, Words: 17, Lines: 5]
about.php               [Status: 200, Size: 4840, Words: 331, Lines: 109]
setup.php               [Status: 200, Size: 4066, Words: 308, Lines: 123]
security.php            [Status: 302, Size: 0, Words: 1, Lines: 1]
wp-forum.phps           [Status: 403, Size: 292, Words: 21, Lines: 11]
:: Progress: [16244/16244] :: Job [1/1] :: 173 req/sec :: Duration: [0:01:48] :: Errors: 0 ::

```

---

Task 5


###    Q1.    What is the parameter you found?

```
 ffuf -u 'http://10.10.67.54/sqli-labs/Less-1/?FUZZ=1' -c -w SecLists/Discovery/Web-Content/burp-parameter-names.txt -fw 39

        /'___\  /'___\           /'___\
       /\ \__/ /\ \__/  __  __  /\ \__/
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/
         \ \_\   \ \_\  \ \____/  \ \_\
          \/_/    \/_/   \/___/    \/_/

       v1.3.1-dev
________________________________________________

 :: Method           : GET
 :: URL              : http://10.10.67.54/sqli-labs/Less-1/?FUZZ=1
 :: Wordlist         : FUZZ: SecLists/Discovery/Web-Content/burp-parameter-names.txt
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405
 :: Filter           : Response words: 39
________________________________________________

id                      [Status: 200, Size: 721, Words: 37, Lines: 29]
:: Progress: [2588/2588] :: Job [1/1] :: 184 req/sec :: Duration: [0:00:25] :: Errors: 0 ::

```
---

###    Q2.    What is the highest valid id?
```
seq 0 255 | ffuf -u 'http://10.10.67.54/sqli-labs/Less-1/?id=FUZZ' -c -w - -fw 33

        /'___\  /'___\           /'___\
       /\ \__/ /\ \__/  __  __  /\ \__/
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/
         \ \_\   \ \_\  \ \____/  \ \_\
          \/_/    \/_/   \/___/    \/_/

       v1.3.1-dev
________________________________________________

 :: Method           : GET
 :: URL              : http://10.10.67.54/sqli-labs/Less-1/?id=FUZZ
 :: Wordlist         : FUZZ: -
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405
 :: Filter           : Response words: 33
________________________________________________

3                       [Status: 200, Size: 726, Words: 37, Lines: 29]
4                       [Status: 200, Size: 725, Words: 37, Lines: 29]
6                       [Status: 200, Size: 728, Words: 37, Lines: 29]
7                       [Status: 200, Size: 725, Words: 37, Lines: 29]
10                      [Status: 200, Size: 725, Words: 37, Lines: 29]
9                       [Status: 200, Size: 725, Words: 37, Lines: 29]
8                       [Status: 200, Size: 723, Words: 37, Lines: 29]
12                      [Status: 200, Size: 725, Words: 37, Lines: 29]
5                       [Status: 200, Size: 728, Words: 37, Lines: 29]
11                      [Status: 200, Size: 725, Words: 37, Lines: 29]
2                       [Status: 200, Size: 731, Words: 37, Lines: 29]
1                       [Status: 200, Size: 721, Words: 37, Lines: 29]
14                      [Status: 200, Size: 725, Words: 37, Lines: 29]
:: Progress: [256/256] :: Job [1/1] :: 175 req/sec :: Duration: [0:00:05] :: Errors: 0 ::

```
---
###    Q3.    What is Dummy's password?

```
ffuf -u http://10.10.67.54/sqli-labs/Less-11/ -c -w SecLists/Passwords/Leaked-Databases/hak5.txt -X POST -d 'uname=Dummy&passwd=FUZZ&submit=Submit' -fs 1435 -H 'Content-Type: application/x-www-form-urlencoded'

        /'___\  /'___\           /'___\
       /\ \__/ /\ \__/  __  __  /\ \__/
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/
         \ \_\   \ \_\  \ \____/  \ \_\
          \/_/    \/_/   \/___/    \/_/

       v1.3.1-dev
________________________________________________

 :: Method           : POST
 :: URL              : http://10.10.67.54/sqli-labs/Less-11/
 :: Wordlist         : FUZZ: SecLists/Passwords/Leaked-Databases/hak5.txt
 :: Header           : Content-Type: application/x-www-form-urlencoded
 :: Data             : uname=Dummy&passwd=FUZZ&submit=Submit
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405
 :: Filter           : Response size: 1435
________________________________________________

p@ssword                [Status: 200, Size: 1526, Words: 100, Lines: 50]
:: Progress: [2351/2351] :: Job [1/1] :: 180 req/sec :: Duration: [0:00:17] :: Errors: 0 ::

```

---

Task 6

ffuf may not be as efficient as specialized tools when it comes to subdomain enumeration but it's possible to do.

```
$ ffuf -u http://FUZZ.mydomain.com -c -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt
```
You could compare the results obtained with direct subdomain enumeration and with vhost enumeration:
```
$ ffuf -u http://FUZZ.mydomain.com -c -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt -fs 0
$ ffuf -u http://mydomain.com -c -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt -H 'Host: FUZZ.mydomain.com' -fs 0
```
---

Task 7


Whether it' for network pivoting or for using BurpSuite plugins you can send all the ffuf traffic through a web proxy (HTTP or SOCKS5).
```
$ ffuf -u http://10.10.67.54/ -c -w /usr/share/seclists/Discovery/Web-Content/common.txt -x http://127.0.0.1:8080
```
It's also possible to send only matches to your proxy for replaying:
```
$ ffuf -u http://10.10.67.54/ -c -w /usr/share/seclists/Discovery/Web-Content/common.txt -replay-proxy http://127.0.0.1:8080
```
This may be useful if you don't need all the traffic to traverse an upstream proxy and want to minimize resource usage or to avoid polluting your proxy history.

---

Task 8


As you start to use ffuf more, some options will prove to be very useful depending on your situation. For example, -ic allows you to ignore comments in wordlists that such as headers, copyright notes, comments, etc
```
$ head /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt
# directory-list-2.3-medium.txt
#
# Copyright 2007 James Fisher
#
# This work is licensed under the Creative Commons
# Attribution-Share Alike 3.0 License. To view a copy of this
# license, visit http://creativecommons.org/licenses/by-sa/3.0/
# or send a letter to Creative Commons, 171 Second Street,
# Suite 300, San Francisco, California, 94105, USA.
#

$ ffuf -u http://10.10.67.54/FUZZ -c -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -ic -fs 0
```
