#	Day 23

#### 05-02-2022

# TryHackMe Rank  35665 ( 57 Streak )

[TryHackMe Content Discovery](https://tryhackme.com/room/phishingemails1tryoe)


# Phishing Emails 1

### Intro

-	Spam and Phishing are common social engineering attacks.
-	In social engineering, phishing attack vectors can be a phone call, a text message, or an email.
-	The first email classified as spam dates back to 1978, and it's still thriving today in 2022.

### Email

-	The man who invented the concept of emails and made the @ symbol famous. T
-	he person responsible for the contribution to the way we communicate was *_Ray Tomlinson_*.
-	The invention of the email dates back to the 1970s for *ARPANET*

```
So, what makes up an email address?

    1.	User Mailbox (or Username)
    2.  @
    3.	Domain

```

### Email Delivery

-	There are 3 specific protocols involved to facilitate the outgoing and incoming email messages, and they are briefly listed below.

	-    SMTP (Simple Mail Transfer Protocol) - It is utilized to handle the sending of emails.

	-    POP3 (Post Office Protocol) - Is responsible transferring email between a client and a mail server.

	-    IMAP (Internet Message Access Protocol) - Is responsible transferring email between a client and a mail server.

-	You should have noticed that both POP3 and IMAP have the same definition. But there are differences between the two.

-	The difference between the two is listed below:

	-	POP3

	    -	Emails are downloaded and stored on a single device.
	    -	Sent messages are stored on the single device from which the email was sent.
	    -	Emails can only be accessed from the single device the emails were downloaded to.
	    -	If you want to keep messages on the server, make sure the setting "Keep email on server" is enabled, or all messages are deleted from the server once downloaded to the single device's app or software.

	-	IMAP

	   -	Emails are stored on the server and can be downloaded to multiple devices.
	   -    Sent messages are stored on the server.
	   -    Messages can be synced and accessed across multiple devices.
---


[CyberChef encoded](https://gchq.github.io/CyberChef/)

---

### Type of Phishing
Different types of malicious emails can be classified as one of the following:

-    Spam - unsolicited junk emails sent out in bulk to a large number of recipients. The more malicious variant of Spam is known as MalSpam.
-    Phishing -  emails sent to a target(s) purporting to be from a trusted entity to lure individuals into providing sensitive information.
-    Spear phishing - takes phishing a step further by targeting a specific individual(s) or organization seeking sensitive information.
-    Whaling - is similar to spear phishing, but it's targeted specifically to C-Level high-position individuals (CEO, CFO, etc.), and the objective is the same.
-    Smishing - takes phishing to mobile devices by targeting mobile users with specially crafted text messages.
-    Vishing - is similar to smishing, but instead of using text messages for the social engineering attack, the attacks are based on voice calls.
