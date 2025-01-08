```

Bandit Level 11 → Level 12
Level Goal

The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions
Commands you may need to solve this level

grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd
Helpful Reading Material

    Rot13 on Wikipedia
```

data.txtの中身を見る。  

`
bandit11@bandit:~$ cat data.txt 
Gur cnffjbeq vf 7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4
`

問題文から[ROT13](https://ja.wikipedia.org/wiki/ROT13)で暗号化していると思われる。  
13文字ずらして資格情報ゲット。  

