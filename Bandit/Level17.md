```

Bandit Level 17 → Level 18
Level Goal

There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19
Commands you may need to solve this level

cat, grep, ls, diff
```

次の課題は、`passwords.old`と`passwords.new`ファイルの2つの差異を見つけること。  

`diff`コマンドで２つのファイルの差異を見つける。  

```
bandit17@bandit:~$ diff passwords.new passwords.old 
42c42
< ********************************
---
> ktfgBvpMzWKR5ENj26IbLGSblgUG9CzB
```

クリア  

