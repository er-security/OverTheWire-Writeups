```
Bandit Level 14 → Level 15
Level Goal

The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.
Commands you may need to solve this level

ssh, telnet, nc, openssl, s_client, nmap
Helpful Reading Material

    How the Internet works in 5 minutes (YouTube) (Not completely accurate, but good enough for beginners)
    IP Addresses
    IP Address on Wikipedia
    Localhost on Wikipedia
    Ports
    Port (computer networking) on Wikipedia

```

今回の課題は、現在のレベル（Level14）のパスワードをlocalhost:30000に送信するとクリアらしい。  

nmapが使えるらしいのでlocalhostに向けてnmapを行う。  

```
bandit14@bandit:~$ nmap localhost
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-01-08 13:27 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00016s latency).
Not shown: 992 closed tcp ports (conn-refused)
PORT      STATE SERVICE
22/tcp    open  ssh
1111/tcp  open  lmsocialserver
1234/tcp  open  hotline
1840/tcp  open  netopia-vo2
4321/tcp  open  rwhois
8000/tcp  open  http-alt
30000/tcp open  ndmps
50001/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.10 seconds
```

確かに30000番ポートが開放されている。  

次に`nc`で30000番に繋いで適当な文字を送ってみる。  

```
bandit14@bandit:~$ nc localhost 30000
hoge
Wrong! Please enter the correct current password.
```

パスワードが違うと弾かれた。  


一つ前のレベル、Bandit13（Level13）からBandit14（Level14）に繋ぐのにRSA秘密鍵を使用したので、パスワードがわからないと思ったがLevel13のパスワードがよかったらしい。  

```
bandit14@bandit:~$ nc localhost 30000
*****************************
Correct!
*****************************
```

クリア  

