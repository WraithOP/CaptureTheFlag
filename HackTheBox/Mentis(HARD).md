![image](https://user-images.githubusercontent.com/68326057/129859622-9e543cb2-eebe-407a-8d81-ffbccba0dd3f.png)

# Enumeration

## NMAP

```bash
PORT      STATE SERVICE      REASON          VERSION
88/tcp    open  kerberos-sec syn-ack ttl 127 Microsoft Windows Kerberos (server time: 2021-08-18 07:59:06Z)
135/tcp   open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
139/tcp   open  netbios-ssn  syn-ack ttl 127 Microsoft Windows netbios-ssn
389/tcp   open  ldap         syn-ack ttl 127 Microsoft Windows Active Directory LDAP (Domain: htb.local, Site: Default-First-Site-Name)
445/tcp   open  microsoft-ds syn-ack ttl 127 Windows Server 2008 R2 Standard 7601 Service Pack 1 microsoft-ds (workgroup: HTB)
464/tcp   open  kpasswd5?    syn-ack ttl 127
593/tcp   open  ncacn_http   syn-ack ttl 127 Microsoft Windows RPC over HTTP 1.0
636/tcp   open  tcpwrapped   syn-ack ttl 127
49152/tcp open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
49153/tcp open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
49154/tcp open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
49155/tcp open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
49157/tcp open  ncacn_http   syn-ack ttl 127 Microsoft Windows RPC over HTTP 1.0
49158/tcp open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
Service Info: Host: MANTIS; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_clock-skew: mean: 1h27m54s, deviation: 2h18m36s, median: 7m52s
| p2p-conficker: 
|   Checking for Conficker.C or higher...
|   Check 1 (port 22023/tcp): CLEAN (Couldn't connect)
|   Check 2 (port 10637/tcp): CLEAN (Couldn't connect)
|   Check 3 (port 19802/udp): CLEAN (Failed to receive data)
|   Check 4 (port 64767/udp): CLEAN (Timeout)
|_  0/4 checks are positive: Host is CLEAN or ports are blocked
| smb-os-discovery: 
|   OS: Windows Server 2008 R2 Standard 7601 Service Pack 1 (Windows Server 2008 R2 Standard 6.1)
|   OS CPE: cpe:/o:microsoft:windows_server_2008::sp1
|   Computer name: mantis
|   NetBIOS computer name: MANTIS\x00
|   Domain name: htb.local
|   Forest name: htb.local
|   FQDN: mantis.htb.local
|_  System time: 2021-08-18T04:00:06-04:00
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: required
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled and required
| smb2-time: 
|   date: 2021-08-18T08:00:04
|_  start_date: 2021-08-18T07:58:28
```

# Information Gathering

## PORT 1337

![image](https://user-images.githubusercontent.com/68326057/129876768-c27df567-4920-44ed-b133-180911881b6b.png)

![image](https://user-images.githubusercontent.com/68326057/129876837-daabf4cc-f01c-4e50-9f2a-a51ba8a7693e.png)

There is a wierd hash in the name.

![image](https://user-images.githubusercontent.com/68326057/129879441-71c1f20b-dfe3-4e9c-bf7d-860e5d3b0727.png)

![image](https://user-images.githubusercontent.com/68326057/129879761-e0fdaf3d-9594-4b1f-92a0-7e2cb696133c.png)

hash:-

```bash
6d2424716c5f53405f504073735730726421
```

![image](https://user-images.githubusercontent.com/68326057/129879905-a5820c5f-3804-48de-8431-d6041795ca1f.png)


Credentials:-

```bash
admin:m$$ql_S@_P@ssW0rd!
```

# MSSQL Admin user

![image](https://user-images.githubusercontent.com/68326057/129880329-757ab0fa-5283-4d9e-893e-9d5db30eeff5.png)


![image](https://user-images.githubusercontent.com/68326057/129892921-6d381d48-d580-45a3-99df-6380f9b8c520.png)


## Extracting Information From MSSQL

![image](https://user-images.githubusercontent.com/68326057/129893197-d2e4f732-5709-4a75-8d2e-acc7f70c2ad0.png)


### Connected with Dbeaver

![image](https://user-images.githubusercontent.com/68326057/129895029-032fad26-db22-49bf-bccc-03016be14089.png)

![image](https://user-images.githubusercontent.com/68326057/129895199-5fbfbc0f-3244-48ea-8266-88d6c54ddd47.png)

Credeantails:-

```bash
james:J@m3s_P@ssW0rd!
admin:AL1337E2D6YHm0iIysVzG8LA76OozgMSlyOJk1Ov5WCGK+lgKY6vrQuswfWHKZn2+A==
```


