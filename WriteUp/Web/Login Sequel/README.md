## Login Sequel, 40 ##

Soal : 

`Login as admin you must. This time, the client is of no use :(. What to do?`

[login](http://login_sequel.tjctf.org/)

Ketika website dibuka akan ada form untuk login. Ketika meneliti page sourcenya, ada hint didalamnya berupa Querry yang digunakan untuk login.

```php
def get_user(username, password):
    database = connect_database()
    cursor = database.cursor()
    try:
        cursor.execute('SELECT username, password FROM `userandpassword` WHERE username=\'%s\' AND password=\'%s\'' % (username, hashlib.md5(password.encode())))
    except:
        return render_template("failure.html")
    row = cursor.fetchone()
    database.commit()
    database.close()
    if row is None: return None
    return (row[0],row[1])
```

Dilihat dari situ, kita dapat melakukan sql injection dengan menggunakan comment. Ketika mencoba menginputkan `admin'--` akan muncul page `SQL Injection Detected`.

Comment yang benar adalah `admin'/*`.

Flag : `tjctf{W0w_wHa1_a_SqL1_exPeRt!}`
