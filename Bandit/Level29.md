```

Bandit Level 29 → Level 30
Level Goal

There is a git repository at ssh://bandit29-git@localhost/home/bandit29-git/repo via the port 2220. The password for the user bandit29-git is the same as for the user bandit29.

Clone the repository and find the password for the next level.
Commands you may need to solve this level

git
```

3問連続git関連。  

一時ディレクトリを作成して、指定されたgitリポジトリよりcloneした後...


```
bandit29@bandit:/tmp/tmp.qftdLNW5NN/repo$ ls -la
total 16
drwxrwxr-x 3 bandit29 bandit29 4096 Jan 13 16:32 .
drwx------ 3 bandit29 bandit29 4096 Jan 13 16:32 ..
drwxrwxr-x 8 bandit29 bandit29 4096 Jan 13 16:32 .git
-rw-rw-r-- 1 bandit29 bandit29  131 Jan 13 16:32 README.md
bandit29@bandit:/tmp/tmp.qftdLNW5NN/repo$ cat README.md 
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: <no passwords in production!>

```

一応更新Logを確認する。  

```
bandit29@bandit:/tmp/tmp.qftdLNW5NN/repo$ git log
WARNING: terminal is not fully functional
Press RETURN to continue 
commit 6ac7796430c0f39290a0e29a4d32e5126544b022 (HEAD -> master, origin/master, origin/HEAD)
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Sep 19 07:08:41 2024 +0000

    fix username

commit e65a928cca4db1863b478cf5e93d1d5b1c1bd6b2
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Sep 19 07:08:41 2024 +0000

    initial commit of README.md
```

2つ表示する。  

```
bandit29@bandit:/tmp/tmp.qftdLNW5NN/repo$ git show e65a928cca4db1863b478cf5e93d1d5b1c1bd6b2
WARNING: terminal is not fully functional
Press RETURN to continue 
commit e65a928cca4db1863b478cf5e93d1d5b1c1bd6b2
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Sep 19 07:08:41 2024 +0000

    initial commit of README.md

diff --git a/README.md b/README.md
new file mode 100644
index 0000000..2da2f39
--- /dev/null
+++ b/README.md
@@ -0,0 +1,8 @@
+# Bandit Notes
+Some notes for bandit30 of bandit.
+
+## credentials
+
+- username: bandit29
+- password: <no passwords in production!>
+
bandit29@bandit:/tmp/tmp.qftdLNW5NN/repo$ git show 6ac7796430c0f39290a0e29a4d32e5126544b022
WARNING: terminal is not fully functional
Press RETURN to continue 
commit 6ac7796430c0f39290a0e29a4d32e5126544b022 (HEAD -> master, origin/master, origin/HEAD)
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Sep 19 07:08:41 2024 +0000

    fix username

diff --git a/README.md b/README.md
index 2da2f39..1af21d3 100644
--- a/README.md
+++ b/README.md
@@ -3,6 +3,6 @@ Some notes for bandit30 of bandit.
 
 ## credentials
 
-- username: bandit29
+- username: bandit30
 - password: <no passwords in production!>
```

まぁ、ないだろうな。  

gitで他にできることをやっていく...  


すると全てのBranchを表示したら色々出てきた。  

```
bandit29@bandit:/tmp/tmp.qftdLNW5NN/repo$ git branch -a
WARNING: terminal is not fully functional
Press RETURN to continue 
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/dev
  remotes/origin/master
  remotes/origin/sploits-dev
```

一応説明するとBranchとは、  
・プロジェクトの開発履歴を分岐させる機能  
・異なる機能開発やバグ修正を並行して進めることができる  
・各ブランチは独立して作業でき、メインの開発に影響を与えずに実験的な変更を試せる  
というもの。  

`git checkout <ブランチ名>`でBranchの切り替えができる。  

```
bandit29@bandit:/tmp/tmp.qftdLNW5NN/repo$ git checkout dev
Switched to branch 'dev'
Your branch is up to date with 'origin/dev'.
```

README.mdを見てみる。  

```
bandit29@bandit:/tmp/tmp.qftdLNW5NN/repo$ cat README.md 
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: ***************************
```

クリア。  









