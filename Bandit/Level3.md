```
Bandit Level 3 → Level 4
Level Goal

The password for the next level is stored in a hidden file in the inhere directory.
Commands you may need to solve this level

ls , cd , cat , file , du , find
```

次の課題は隠しファイルを見られるか。  

`ls`コマンドに`-a`オプションを付けると隠しファイルも表示される。  

```
bandit3@bandit:~/inhere$ ls -la
total 12
drwxr-xr-x 2 root    root    4096 Sep 19 07:08 .
drwxr-xr-x 3 root    root    4096 Sep 19 07:08 ..
-rw-r----- 1 bandit4 bandit3   33 Sep 19 07:08 ...Hiding-From-You
```

クリア  

