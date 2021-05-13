
# NMAP
```bash
PORT     STATE SERVICE     REASON  VERSION

80/tcp   open  http        syn-ack Apache httpd 2.4.38 ((Debian))
| http-methods: 
|_  Supported Methods: GET POST OPTIONS HEAD
|_http-server-header: Apache/2.4.38 (Debian)
|_http-title: Site doesn't have a title (text/html).

139/tcp  open  netbios-ssn syn-ack Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp  open  netbios-ssn syn-ack Samba smbd 4.9.5-Debian (workgroup: WORKGROUP)

3306/tcp open  mysql       syn-ack MySQL 5.5.5-10.3.15-MariaDB-1
| mysql-info: 
|   Protocol: 10
|   Version: 5.5.5-10.3.15-MariaDB-1
|   Thread ID: 16
|   Capabilities flags: 63486
|   Some Capabilities: Speaks41ProtocolOld, ODBCClient, Support41Auth, ConnectWithDatabase, SupportsTransactions, SupportsLoadDataLocal, SupportsCompression, FoundRows, IgnoreSigpipes, InteractiveClient, Speaks41ProtocolNew, IgnoreSpaceBeforeParenthesis, DontAllowDatabaseTableColumn, LongColumnFlag, SupportsMultipleStatments, SupportsMultipleResults, SupportsAuthPlugins
|   Status: Autocommit
|   Salt: LS<o>(Iw?p:l3V8V']~%
|_  Auth Plugin Name: mysql_native_password
Service Info: Host: DAWN

Host script results:
|_clock-skew: mean: -4h09m55s, deviation: 2h18m34s, median: -5h29m56s
| nbstat: NetBIOS name: DAWN, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
| Names:
|   DAWN<00>             Flags: <unique><active>
|   DAWN<03>             Flags: <unique><active>
|   DAWN<20>             Flags: <unique><active>
|   WORKGROUP<00>        Flags: <group><active>
|   WORKGROUP<1e>        Flags: <group><active>
| Statistics:
|   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
|   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
|_  00 00 00 00 00 00 00 00 00 00 00 00 00 00
| p2p-conficker: 
|   Checking for Conficker.C or higher...
|   Check 1 (port 55392/tcp): CLEAN (Couldn't connect)
|   Check 2 (port 61235/tcp): CLEAN (Couldn't connect)
|   Check 3 (port 20586/udp): CLEAN (Failed to receive data)
|   Check 4 (port 29822/udp): CLEAN (Failed to receive data)
|_  0/4 checks are positive: Host is CLEAN or ports are blocked![image](https://user-images.githubusercontent.com/68326057/118093601-4b7b7280-b3eb-11eb-86bd-65c5c1bdb3f8.png)

| smb-os-discovery: 
|   OS: Windows 6.1 (Samba 4.9.5-Debian)
|   Computer name: dawn
|   NetBIOS computer name: DAWN\x00
|   Domain name: dawn
|   FQDN: dawn.dawn
|_  System time: 2021-05-13T03:25:47-04:00
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2021-05-13T07:25:48
|_  start_date: N/A
```

# SMB

```bash
smbclient -L \\\\192.168.51.11
```


![image](https://user-images.githubusercontent.com/68326057/118093042-7e713680-b3ea-11eb-914e-c4cfc59b4e93.png)

![image](https://user-images.githubusercontent.com/68326057/118093843-a44b0b00-b3eb-11eb-95d2-521304a645b4.png)


SO ,we can write here


# WEB

![image](https://user-images.githubusercontent.com/68326057/118094052-df4d3e80-b3eb-11eb-969a-337597be7b01.png)

![image](https://user-images.githubusercontent.com/68326057/118094078-e83e1000-b3eb-11eb-96ba-f40ca0020af8.png)

![image](https://user-images.githubusercontent.com/68326057/118096557-21c44a80-b3ef-11eb-99ec-596a585e6c9f.png)

USER:-
```
ganimedes
dawn
```

![image](https://user-images.githubusercontent.com/68326057/118096693-533d1600-b3ef-11eb-926b-e73316176413.png)


![image](https://user-images.githubusercontent.com/68326057/118096754-6819a980-b3ef-11eb-9b60-dc736067e8df.png)


# USER - www-data

![image](https://user-images.githubusercontent.com/68326057/118097102-d9f1f300-b3ef-11eb-99bb-76cdbc2b6709.png)

![image](https://user-images.githubusercontent.com/68326057/118097130-e413f180-b3ef-11eb-9056-2000c3276968.png)

# ROOT

![image](https://user-images.githubusercontent.com/68326057/118097236-0f96dc00-b3f0-11eb-82dc-58b3c7d60857.png)

![image](https://user-images.githubusercontent.com/68326057/118097639-9481f580-b3f0-11eb-99db-41f6e550c58c.png)

![image](https://user-images.githubusercontent.com/68326057/118097755-b54a4b00-b3f0-11eb-8469-4ea32be1b7ee.png)

![image](https://user-images.githubusercontent.com/68326057/118097773-ba0eff00-b3f0-11eb-8487-908eb0fc44a4.png)

