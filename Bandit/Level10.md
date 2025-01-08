```

Bandit Level 10 → Level 11
Level Goal

The password for the next level is stored in the file data.txt, which contains base64 encoded data
Commands you may need to solve this level

grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd
Helpful Reading Material

    Base64 on Wikipedia

```

`data.txt`がありcatするとbase64でencodeされた文字列が格納（これは記載してもいいよな...?）  
```
bandit10@bandit:~$ cat data.txt 
VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTR3NnMlJXbnBOVmozcVJyCg==
```

`base64`コマンドでdecodeを行える。  

クリア  

