# 2/100

# NMAP

```bash
PORT   STATE SERVICE REASON         VERSION
22/tcp open  ssh     syn-ack ttl 63 OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 9d:d0:98:da:0d:32:3d:0b:3f:42:4d:d7:93:4f:fd:60 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDLSsGJtpg5KvawG56yanORlHOGP7anzFKXq8ZDjuBD20sWrHl6g0J1+w497SyvRnB6EDOBGrjqlEXqlI7DvgrAo08GOCvoajuPpitLuC2rCfRC3b3ctn/n2+zGkkfsD5Y0U6PQrchRNpMKH/4nsaBcrTV8ZkEGF+VNYhnTO7c1vGhpH0i5c7UzyKvfqz/KzH4YryUpC1opxB9pn0jHH+iQ8H+Brne/bvOmpyvoy84CzuunshxMmAV9qdaLmZxOOF25SF5uHh6r1h8tVG8yLbD1N7IfPXXy0GpZZZIBt4i/ZQVpfk1i0GsY4/mL3VCrtFsO4p2PxRLVws5Fpces+pDN
|   256 4c:f4:2e:24:82:cf:9c:8d:e2:0c:52:4b:2e:a5:12:d9 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBDwKM2aO1LW/C4gfLHyFmkrfcPcXVHvIEK8JN9pk/9kNhZKz8X9byyxiWMnNS/6AQNMAV0d5B+d0/VK2eps90ZI=
|   256 a9:fb:e3:f4:ba:d6:1e:72:e7:97:25:82:87:6e:ea:01 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIEOULyvRe2blVRaHM9twRKyE34SQUyGPMjVmRv2srgvv
80/tcp open  http    syn-ack ttl 63 Apache httpd 2.4.29 ((Ubuntu))
| http-methods: 
|_  Supported Methods: GET POST OPTIONS HEAD
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: Apache2 Ubuntu Default Page: It works
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

# Enumeration

1. wordpress

![image](https://user-images.githubusercontent.com/68326057/120770802-27b7d200-c53c-11eb-9e06-dd7f49208da5.png)

So I added IP localhost >> /etc/hosts

![image](https://user-images.githubusercontent.com/68326057/120771109-7d8c7a00-c53c-11eb-98be-1b46a5772226.png)


![image](https://user-images.githubusercontent.com/68326057/120771630-0acfce80-c53d-11eb-8ada-e3dcdf1c9502.png)

```bash
yash
haclabs
```

![image](https://user-images.githubusercontent.com/68326057/120774109-95b1c880-c53f-11eb-9ba1-22908ecc4a6c.png)


![image](https://user-images.githubusercontent.com/68326057/120774139-a06c5d80-c53f-11eb-9190-1e4f412aeb5a.png)


--> http://localhost/wordpress/hint.html
```bash
Please collect all the API tokens availabe on the home page
```

![image](https://user-images.githubusercontent.com/68326057/120775283-b0d10800-c540-11eb-8a34-80c67c7105d8.png)

![image](https://user-images.githubusercontent.com/68326057/120775412-cba37c80-c540-11eb-8599-8dcbfa386472.png)

![image](https://user-images.githubusercontent.com/68326057/120775554-eece2c00-c540-11eb-8846-44963844b5f7.png)

![image](https://user-images.githubusercontent.com/68326057/120775622-ff7ea200-c540-11eb-8f59-cfec441625c8.png)


```bash
5F4DCC3B5AA765D61D8327DEB882CF99
```

This os yash password

# USER - yash

![image](https://user-images.githubusercontent.com/68326057/120776396-d3afec00-c541-11eb-8463-05dbb4ed102e.png)

![image](https://user-images.githubusercontent.com/68326057/120776946-62bd0400-c542-11eb-9b60-65c9aa022a3f.png)


# root

![image](https://user-images.githubusercontent.com/68326057/120776985-6e102f80-c542-11eb-85d2-a84f0176ae8a.png)


# Post Exploitation

```bash
haclabs:$6$wecIqAfW$Ej3MCSKYXsdkJwaLVDEYPhBvvklJZQDBDqlqVSuLCpt8jEZ5G1Ca4hBueJBdm2EKNjOr5xPkI02FO9o701f9.1:18284:0:99999:7:::
yash:$6$y9K7WfOh$dNaOJ38eyPwoADmaWPdEVisttsF6pu/q3Z/H5edgmLobzjsZQ.QF6bqtXMGA2cNiWFn4HBqV2m9RShr9yWXxc/:18617:0:99999:7:::
root:$6$6vSfM1CE$KoAzJ1zdEufgtMABqD2ZjXFZXOrVJmJlxT/R4vgbLUCPxc39rNdH1hGqr1y/AEQDuNZfssNc6wqv2Mu5Cxjzb1:18330:0:99999:7::: 
```

```bash
define( 'DB_NAME', 'wordpress' );                                                                                                      
                                                                                                                                       
/** MySQL database username */                                     
define( 'DB_USER', 'wordpressuser' );
                                                                                                                                       
/** MySQL database password */                                                                                                         
define( 'DB_PASSWORD', 'cry4moon' );                                                                                                   
                                                                   
/** MySQL hostname */                                                                                                                  
define( 'DB_HOST', 'localhost' ); 
```
