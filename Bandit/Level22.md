```

Bandit Level 22 → Level 23
Level Goal

A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.
Commands you may need to solve this level

cron, crontab, crontab(5) (use “man 5 crontab” to access this)
```

前のレベルに続きcron問題。  

以下な通り  
```
bandit22@bandit:~$ ls -l /etc/cron.d/
cronjob_bandit22  cronjob_bandit24  otw-tmp-dir       sysstat           
cronjob_bandit23  e2scrub_all       .placeholder      
bandit22@bandit:~$ ls -l /etc/cron.d/cronjob_bandit23
-rw-r--r-- 1 root root 122 Sep 19 07:08 /etc/cron.d/cronjob_bandit23
bandit22@bandit:~$ cat /etc/cron.d/cronjob_bandit23
@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
bandit22@bandit:~$ ls -la /usr/bin/cronjob_bandit23.sh
-rwxr-x--- 1 bandit23 bandit22 211 Sep 19 07:08 /usr/bin/cronjob_bandit23.sh
```

/usr/bin/cronjob_bandit23.shの中身  
```
bandit22@bandit:~$ cat /usr/bin/cronjob_bandit23.sh
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
```

`whoami`の結果を変数mynameに入れてる。  
変数mynameをmd5sumした出力の空白区切りされた最初の文字列を変数mytargetに入れてる。  

/etc/bandit_pass/$mynameの内容を/tmp/$mytargetにコピーしている。  

つまり、現在のユーザー（bandit23）をmd5でhash化した/tmp配下のファイル名に次の資格情報が入っているということ。  


クリア  

