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




