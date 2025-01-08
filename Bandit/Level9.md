```

Bandit Level 9 → Level 10
Level Goal

The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.
Commands you may need to solve this level

grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd
```

`data.txt`から先頭に数個の"="記号のある文字列が次の資格情報らしい。  
`cat`コマンドで表示するとバイナリファイルのようにめちゃくちゃな出力なので`string`コマンドで印字可能な文字列を抽出して出力する。  

```
D+io?
=tZ~07
^6Og

 Uum
D9========== FGUW5i******************bpfMiqey
u1Ebi
&x(>G
.`EQ
w>}x
D%(f
1#4!9

```

出力の中に資格情報らしきものがありクリア。  

