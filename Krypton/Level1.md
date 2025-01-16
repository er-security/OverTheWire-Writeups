```

Krypton Level 0 → Level 1
Level Info

Welcome to Krypton! The first level is easy. The following string encodes the password using Base64:

S1JZUFRPTklTR1JFQVQ=

Use this password to log in to krypton.labs.overthewire.org with username krypton1 using SSH on port 2231. You can find the files for other levels in /krypton/
```

base64でencodeされたpasswordをdecodeしてssh接続するらしい。  

encodeされた文字列をファイルに記載して、`base64 -d`コマンドでdecodeを行える。  

decodeしたpasswordでsshログインを試みる。  

```
krypton1@bandit:~$ id
uid=8001(krypton1) gid=8001(krypton1) groups=8001(krypton1)
```

クリア  

