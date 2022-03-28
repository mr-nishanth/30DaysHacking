```

One of the main problems of web penetration testing is not knowing where anything is. Basic reconnaissance can tell you where some files and directories are; however, some of the more hidden stuff is often hidden away from the eyes of users. This is where gobuster comes in, the idea behind gobuster is that it tries to find valid directories from a wordlist of possible directories. gobuster can also be used to valid subdomains using the same method.

obuster dir -x xxa -k  -a <user-agent -w /usr/share/wordlists/dirb/common.txt -u <url>

x for extension
k for skip ssl verification
w wordlist
a for user agent
u for url
https://gist.github.com/pzb/b4b6f57144aea7827ae4


nikto is a popular web scanning tool that allows users to find common web vulnerabilities. It is commonly used to check for common CVE's such as shellshock, and to get general information about the web server that you're enumerating.


nikto -h http://10.10.238.231 -nossl -Plugins dir_traversal


-> h or host is used for specifice the host

-> if the host have ssl cert means set -ssl else -nossl

-> -Plugins for set specifice the plugins

```