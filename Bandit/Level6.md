```

Bandit Level 6 → Level 7
Level Goal

The password for the next level is stored somewhere on the server and has all of the following properties:

    owned by user bandit7
    owned by group bandit6
    33 bytes in size

Commands you may need to solve this level

ls , cd , cat , file , du , find , grep
```

Level5で行ったように問題ページから得られる情報を`find`コマンドのオプションを駆使して探す。  

ただ今回は、ホームディレクトリ配下に何もなくrootディレクトリから探す。  

```
bandit6@bandit:~$ find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
/var/lib/dpkg/info/bandit7.password
```

`/var/lib/dpkg/info/bandit7.password`をcatしてクリア。  

