```
Bandit Level 15 → Level 16
Level Goal

The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.

Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.
Commands you may need to solve this level

ssh, telnet, nc, ncat, socat, openssl, s_client, nmap, netstat, ss
Helpful Reading Material

    Secure Socket Layer/Transport Layer Security on Wikipedia
    OpenSSL Cookbook - Testing with OpenSSL
```

次の課題は、Level14でやったこと同様現在（Level15）のパスワードを指定されたポートに送るというもの。  

ただし、今回はSSL/TLS通信を行ってパスワードを送る必要がある。  

`openssl`コマンドが用意されているので以下の形式でSSL/TLS通信を行うことができる。  

$ openssl s_client -connect [host:port]

今回の場合は、  
`$ openssl s_client -connect localhost:30001`  


鍵交換を終え接続が完了して、パスワードを送信するとクリア。  

```
省略
    0060 - 83 90 0a 06 41 fc 6b 9c-4b 3d d9 d9 1d 32 5c d7   ....A.k.K=...2\.
    0070 - 17 2f b4 bf d3 d8 f7 03-e1 b9 04 4f 30 36 73 7f   ./.........O06s.
    0080 - 22 8a 21 cb af ad e0 26-08 e7 1b 39 f2 e6 57 b6   ".!....&...9..W.
    0090 - 79 30 51 e3 6e f8 41 22-13 d7 35 04 99 b0 5b 14   y0Q.n.A"..5...[.
    00a0 - 44 ba 00 05 c7 7c 8f 1f-8a bd a8 04 87 e3 c7 42   D....|.........B
    00b0 - 20 56 67 1c 1d 10 ad e5-27 f4 c6 52 be 12 ac 2f    Vg.....'..R.../
    00c0 - e4 86 43 b5 11 4f 14 40-a0 7b 24 67 d1 73 e8 50   ..C..O.@.{$g.s.P
    00d0 - 91 40 33 e8 82 e5 9d fa-76 7f 84 0b 35 a9 7a 65   .@3.....v...5.ze

    Start Time: 1736343299
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
*********************************
Correct!
*********************************

closed
```
