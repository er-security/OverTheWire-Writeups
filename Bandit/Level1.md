```
Bandit Level 1 → Level 2
Level Goal

The password for the next level is stored in a file called - located in the home directory
Commands you may need to solve this level

ls , cd , cat , file , du , find
Helpful Reading Material

    Google Search for “dashed filename”
    Advanced Bash-scripting Guide - Chapter 3 - Special Characters
```

次の課題はLevel0で入手したflag（資格情報）でsshを行い、  
`ls , cd , cat , file , du , find`コマンドを駆使して次の資格情報を探すというもの。  

ログインを行い`ls`を使うとファイル名が「-」ハイフンのファイルがある。  
```
bandit1@bandit:~$ ls
-
```

ただ`cat -`で読み込もうとすると「-」ファイル名がオプションとして認識してしまい読み込めない。  

そういった場合は、現在のディレクトリを指定して読み込む。  

`cat ./-`

次の資格情報を入手してクリア  

