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

ところが、以下のように接続が切れてしまう。  
```

  _                     _ _ _   ___   __  
 | |                   | (_) | |__ \ / /  
 | |__   __ _ _ __   __| |_| |_   ) / /_  
 | '_ \ / _` | '_ \ / _` | | __| / / '_ \ 
 | |_) | (_| | | | | (_| | | |_ / /| (_) |
 |_.__/ \__,_|_| |_|\__,_|_|\__|____\___/ 
Connection to bandit.labs.overthewire.org closed.
```

とりあえず、bandit25のターミナルに戻って解決策を探す。  

`/etc/passwd`のbandit26のログインシェルを見てみると...  
`bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext`  

`/usr/bin/showtext`というものが設定されている。  
OverTheWire独自のファイルらしいのでドキュメントは存在しない。  

/usr/bin/showtextのコードはこんな感じ。  

```
bandit25@bandit:~$ file /usr/bin/showtext 
/usr/bin/showtext: POSIX shell script, ASCII text executable
bandit25@bandit:~$ cat /usr/bin/showtext 
#!/bin/sh

export TERM=linux

exec more ~/text.txt
exit 0
```


ここで私は解き方がわからず他の方の解法を見た。  

なんと、ターミナルのウィンドウサイズを変えて`v`コマンドよりエディタを起動してエディタの機能をシェルの起動を行う解法であった。  

つまり、`exec more ~/text.txt`でアスキーアートが表示されるがその時にターミナルのウィンドウサイズを変える。  

```
  _                     _ _ _   ___   __  
 | |                   | (_) | |__ \ / /  
 | |__   __ _ _ __   __| |_| |_   ) / /_  
 | '_ \ / _` | '_ \ / _` | | __| / / '_ \ 
--More--(66%)
```

こんな感じで、``--More--``にする。  
ここで`v`を入力しEnter。  

```
  _                     _ _ _   ___   __
 | |                   | (_) | |__ \ / /
 | |__   __ _ _ __   __| |_| |_   ) / /_
 | '_ \ / _` | '_ \ / _` | | __| / / '_ \
 | |_) | (_| | | | | (_| | | |_ / /| (_) |
 |_.__/ \__,_|_| |_|\__,_|_|\__|____\___/
~                                                                                                                    
~                                                                                                                    
~                                                                                                                    
~                                                                                                                    
~                                                                                                                    
~                                                                                                                    
~                                                                                                                    
~                                                                                                                    
~   
```

エディタ（vi）を起動。  

`:!sh`または`:!ls -la`とかで好きなコマンドを実行できる。  

今回は、`:e [filename]`という形で読み込み権限のあるファイルを開く（編集という形で）。  

`:e /etc/bandit_pass/bandit26`  

クリア
