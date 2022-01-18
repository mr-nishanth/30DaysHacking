```

nikto is a popular web scanning tool that allows users to find common web vulnerabilities. It is commonly used to check for common CVE's such as shellshock, and to get general information about the web server that you're enumerating.


nikto -h http://10.10.238.231 -nossl -Plugins dir_traversal


-> h or host is used for specifice the host

-> if the host have ssl cert means set -ssl else -nossl

-> -Plugins for set specifice the plugins

```