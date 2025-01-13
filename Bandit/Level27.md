```

Bandit Level 27 → Level 28
Level Goal

There is a git repository at ssh://bandit27-git@localhost/home/bandit27-git/repo via the port 2220. The password for the user bandit27-git is the same as for the user bandit27.

Clone the repository and find the password for the next level.
Commands you may need to solve this level

git
```

今回は、git関連の問題。  

まずは、一時作業ディレクトリを作成する。  
```
bandit27@bandit:~$ cd $(mktemp -d)
bandit27@bandit:/tmp/tmp.xdpS8J40C9$
```

`ssh://bandit27-git@localhost:2220/home/bandit27-git/repo`よりgitリポジトリをcloneする。  
```
bandit27@bandit:/tmp/tmp.xdpS8J40C9$ git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo
Cloning into 'repo'...
```

cloneを行ったリポジトリ内に`README`ファイルが存在し、中身に次のステージへの資格情報がありクリア。  
```
bandit27@bandit:/tmp/tmp.xdpS8J40C9$ ls -la
total 17016
drwx------ 3 bandit27 bandit27     4096 Jan 13 16:09 .
drwxrwx-wt 1 root     root     17412096 Jan 13 16:10 ..
drwxrwxr-x 3 bandit27 bandit27     4096 Jan 13 16:09 repo
bandit27@bandit:/tmp/tmp.xdpS8J40C9$ cd repo/
bandit27@bandit:/tmp/tmp.xdpS8J40C9/repo$ ls
README
bandit27@bandit:/tmp/tmp.xdpS8J40C9/repo$ cat README 
The password to the next level is: ******************************
```
