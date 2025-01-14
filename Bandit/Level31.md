```

Bandit Level 31 → Level 32
Level Goal

There is a git repository at ssh://bandit31-git@localhost/home/bandit31-git/repo via the port 2220. The password for the user bandit31-git is the same as for the user bandit31.

Clone the repository and find the password for the next level.
Commands you may need to solve this level

git
```

同じく  
```
bandit31@bandit:~$ cd $(mktemp -d)
bandit31@bandit:/tmp/tmp.JtE6SrxG8y$ git clone ssh://bandit31-git@localhost:2220/home/bandit31-git/repo
Cloning into 'repo'...
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit31/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit31/.ssh/known_hosts).
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

bandit31-git@localhost's password: 
remote: Enumerating objects: 4, done.        
remote: Counting objects: 100% (4/4), done.        
remote: Compressing objects: 100% (3/3), done.        
remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0        
Receiving objects: 100% (4/4), done.
bandit31@bandit:/tmp/tmp.JtE6SrxG8y$ 
```

README.mdの中身  
```
bandit31@bandit:/tmp/tmp.JtE6SrxG8y/repo$ ls -la
total 20
drwxrwxr-x 3 bandit31 bandit31 4096 Jan 14 08:44 .
drwx------ 3 bandit31 bandit31 4096 Jan 14 08:44 ..
drwxrwxr-x 8 bandit31 bandit31 4096 Jan 14 08:48 .git
-rw-rw-r-- 1 bandit31 bandit31    6 Jan 14 08:44 .gitignore
-rw-rw-r-- 1 bandit31 bandit31  147 Jan 14 08:44 README.md
bandit31@bandit:/tmp/tmp.JtE6SrxG8y/repo$ cat README.md 
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master
```

`la -ls`を行った時に`.gitignore`がある。  

.gitignoreの中身  
```
bandit31@bandit:/tmp/tmp.JtE6SrxG8y/repo$ cat .gitignore 
*.txt
```

そしてREADME.mdには、'May I come in?'と書かれたkey.txtファイルをリモートリポジトリにpushするよう指示している。  

やっていく。  

すると途中で警告が発生した。  
```
The following paths are ignored by one of your .gitignore files:
key.txt
hint: Use -f if you really want to add them.
hint: Turn this message off by running
hint: "git config advice.addIgnoredFile false"
```

.gitignoreは"Gitの管理下に置きたくないファイルを指定するファイル"だそうで中身には`*.txt`が書かれていたため、  
addしようとしたらこのように出力された。  

`-f`オプションを使用して追加させる。  

```
bandit31@bandit:/tmp/tmp.JtE6SrxG8y/repo$ git add key.txt -f
```

commitしてpushする。  

```
bandit31@bandit:/tmp/tmp.JtE6SrxG8y/repo$ git commit -m "add a file"
[master 12b54be] add a file
 1 file changed, 1 insertion(+)
 create mode 100644 key.txt
bandit31@bandit:/tmp/tmp.JtE6SrxG8y/repo$ git push
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit31/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit31/.ssh/known_hosts).
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

bandit31-git@localhost's password: 
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 2 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 321 bytes | 321.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote: ### Attempting to validate files... ####        
remote: 
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.        
remote: 
remote: Well done! Here is the password for the next level:        
remote: *******************************         
remote: 
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.        
remote: 
To ssh://localhost:2220/home/bandit31-git/repo
 ! [remote rejected] master -> master (pre-receive hook declined)
error: failed to push some refs to 'ssh://localhost:2220/home/bandit31-git/repo'
```

資格情報を手に入れ、クリア。  

