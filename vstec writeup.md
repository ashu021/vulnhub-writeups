\# enumeration
--------------

\# I used Nmap for enumeration and scanning.

*\# nmap -sV -sC -O -A 10.0.2.7*

\# These options are used for aggressive scan and os fingerprinting, results are
given below:

![](media/6a7eaa5a5d257061fcaf115a7646d67f.png)

\#

Running dirb results are given below:

![](media/fca693827fbfe9bd9550cf013daf6d81.png)

\# there are important directories that , I found out using dirb ,it is very
useful for finding hidden sub-directories and in any website.

\# using dirb found the directory, <http://10.0.2.7/secret> this is a basic
wordpress html page.

\# Results are given below.

![](media/40e41a7670360b82612b8ab949d56dd9.png)

\# I saw port 21 is open that is running ftp service, I searched for the
exploits using searchsploit.

\# Results for the version running on port 21 for ftp service:

![](media/2a031af6caf7e41a59d790a1cdbc1fa4.png)

\# Exploitation
---------------

\# Here I used metasploit to exploit the vulnerability on port 21.

\# Results are given below:

![](media/a3c3e867daccba8f9f09f0993b82ad91.png)

\# using Metasploit I gained the shell.

![](media/7119ad89ee1fa6b9d15621bf8f9fd4f7.png)

\# privelage esclation 
-----------------------

\# we just need to gain the root access in this machine there is no flag as such
in this vulnhub machine.

![](media/8c1062a719413f9fa8c1ca8143a75912.png)

\# Here we gained the root access:

\# Results are shown below:

![](media/93ac539f4277600c3212170315986712.png)

\#This is a beginner level pentesting vm from Vulnhub, As I am a beginner I
chose to start with the basic one to get an idea.
