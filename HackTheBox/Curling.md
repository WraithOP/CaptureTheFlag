
![image](https://user-images.githubusercontent.com/68326057/117125257-eb674980-adb6-11eb-8326-9a0dc71190e4.png)

# NMAP

```bash
PORT   STATE SERVICE REASON  VERSION

22/tcp open  ssh     syn-ack OpenSSH 7.6p1 Ubuntu 4 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 8a:d1:69:b4:90:20:3e:a7:b6:54:01:eb:68:30:3a:ca (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDGsat32aGJHTbu0gQU9FYIMlMqF/uiytTZ6lsW+EIodvlPp6Cu5VHfs2iEFd5nfn0s+97qTfJ258lf7Gk3rHrULvCrUif2wThIeW3m4fS5j6O2ZPjv0Gl5g02TItSklwQmjJfyH0KR5b1D9bGCXQV3Gm585DD8wZrOpTxDjGCnmByYoHitfG6sa1LC7Sckb8g9Km40fvfKPPWMHgzUhXC3g3wXyjXXeByZvhjbAAuOv7MKda6MjeNUH71hkiQRkTwZ8qqY9fbDDnSKOHdkC2Scs+8tcpz8AIekc/hmDSn+QKbs+3iV0FLoW9TOPmT8xz45etnqW6DhhlcrO7aFju33
|   256 9f:0b:c2:b2:0b:ad:8f:a1:4e:0b:f6:33:79:ef:fb:43 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBN2TI0Uv8Dr/6h+pEZ34kyKx7H6tD1gC/FB4q19PO4klA767pC7YVB3NTdEs2TGI+8XAevVqHiQv/8ZniMwG9IU=
|   256 c1:2a:35:44:30:0c:5b:56:6a:3f:a5:cc:64:66:d9:a9 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAILhmU6S36IrO41biIUZrXnzMGw3OZmLLHS/DxqKLPkVU

80/tcp open  http    syn-ack Apache httpd 2.4.29 ((Ubuntu))
|_http-favicon: Unknown favicon MD5: 1194D7D32448E1F90741A97B42AF91FA
|_http-generator: Joomla! - Open Source Content Management
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: Home
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

```


# WEB

![image](https://user-images.githubusercontent.com/68326057/117125995-d6d78100-adb7-11eb-9def-ecde46713666.png)

--> secret.txt

```bash
Q3VybGluZzIwMTgh -> Curling2018!(After decoding it in base64)
```

![image](https://user-images.githubusercontent.com/68326057/117126601-99bfbe80-adb8-11eb-918b-06d3401a68eb.png)

```bash
Super User named Floris
```

# Logged in 

```
Floris:Curling2018!
```

# Joomla -CMS

/administrator

![image](https://user-images.githubusercontent.com/68326057/117127553-d9d37100-adb9-11eb-8d94-3e1895693f62.png)

```bash
Old Username and password worked again
````

```bash
http://10.10.10.150/administrator/index.php?option=com_templates&view=template&id=506&file=aG9tZQ==
```

![image](https://user-images.githubusercontent.com/68326057/117129337-2d46be80-adbc-11eb-8ee8-019b5ebec8f8.png)

1. add new file name shell.php
2. paste code
3. vist --> http://10.10.10.150/templates/protostar/shell.php


![image](https://user-images.githubusercontent.com/68326057/117129990-0d63ca80-adbd-11eb-9f52-8dd3ffee4207.png)

# user - wwwdata

![image](https://user-images.githubusercontent.com/68326057/117130069-28363f00-adbd-11eb-9681-2c45bf800267.png)


![image](https://user-images.githubusercontent.com/68326057/117130291-78ad9c80-adbd-11eb-9099-accbd60243d6.png)

```bash
00000000: 425a 6839 3141 5926 5359 819b bb48 0000  BZh91AY&SY...H..
00000010: 17ff fffc 41cf 05f9 5029 6176 61cc 3a34  ....A...P)ava.:4
00000020: 4edc cccc 6e11 5400 23ab 4025 f802 1960  N...n.T.#.@%...`
00000030: 2018 0ca0 0092 1c7a 8340 0000 0000 0000   ......z.@......
00000040: 0680 6988 3468 6469 89a6 d439 ea68 c800  ..i.4hdi...9.h..
00000050: 000f 51a0 0064 681a 069e a190 0000 0034  ..Q..dh........4
00000060: 6900 0781 3501 6e18 c2d7 8c98 874a 13a0  i...5.n......J..
00000070: 0868 ae19 c02a b0c1 7d79 2ec2 3c7e 9d78  .h...*..}y..<~.x
00000080: f53e 0809 f073 5654 c27a 4886 dfa2 e931  .>...sVT.zH....1
00000090: c856 921b 1221 3385 6046 a2dd c173 0d22  .V...!3.`F...s."
000000a0: b996 6ed4 0cdb 8737 6a3a 58ea 6411 5290  ..n....7j:X.d.R.
000000b0: ad6b b12f 0813 8120 8205 a5f5 2970 c503  .k./... ....)p..
000000c0: 37db ab3b e000 ef85 f439 a414 8850 1843  7..;.....9...P.C
000000d0: 8259 be50 0986 1e48 42d5 13ea 1c2a 098c  .Y.P...HB....*..
000000e0: 8a47 ab1d 20a7 5540 72ff 1772 4538 5090  .G.. .U@r..rE8P.
000000f0: 819b bb48                                ...H
```

1. copy paste on attacker machine.

![image](https://user-images.githubusercontent.com/68326057/117131531-308f7980-adbf-11eb-8214-43c272810b4e.png)

2. file backup

```bash
backup: bzip2 compressed data, block size = 900k
```

3. unzip it . cat password.txt

```bash
5d<wdCbdZu)|hChXll
```

## UNAME -a
```bash
Linux curling 4.15.0-22-generic #24-Ubuntu SMP Wed May 16 12:15:17 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

![image](https://user-images.githubusercontent.com/68326057/117132183-13a77600-adc0-11eb-9d20-1adc824cb786.png)
