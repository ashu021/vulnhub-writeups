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

