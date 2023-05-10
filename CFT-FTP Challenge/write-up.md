# Root Me

[![N|Solid](https://www.root-me.org/IMG/logo/siteon0.svg?1637496509)](https://www.root-me.org/?page=news&lang=en)

## Network
Investigate captured traffic, network services and perform packet analysis
The following set of problems deal with network traffic including different protocols. You need to analyse the packet captures to solve these challenges.

Prerequisites:
 - Knowledge of a network capture analyzing tool.
 -Knowlege of the most common network protocols.

### FTP - authentication
https://www.root-me.org/en/Challenges/Network/FTP-authentication
An authenticated file exchange achieved through FTP. Recover the password used by the user.
To begin we must download the file below and run it with wireshark .You will have this interface and then you simply follow the tcp stream

![Capture d'écran](https://media.geeksforgeeks.org/wp-content/uploads/20220812133910/ws.jpg)

## TELNET - authentication
https://www.root-me.org/en/Challenges/Network/TELNET-authentication
Find the user password in this TELNET session capture. the instructions are the same as that of ftp


## ETHERNET - frame
https://www.root-me.org/en/Challenges/Network/ETHERNET-frame

Find the (supposed to be) confidential data in this ethernet frame. the instructions are the same as those of ftp but the difference here is that you are redirected to a site where there is this data

> 00 05 73 a0 00 00 e0 69 95 d8 5a 13 86 dd 60 00
00 00 00 9b 06 40 26 07 53 00 00 60 2a bc 00 00
00 00 ba de c0 de 20 01 41 d0 00 02 42 33 00 00
00 00 00 00 00 04 96 74 00 50 bc ea 7d b8 00 c1
d7 03 80 18 00 e1 cf a0 00 00 01 01 08 0a 09 3e
69 b9 17 a1 7e d3 47 45 54 20 2f 20 48 54 54 50
2f 31 2e 31 0d 0a 41 75 74 68 6f 72 69 7a 61 74
69 6f 6e 3a 20 42 61 73 69 63 20 59 32 39 75 5a
6d 6b 36 5a 47 56 75 64 47 6c 68 62 41 3d 3d 0d
0a 55 73 65 72 2d 41 67 65 6e 74 3a 20 49 6e 73
61 6e 65 42 72 6f 77 73 65 72 0d 0a 48 6f 73 74
3a 20 77 77 77 2e 6d 79 69 70 76 36 2e 6f 72 67
0d 0a 41 63 63 65 70 74 3a 20 2a 2f 2a 0d 0a 0d
0a

So these are hexadecimal numbers so you need to decode it you can use any tool you want to decode it into human readable text.
After the decoding you will get this

>s��i��Z��`�@&S`*����� A�B3�tP��}�����Ϡ
	>i��~�GET / HTTP/1.1
Authorization: Basic Y29uZmk6ZGVudGlhbA==
User-Agent: InsaneBrowser
Host: www.myipv6.org
Accept: * */* *

In the decoded text there will be a base 64 word and you will only have to decode that to get the password.

## Twitter authentication
A twitter authentication session has been captured, you have to retrieve the password.
Here we come back with the same instructions as ftp and telnet authentication. you download the file and you open it in wireshark and you follow the tcp stream. After you follow tcp stream you'd get this :

>GET /statuses/replies.xml HTTP/1.1
User-Agent: CFNetwork/330
Cookie: _twitter_sess=BAh7CDoJdXNlcjA6B2lkIiVmZGQ2ODc5MTMwMWFhOTFiMWExZDViZmQwMGEz%250AOWNkMyIKZmxhc2hJQzonQWN0aW9uQ29udHJvbGxlcjo6Rmxhc2g6OkZsYXNo%250ASGFzaHsABjoKQHVzZWR7AA%253D%253D--ea12e7bc090d05202cd7e3f972c2b4414a97f657
Accept: */*
Accept-Language: en-us
Accept-Encoding: gzip, deflate
Authorization: Basic dXNlcnRlc3Q6cGFzc3dvcmQ=
Connection: keep-alive
Host: twitter.com

To get the password you just have to decode the word in base 64.

 
