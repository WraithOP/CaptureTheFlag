
![image](https://user-images.githubusercontent.com/68326057/117400027-6fd4dc00-af1f-11eb-8046-df1a40ae941f.png)


# NMAP

```bash
PORT      STATE SERVICE       VERSION
21/tcp    open  ftp           Microsoft ftpd
|_ftp-anon: Anonymous FTP login allowed (FTP code 230)
| ftp-syst: 
|_  SYST: Windows_NT

80/tcp    open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-title: Home - Acme Widgets

111/tcp   open  rpcbind       2-4 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/tcp6  rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100000  2,3,4        111/udp6  rpcbind
|   100003  2,3         2049/udp   nfs
|   100003  2,3         2049/udp6  nfs
|   100003  2,3,4       2049/tcp   nfs
|   100003  2,3,4       2049/tcp6  nfs
|   100005  1,2,3       2049/tcp   mountd
|   100005  1,2,3       2049/tcp6  mountd
|   100005  1,2,3       2049/udp   mountd
|   100005  1,2,3       2049/udp6  mountd
|   100021  1,2,3,4     2049/tcp   nlockmgr
|   100021  1,2,3,4     2049/tcp6  nlockmgr
|   100021  1,2,3,4     2049/udp   nlockmgr
|   100021  1,2,3,4     2049/udp6  nlockmgr
|   100024  1           2049/tcp   status
|   100024  1           2049/tcp6  status
|   100024  1           2049/udp   status
|_  100024  1           2049/udp6  status

135/tcp   open  msrpc         Microsoft Windows RPC

139/tcp   open  netbios-ssn   Microsoft Windows netbios-ssn

445/tcp   open  microsoft-ds?

2049/tcp  open  mountd        1-3 (RPC #100005)

5985/tcp  open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found

47001/tcp open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found

49664/tcp open  msrpc         Microsoft Windows RPC
49665/tcp open  msrpc         Microsoft Windows RPC
49666/tcp open  msrpc         Microsoft Windows RPC
49667/tcp open  msrpc         Microsoft Windows RPC
49678/tcp open  msrpc         Microsoft Windows RPC
49679/tcp open  msrpc         Microsoft Windows RPC
49680/tcp open  msrpc         Microsoft Windows RPC
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_clock-skew: -5h23m09s
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2021-05-07T05:11:25
|_  start_date: N/A
```

# Port 111

```bash
showmount -e ip
```

![image](https://user-images.githubusercontent.com/68326057/117400066-82e7ac00-af1f-11eb-9826-ce7e0d92a9b4.png)

```bash
sudo mount -o rw 10.10.10.180:/site_backups /tmp/mountme
```

![image](https://user-images.githubusercontent.com/68326057/117402086-5cc40b00-af23-11eb-883a-e669c8487d63.png)

![image](https://user-images.githubusercontent.com/68326057/117402111-6a799080-af23-11eb-87a7-dd33db17465b.png)


```bash
User "admin" <admin@htb.local>192.168.195.1User "smith" <smith@htb.local>umbraco/user/password/changepassword change
User "admin" <admin@htb.local>192.168.195.1User "ssmith" <ssmith@htb.local>umbraco/user/password/changepassword change
```

```bash
adminadmin@htb.localb8be16afba8c314ad33d812f22a04991b90e2aaa{"hashAlgorithm":"SHA1"}admin@htb.localen-USfeb1a998-d3bf-406a-b30b-e269d7a
bdf50   --> b8be16afba8c314ad33d812f22a04991b90e2aaa
```

![image](https://user-images.githubusercontent.com/68326057/117402508-263ac000-af24-11eb-9325-6c76097ed72f.png)

```bash
users:-
admin
ssmith

password:-
baconandcheese
```



# SMB

```bash
crackmapexec smb 10.10.10.180 --shares
SMB         10.10.10.180    445    REMOTE           [*] Windows 10.0 Build 17763 x64 (name:REMOTE) (domain:remote) (signing:False) (SMBv1:False)
```

# WEB

## CMS - umbraco

![image](https://user-images.githubusercontent.com/68326057/117400993-56349400-af21-11eb-8185-36f4e4a92574.png)

--> Windows web server are not case sensitive.

--> cd - (will take u to previous working directory)

--> http://10.10.10.180/umbraco#/login/false?returnPath=%252Fumbraco

![image](https://user-images.githubusercontent.com/68326057/117403042-2c7d6c00-af25-11eb-8116-22166c8c0bac.png)


Login is not working Machine is crashed
