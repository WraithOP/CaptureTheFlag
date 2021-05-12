
# NMAP

```bash
PORT   STATE SERVICE REASON  VERSION
21/tcp open  ftp     syn-ack vsftpd 3.0.3
22/tcp open  ssh     syn-ack OpenSSH 8.0 (protocol 2.0)
| ssh-hostkey: 
|   3072 de:5b:0e:b5:40:aa:43:4d:2a:83:31:14:20:77:9c:a1 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDfSHQR3OtIeAUFx18phN/nfAIQ2uGHuJs0epoqF184E4Xr8fkjSFJHdA6GsVyGUjdlPqylT8Lpa+UhSSegb8sm1So8Nz42bthsftsOxMQVb/tpQzMUfjcxQOiyVmgxfEqs2Zzdv6GtxwgZWhKHt7T369ejxnVrZhn0m6jzQNfRhVoQe/jC20RKvBf8l8s6/SusbZR5SFfsg71KyrSKOXOxs12GhXkdbP32K3sXVEpWgfCfmIZAc2ZxNtL5uPCM4AOfjIFJHl1z9EX04ZjQ1rMzzOh9pD/b+W2mXt2nQGzRPnc8LyGDE0hFtw4+lBCoiH8zIt14S7dwbFFV1mWxbtZXVf7JhPiZDM2vBfqyowsDZ5oc2qyR+JEU4pqeVhRygs41isej/el19G8+ehz4W07KR97eM2omB25JehO7E4tpX1l8Imjs1XjqhhVuGE2tru/p62SRQOKzRZ19MCIFPxleSLorrHq/uuKdvd8j6rm0A9BrCsiB6gmPfal6Kr55vlU=
|   256 f4:b5:a6:60:f4:d1:bf:e2:85:2e:2e:7e:5f:4c:ce:38 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBAPAji9Nkb2U9TeP47Pz7BEa943WGOeu5XrRrTV0+CS0eGfNQyZkK6ZICNdeov65c2NWFPFsZTFjO8Sg+e2n/lM=
|   256 29:e6:61:09:ed:8a:88:2b:55:74:f2:b7:33:ae:df:c8 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIM/U6Td7C0nC8tiqS0Eejd+gQ3rjSyQW2DvcN0eoMFLS
80/tcp open  http    syn-ack Apache httpd 2.4.37 ((centos))
| http-methods: 
|   Supported Methods: HEAD GET POST OPTIONS TRACE
|_  Potentially risky methods: TRACE
|_http-server-header: Apache/2.4.37 (centos)
|_http-title: Overpass Hosting
Service Info: OS: Unix

```

# WEB

USERS

![image](https://user-images.githubusercontent.com/68326057/117946454-f2e5a000-b32c-11eb-81f1-bd306a017158.png)

```bash
Paradox
Elf 
MuirlandOracle 
NinjaJc01 
```

--> http://10.10.116.97/backups/

![image](https://user-images.githubusercontent.com/68326057/117947080-7c956d80-b32d-11eb-9ed9-ac4518eb6643.png)

```bash
--> gpg --import priv.key
-->  gpg --decrypt CustomerDetails.xlsx.gpg > file
--> file file
```

![image](https://user-images.githubusercontent.com/68326057/117947532-e877d600-b32d-11eb-9f8b-02fb01cd78f2.png)

![image](https://user-images.githubusercontent.com/68326057/117947664-0f360c80-b32e-11eb-95ac-ea31daf1148e.png)

# HYDRA
![image](https://user-images.githubusercontent.com/68326057/117948464-c894e200-b32e-11eb-9d9b-8e94226b8e4d.png)

# ftp

![image](https://user-images.githubusercontent.com/68326057/117948912-393bfe80-b32f-11eb-9e6a-1eac75d0204b.png)

as a website content

![image](https://user-images.githubusercontent.com/68326057/117949446-c1ba9f00-b32f-11eb-8a04-8e766ab0d878.png)

where k.php is my reverseshell

# user - apache

![image](https://user-images.githubusercontent.com/68326057/117949564-de56d700-b32f-11eb-99a7-3280e220bb78.png)

![image](https://user-images.githubusercontent.com/68326057/117949596-e7e03f00-b32f-11eb-9019-05dea1e7b9a3.png)

USERS

![image](https://user-images.githubusercontent.com/68326057/117950079-70f77600-b330-11eb-9ab6-b1dcee9d8999.png)

![image](https://user-images.githubusercontent.com/68326057/117954315-88386280-b334-11eb-8aa4-564a37e2cc0a.png)


# user - paradox

![image](https://user-images.githubusercontent.com/68326057/117954371-95555180-b334-11eb-89ae-84e06421a5ea.png)

![image](https://user-images.githubusercontent.com/68326057/117954891-17de1100-b335-11eb-8648-ac8560cebbc0.png)

Put your id_rsa.pub here as 

authorized_keys

```bash
ssh -i authorized_keys paradox@10.10.116.97
Last login: Wed May 12 10:42:00 2021
[paradox@localhost ~]$ 
```

Ran linpeas:-

![image](https://user-images.githubusercontent.com/68326057/117956254-81125400-b336-11eb-807f-0ddfc4269d30.png)

![image](https://user-images.githubusercontent.com/68326057/117957375-a3f13800-b337-11eb-9fb0-fd4962916f16.png)

![image](https://user-images.githubusercontent.com/68326057/117958074-4a3d3d80-b338-11eb-813a-d0ea4551f8a2.png)

## PORT FORWARDING

```bash
 ssh -i authorized_keys -L 2049:localhost:2049 paradox@10.10.116.97
```

```bash
sudo mount -t nfs  localhost:/ /tmp/mountme
```

![image](https://user-images.githubusercontent.com/68326057/117959644-dac84d80-b339-11eb-9b39-2542e6696581.png)

Put your authorized_keys in .ssh folder

# user - james

```bash
ssh -i authorized_keys james@10.10.116.97
```

![image](https://user-images.githubusercontent.com/68326057/117960018-32ff4f80-b33a-11eb-8206-f3ef265270b4.png)

![image](https://user-images.githubusercontent.com/68326057/117962148-87a3ca00-b33c-11eb-9435-6d897edfa38c.png)

![image](https://user-images.githubusercontent.com/68326057/117962175-8ecad800-b33c-11eb-80d4-1423daefc8ba.png)

![image](https://user-images.githubusercontent.com/68326057/117962211-98ecd680-b33c-11eb-8db8-9a46e41779c8.png)


# ROOT

![image](https://user-images.githubusercontent.com/68326057/117962254-a5712f00-b33c-11eb-871e-47bcf99184d5.png)

