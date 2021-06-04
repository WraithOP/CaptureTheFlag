3/100

# NMAP

```bash
PORT     STATE SERVICE       REASON          VERSION
80/tcp   open  http          syn-ack ttl 127 Microsoft IIS httpd 10.0
| http-methods: 
|   Supported Methods: OPTIONS TRACE GET HEAD POST
|_  Potentially risky methods: TRACE
|_http-server-header: Microsoft-IIS/10.0
|_http-title: IIS Windows Server
3389/tcp open  ms-wbt-server syn-ack ttl 127 Microsoft Terminal Services
| rdp-ntlm-info: 
|   Target_Name: RETROWEB
|   NetBIOS_Domain_Name: RETROWEB
|   NetBIOS_Computer_Name: RETROWEB
|   DNS_Domain_Name: RetroWeb
|   DNS_Computer_Name: RetroWeb
|   Product_Version: 10.0.14393
|_  System_Time: 2021-06-04T09:29:39+00:00
| ssl-cert: Subject: commonName=RetroWeb
| Issuer: commonName=RetroWeb
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2021-06-03T09:18:03
| Not valid after:  2021-12-03T09:18:03
| MD5:   9a59 4340 456c 5a77 d0ce 859c 0426 328c
| SHA-1: 0a2c 6189 7436 b119 09f1 ba74 1023 c270 ba11 e158
| -----BEGIN CERTIFICATE-----
| MIIC1DCCAbygAwIBAgIQESgSpNqCspRB0ivhVfZJMjANBgkqhkiG9w0BAQsFADAT
| MREwDwYDVQQDEwhSZXRyb1dlYjAeFw0yMTA2MDMwOTE4MDNaFw0yMTEyMDMwOTE4
| MDNaMBMxETAPBgNVBAMTCFJldHJvV2ViMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8A
| MIIBCgKCAQEApZiZXgHUp+im8RH8LGe1Ktz9ot/eC6JIVlsQYseQ092S1nqhY4j9
| hlzBVJGte05YebzoDmNCsFuMOihb1HF/RXVhsNDlh24O5hoSty8xNgp1a2I3Mrry
| YjC1qZWqdb4egbMT4O/QH1JswWyew+hgknh8yxT3ww5NWAsmDQdz7oNdIKVRa/0p
| 17CW75FdNPm++352vMnnEHN33rG8l53DoKd773fXrVUQjnOTqlvijKAxnqDiQsiX
| gCOJ5XWmgESwVeoNqZdU7oamcSuda3iHZBa0ZKa53fR5yFEZ+BRdVDEvRqrrhgN8
| Wi/yaZen3wY2xA5YN9a0zA0CZmMxF6lGQwIDAQABoyQwIjATBgNVHSUEDDAKBggr
| BgEFBQcDATALBgNVHQ8EBAMCBDAwDQYJKoZIhvcNAQELBQADggEBAIjCDagWsQ+z
| YoAzdd7+hWHtC8ete7zGU2N9Y508heMzCUADFrkMvlXPNVGOEvzqYLkZHZMgI3Cr
| y5nGzC8HSctUiDU2cE6mM263VrQPRONZ45ClfFgHXvldH/1Pg/H8doOrNiT6V9Em
| Ua09B7q/2M5mVC1RCLEkMrVAQT23UxVO81ihHhZpRUUSFrH1fLXrVQLaIwj7cStr
| rpQoSScsH2ktSZrYT1eTD3WzwtLEVF3ZneReF8yBKHuh09tUvnw3JdHFZYYHqCoZ
| tndAOseda2ODa74KpzFeE8LU9UhxLKAULwDAxL6gIlcJCHw6IZ9rmdJu1wz5WpQj
| LwFH4kW0Ojg=
|_-----END CERTIFICATE-----
|_ssl-date: 2021-06-04T09:30:16+00:00; -5h29m49s from scanner time.
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows
```

# Enumeration

## WEB

--> User Found

```bash
wade
```

![image](https://user-images.githubusercontent.com/68326057/120781792-08727200-c547-11eb-89ee-73d4ff2ea1db.png)


So it is a wordpress site

![image](https://user-images.githubusercontent.com/68326057/120782456-a36b4c00-c547-11eb-8105-2679f7f069fb.png)

I check his comments

![image](https://user-images.githubusercontent.com/68326057/120785581-e24ed100-c54a-11eb-8d38-28e4bed5737d.png)

```bash
parzival
``` 

So i Tried login in with xfreerdp with user:wade adn pass:parzival

![image](https://user-images.githubusercontent.com/68326057/120785710-05798080-c54b-11eb-8438-efe6cf324e50.png)


Yes we are IN

# USER - wade

```bash
define('DB_NAME', 'wordpress567');

/** MySQL database username */
define('DB_USER', 'wordpressuser567');

/** MySQL database password */
define('DB_PASSWORD', 'YSPgW[%C.mQE');

/** MySQL hostname */
define('DB_HOST', 'localhost');
```


https://github.com/jas502n/CVE-2019-1388

Read it

![image](https://user-images.githubusercontent.com/68326057/120788684-3e672480-c54e-11eb-9aec-403979872b82.png)

Found it in recycle bin

That exploit wasn't woking So, I used it :-

![image](https://user-images.githubusercontent.com/68326057/120791017-44aad000-c551-11eb-8302-0c247af6fa37.png)

https://github.com/SecWiki/windows-kernel-exploits

