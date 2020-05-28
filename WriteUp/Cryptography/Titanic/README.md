## Titanic, 35 ##

Disediakan soal sebagai berikut : 

`I wrapped tjctf{} around the lowercase version of a word said in the 1997 film "Titanic" and created an MD5 hash of it: 9326ea0931baf5786cde7f280f965ebb`

Maksudnya adalah flag adalah salah satu kata yang diucapkan di film titanic, yang dimana kata tersebut akan ditambahkan `tjcft{}` lalu di hash.
Karena aktor tidak selalu mengucapkan kata yang persis dengan yang ada di skrip, saya memilih menggunakan subtitle saja. Saya juga menambahkan `'` di regex karena ada beberapa kata yang menggunakan `'`, seperti `titanic's`.

Dengan menggunakan script
```python
import re
from hashlib import md5

with open('titanic.txt', 'r') as file:
	for line in file:
		for word in line.split():
			flag = "tjctf{" + re.sub('[^a-zA-Z\']', '', word).lower() + "}"
			if md5(flag.encode('utf-8')).hexdigest()=="9326ea0931baf5786cde7f280f965ebb":
				print(flag)
				break
```

flag dapat ditemukan yaitu : `tjctf{marlborough's}`
