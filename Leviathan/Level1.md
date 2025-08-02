"ls -la"を行う。  

```
leviathan0@leviathan:~$ ls -la
total 24
drwxr-xr-x   3 root       root       4096 Jul 28 19:05 .
drwxr-xr-x 150 root       root       4096 Jul 28 19:06 ..
drwxr-x---   2 leviathan1 leviathan0 4096 Jul 28 19:05 .backup
-rw-r--r--   1 root       root        220 Mar 31  2024 .bash_logout
-rw-r--r--   1 root       root       3851 Jul 28 18:47 .bashrc
-rw-r--r--   1 root       root        807 Mar 31  2024 .profile
```

標準では見かけない`.backup`ディレクトリが存在する。  

`.backup`ディレクトリ配下  
```
leviathan0@leviathan:~/.backup$ ls -la
total 140
drwxr-x--- 2 leviathan1 leviathan0   4096 Jul 28 19:05 .
drwxr-xr-x 3 root       root         4096 Jul 28 19:05 ..
-rw-r----- 1 leviathan1 leviathan0 133259 Jul 28 19:05 bookmarks.html
```

`bookmarks.html`ファイルの中身  
```
leviathan0@leviathan:~/.backup$ head bookmarks.html 
<!DOCTYPE NETSCAPE-Bookmark-file-1>
<!-- This is an automatically generated file.
     It will be read and overwritten.
     DO NOT EDIT! -->
<META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=UTF-8">
<TITLE>Bookmarks</TITLE>
<H1 LAST_MODIFIED="1160271046">Bookmarks</H1>

<DL><p>
    <DT><H3 LAST_MODIFIED="1160249304" PERSONAL_TOOLBAR_FOLDER="true" ID="rdf:#$FvPhC3">Bookmarks Toolbar Folder</H3>

```

なんかずらっと書かれている。  

目指すべき、leviathan1のパスワードがここに書かれているかもしれないので探す。  

```
leviathan0@leviathan:~/.backup$ cat bookmarks.html | grep leviathan1
<DT><A HREF="http://leviathan.labs.overthewire.org/passwordus.html | This will be fixed later, the password for leviathan1 is 3QJ3TgzHDq" ADD_DATE="1155384634" LAST_CHARSET="ISO-8859-1" ID="rdf:#$2wIU71">password to leviathan1</A>
```

見つけた。  

