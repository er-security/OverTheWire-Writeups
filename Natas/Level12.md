```

Natas Level 11 → Level 12

Username: natas12
URL:      http://natas12.natas.labs.overthewire.org
```

![](img/natas12-1.png)  

画像ファイルをアップロードする機能が存在する。  
フリー画像をアップロードしようと思ったが" Choose a JPEG to upload (max 1KB)"とあるように、  
1KBまでのjpeg形式の画像じゃないとだめらしい。  

ImageMagickを使用して1KB未満サイズのjpen画像を生成する。  
```
convert -size 1x1 xc:black image.jpg
```

