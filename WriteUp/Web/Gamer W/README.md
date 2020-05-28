## Gamer W, 60 ##

Soal :

`Can you figure out how to cheat the system? Grab his hat to prove your victory!`

[Game](http://gamer_w.tjctf.org/)

Disediakan sebuah site yang merupakan game webassembly. Kita disuruh menginstall ekstensi CETUS untuk googe chrome.

Gamenya adalah game aksi dimana kita mengendalikan karakter yang mempunyai 4 atribut :

`Speed, Health, Ranged Damaage,` dan `Melee Damage`.

* Pertama kita buat karakter kita immune terlebih dahulu, dengan menggunakan cetus.
Cari nilai health kita sebesar `20` dalam `f32` karena nilai yang digunakan di game hampir selalu float. Kenakan hit dengan sengaja, maka health akan berkurang menjadi `15`. Cari dengan notasi `EQ` sebesar `15`. Lakukan terus sampai hanya ada satu memori yang tersisa. Ambil memori, freeze, voila, kita sekarang menjadi immune.

* Selanjutnya, kita harus dapatkan memori untuk health boss. Ketika boss keluar, jangan cepat - cepat membunuhnya. Base damage dari `Melee Damage` kita adalah 10. Maka coba perkirakan nyawa boss dengan mendamage sekali saja. Karena nyawa boss hanya terlihat berkurang 5% saja, saya menyimpulkan nyawa boss adalah 200. Karena sudah terkena hit sekali, maka search di cetus dengan value `190`. Lanjutkan sampai dapat memori boss.

* Fase berikutnya adalah boss akan menembakkan ribuan item yang dapat mendamage kita. Ini tidak mungkin dilewati jika kita tidak memfreeze health kita. Bunuh boss dengan `MANUAL`.

* Setelah itu, boss akan menggunakan potion yang menyebabkan boss tidak dapat dibunuh sama sekali. Buka cetus, set value nyawa boss ke `0`, lalu `freeze memori`. Perhatikan bahwa karakter `HARUS TEPAT DI DEPAN BOS TANPA CELAH SEDIKITPUN`.

* Game berhasil di tamatkan ketika topi boss anda ambil.

Flag : `tjctf{3tus_d3letus_ur_m3ms_g0ne}`
