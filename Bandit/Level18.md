```

Bandit Level 18 → Level 19
Level Goal

The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.
Commands you may need to solve this level

ssh, ls, cat
```

次の問題は.bashrcが書き換えられており普通のssh接続ではコントロールすることはできないよって問題。  

ssh接続後に「Byebyte!」と表示されて、接続が閉じられる。  
恐らく.bashrcでBashが起動されないよう書き換えられている。  

SSHコマンドでのオプション`-t`で"強制的に擬似ターミナルを割り当てる。"  

こんな感じ↓  
$ ssh -p 2220 bandit.labs.overthewire.org -l bandit18 -t /bin/sh  

接続後にbandit18のホームディレクトリに移動し、readmeを開いてクリア。  

