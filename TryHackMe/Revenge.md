![image](https://user-images.githubusercontent.com/68326057/120645086-aa398680-c495-11eb-913b-9ac73df50dbd.png)

# NMAP

```bash
PORT   STATE SERVICE REASON  VERSION
22/tcp open  ssh     syn-ack OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 72:53:b7:7a:eb:ab:22:70:1c:f7:3c:7a:c7:76:d9:89 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDBiHOfDlVoYCp0+/LM7BhujeUicHQ+HwAidwcp1yMZE3j6K/7RW3XsNSEyUR8RpVaXAHl7ThNfD2pmzGPBV9uOjNlgNuzhASOgQuz9G4hQyLh5u1Sv9QR8R9udClyRoqUwGBfdNKjqAK2Kw7OghAHXlwUxniYRLUeAD60oLjm4uIv+1QlA2t5/LL6utV2ePWOEHe8WehXPGrstJtJ8Jf/uM48s0jhLhMEewzSqR2w0LWAGDFzOdfnOvcyQtJ9FeswJRG7fWXXsOms0Fp4lhTL4fknL+PSdWEPagTjRfUIRxskkFsaxI//3EulETC+gSa+KilVRfiKAGTdrdz7RL5sl
|   256 43:77:00:fb:da:42:02:58:52:12:7d:cd:4e:52:4f:c3 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBNNoSioP7IDDu4yIVfGnhLoMTyvBuzxILnRr7rKGX0YpNShJfHLjEQRIdUoYq+/7P0wBjLoXn9g7XpLLb7UMvm4=
|   256 2b:57:13:7c:c8:4f:1d:c2:68:67:28:3f:8e:39:30:ab (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIEpROzuQcffRwKXCOz+JQ5p7QKnAQVEDUwwUkkblavyh

80/tcp open  http    syn-ack nginx 1.14.0 (Ubuntu)
|_http-favicon: Unknown favicon MD5: E859DC70A208F0F0242640410296E06A
| http-methods: 
|_  Supported Methods: HEAD OPTIONS GET
|_http-server-header: nginx/1.14.0 (Ubuntu)
|_http-title: Home | Rubber Ducky Inc.
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

# Enumeration

--> qTyAhRp.txt

1. User: Billy

## WEB

1. Users Leaked:-
```bash
Vishas
Amanda
Johnny
Karen
```

![image](https://user-images.githubusercontent.com/68326057/120651631-9fcebb00-c49c-11eb-8968-2d415a190e9f.png)


In gobuster I added .py as extention

Found app.py

![image](https://user-images.githubusercontent.com/68326057/120651972-f3410900-c49c-11eb-9941-07ffee8e11d1.png)


```bash
root:PurpleElephants90!
```

I brute forces The above password with hydra but None worked with the usernames we got.

![image](https://user-images.githubusercontent.com/68326057/120652233-313e2d00-c49d-11eb-8c70-32d14f1c1fbc.png)


This is where I think SQL Injection Takes Place

![image](https://user-images.githubusercontent.com/68326057/120653955-d0afef80-c49e-11eb-9a2e-727665bfbf31.png)

![image](https://user-images.githubusercontent.com/68326057/120654020-e7564680-c49e-11eb-9f45-2eda7915dadc.png)

![image](https://user-images.githubusercontent.com/68326057/120655849-b2e38a00-c4a0-11eb-8e37-6650bb2a0c75.png)

# Information Gathering

```bash
Table: user
[10 entries]
+----+---------------------------------+------------------+----------+--------------------------------------------------------------+--
--------------------------+
| id | email                           | company          | username | _password                                                    | c
redit_card                |
+----+---------------------------------+------------------+----------+--------------------------------------------------------------+--
--------------------------+
| 1  | sales@fakeinc.org               | Fake Inc         | jhenry   | $2a$12$dAV7fq4KIUyUEOALi8P2dOuXRj5ptOoeRtYLHS85vd/SBDv.tYXOa | 4
338736490565706           |
| 2  | accountspayable@ecorp.org       | Evil Corp        | smonroe  | $2a$12$6KhFSANS9cF6riOw5C66nerchvkU9AHLVk7I8fKmBkh6P/rPGmanm | 3
55219744086163            |
| 3  | accounts.payable@mcdoonalds.org | McDoonalds Inc   | dross    | $2a$12$9VmMpa8FufYHT1KNvjB1HuQm9LF8EX.KkDwh9VRDb5hMk3eXNRC4C | 3
49789518019219            |
| 4  | sales@ABC.com                   | ABC Corp         | ngross   | $2a$12$LMWOgC37PCtG7BrcbZpddOGquZPyrRBo5XjQUIVVAlIKFHMysV9EO | 4
499108649937274           |
| 5  | sales@threebelow.com            | Three Below      | jlawlor  | $2a$12$hEg5iGFZSsec643AOjV5zellkzprMQxgdh1grCW3SMG9qV9CKzyRu | 4
563593127115348           |
| 6  | ap@krasco.org                   | Krasco Org       | mandrews | $2a$12$reNFrUWe4taGXZNdHAhRme6UR2uX..t/XCR6UnzTK6sh1UhREd1rC | t
hm{br3ak1ng_4nd_3nt3r1ng} |
| 7  | payable@wallyworld.com          | Wally World Corp | dgorman  | $2a$12$8IlMgC9UoN0mUmdrS3b3KO0gLexfZ1WvA86San/YRODIbC8UGinNm | 4
905698211632780           |
| 8  | payables@orlando.gov            | Orlando City     | mbutts   | $2a$12$dmdKBc/0yxD9h81ziGHW4e5cYhsAiU4nCADuN0tCE8PaEv51oHWbS | 4
690248976187759           |
| 9  | sales@dollatwee.com             | Dolla Twee       | hmontana | $2a$12$q6Ba.wuGpch1SnZvEJ1JDethQaMwUyTHkR0pNtyTW6anur.3.0cem | 3
75019041714434            |
| 10 | sales@ofamdollar                | O!  Fam Dollar   | csmith   | $2a$12$gxC7HlIWxMKTLGexTq8cn.nNnUaYKUpI91QaqQ/E29vtwlwyvXe36 | 3
64774395134471            |
+----+---------------------------------+------------------+----------+--------------------------------------------------------------+--
--------------------------+
```
```bash
system_user

+----+----------------------+--------------+--------------------------------------------------------------+                            
| id | email                | username     | _password                                                    |                            
+----+----------------------+--------------+--------------------------------------------------------------+                            
| 1  | sadmin@duckyinc.org  | server-admin | $2a$08$GPh7KZcK2kNIQEm5byBj1umCQ79xP.zQe19hPoG/w2GoebUtPfT8a |                            
| 2  | kmotley@duckyinc.org | kmotley      | $2a$12$LEENY/LWOfyxyCBUlfX8Mu8viV9mGUse97L8x.4L66e9xwzzHfsQa |                            
| 3  | dhughes@duckyinc.org | dhughes      | $2a$12$22xS/uDxuIsPqrRcxtVmi.GR2/xh0xITGdHuubRF4Iilg5ENAFlcK |                            
+----+----------------------+--------------+--------------------------------------------------------------+ 
```

![image](https://user-images.githubusercontent.com/68326057/120659237-c9d7ab80-c4a3-11eb-9288-5ee7cb2e28dc.png)


![image](https://user-images.githubusercontent.com/68326057/120659279-d78d3100-c4a3-11eb-8758-823e9da3e66c.png)


```bash
server-admin:inuyasha
```

![image](https://user-images.githubusercontent.com/68326057/120659456-02778500-c4a4-11eb-9b55-cbf05db56d21.png)


# USER - server-admin

![image](https://user-images.githubusercontent.com/68326057/120660392-e88a7200-c4a4-11eb-9a52-704f33b05323.png)

# Kernal Exploit

![image](https://user-images.githubusercontent.com/68326057/120665887-cb0bd700-c4a9-11eb-8c4a-d68fc726a929.png)

