## Chord Encoder, 40 ##

Soal : 

`I tried creating my own chords, but my encoded sheet music is a little hard to read. Please play me my song!`

[chord_encoder.py](https://static.tjctf.org/da36df431da358250884ff9765e8c0c5f054b845aff31b85e37229159176bb9f_chord_encoder.py)

Notes : 

`1121112111211002112101121121001001210000101221121011200102000110120200101100100111211011001020020010111012011202001011112110121121011211211002112110020200101111210112020010111121010112102001121100211211011020020001010`

Chord :

`A 0112
B 2110
C 1012
D 020
E 0200
F 1121
G 001
a 0122
b 2100
c 1002
d 010
e 0100
f 1011
g 000`

Kita hanya perlu merekonversi dari notes ke chord lagi. Saya membuat sebuah `decoder.py`, tetapi setelah output berhasil didapat, yang terjadi adalah error.
Setelah saya teliti lag, ada 2 pasang note yang membuat error, yaitu `D = 020 E = 0200` dan `d = 010 e = 0100`. Karena saya sudah tidak bisa fokus lagi membuat `decoder.py` yang sepertinya harus mengimplementasikan dynamic programming, saya memutuskan untuk melakukan decode secara manual saja.

Setelah beberapa waktu, akhirnya flag didapat.

Flag : `flag{zats_wot_1_call_a_meloD}` 
