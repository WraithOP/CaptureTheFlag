<!-- 4/100 -->

# NMAP

```bash
PORT   STATE SERVICE REASON         VERSION
22/tcp open  ssh     syn-ack ttl 63 OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    syn-ack ttl 63 Apache httpd 2.4.29 ((Ubuntu))
|_http-favicon: Unknown favicon MD5: 9899F13BCC614EE8275B88FFDC0D04DB
| http-methods: 
|_  Supported Methods: GET POST OPTIONS HEAD
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: Marco's Blog
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

# Enumeratiob

## WEB

![image](https://user-images.githubusercontent.com/68326057/120795370-031d2380-c557-11eb-86eb-5f5f9a8e1b29.png)

There is lot of information on the main page So it .So i genereated a wordlist of it with cewl.

In Login.php

Something unual with js

![image](https://user-images.githubusercontent.com/68326057/120795988-d3bae680-c557-11eb-8202-99287ade6567.png)

I use js Beautifier to beautify the code

```js
    const _0x44d4 = ['auth', 'querySelector', 'click', 'replace', 'post', '#submit-btn', 'input', 'then', 'authLogin=', 'addEventListener', 'keyCode', '#username', 'style', 'Success', '/admin', 'keyup', 'location', 'Response', 'cookie', 'application/json', 'stringify', 'same-origin', 'querySelectorAll', 'value', 'opacity:\x201'];
(function(_0x2a05df, _0x44d43e) {
    const _0x48fdee = function(_0x21eb22) {
        while (--_0x21eb22) {
            _0x2a05df['push'](_0x2a05df['shift']());
        }
    };
    _0x48fdee(++_0x44d43e);
}(_0x44d4, 0x114));

const _0x48fd = function(_0x2a05df, _0x44d43e) {
    _0x2a05df = _0x2a05df - 0x0;
    let _0x48fdee = _0x44d4[_0x2a05df];
    return _0x48fdee;
};

function login() {
    const _0x289586 = document[_0x48fd('0x0')]('#username'),
        _0x56c661 = document[_0x48fd('0x0')]('#password'),
        _0x236a57 = md5(_0x56c661[_0x48fd('0x16')]);
    fetch('/api/login', {
        'method': _0x48fd('0x3'),
        'credentials': _0x48fd('0x14'),
        'headers': {
            'Accept': _0x48fd('0x12')
        },
        'body': JSON[_0x48fd('0x13')]({
            'username': _0x289586[_0x48fd('0x16')],
            'password': _0x236a57
        })
    })[_0x48fd('0x6')](_0x59ed95 => _0x59ed95['json']())['then'](_0x5d33bc => {
        document[_0x48fd('0x0')](_0x48fd('0xa'))['value'] = '', document[_0x48fd('0x0')]('#password')[_0x48fd('0x16')] = '', _0x5d33bc[_0x48fd('0x10')] == _0x48fd('0xc') ? (document[_0x48fd('0x11')] = _0x48fd('0x7') + _0x5d33bc[_0x48fd('0x18')] + ';\x20samesite=lax;\x20path=\x22/\x22', window[_0x48fd('0xf')][_0x48fd('0x2')](_0x48fd('0xd'))) : (alert(_0x5d33bc['Verbose']), document[_0x48fd('0x0')]('#pass-hint')[_0x48fd('0xb')] = _0x48fd('0x17'));
    });
}
document[_0x48fd('0x15')](_0x48fd('0x5'))['forEach'](_0x47694c => {
    _0x47694c[_0x48fd('0x8')](_0x48fd('0xe'), _0x571e21 => {
        _0x571e21[_0x48fd('0x9')] === 0xd && document[_0x48fd('0x0')](_0x48fd('0x4'))[_0x48fd('0x1')]();
    });
}); 
```

![image](https://user-images.githubusercontent.com/68326057/120798315-cf43fd00-c55a-11eb-9b09-b0b50923c4da.png)


Then Use md5sum on on wordlist to generate new hash wordlist
Made a for loop of curl 

And got credential

# Information Gathering
```bash
marco:savoia21!
```

![image](https://user-images.githubusercontent.com/68326057/120805334-55644180-c563-11eb-8f03-560c2c00eb1e.png)

![image](https://user-images.githubusercontent.com/68326057/120805483-7d53a500-c563-11eb-9b03-fdb8ff489507.png)

I tried to login in ssh

And yes we got in

![image](https://user-images.githubusercontent.com/68326057/120805866-dd4a4b80-c563-11eb-8a80-1561e6ef5c04.png)


USERS:-

![image](https://user-images.githubusercontent.com/68326057/120806032-ffdc6480-c563-11eb-892a-c49106f5e9fb.png)


![image](https://user-images.githubusercontent.com/68326057/120806380-68c3dc80-c564-11eb-914e-2905939e6458.png)


![image](https://user-images.githubusercontent.com/68326057/120806490-8c872280-c564-11eb-87ed-96cbf6e7a51b.png)


![image](https://user-images.githubusercontent.com/68326057/120807708-dae8f100-c565-11eb-8bda-e3a494575cb6.png)

I canged the command to download a file

![image](https://user-images.githubusercontent.com/68326057/120807793-f81dbf80-c565-11eb-8a6e-32a4b7d76bf3.png)


![image](https://user-images.githubusercontent.com/68326057/120807855-08ce3580-c566-11eb-947f-95c572bdc1be.png)

![image](https://user-images.githubusercontent.com/68326057/120807973-30250280-c566-11eb-8ca3-3f8b01a1a7f8.png)

![image](https://user-images.githubusercontent.com/68326057/120808050-48951d00-c566-11eb-9956-b68da688d04c.png)

```bash
curtis:Donald1983$
```

![image](https://user-images.githubusercontent.com/68326057/120808144-62cefb00-c566-11eb-9f7c-8f581912fc1d.png)

![image](https://user-images.githubusercontent.com/68326057/120808311-927e0300-c566-11eb-8ded-f13dca135e88.png)


In marco
![image](https://user-images.githubusercontent.com/68326057/120812441-99a71000-c56a-11eb-9b99-aaf4f7114009.png)

In curtis
![image](https://user-images.githubusercontent.com/68326057/120812225-6b293500-c56a-11eb-95af-673ca1175513.png)

![image](https://user-images.githubusercontent.com/68326057/120812183-619fcd00-c56a-11eb-958e-7c83f7805df1.png)




