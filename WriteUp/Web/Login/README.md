## Login, 30 ##

Soal :

`Could you login into this very secure site? Best of luck!`

Disediakan sebuah web dengan link https://login.tjctf.org/.

Jika kita cek page source nya, kita akan tahu ada fungsi `checkUsername` ketika kita mengklik button login.
```js
checkUsername = function() {
    username = document[_0x4a84('0x1')]('username')[0x0]['value'];
    password = document[_0x4a84('0x1')]('password')[0x0][_0x4a84('0x3')];
    temp = md5(password)[_0x4a84('0x2')]();
    if (username == _0x4a84('0x6') && temp == _0x4a84('0x4'))
        alert(_0x4a84('0x0') + password + '890898}');
    else
        alert(_0x4a84('0x5'));
}
```

Jelas ada beberapa string yang di obfuskasi. Untuk meng-undo-obfuskasi, cukup salin fungsi di atas ke js unobfuscator di internet.

Didapat line yang mencurigakan 
```js
["value", "c2a094f7d35f2299b414b6a1b3bd595a", "Sorry. Wrong username or password.", "admin", "tjctf{", "getElementsByName", "toString"];
```
dan dilihat dar
```js
alert(_0x4a84("0x0") + password + "890898}");
```
Dapat disimpulkan kalau flag adalah `tjctf{(pass)89098}`.

Value `c2a094f7d35f2299b414b6a1b3bd595a` adalah pass yang sepertinya dalam bentuk hash. Cukup salin ke web pemecah password seperti [crackstation.net](https://crackstation.net/).

Didapat password `inevitable`, maka flag adalah :

`inevitable89098`
