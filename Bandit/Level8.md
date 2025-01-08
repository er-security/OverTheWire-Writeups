```

Bandit Level 8 → Level 9
Level Goal

The password for the next level is stored in the file data.txt and is the only line of text that occurs only once
Commands you may need to solve this level

grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd
Helpful Reading Material

    Piping and Redirection

```

sshすると`data.txt`があり`cat`すると、約1000行の資格情報らしきものが表示される。  

問題文には一度だけ出現するテキスト行が次の資格情報らしいので、`uniq`コマンドで重複行を削除する。  

```
bandit8@bandit:~$ sort data.txt | uniq -u
************************
```

クリア
