```

Bandit Level 30 → Level 31
Level Goal

There is a git repository at ssh://bandit30-git@localhost/home/bandit30-git/repo via the port 2220. The password for the user bandit30-git is the same as for the user bandit30.

Clone the repository and find the password for the next level.
Commands you may need to solve this level

git
```

またgit問題。  


README.mdの中身  
```
bandit30@bandit:/tmp/tmp.PZ8RFzuFRj/repo$ ls -la
total 16
drwxrwxr-x 3 bandit30 bandit30 4096 Jan 13 16:51 .
drwx------ 3 bandit30 bandit30 4096 Jan 13 16:50 ..
drwxrwxr-x 8 bandit30 bandit30 4096 Jan 13 16:51 .git
-rw-rw-r-- 1 bandit30 bandit30   30 Jan 13 16:51 README.md
bandit30@bandit:/tmp/tmp.PZ8RFzuFRj/repo$ cat README.md 
just an epmty file... muahaha
```

git logはこんな感じ。  
```
bandit30@bandit:/tmp/tmp.PZ8RFzuFRj/repo$ git log
WARNING: terminal is not fully functional
Press RETURN to continue 
commit acfc3c67816fc778c4aeb5893299451ca6d65a78 (HEAD -> master, origin/master, origin/HEAD)
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Sep 19 07:08:44 2024 +0000

    initial commit of README.md
bandit30@bandit:/tmp/tmp.PZ8RFzuFRj/repo$ git show acfc3c67816fc778c4aeb5893299451ca6d65a78
WARNING: terminal is not fully functional
Press RETURN to continue 
commit acfc3c67816fc778c4aeb5893299451ca6d65a78 (HEAD -> master, origin/master, origin/HEAD)
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Sep 19 07:08:44 2024 +0000

    initial commit of README.md

diff --git a/README.md b/README.md
new file mode 100644
index 0000000..029ba42
--- /dev/null
+++ b/README.md
@@ -0,0 +1 @@
+just an epmty file... muahaha
```

Branchはこんな感じ。  
```
bandit30@bandit:/tmp/tmp.PZ8RFzuFRj/repo$ git branch -a
WARNING: terminal is not fully functional
Press RETURN to continue 
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/master
```

何もないので、gitコマンドを色々試していく。  


すると、Commitに好きな名前を付けられる（エイリアス）tagというものに気になるものが見つかった。  
```
bandit30@bandit:/tmp/tmp.PZ8RFzuFRj/repo$ git tag
WARNING: terminal is not fully functional
Press RETURN to continue 
secret
```

showする。  
```
bandit30@bandit:/tmp/tmp.PZ8RFzuFRj/repo$ git show secret 
WARNING: terminal is not fully functional
Press RETURN to continue 
******************************
```


クリア


