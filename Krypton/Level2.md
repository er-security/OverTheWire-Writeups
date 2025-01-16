```

Krypton Level 1 → Level 2
Level Info

The password for level 2 is in the file ‘krypton2’. It is ‘encrypted’ using a simple rotation. It is also in non-standard ciphertext format. When using alpha characters for cipher text it is normal to group the letters into 5 letter clusters, regardless of word boundaries. This helps obfuscate any patterns. This file has kept the plain text word boundaries and carried them to the cipher text. Enjoy!
```


前のlevelの説明で、"You can find the files for other levels in /krypton/"とあったので、/krypton配下を見てみる。  

```
krypton1@bandit:/krypton$ ls -la
total 36
drwxr-xr-x  9 root root 4096 Sep 19 07:10 .
drwxr-xr-x 25 root root 4096 Jan  7 17:25 ..
drwxr-xr-x  2 root root 4096 Sep 19 07:09 krypton1
drwxr-xr-x  2 root root 4096 Sep 19 07:09 krypton2
drwxr-xr-x  2 root root 4096 Sep 19 07:09 krypton3
drwxr-xr-x  2 root root 4096 Sep 19 07:10 krypton4
drwxr-xr-x  2 root root 4096 Sep 19 07:10 krypton5
drwxr-xr-x  3 root root 4096 Sep 19 07:10 krypton6
drwxr-xr-x  2 root root 4096 Sep 19 07:10 krypton7
```

level2へ進むためのファイル、"krypton1"を見てみる。  


```
krypton1@bandit:/krypton/krypton1$ ls -la
total 16
drwxr-xr-x 2 root     root     4096 Sep 19 07:09 .
drwxr-xr-x 9 root     root     4096 Sep 19 07:10 ..
-rw-r----- 1 krypton1 krypton1   26 Sep 19 07:09 krypton2
-rw-r----- 1 krypton1 krypton1  882 Sep 19 07:09 README
```

ひとまず"README"ファイルを見る。  

```
Welcome to Krypton!

This game is intended to give hands on experience with cryptography
and cryptanalysis.  The levels progress from classic ciphers, to modern,
easy to harder.

Although there are excellent public tools, like cryptool,to perform
the simple analysis, we strongly encourage you to try and do these
without them for now.  We will use them in later excercises.

** Please try these levels without cryptool first **


The first level is easy.  The password for level 2 is in the file 
'krypton2'.  It is 'encrypted' using a simple rotation called ROT13.  
It is also in non-standard ciphertext format.  When using alpha characters for
cipher text it is normal to group the letters into 5 letter clusters, 
regardless of word boundaries.  This helps obfuscate any patterns.

This file has kept the plain text word boundaries and carried them to
the cipher text.

Enjoy!
```

krypton2のpasswordは、ROT13で暗号化されているらしい。  

ROT13とは、それぞれの平文の文字列を13文字ずらしで表現する方法である。  

"krypton2"ファイルを開く。  
```
krypton1@bandit:/krypton/krypton1$ cat krypton2 
YRIRY GJB CNFFJBEQ EBGGRA
```

`YRIRY GJB CNFFJBEQ EBGGRA`をROT13でdecrypt、つまり13文字ずらす。  

`LEVEL TWO PASSWORD ******` となった。 
念の為、passwordは消している。  


クリア。  


