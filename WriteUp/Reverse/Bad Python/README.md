## Bad Python, 50 ##

Soal : 

`My friend wrote a cool program to encode text data! His code is sometimes hard to understand, and only he knows how it works. I ran the program twice, but forgot the input I used for the first time. I didn't save the key I used either, but I know it was 15 characters long. Can you figure out what text I encoded the first time?`

[Program](https://static.tjctf.org/0dd987c8e6311daa4dc0ff94e217e1bd33834a6c1a337d50a8218b35164c670e_encoder.py)

Output 1 :

`b'\x02\x19\x01\x16Q\r\x07\nS\x02)\x1a1=EE2\x0e=G/D\nRY)\nV\x1bJ'`

Input 2 :

`Lorem ipsum dolor sit amet, consectetur adipiscing elit`

Output 2 :

`b':\x1c\x10\x07ZV\x1a\x12\x11B\x1bS\x06\r[\x19\x01B\x11^\x02S\x03\x0fR\x02_B\x01X\x18\x00\x07\x01C\x13\x07\x17\x10\x17\x17\x17\x0b\x12^\x05\x10\x0b\x0cPV\x16\x0e\x0bC'`

Setelah meneliti dan merapikan program selama beberapa jam, ternyata program hanya menirukan fungsi `^(xor)` di python. Kita bisa tau key dengan cara melakukan xor antara input 2 dan output 2.
Ubah output 2 dari bit ke decimal dengan menggunakan python. 

![img1](https://github.com/nashirat/TJCTF-2020-cepalopod-EAS-KWA/blob/master/WriteUp/Reverse/Bad%20Python/img/ouput2.png)

XOR dengan input. Value adalah ascii.

![img2](https://github.com/nashirat/TJCTF-2020-cepalopod-EAS-KWA/blob/master/WriteUp/Reverse/Bad%20Python/img/XOR.png)

Setelah mengulangi selama beberapa kali, didapatkan key `vsbb7`. Tinggal xor output 1 dengan `ASCII dari vsbb7` sampai habis.



Flag : `tjctf{th15_iS_r3Al_pY7h0n_y4y}`
