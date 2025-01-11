```

Bandit Level 26 → Level 27
Level Goal

Good job getting a shell! Now hurry and grab the password for bandit27!
Commands you may need to solve this level

ls
```


前回の問題で、moreからエディタ起動して資格情報を手に入れられた。  

今回はエディタのシェルを`/bin/bash`に設定して容易にコンピュータを操作できるようにする。  

Level26の資格情報は既に判明しているのでRSAキーではなくパスワード入力でsshを行う。  
そして、前回の方法でエディタをコマンドモードにし、シェルの設定を行う。  
```
  _                     _ _ _   ___   __
 | |                   | (_) | |__ \ / /  
 | |__   __ _ _ __   __| |_| |_   ) / /_  
 | '_ \ / _` | '_ \ / _` | | __| / / '_ \
 | |_) | (_| | | | | (_| | | |_ / /| (_) |
:set shell=/bin/bash
```

あとは、資格情報を探す。  
```
 | '_ \ / _` | '_ \ / _` | | __| / / '_ \
 | |_) | (_| | | | | (_| | | |_ / /| (_) |
:!ls
bandit27-do  text.txt
```
次  
```
 | |_) | (_| | | | | (_| | | |_ / /| (_) |
 |_.__/ \__,_|_| |_|\__,_|_|\__|____\___/
~                                                                                                                    
~                                                                                                                    
:!file bandit27-do
bandit27-do: setuid ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, BuildID[sha1]=368cd8ac4633fabdf3f4fb1c47a250634d6a8347, for GNU/Linux 3.2.0, not stripped
```
次  
```
 | |_) | (_| | | | | (_| | | |_ / /| (_) |
 |_.__/ \__,_|_| |_|\__,_|_|\__|____\___/
~                                                                                                                    
~                                                                                                                    
:!./bandit27-do
Run a command as another user.
  Example: ./bandit27-do id
```
次  
```
 | |_) | (_| | | | | (_| | | |_ / /| (_) |
 |_.__/ \__,_|_| |_|\__,_|_|\__|____\___/
~                                                                                                                    
~                                                                                                                    
:!./bandit27-do cat /etc/bandit_pass/bandit27
***************************
```

クリア  
