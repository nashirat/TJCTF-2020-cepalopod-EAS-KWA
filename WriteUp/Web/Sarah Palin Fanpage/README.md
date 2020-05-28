## Sarah Palin Fanpage, 35 ##

Soal 

`Are you a true fan of Alaska's most famous governor? Visit the Sarah Palin fanpage.`
 
 Diberikan link website [Sarah Palin Fanpage](https://sarah_palin_fanpage.tjctf.org)
 
 Website meminta 10 likes di halaman Top 10 Moments, tetapi akan ada notifikasi anti spam yang membuat kita hanya bisa melakukan 5 likes.
 
Jika cek cookienya, kita akan dapatkan cookie value yang masih terenkripsi. Dekripsi menggunakan base64 decryptor atau [website ini](https://www.kirsle.net/wizards/flask-session.cgi).
Akan menghasilkan string JSON :

`{"1":false,"2":false,"3":false,"4":false,"5":false,"6":false,"7":false,"8":false,"9":false,"10":false}`

Cukup ganti valuenya menjadi true semua, lalu send cookie dengan ekstensi chrome `EditThisCookie`, lalu masuk ke VIP area untuk mendapatkan flag.

Flag : `tjctf{wkDd2Pi4rxiRaM5lOcLo979rru8MFqVHKdTqPBm4k3iQd8n0sWbBkOfuq9vDTGN9suZgYlH3jq6QTp3tG3EYapzsTHL7ycqRTP5Qf6rQSB33DcQaaqwQhpbuqPBm4k3iQd8n0sWbBkOf}`
