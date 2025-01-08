```
Bandit Level 2 → Level 3
Level Goal

The password for the next level is stored in a file called spaces in this filename located in the home directory
Commands you may need to solve this level

ls , cd , cat , file , du , find
Helpful Reading Material

    Google Search for “spaces in filename”
```

Level2で入手した資格情報でSSHする。  

```
bandit2@bandit:~$ ls -la
total 24
drwxr-xr-x  2 root    root    4096 Sep 19 07:08 .
drwxr-xr-x 70 root    root    4096 Sep 19 07:09 ..
-rw-r--r--  1 root    root     220 Mar 31  2024 .bash_logout
-rw-r--r--  1 root    root    3771 Mar 31  2024 .bashrc
-rw-r--r--  1 root    root     807 Mar 31  2024 .profile
-rw-r-----  1 bandit3 bandit2   33 Sep 19 07:08 spaces in this filename
```

"spaces in this filename"というスペースが含まれたファイル名が存在する。  
これを読み込むというのが今回の課題。  

以下のようにスペースを「\」バックスラッシュでエスケープさせる。  

```
bandit2@bandit:~$ cat spaces\ in\ this\ filename
```

資格情報を入手してクリア。  

