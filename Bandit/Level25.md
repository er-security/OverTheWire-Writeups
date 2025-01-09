```

Bandit Level 25 → Level 26
Level Goal

Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it.

    NOTE: if you’re a Windows user and typically use Powershell to ssh into bandit: Powershell is known to cause issues with the intended solution to this level. You should use command prompt instead.

Commands you may need to solve this level

ssh, cat, more, vi, ls, id, pwd
```

問題の言ってることがよくわからないのでとりあえずssh。  

```
bandit25@bandit:~$ ls
bandit26.sshkey
bandit25@bandit:~$ cat bandit26.sshkey 
-----BEGIN RSA PRIVATE KEY-----
~
省略
~
-----END RSA PRIVATE KEY-----
```

ホームディレクトリに`bandit26.sshkey`のファイルがある。  
bandit26のRSA秘密鍵らしきものである。  

このキーを使ってbandit26に繋ぐ。  

