```
Bandit Level 4 → Level 5
Level Goal

The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.
Commands you may need to solve this level

ls , cd , cat , file , du , find
```

`ls -la`を使う。  
```
bandit4@bandit:~/inhere$ ls -la
total 48
drwxr-xr-x 2 root    root    4096 Sep 19 07:08 .
drwxr-xr-x 3 root    root    4096 Sep 19 07:08 ..
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file00
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file01
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file02
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file03
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file04
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file05
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file06
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file07
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file08
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file09
```

ファイル名の先頭に「-」ハイフンがあるので`cat *`で読み込もうとするとオプションとして認識されてしまうので、  
`cat ./*`とする。  

```
bandit4@bandit:~/inhere$ cat ./*
�p��&�y�,�(jo�.at�:uf�^���@i�R�,�Λ�:Y���?�%�A����B��ͩ�3�	�)Ʈ�#Y��-6c��IR-�$����:�����/�
                                                                                      ������qGi��,�2�Yb�
dۙ�rOx����h0~ey
��c�~�h�n��G1}���ߓ��ߤ��W>��#lk�d�ܮ��yE��6�0]�\�$�1�%�������o@��b/��4oQY*********************UQw
�nS�
�<��]�
W��e�˥m�����O��D��2g��?�����`>5HYA�u���8�g�`0�$`��
```

ルール上writeupに資格情報を書いてはいけないので米印で隠しているがここに資格情報が書かれておりクリア。  

