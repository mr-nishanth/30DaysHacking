#	Day 22

#### 04-02-2022

# TryHackMe Rank  37832 ( 56 Streak )

[TryHackMe Content Discovery](https://tryhackme.com/room/contentdiscovery)

# Content Discovery

-	Firstly, we should ask, in the context of web application security, what is content? Content can be many things, a file, video, picture, backup, a website feature.

-	When we talk about content discovery, we're not talking about the obvious things we can see on a website; it's the things that aren't immediately presented to us and that weren't always intended for public access.

-	This content could be, for example, pages or portals intended for staff usage, older versions of the website, backup files, configuration files, administration panels, etc.

-	There are three main ways of discovering content on a website which we'll cover.
	-	Manually, Automated and OSINT (Open-Source Intelligence).



# Manually
Here are multiple places we can manually check on a website to start discovering more content.


##	Robots.txt

-	The robots.txt file is a document that tells search engines which pages they are and aren't allowed to show on their search engine results or ban specific search engines from crawling the website altogether.
-	It can be common practice to restrict certain website areas so they aren't displayed in search engine results.
-	These pages may be areas such as administration portals or files meant for the website's customers.
-	This file gives us a great list of locations on the website that the owners don't want us to discover as penetration testers.



What is the directory in the robots.txt that isn't allowed to be viewed by web crawlers?

```
curl  -v http://10.10.228.240/robots.txt
*   Trying 10.10.228.240:80...
* Connected to 10.10.228.240 (10.10.228.240) port 80 (#0)
> GET /robots.txt HTTP/1.1
> Host: 10.10.228.240
> User-Agent: curl/7.81.0
> Accept: */*
>
* Mark bundle as not supporting multiuse
< HTTP/1.1 200 OK
< Server: nginx/1.18.0 (Ubuntu)
< Date: Fri, 04 Feb 2022 05:32:57 GMT
< Content-Type: text/plain
< Content-Length: 46
< Last-Modified: Mon, 23 Aug 2021 08:53:28 GMT
< Connection: keep-alive
< ETag: "61236208-2e"
< Accept-Ranges: bytes
<
User-agent: *
Allow: /
* Connection #0 to host 10.10.228.240 left intact
Disallow: /staff-portal

```
---

##	Favicon

-	The favicon is a small icon displayed in the browser's address bar or tab used for branding a website.


-	Sometimes when frameworks are used to build a website, a favicon that is part of the installation gets leftover, and if the website developer doesn't replace this with a custom one, this can give us a clue on what framework is in use.

-	OWASP host a database of common framework icons that you can use to check against the targets favicon https://wiki.owasp.org/index.php/OWASP_favicon_database. Once we know the framework stack, we can use external resources to discover more about it (see next section).


What framework did the favicon belong to?

```
curl -v https://static-labs.tryhackme.cloud/sites/favicon/images/favicon.ico | md5sum
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0*   Trying 172.67.222.63:443...
* Connected to static-labs.tryhackme.cloud (172.67.222.63) port 443 (#0)
* ALPN, offering h2
* ALPN, offering http/1.1
*  CAfile: /etc/ssl/certs/ca-certificates.crt
*  CApath: /etc/ssl/certs
} [5 bytes data]
* TLSv1.3 (OUT), TLS handshake, Client hello (1):
} [512 bytes data]
* TLSv1.3 (IN), TLS handshake, Server hello (2):
{ [122 bytes data]
* TLSv1.3 (IN), TLS handshake, Encrypted Extensions (8):
{ [19 bytes data]
* TLSv1.3 (IN), TLS handshake, Certificate (11):
{ [2340 bytes data]
* TLSv1.3 (IN), TLS handshake, CERT verify (15):
{ [79 bytes data]
* TLSv1.3 (IN), TLS handshake, Finished (20):
{ [52 bytes data]
* TLSv1.3 (OUT), TLS change cipher, Change cipher spec (1):
} [1 bytes data]
* TLSv1.3 (OUT), TLS handshake, Finished (20):
} [52 bytes data]
* SSL connection using TLSv1.3 / TLS_AES_256_GCM_SHA384
* ALPN, server accepted to use h2
* Server certificate:
*  subject: C=US; ST=California; L=San Francisco; O=Cloudflare, Inc.; CN=sni.cloudflaressl.com
*  start date: Jul 13 00:00:00 2021 GMT
*  expire date: Jul 12 23:59:59 2022 GMT
*  subjectAltName: host "static-labs.tryhackme.cloud" matched cert's "*.tryhackme.cloud"
*  issuer: C=US; O=Cloudflare, Inc.; CN=Cloudflare Inc ECC CA-3
*  SSL certificate verify ok.
* Using HTTP2, server supports multiplexing
* Connection state changed (HTTP/2 confirmed)
* Copying HTTP/2 data in stream buffer to connection buffer after upgrade: len=0
} [5 bytes data]
* Using Stream ID: 1 (easy handle 0x55ea325726d0)
} [5 bytes data]
> GET /sites/favicon/images/favicon.ico HTTP/2
> Host: static-labs.tryhackme.cloud
> user-agent: curl/7.81.0
> accept: */*
>
{ [5 bytes data]
* TLSv1.3 (IN), TLS handshake, Newsession Ticket (4):
{ [230 bytes data]
* TLSv1.3 (IN), TLS handshake, Newsession Ticket (4):
{ [230 bytes data]
* old SSL session ID is stale, removing
{ [5 bytes data]
* Connection state changed (MAX_CONCURRENT_STREAMS == 256)!
} [5 bytes data]
< HTTP/2 200
< date: Fri, 04 Feb 2022 05:50:15 GMT
< content-type: image/vnd.microsoft.icon
< content-length: 1406
< x-amz-id-2: viKAzd6SPlq3vcwWuKy5sbW/kEHTa93EERSrszCQ5/ssk4v9yqVHpeCuZqoz6WnQPfZQiR3BlUI=
< x-amz-request-id: 850GYDC10TEVDCB0
< last-modified: Mon, 24 Jan 2022 16:49:56 GMT
< etag: "f276b19aabcb4ae8cda4d22625c6735f"
< cache-control: max-age=14400
< cf-cache-status: HIT
< age: 296
< accept-ranges: bytes
< expect-ct: max-age=604800, report-uri="https://report-uri.cloudflare.com/cdn-cgi/beacon/expect-ct"
< report-to: {"endpoints":[{"url":"https:\/\/a.nel.cloudflare.com\/report\/v3?s=9Uf534mKuodg4q5rG4R0Cz3rPwEUbQd7TTj%2BykTn9MPJAYYnGWsDEOn%2B1OouOO30po3rK2%2BWYc6VoYKdYhlQwSam5h14VpyOlpvVfOYjP9AVA%2F0XBr7yfxeEWx9lPbM4EoCp9xEjMiqriki9A2w%3D"}],"group":"cf-nel","max_age":604800}
< nel: {"success_fraction":0,"report_to":"cf-nel","max_age":604800}
< server: cloudflare
< cf-ray: 6d819ed36bb96eef-BOM
< alt-svc: h3=":443"; ma=86400, h3-29=":443"; ma=86400
<
{ [676 bytes data]
100  1406  100  1406    0     0   4498      0 --:--:-- --:--:-- --:--:--  4506
* Connection #0 to host static-labs.tryhackme.cloud left intact
f276b19aabcb4ae8cda4d22625c6735f  -


```
	- Take f276b19aabcb4ae8cda4d22625c6735f and go to [Favicon database](https://wiki.owasp.org/index.php/OWASP_favicon_database)

```


    OWASP favicon database
    f276b19aabcb4ae8cda4d22625c6735f:cgiirc (0.5.9)
    14 KB (2,567 words) - 23:55, 12 December 2013

```

---

## Sitemap.xml

-	Unlike the robots.txt file, which restricts what search engine crawlers can look at, the sitemap.xml file gives a list of every file the website owner wishes to be listed on a search engine.

-	These can sometimes contain areas of the website that are a bit more difficult to navigate to or even list some old webpages that the current site no longer uses but are still working behind the scenes.

-	Sitemap is responsiable for indexing in SEO


What is the path of the secret area that can be found in the sitemap.xml file?


```
curl  -v http://10.10.228.240/sitemap.xml
*   Trying 10.10.228.240:80...
* Connected to 10.10.228.240 (10.10.228.240) port 80 (#0)
> GET /sitemap.xml HTTP/1.1
> Host: 10.10.228.240
> User-Agent: curl/7.81.0
> Accept: */*
>
* Mark bundle as not supporting multiuse
< HTTP/1.1 200 OK
< Server: nginx/1.18.0 (Ubuntu)
< Date: Fri, 04 Feb 2022 05:38:48 GMT
< Content-Type: application/xml; charset=utf-8
< Transfer-Encoding: chunked
< Connection: keep-alive
< X-FLAG: THM{HEADER_FLAG}
<
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    <url>
        <loc>http://10.10.228.240/</loc>
        <lastmod>2021-07-19T13:07:32+00:00</lastmod>
        <priority>1.00</priority>
    </url>
    <url>
        <loc>http://10.10.228.240/news</loc>
        <lastmod>2021-07-19T13:07:32+00:00</lastmod>
        <priority>0.80</priority>
    </url>
    <url>
        <loc>http://10.10.228.240/news/article?id=1</loc>
        <lastmod>2021-07-19T13:07:32+00:00</lastmod>
        <priority>0.80</priority>
    </url>
    <url>
        <loc>http://10.10.228.240/news/article?id=2</loc>
        <lastmod>2021-07-19T13:07:32+00:00</lastmod>
        <priority>0.80</priority>
    </url>
    <url>
        <loc>http://10.10.228.240/news/article?id=3</loc>
        <lastmod>2021-07-19T13:07:32+00:00</lastmod>
        <priority>0.80</priority>
    </url>
    <url>
        <loc>http://10.10.228.240/contact</loc>
        <lastmod>2021-07-19T13:07:32+00:00</lastmod>
        <priority>0.80</priority>
    </url>
    <url>
        <loc>http://10.10.228.240/customers/login</loc>
        <lastmod>2021-07-19T13:07:32+00:00</lastmod>
        <priority>0.80</priority>
    </url>
    <url>
        <loc>http://10.10.228.240/s3cr3t-area</loc>
        <lastmod>2021-07-19T13:07:32+00:00</lastmod>
        <priority>0.80</priority>
    </url>
* Connection #0 to host 10.10.228.240 left intact
</urlset>

```
---

##	HTTP Headers


-	When we make requests to the web server, the server returns various HTTP headers.

-	These headers can sometimes contain useful information such as the webserver software and possibly the programming/scripting language in use.


What is the flag value from the X-FLAG header?

```

 curl http://10.10.228.240 -v
*   Trying 10.10.228.240:80...
* Connected to 10.10.228.240 (10.10.228.240) port 80 (#0)
> GET / HTTP/1.1
> Host: 10.10.228.240
> User-Agent: curl/7.81.0
> Accept: */*
>
* Mark bundle as not supporting multiuse
< HTTP/1.1 200 OK
< Server: nginx/1.18.0 (Ubuntu)
< Date: Fri, 04 Feb 2022 05:57:45 GMT
< Content-Type: text/html; charset=UTF-8
< Transfer-Encoding: chunked
< Connection: keep-alive
< X-FLAG: THM{HEADER_FLAG}
<
<!--
This page is temporary while we work on the new homepage @ /new-home-beta
-->
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Acme IT Support - Home</title>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
        <link rel="stylesheet" href="https://pro.fontawesome.com/releases/v5.12.0/css/all.css" integrity="sha384-ekOryaXPbeCpWQNxMwSWVvQ0+1VrStoPJq54shlYhR8HzQgig1v5fas6YgOqLoKz" crossorigin="anonymous">
        <link rel="stylesheet" href="/assets/bootstrap.min.css">
    <link rel="stylesheet" href="/assets/style.css">
</head>
<body>
    <nav class="navbar navbar-inverse navbar-fixed-top">
        <div class="container">
            <div class="navbar-header">
                <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#navbar" aria-expanded="false" aria-controls="navbar">
                    <span class="sr-only">Toggle navigation</span>
                    <span class="icon-bar"></span>
                    <span class="icon-bar"></span>
                    <span class="icon-bar"></span>
                </button>
                <a class="navbar-brand" href="#">Acme IT Support</a>
            </div>
            <div id="navbar" class="collapse navbar-collapse">
                <ul class="nav navbar-nav">
                    <li class="active"><a href="/">Home</a></li>
                    <li><a href="/news">News</a></li>
                    <li><a href="/contact">Contact</a></li>
                    <li><a href="/customers">Customers</a></li>
                </ul>
            </div><!--/.nav-collapse -->
        </div>
    </nav><div class="container" style="padding-top:60px">
    <h1 class="text-center">Acme IT Support</h1>
    <div class="row">
        <div class="col-md-8 col-md-offset-2 text-center">
            <img src="/assets/staff.png">
            <p class="welcome-msg">Our dedicated staff are ready <a href="/secret-page">to</a> assist you with your IT problems.</p>
        </div>
    </div>
</div>
<script src="/assets/jquery.min.js"></script>
<script src="/assets/bootstrap.min.js"></script>
<script src="/assets/site.js"></script>
</body>
</html>
<!--
Page Generated in 0.03253 Seconds using the THM Framework v1.2 ( https://static-labs.tryhackme.cloud/sites/thm-web-framework )
* Connection #0 to host 10.10.228.240 left intact
-->

```

---


## Automated Discovery

What is Automated Discovery?

-	Automated discovery is the process of using tools to discover content rather than doing it manually.

-	This process is automated as it usually contains hundreds, thousands or even millions of requests to a web server.

-	These requests check whether a file or directory exists on a website, giving us access to resources we didn't previously know existed. This process is made possible by using a resource called wordlists.


What are wordlists?

-	Wordlists are just text files that contain a long list of commonly used words;

-	they can cover many different use cases. For example, a password wordlist would include the most frequently used passwords, whereas we're looking for content in our case, so we'd require a list containing the most commonly used directory and file names.

-	An excellent resource for wordlists that is preinstalled on the THM AttackBox is https://github.com/danielmiessler/SecLists which Daniel Miessler curates.


Automation Tools

-	Although there are many different content discovery tools available, all with their features and flaws, we're going to cover three which are preinstalled on our attack box, ffuf, dirb and gobuster.




Using ffuf:

```
user@machine$ ffuf -w /usr/share/wordlists/SecLists/Discovery/Web-Content/common.txt -u http://10.10.228.240/FUZZ
```

Using dirb:

```
user@machine$ dirb http://10.10.228.240/ /usr/share/wordlists/SecLists/Discovery/Web-Content/common.txt
```

Using Gobuster:
```
user@machine$ gobuster dir --url http://10.10.228.240/ -w /usr/share/wordlists/SecLists/Discovery/Web-Content/common.txt
```
