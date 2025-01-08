```

Bandit Level 7 → Level 8
Level Goal

The password for the next level is stored in the file data.txt next to the word millionth
Commands you may need to solve this level

man, grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd
```

`ls -l`を使う。  
```
bandit7@bandit:~$ ls -l
total 4088
-rw-r----- 1 bandit8 bandit7 4184396 Sep 19 07:08 data.txt
```

`data.txt`があり`cat`で開くとたくさんのユーザー名と資格情報が表示される。（この資格情報は載せていいよな...?）  
```
bandit7@bandit:~$ cat data.txt | more
momentary	MBLQ2x4SPU4Y6XIscWooXopjdSntWOhY
vicuña	6nKKKgzHbJvPFsEFQgzd2wqJWcv8TGGQ
equities	ZhOy86fNIP8sWsOLLYiHrtjRsrpu1bND
various	Eg1ZcmYmpvkXS10Vu04areb2hhT9Pkft
redefinition's	vPzYXGDGwByIVBRIKQDRHn5xqoekZKME
Allison	4JPUMGRznD4JAyy1SX2Cf5zAwEhT7AP7
compels	8XgWaEyaUVmm1FLZksXE6vRBAKfm7xGB
misstep	0p0wfzDrUfyAbU6V5MVGlrvDKjmc6a0Z
coagulating	Ff0C46bfOMzwOojIDTWJAq9O59WdKSdw
Onega's	YiR7TkXXHKpt0Oqs2EtFzRSXu8XGCqQA
checkmate	XjaNSCEGpEdkJIMfCnwWGJuRQ6fUIoUq
Lyndon	7m6zWzaFwemeBJ7jKzXO1REfc9QtC9SQ
archivist	j1kdDmGHBGtcor81a2lIZzVd9ulFtifz
Jerri's	2fCe8FdpTJFt4gtanwmG7a8A1AYlEpDQ
underarms	ZSucs304S5mq2TONuDqpN5gwz7HsbCOQ
scrooge	SYI06iTGl1SdxwJV21kH4fty0AAer8Rv
Elnora	i1GGmWJChr5PUq8N8s9nt6nhYvoUtoRu
salver	uZf07mMWSaF4hLwFmGKIKt0qrSeTIPjy
.
.
.
省略
```

問題文には、"millionth"の行が次の資格情報と書かれているので`cat`をパイプして`grep`に流す。  

```
bandit7@bandit:~$ cat data.txt | grep 'millionth'
millionth	**********************
```

クリア
