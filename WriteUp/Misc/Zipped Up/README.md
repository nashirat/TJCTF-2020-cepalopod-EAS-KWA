## Zipped Up, 70 ##

Soal :

`My friend changed the password of his Minecraft account that I was using so that I would stop being so addicted. Now he wants me to work for the password and sent me this zip file. I tried unzipping the folder, but it just led to another zipped file. Can you find me the password so I can play Minecraft again?`

[zip](https://static.tjctf.org/663d7cda5bde67bd38a8de1f07fb9fab9dd8dd0b75607bb459c899acb0ace980_0.zip)

Ketika membuka file, didapat banyak file didalmnya yaitu 
* flag.txt, isinya flag disini, tetapi kita tidak tau ada di file zip keberapa
* folder dengan nama urut dari `1,2,3,...`
* file compressed dengan 2 macam ekstensi, kalau tidak `tar` ya `zip`.

Jelas kita harus membuat script untuk melakukan otomasi untuk mencari flagnya.

Pertama saya menggunakan range `{1...500}`. Ternyata tidak ketemu, saya lalu menaikkan ke `1000`

```sh
for i in {1..1000}
do
	for f in $i.*
	do
		unzip $f
		tar -xvf $f
		rm $f
	done
	mv $i/* ./
	rmdir $i
done
```

Gunakan unzip dan tar untuk 2 ekstensi yang berbeda, lalu hapus file yang sudah diekstrak. Lalu move semua file didalam folder keluar sesuai dengan urutan i karena nama folder hanya berupa angka, lalu hapus folder.

Akan ada 1000 file txt seperti ini

![img1](https://github.com/nashirat/TJCTF-2020-cepalopod-EAS-KWA/blob/master/WriteUp/Misc/Zipped%20Up/img/text.png)

Karena kita tahu flag palsunya adalah `tjctf{n0t_th3_fl4g}`, gunakan `grep -v` untuk mengambil nilai inverse.

![img2](https://github.com/nashirat/TJCTF-2020-cepalopod-EAS-KWA/blob/master/WriteUp/Misc/Zipped%20Up/img/flag.png)

Ternyata flag terletak di `829.txt`.

Flag : `tjctf{p3sky_z1p_f1L35}`
