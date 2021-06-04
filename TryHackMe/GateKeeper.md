#1/100

![image](https://user-images.githubusercontent.com/68326057/120747642-04caf500-c51f-11eb-85e1-5cc0653d7d56.png)

TTL --> 127 So it is a windows machine.

# NMAP

```bash
PORT      STATE SERVICE      REASON          VERSION
135/tcp   open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
139/tcp   open  netbios-ssn  syn-ack ttl 127 Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds syn-ack ttl 127 Windows 7 Professional 7601 Service Pack 1 microsoft-ds (workgroup: WORKGROUP)
3389/tcp  open  tcpwrapped   syn-ack ttl 127
| ssl-cert: Subject: commonName=gatekeeper
| Issuer: commonName=gatekeeper
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha1WithRSAEncryption
| Not valid before: 2021-06-03T04:56:50
| Not valid after:  2021-12-03T04:56:50
| MD5:   7cf5 188b aa7b 4cc0 2685 5c49 f283 fba0
| SHA-1: 5608 a7fc 1a35 b6e9 315d 2122 9e0a 0796 0624 83c0
| -----BEGIN CERTIFICATE-----
| MIIC2DCCAcCgAwIBAgIQdS4gLd0RlLBESbxgvk2MczANBgkqhkiG9w0BAQUFADAV
| MRMwEQYDVQQDEwpnYXRla2VlcGVyMB4XDTIxMDYwMzA0NTY1MFoXDTIxMTIwMzA0
| NTY1MFowFTETMBEGA1UEAxMKZ2F0ZWtlZXBlcjCCASIwDQYJKoZIhvcNAQEBBQAD
| ggEPADCCAQoCggEBALXcBZ01a/0UrGx0biimiQDo5pRxHhIvAvb3S/iCrfQ6qyko
| Se17ccePKKNCjCWgiJ05VAbp7QNvcKzKorLPvhcojCaQ6is8/hNv8sMaNiTGBpk4
| 0qeeN9upYKFYIkoeNCKVoz38kAk0y6ui9FxDHAhETKv6Nlvq1oV/968dYyyBYRHa
| /cvSLEkm+xTRVA2U/Lja8odM/JxaaZ+VLghIjglyhhG0sUVKiCbfAqc+2hJtdpT7
| TPsPp6v5pMEz75ym/Rczs6SWGeT6M93KsDcEwAHCGV+6SIbeXaoWd//ynx10hjBA
| cgV7NSFg/1rDjgr6X93A2tf2yX3a4WNwyURTsr8CAwEAAaMkMCIwEwYDVR0lBAww
| CgYIKwYBBQUHAwEwCwYDVR0PBAQDAgQwMA0GCSqGSIb3DQEBBQUAA4IBAQCZ2VAt
| U7bB5q/PtxLJ9DrOqDTT4XIVM3GTQSGcygCc2/Z4ugV/jmamGpR7vRg/U3+y1xha
| IAWVDAONnbyEZ22Kn4vg/968mFeBJ4rkXZyrnoLNz63pTOZV2FY0F3Qf+es1Muij
| OQMipk3RMYc/0lA8+YekynTV+Lx7gJg0GKEh+ffBi5r9iUM/P+o0VhbArSAsSUnD
| Z5gOiGdy+QkqzyRXqyu09wt55o9TOOw0uDmLWaGak+kzGbsZcNUt+gIqXiLj23UC
| klC4Z91uAigXKRwVD45xBNbvqSjL8XpG4djk4gdOP/ke87on+/BHoOsEpK3L3OOv
| J2SJnOtAyYV2ZUC2
|_-----END CERTIFICATE-----
|_ssl-date: 2021-06-04T05:00:42+00:00; -5h29m48s from scanner time.
31337/tcp open  Elite?       syn-ack ttl 127
| fingerprint-strings: 
|   FourOhFourRequest: 
|     Hello GET /nice%20ports%2C/Tri%6Eity.txt%2ebak HTTP/1.0
|     Hello
|   GenericLines: 
|     Hello 
|     Hello
|   GetRequest: 
|     Hello GET / HTTP/1.0
|     Hello
|   HTTPOptions: 
|     Hello OPTIONS / HTTP/1.0
|     Hello
|   Help: 
|     Hello HELP
|   Kerberos: 
|     Hello !!!
|   LDAPSearchReq: 
|     Hello 0
|     Hello
|   LPDString: 
|     Hello 
|     default!!!
|   RTSPRequest: 
|     Hello OPTIONS / RTSP/1.0
|     Hello
|   SIPOptions: 
|     Hello OPTIONS sip:nm SIP/2.0
|     Hello Via: SIP/2.0/TCP nm;branch=foo
|     Hello From: <sip:nm@nm>;tag=root
|     Hello To: <sip:nm2@nm2>
|     Hello Call-ID: 50000
|     Hello CSeq: 42 OPTIONS
|     Hello Max-Forwards: 70
|     Hello Content-Length: 0
|     Hello Contact: <sip:nm@nm>
|     Hello Accept: application/sdp
|     Hello
|   SSLSessionReq, TLSSessionReq, TerminalServerCookie: 
|_    Hello
49152/tcp open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
49153/tcp open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
49154/tcp open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
49155/tcp open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
49161/tcp open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port31337-TCP:V=7.91%I=7%D=6/4%Time=60BA001D%P=x86_64-pc-linux-gnu%r(Ge
SF:tRequest,24,"Hello\x20GET\x20/\x20HTTP/1\.0\r!!!\nHello\x20\r!!!\n")%r(
SF:SIPOptions,142,"Hello\x20OPTIONS\x20sip:nm\x20SIP/2\.0\r!!!\nHello\x20V
SF:ia:\x20SIP/2\.0/TCP\x20nm;branch=foo\r!!!\nHello\x20From:\x20<sip:nm@nm
SF:>;tag=root\r!!!\nHello\x20To:\x20<sip:nm2@nm2>\r!!!\nHello\x20Call-ID:\
SF:x2050000\r!!!\nHello\x20CSeq:\x2042\x20OPTIONS\r!!!\nHello\x20Max-Forwa
SF:rds:\x2070\r!!!\nHello\x20Content-Length:\x200\r!!!\nHello\x20Contact:\
SF:x20<sip:nm@nm>\r!!!\nHello\x20Accept:\x20application/sdp\r!!!\nHello\x2
SF:0\r!!!\n")%r(GenericLines,16,"Hello\x20\r!!!\nHello\x20\r!!!\n")%r(HTTP
SF:Options,28,"Hello\x20OPTIONS\x20/\x20HTTP/1\.0\r!!!\nHello\x20\r!!!\n")
SF:%r(RTSPRequest,28,"Hello\x20OPTIONS\x20/\x20RTSP/1\.0\r!!!\nHello\x20\r
SF:!!!\n")%r(Help,F,"Hello\x20HELP\r!!!\n")%r(SSLSessionReq,C,"Hello\x20\x
SF:16\x03!!!\n")%r(TerminalServerCookie,B,"Hello\x20\x03!!!\n")%r(TLSSessi
SF:onReq,C,"Hello\x20\x16\x03!!!\n")%r(Kerberos,A,"Hello\x20!!!\n")%r(Four
SF:OhFourRequest,47,"Hello\x20GET\x20/nice%20ports%2C/Tri%6Eity\.txt%2ebak
SF:\x20HTTP/1\.0\r!!!\nHello\x20\r!!!\n")%r(LPDString,12,"Hello\x20\x01def
SF:ault!!!\n")%r(LDAPSearchReq,17,"Hello\x200\x84!!!\nHello\x20\x01!!!\n");
Service Info: Host: GATEKEEPER; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_clock-skew: mean: -4h29m47s, deviation: 2h00m00s, median: -5h29m48s
| nbstat: NetBIOS name: GATEKEEPER, NetBIOS user: <unknown>, NetBIOS MAC: 02:66:d3:d3:05:47 (unknown)
| Names:
|   GATEKEEPER<00>       Flags: <unique><active>
|   WORKGROUP<00>        Flags: <group><active>
|   GATEKEEPER<20>       Flags: <unique><active>
|   WORKGROUP<1e>        Flags: <group><active>
|   WORKGROUP<1d>        Flags: <unique><active>
|   \x01\x02__MSBROWSE__\x02<01>  Flags: <group><active>
| Statistics:
|   02 66 d3 d3 05 47 00 00 00 00 00 00 00 00 00 00 00
|   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
|_  00 00 00 00 00 00 00 00 00 00 00 00 00 00
| p2p-conficker: 
|   Checking for Conficker.C or higher...
|   Check 1 (port 33274/tcp): CLEAN (Couldn't connect)
|   Check 2 (port 33195/tcp): CLEAN (Couldn't connect)
|   Check 3 (port 61704/udp): CLEAN (Failed to receive data)
|   Check 4 (port 4182/udp): CLEAN (Timeout)
|_  0/4 checks are positive: Host is CLEAN or ports are blocked
| smb-os-discovery: 
|   OS: Windows 7 Professional 7601 Service Pack 1 (Windows 7 Professional 6.1)
|   OS CPE: cpe:/o:microsoft:windows_7::sp1:professional
|   Computer name: gatekeeper
|   NetBIOS computer name: GATEKEEPER\x00
|   Workgroup: WORKGROUP\x00
|_  System time: 2021-06-04T01:00:25-04:00
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2021-06-04T05:00:25
|_  start_date: 2021-06-04T04:56:07
```

# Enumeration

1. SMBCLIENT

```bash
smbclient -L \\\\10.10.143.183
Enter WORKGROUP\kalikali's password: 

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        IPC$            IPC       Remote IPC
        Users           Disk      
SMB1 disabled -- no workgroup available
```

2. Crackmapexec

![image](https://user-images.githubusercontent.com/68326057/120748157-ee716900-c51f-11eb-9201-e59414c38825.png)

3. ![image](https://user-images.githubusercontent.com/68326057/120748728-e0701800-c520-11eb-8e86-d8bdca0a1b95.png)

4. Port 31337

```bash
--> nc 10.10.143.183 31337
HELP
Hello HELP!!!
exit
Bye!
```

![image](https://user-images.githubusercontent.com/68326057/120751555-d69ce380-c525-11eb-945a-0c2d0ebc68cb.png)

```bash
 /usr/share/metasploit-framework/tools/exploit/pattern_create.rb -l 483
Aa0Aa1Aa2Aa3Aa4Aa5Aa6Aa7Aa8Aa9Ab0Ab1Ab2Ab3Ab4Ab5Ab6Ab7Ab8Ab9Ac0Ac1Ac2Ac3Ac4Ac5Ac6Ac7Ac8Ac9Ad0Ad1Ad2Ad3Ad4Ad5Ad6Ad7Ad8Ad9Ae0Ae1Ae2Ae3Ae4Ae5Ae6Ae7Ae8Ae9Af0Af1Af2Af3Af4Af5Af6Af7Af8Af9Ag0Ag1Ag2Ag3Ag4Ag5Ag6Ag7Ag8Ag9Ah0Ah1Ah2Ah3Ah4Ah5Ah6Ah7Ah8Ah9Ai0Ai1Ai2Ai3Ai4Ai5Ai6Ai7Ai8Ai9Aj0Aj1Aj2Aj3Aj4Aj5Aj6Aj7Aj8Aj9Ak0Ak1Ak2Ak3Ak4Ak5Ak6Ak7Ak8Ak9Al0Al1Al2Al3Al4Al5Al6Al7Al8Al9Am0Am1Am2Am3Am4Am5Am6Am7Am8Am9An0An1An2An3An4An5An6An7An8An9Ao0Ao1Ao2Ao3Ao4Ao5Ao6Ao7Ao8Ao9Ap0Ap1Ap2Ap3Ap4Ap5Ap6Ap7Ap8Ap9Aq0
```

![image](https://user-images.githubusercontent.com/68326057/120751790-40b58880-c526-11eb-8308-87533ce9da1d.png)

```bash
/usr/share/metasploit-framework/tools/exploit/pattern_offset.rb -q 39654138
[*] Exact match at offset 146
```

EIP --> 146

![image](https://user-images.githubusercontent.com/68326057/120752968-1f559c00-c528-11eb-95e0-c5685bfeaf80.png)

