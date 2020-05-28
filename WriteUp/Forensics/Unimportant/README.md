### Unimportant, 60 ###

Disediakan sebuah img dengan link berikut :
https://static.tjctf.org/6996b9ea93971d907329dd61be2a22c50e7608d6c183bfe66bbb621ac338b51b_unimportant.png

Dengan soal :
 `It's probably at least a bit important? Like maybe not the least significant, but still unimportant...`

Dan source : 
https://static.tjctf.org/6b90153752e1f3c51c9e07f2e6f182eef25edcb59101c5f0f4c8a6b815029b08_encode.py
 
Jika kita buka sourcenya, dan memahami kodenya, maka kita akan tahu bahwa akan diambil nilai RGBA tiap pixel, lalu dengan mengambil data dari flags.txt, pixel[1] (green) akan di xor dengan 0b10 atau 10, lalu bits[i] flag flags.txt akan di left shift.
Versi pendeknya adalah hilangkan nilai bit 7, lalu masukan flag dari flag.txt yang sudah diubah dalam bentuk bit.

Untuk mendapatkan flag, berarti kita harus mendapatkan nilai green dengan code
```python
for i in range(img.width):
	for j in range(img.height):
		pixel = pixels[i,j]
```
Lalu lakukan right shift, lalu xor kembali
```python
list_pixel += [str((pixel[1]>>1)&1)]
```
Valuenya berhasil didapat dalam bentuk binary. Bersihkan format list, lalu ubah binary yang didapat ke hex dengan online tool atau coding. Hex yang didapat adalah
`0A7B6E30745F7468335F6C653473745F7369396E31666963346E747D0A`

Convert hex ke ASCII, kita akan dapat flagnya
`{n0t_th3_le4st_si9n1fic4nt}`
