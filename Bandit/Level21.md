```

Bandit Level 21 → Level 22
Level Goal

A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.
Commands you may need to solve this level

cron, crontab, crontab(5) (use “man 5 crontab” to access this)
```

cronの設定を見よ。という問題。  

cronとは  
>LinuxやUnix系のシステムで、指定した時間に自動的にコマンドやスクリプトを実行するための機能

`/etc/cron.d/`ディレクトリ配下の結果  
```
bandit21@bandit:~$ ls -la /etc/cron.d/
total 44
drwxr-xr-x   2 root root  4096 Sep 19 07:10 .
drwxr-xr-x 121 root root 12288 Sep 20 18:37 ..
-rw-r--r--   1 root root   120 Sep 19 07:08 cronjob_bandit22
-rw-r--r--   1 root root   122 Sep 19 07:08 cronjob_bandit23
-rw-r--r--   1 root root   120 Sep 19 07:08 cronjob_bandit24
-rw-r--r--   1 root root   201 Apr  8  2024 e2scrub_all
-rwx------   1 root root    52 Sep 19 07:10 otw-tmp-dir
-rw-r--r--   1 root root   102 Mar 31  2024 .placeholder
-rw-r--r--   1 root root   396 Jan  9  2024 sysstat
```

`cronjob_bandit22`という今回の問題に関係がありそうなファイルがあるので開いてみる。  

```
bandit21@bandit:~$ cat /etc/cron.d/cronjob_bandit22
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
```

`/usr/bin/cronjob_bandit22.sh`のシェルスクリプトを毎分動かす設定がなされている。  

次は`/usr/bin/cronjob_bandit22.sh`の内容を見る。  

```
bandit21@bandit:~$ cat /usr/bin/cronjob_bandit22.sh
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```

bandit22の資格情報を/tmp配下のファイルに書き出している。  

/tmp配下の書き出しているファイルを開くと資格情報をゲットしてクリア。  

