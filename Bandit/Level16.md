```

Bandit Level 16 → Level 17
Level Goal

The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL/TLS and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.
Commands you may need to solve this level

ssh, telnet, nc, ncat, socat, openssl, s_client, nmap, netstat, ss
Helpful Reading Material

    Port scanner on Wikipedia

```

次もLevel15同様パスワードを送信するのだが今回は、31000~32000番ポートから正しいのを探すらしい。  

nmapを使って探す。  
```
bandit16@bandit:~$ nmap -Pn -sT -p- localhost
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-01-08 13:44 UTC
Stats: 0:00:01 elapsed; 0 hosts completed (1 up), 1 undergoing Connect Scan
Connect Scan Timing: About 48.25% done; ETC: 13:44 (0:00:02 remaining)
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00012s latency).
Not shown: 65512 closed tcp ports (conn-refused)
PORT      STATE SERVICE
22/tcp    open  ssh
1111/tcp  open  lmsocialserver
1234/tcp  open  hotline
1840/tcp  open  netopia-vo2
2220/tcp  open  netiq
2230/tcp  open  queueadm
2231/tcp  open  wimaxasncp
2232/tcp  open  ivs-video
4091/tcp  open  ewinstaller
4321/tcp  open  rwhois
4444/tcp  open  krb524
8000/tcp  open  http-alt
30000/tcp open  ndmps
30001/tcp open  pago-services1
30002/tcp open  pago-services2
31046/tcp open  unknown
31518/tcp open  unknown
31691/tcp open  unknown
31790/tcp open  unknown
31960/tcp open  unknown
50001/tcp open  unknown
51790/tcp open  unknown
60917/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 2.52 seconds
```

31000~32000番の範囲で5つ見つかった。  

opensslを使って5つのポートに接続を行った。  
そして、31790番が間違ったパスワードの時に"Wrong! Please enter the correct current password."と返してくると判明。  

早速、現在のパスワードを送ってみるが"KEYUPDATE"と返されて終了してしまう。  

```
省略
    0070 - 1c 4e 45 99 b8 ef b0 98-16 ed f0 57 0a 6b 82 73   .NE........W.k.s
    0080 - 06 df b2 f1 fe 76 87 4f-ad 5e 88 4d 5d c2 56 a2   .....v.O.^.M].V.
    0090 - 7c f9 23 2f ec 9f ac 7c-43 67 37 69 f3 67 1f 3d   |.#/...|Cg7i.g.=
    00a0 - 28 1f 50 a9 a7 e7 0a 8b-63 55 d9 cc 74 5d 1b 5c   (.P.....cU..t].\
    00b0 - dc a4 c3 b0 70 ac 95 45-f2 3c 45 69 5f dc 8c 30   ....p..E.<Ei_..0
    00c0 - 4d 4b 73 3e b4 2c fb 24-3b 26 06 6f 35 13 ad 3c   MKs>.,.$;&.o5..<
    00d0 - 8e 04 7e 57 0f b8 c2 2e-1d 46 98 65 c0 cd 95 dd   ..~W.....F.e....

    Start Time: 1736345143
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
*******************************
KEYUPDATE
```

調べたら`-quiet`オプションというデバッグ情報を抑えるオプションでいけるらしい。  

サーバー側からRSA秘密鍵をもらってクリア。  

