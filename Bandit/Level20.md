```

Bandit Level 20 → Level 21
Level Goal

There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

NOTE: Try connecting to your own network daemon to see if it works as you think
Commands you may need to solve this level

ssh, nc, cat, bash, screen, tmux, Unix ‘job control’ (bg, fg, jobs, &, CTRL-Z, …)
```

ホームディレクトリに`suconnect`バイナリファイルがあり、setuidが設定されている。  
bandit21ユーザの権限でこのバイナリファイルを動かせる。  

```
bandit20@bandit:~$ ls -l suconnect 
-rwsr-x--- 1 bandit21 bandit20 15604 Sep 19 07:08 suconnect
```

問題文には`suconnect`バイナリファイルで指定したポートに接続を行い、前のパスワード（bandit20）を送信して比較し、正しければ  
次の資格情報を送信するよというもの。  

CTRL-Zやfgコマンドなどを駆使して行っていく。  

`nc -nlvp 54321`  

上記のncコマンドで54321番ポートで接続を待ち受ける。  
CTRL-Zでバックグラウンド処理に変更する。  

`./suconnect 54321`を行ってncで待ち受けているポートに接続を行いパスワードを送信する。  

fgコマンドでバッググラウンド処理をしているncコマンドをフォアグラウンドに戻す。  

資格情報が送られているのでこれでクリア。  

