![](img/natas28-1.png)  

" Whack Computer Joke Database"とある。  
適当に"computer"と検索してみる。  

![](img/natas28-2.png)  

エラー  

空白など何も入力しなくてもエラーが発生する。  

URLを確認してみる。  

```
http://natas28.natas.labs.overthewire.org/search.php/?query=G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLOxD5BEouuJBr2svTs3MqTiW3pCIT4YQixZ%2Fi0rqXXY5FyMgUUg%2BaORY%2FQZhZ7MKM%3D
```

queryパラメータで何かを送っている。  

ちなみに、検索した文字列はPOSTで送っている。  

試しにqueryパラメータを空白にしてリクエストを行ってみると、  
```
http://natas28.natas.labs.overthewire.org/search.php/?query=
```

![](img/natas28-3.png)  

```
 Zero padding found instead of PKCS#7 padding
```
とPKCS#7のエラー文字列が出力された。  

queryパラメータの文字列はデジタル署名の文字列なんだろうか...?  


後日アクセスを行うとエラーが発生しなくなった。  
仕込まれたエラーではなかったようだ。  

![](img/natas28-4.png)  


適当な単語で検索を続けていくうちにqueryパラメータの値に規則性があるのが判明した。  

```
?query=G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLOxD5BEouuJBr2svTs3MqTiW3pCIT4YQixZ%2Fi0rqXXY5FyMgUUg%2BaORY%2FQZhZ7MKM%3D
?query=G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPKriAqPE2%2B%2BuYlniRMkobB1vfoQVOxoUVz5bypVRFkZR5BPSyq%2FLC12hqpypTFRyXA%3D
?query=G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPIYiwNnSJY7KHJGU%2BXjuMzVvfoQVOxoUVz5bypVRFkZR5BPSyq%2FLC12hqpypTFRyXA%3D
```


どれも`?query=G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjP`までは同じ。  






