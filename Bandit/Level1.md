```

Bandit Level 0 → Level 1
Level Goal

The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.
Commands you may need to solve this level

ls , cd , cat , file , du , find

TIP: Create a file for notes and passwords on your local machine!

Passwords for levels are not saved automatically. If you do not save them yourself, you will need to start over from bandit0.

Passwords also occasionally change. It is recommended to take notes on how to solve each challenge. As levels get more challenging, detailed notes are useful to return to where you left off, reference for later problems, or help others after you’ve completed the challenge.
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

