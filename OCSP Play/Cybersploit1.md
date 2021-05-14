

# NMAP

```bash
PORT   STATE SERVICE REASON  VERSION

22/tcp open  ssh     syn-ack OpenSSH 5.9p1 Debian 5ubuntu1.10 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   1024 01:1b:c8:fe:18:71:28:60:84:6a:9f:30:35:11:66:3d (DSA)
| ssh-dss AAAAB3NzaC1kc3MAAACBAIvXzKChMFQjoRVJPY3oKyzdX27i0MDEbmLG3yRuSLiPgYBF4jGq+7mn848WJSbLPpNAa/6xMgQb5BhhSTHgA77kg1gS8IhXvpoMlixJoJmGVBAqobxKAEbZnfbSKfjtJk7jI9mfoZjmOhznnzEwsODjzEDqtBYGEo4Mf/9KUX/jAAAAFQCdv46IJ36Dkyv7av5KP+Ghs7TzSwAAAIAVxh4PVUljX8ECckYq40LJ/jRL4qWhLSctMRK9J34+WSe2RHpRKRB+0eTpjffzNktRgFgKJJwW+3kd4HzOROMDvLEuhdrALiiNwqxYzIv70i+mwxNWoghoUcslgXOmeTAvyiW/jNU/Uav39nutehkX62PfvTRrulRzlbayMbkU4AAAAIABwdKXqzEKdPr7L+bCBLEe06k3Vd2bWvTOD3wwGzz+rzvmcexiPvgc1xRYE6Fno0QG2yfow9cvgrajyiDoMdUVogH7N8hm3+KbaKnO8mA7jkxVMACpfanwHRVJfM/+PHPOvML2v8QJ7JYGRgwlTyI5UxqUw9YuJSNJWThRWyw49A==
|   2048 d9:53:14:a3:7f:99:51:40:3f:49:ef:ef:7f:8b:35:de (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDAgVBhkY/5TpbZpI7WmUiKX7koUuK6+K+usitE5rg6V326mmdJKt69IFmq4gcgpqXuImopLdGczY/8ulNoEj3aaPckhAVG5CLmlGMvRR5h2AW6pI7pUI9NkyAtLkm0fkyLDKLvKS32KSQ9jSdVPeXeCE0EpGJW5J5QOMWxEbS4z3XnLlkLqGz/wPRCwupYjJ+UsAgHfJVDKC7foPZj1ft/XX9oqcNkcykxz3AQtn0sEEZ8MfuWyePiVgYmsDLl0tBGdm0p9GExfWE0KAhpScWaxJzKmSFfzAjVpg60SyegBAhcIs0xMS18cBAS05OHNLKmMCfzOqm+8AjbVAyl+RF3
|   256 ef:43:5b:d0:c0:eb:ee:3e:76:61:5c:6d:ce:15:fe:7e (ECDSA)
|_ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBPHaPjoo6jLLN7KcEqjZCEXgAdRiejIMlLihehQ7+dmmxs4SqtjA8I8EjiqZpVL6kgSmDX5BpNxmyHjWJRHIC9U=

80/tcp open  http    syn-ack Apache httpd 2.2.22 ((Ubuntu))
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.2.22 (Ubuntu)
|_http-title: Hello Pentester!
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

```

# WEB

![image](https://user-images.githubusercontent.com/68326057/118251837-b4371d80-b4c5-11eb-825c-62f0964d8d25.png)

```bash
username:itsskv
```

## robots.txt

```bash
Y3liZXJzcGxvaXR7eW91dHViZS5jb20vYy9jeWJlcnNwbG9pdH0=
```

```bash
echo "Y3liZXJzcGxvaXR7eW91dHViZS5jb20vYy9jeWJlcnNwbG9pdH0=" | base64 -d
cybersploit{youtube.com/c/cybersploit}
```

# SSH

Login with above username and password :- cybersploit{youtube.com/c/cybersploit} 

## USERS

![image](https://user-images.githubusercontent.com/68326057/118253025-12183500-b4c7-11eb-940c-428291debe24.png)

![image](https://user-images.githubusercontent.com/68326057/118253069-1cd2ca00-b4c7-11eb-8df2-3c52b6220889.png)

![image](https://user-images.githubusercontent.com/68326057/118254284-90290b80-b4c8-11eb-883d-2cb3d676416c.png)

![image](https://user-images.githubusercontent.com/68326057/118254319-9919dd00-b4c8-11eb-911d-27f3ea7104f6.png)

# ROOT

![image](https://user-images.githubusercontent.com/68326057/118254351-a20aae80-b4c8-11eb-9db7-b100d4359fec.png)

