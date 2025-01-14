```

Bandit Level 32 → Level 33
Level Goal

After all this git stuff, it’s time for another escape. Good luck!
Commands you may need to solve this level

sh, man
```

そろそろ終わりに近づいている。  

sshを行った後...
```
WELCOME TO THE UPPERCASE SHELL
>> ls
sh: 1: LS: Permission denied
>> id
sh: 1: ID: Permission denied
>> 
```

"UPPERCASE SHELL"ということで大文字に変換されている。  

色々試していと、`${command}`を使用したパラメータ展開の機能で変化があった。  
```
>> ${ls}
>> ${pwd}
sh: 1: /home/bandit32: Permission denied
```

しかし、活用方法がわからない....。  


色々試すと`$0`の時に変化があった。  

```
>> $0
$ ls
uppershell
$ pwd
/home/bandit32
```

つまりuppershell上では小文字が大文字に変換され、環境変数は使える。  
`$0`でシェルを再実行してuppershellから抜けたことでコマンドが実行できるようになった。  


/etc/bandit_passから資格情報を手に入れクリア。  

