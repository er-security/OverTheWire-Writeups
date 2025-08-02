"la -la"をやる  

```
leviathan1@leviathan:~$ ls -la
total 36
drwxr-xr-x   2 root       root        4096 Jul 28 19:05 .
drwxr-xr-x 150 root       root        4096 Jul 28 19:06 ..
-rw-r--r--   1 root       root         220 Mar 31  2024 .bash_logout
-rw-r--r--   1 root       root        3851 Jul 28 18:47 .bashrc
-r-sr-x---   1 leviathan2 leviathan1 15084 Jul 28 19:05 check
-rw-r--r--   1 root       root         807 Mar 31  2024 .profile
```

`check`というバイナリファイルがある。  
```
leviathan1@leviathan:~$ file check 
check: setuid ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, BuildID[sha1]=990fa9b7d511205601669835610d587780d0195e, for GNU/Linux 3.2.0, not stripped
```

実行してみる。  
```
leviathan1@leviathan:~$ ./check 
password: hoge
Wrong password, Good Bye ...
```

パスワードの入力が求められ適当に入力したら間違っていると言われた。  
バイナリファイル内にパスワードがハードコーディングされているかもしれないので調べる。  

```
leviathan1@leviathan:~$ ltrace ./check
__libc_start_main(0x80490ed, 1, 0xffffd384, 0 <unfinished ...>
printf("password: ")                                                    = 10
getchar(0, 0, 0x786573, 0x646f67password: hoge
)                                       = 104
getchar(0, 104, 0x786573, 0x646f67)                                     = 111
getchar(0, 0x6f68, 0x786573, 0x646f67)                                  = 103
strcmp("hog", "sex")                                                    = -1
puts("Wrong password, Good Bye ..."Wrong password, Good Bye ...

```

見つけたけど性的用語じゃないか？？  

`/etc/leviathan_pass`配下にそれぞれのユーザーのパスワードが保存されているので確認してクリア  
```
$ cd /etc/leviathan_pass
$ ls
leviathan0  leviathan1	leviathan2  leviathan3	leviathan4  leviathan5	leviathan6  leviathan7
$ cat leviathan2
NsN1HwFoyN
```
