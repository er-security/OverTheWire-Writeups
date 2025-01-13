```

Bandit Level 28 → Level 29
Level Goal

There is a git repository at ssh://bandit28-git@localhost/home/bandit28-git/repo via the port 2220. The password for the user bandit28-git is the same as for the user bandit28.

Clone the repository and find the password for the next level.
Commands you may need to solve this level

git
```

今回もgit関連。  

一時ディレクトリ内で作業する。  
```
bandit28@bandit:~$ cd $(mktemp -d)
```

`ssh://bandit28-git@localhost:2220/home/bandit28-git/repo`よりcloneを行う。  

```
bandit28@bandit:/tmp/tmp.wV3XKwktMY$ git clone ssh://bandit28-git@localhost:2220/home/bandit28-git/repo
~
省略
~
remote: Enumerating objects: 9, done.        
remote: Counting objects: 100% (9/9), done.        
remote: Compressing objects: 100% (6/6), done.        
remote: Total 9 (delta 2), reused 0 (delta 0), pack-reused 0        
Receiving objects: 100% (9/9), done.
Resolving deltas: 100% (2/2), done.
```

次  
```
bandit28@bandit:/tmp/tmp.wV3XKwktMY$ ls -la
total 17016
drwx------ 3 bandit28 bandit28     4096 Jan 13 16:13 .
drwxrwx-wt 1 root     root     17412096 Jan 13 16:14 ..
drwxrwxr-x 3 bandit28 bandit28     4096 Jan 13 16:14 repo
bandit28@bandit:/tmp/tmp.wV3XKwktMY$ cd repo/
bandit28@bandit:/tmp/tmp.wV3XKwktMY/repo$ ls
README.md
bandit28@bandit:/tmp/tmp.wV3XKwktMY/repo$ cat README.md 
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: xxxxxxxxxx
```

こんな感じで、bandit29のpasswordが"xxxxxxxxxx"と不明な状態である。  

gitのlogに消される前にpasswordがあるかもしれないので見てみる。  

```
bandit28@bandit:/tmp/tmp.wV3XKwktMY/repo$ git log
WARNING: terminal is not fully functional
Press RETURN to continue 
commit 817e303aa6c2b207ea043c7bba1bb7575dc4ea73 (HEAD -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Thu Sep 19 07:08:39 2024 +0000

    fix info leak

commit 3621de89d8eac9d3b64302bfb2dc67e9a566decd
Author: Morla Porla <morla@overthewire.org>
Date:   Thu Sep 19 07:08:39 2024 +0000

    add missing data

commit 0622b73250502618babac3d174724bb303c32182
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Sep 19 07:08:39 2024 +0000

    initial commit of README.md
```

こんな感じ。  

最初の"initial commit of README.md"を見てみる。  

```
bandit28@bandit:/tmp/tmp.wV3XKwktMY/repo$ git show 0622b73250502618babac3d174724bb303c32182
WARNING: terminal is not fully functional
Press RETURN to continue 
commit 0622b73250502618babac3d174724bb303c32182
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Sep 19 07:08:39 2024 +0000

    initial commit of README.md

diff --git a/README.md b/README.md
new file mode 100644
index 0000000..7ba2d2f
--- /dev/null
+++ b/README.md
@@ -0,0 +1,8 @@
+# Bandit Notes
+Some notes for level29 of bandit.
+
+## credentials
+
+- username: bandit29
+- password: <TBD>
+
```

passwordの欄が未定となっている。  

次の"add missing data"を見る。  

```
bandit28@bandit:/tmp/tmp.wV3XKwktMY/repo$ git show 3621de89d8eac9d3b64302bfb2dc67e9a566decd 
WARNING: terminal is not fully functional
Press RETURN to continue 
commit 3621de89d8eac9d3b64302bfb2dc67e9a566decd
Author: Morla Porla <morla@overthewire.org>
Date:   Thu Sep 19 07:08:39 2024 +0000

    add missing data

diff --git a/README.md b/README.md
index 7ba2d2f..d4e3b74 100644
--- a/README.md
+++ b/README.md
@@ -4,5 +4,5 @@ Some notes for level29 of bandit.
 ## credentials
 
 - username: bandit29
-- password: <TBD>
+- password: ****************************
```


passwordの欄が更新されており資格情報が見られた。  

クリア。  

