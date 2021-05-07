![image](https://user-images.githubusercontent.com/68326057/117393657-3a75c180-af12-11eb-9978-dbbf99d1b27f.png)

# NMAP

```bash
PORT   STATE SERVICE REASON  VERSION
21/tcp open  ftp     syn-ack vsftpd 3.0.3
|_ftp-anon: Anonymous FTP login allowed (FTP code 230)
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:192.168.49.180
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 3
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
Service Info: OS: Unix
```

![image](https://user-images.githubusercontent.com/68326057/117394987-d274aa80-af14-11eb-80aa-0f05b942656d.png)


--> We got one Username from challenge `Dredd`.


# FTP

![image](https://user-images.githubusercontent.com/68326057/117394170-48781200-af13-11eb-8adf-05b9c406d562.png)

--> Another username from ftp hannah

# ssh

```bash
chmod 600 id_rsa
ssh -i id_rsa hannah@ip -p 610000
```

![image](https://user-images.githubusercontent.com/68326057/117394474-deac3800-af13-11eb-898a-44a59fd015c5.png)

![image](https://user-images.githubusercontent.com/68326057/117394624-1c10c580-af14-11eb-8b02-120e3d15c6aa.png)

![image](https://user-images.githubusercontent.com/68326057/117394818-7f025c80-af14-11eb-86dc-8d99cd019d7f.png)
