```

Bandit Level 19 → Level 20
Level Goal

To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.
Helpful Reading Material

    setuid on Wikipedia

```

今回の課題は`setuid`がセットされたバイナリファイルを使用して資格情報を手に入れようって感じ。  

setuidとは  
>Linuxにおけるsetuidとは、特定のプログラムを実行する際に、そのプログラムの所有者の権限で実行できるようにする仕組み。

ssh後のホームディレクトリに`bandit20-do`バイナリファイルが存在する。  
```
bandit19@bandit:~$ ls -la bandit20-do 
-rwsr-x--- 1 bandit20 bandit19 14880 Sep 19 07:08 bandit20-do
```

所有者はbandit20ユーザとなっている。  

実行してみると、好きなコマンドを引数に入れてコマンドを実行できるらしい。  
```
bandit19@bandit:~$ ./bandit20-do 
Run a command as another user.
  Example: ./bandit20-do id
```

このファイルには次のレベルのbandit20のsetuidがセットされているのでこのバイナリファイルを使用して`/etc/bandit_pass/bandit20`を開く。  

`bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20`  

クリア  

