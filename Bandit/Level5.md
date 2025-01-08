```

Bandit Level 5 → Level 6
Level Goal

The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

    human-readable
    1033 bytes in size
    not executable

Commands you may need to solve this level

ls , cd , cat , file , du , find
```

`du`コマンドでディレクトリやファイルのディスク容量を表示する。  
```
andit5@bandit:~/inhere$ du -ah
8.0K	./maybehere02/.file1
4.0K	./maybehere02/-file1
8.0K	./maybehere02/spaces file1
8.0K	./maybehere02/-file3
4.0K	./maybehere02/-file2
4.0K	./maybehere02/.file2
4.0K	./maybehere02/spaces file3
12K	./maybehere02/spaces file2
8.0K	./maybehere02/.file3
64K	./maybehere02
8.0K	./maybehere19/.file1
8.0K	./maybehere19/-file1
8.0K	./maybehere19/spaces file1
8.0K	./maybehere19/-file3
8.0K	./maybehere19/-file2
8.0K	./maybehere19/.file2
4.0K	./maybehere19/spaces file3
12K	./maybehere19/spaces file2
4.0K	./maybehere19/.file3
72K	./maybehere19
8.0K	./maybehere08/.file1
.
.
.
省略
```

たくさんのディレクトリにたくさんのファイルがありどこにFLAGが存在するのか探すのが大変。  

そういった場合は、`find`コマンドで探す。  
問題ページから`human-readable`、`1033 bytes in size`、`not executable`が得られるのでオプションを使って`find`する。  

```
bandit5@bandit:~/inhere$ find . -type f -size 1033c ! -perm /111
./maybehere07/.file2
```

見つけた。  
`./maybehere07/.file2`の内容を表示してクリア。  


