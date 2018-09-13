# Memulai Belajar Python
RTFM (Read The F#ck Manual) di [dokumentasi resmi Python 3.7](https://docs.python.org/3/tutorial/index.html)

## 2. Using the Python Interpreter
### 2.1. [Invoking the Interpreter](https://docs.python.org/3/tutorial/interpreter.html#invoking-the-interpreter)
```bash
bigdata on  master [!] via bigdata took 7s
➜ which python3.7
/home/ayam/.virtualenvs/bigdata/bin/python3.7
```
> Python executable pada komputer saya berada di `/usr/bin/python3.7` namun saya
menggunakan virtualenv sehingga python yang tampil diatas adalah Python executale dari virtualenv

Berikut ini adalah Python shell yang sedang dijalankan
```bash
bigdata on  master via bigdata took 14s
➜ python3.7
Python 3.7.0b3 (default, Mar 30 2018, 04:35:22)
[GCC 7.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

Untuk keluar dari Python shell tekan CTRL+D atau mengeksekusi perintah `exit()`.

Cara lain untuk mengeksekusi perintah python pada command line adalah dengan
menambahkan opsi `-c` diikuti dengan syntax yang diapit dengan tanda petik ganda (`"`)
Contoh:
```bash
python -c "import uuid; print(uuid.uuid4().hex)"
```
Dengan menjalankan perintah diatas maka akan muncul kode unik semrawut yang dibuat oleh modul `UUID`

#### 2.1.1. [Argument Passing](https://docs.python.org/3/tutorial/interpreter.html#argument-passing)
Menambahkan argumen pada command line

Buat file dengan nama `argument-passing.py` kemudian tuliskan berikut ini
```python
import sys
print(sys.argv[2])
```

Jalankan kode diatas menggunakan
```bash
python minggu-02/argument-passing.py "Saya dipanggil dari commandline"
```

maka akan muncul
```
Saya dipanggil dari commandline
```

#### 2.1.2. [Interactive Mode](https://docs.python.org/3/tutorial/interpreter.html#interactive-mode)
Menggunakan mode interaktif Python

```bash
bigdata on  master [!?] via bigdata took 46s
➜ python3.7
Python 3.7.0b3 (default, Mar 30 2018, 04:35:22)
[GCC 7.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

`>>>` baris ini adalah perintah utama
`...` adalah baris _continuation_ atau perintah harus dilanjutkan diawali dengan `tab` kemudian perintah

Contohnya sebagai berikut
```
>>> mahasiswa = True
>>> if mahasiswa:
...     print('You are mahasiswa!')
...
You are mahasiswa!
>>>
```

### 2.2. The Interpreter and Its Environment
#### 2.2.1. [Source Code Encoding](https://docs.python.org/3/tutorial/interpreter.html#source-code-encoding)
Secara default penulisan kode python pada berkas sebagai UTF-8 jika ingin mengganti encoding
berikan kode berikut diawal baris berkas `# -*- coding: encoding -*-`

Contoh
```
#!/usr/bin/env python3
# -*- coding: cp1252 -*-
```

===

## 3. An Informal Introduction to Python
Penulisan pada Python

Penulisan blok komentar pada kode sumber Python
```python
# ini adalah komentar pertama
spam = 1  # komentar dua
          # ... dan ini yang ketiga!
text = "# Ini bukan komentar karena diapit dengan tanda petik ganda."
```

### 3.1. Using Python as a Calculator
Mencoba membuat program pertama (kalkulator) menggunakan mode interaktif

#### 3.1.1. [Numbers](https://docs.python.org/3/tutorial/introduction.html#numbers)
Mode interaktif bisa juga digunakan sebagai kalkulator
> Kalo emak-emak yang jualan di pasar pada pakenya Python gimana ya? :/

Python mempunya beberapa operator yang gunakan untuk operasi aritmatika diantaranya :
- `+` Penjumlahan
- `-` Pengurangan
- `*` Perkalian
- `/` Pembagian

> *Tapi!* cinta gak boleh dibagi, tapi kalo ditambah boleh aja :V

```
>>> 4 + 2
6
>>> 23 - 3*3
14
>>> (50 - 3*3) / 2
20.5
>>> 9 / 4
2.25
>>>
```

Jika menggunakan operator pembagian (`/`) akan selalu menghasilkan bilangan pecahan

Angka atau nilai bulat (mis: `2`, `10`, `46`) memiliki tipe data `int` (integer) dan
angka atau bilangan pecahan (mis: `2.3`, `30.5`) memiliki tipe data `float`

Operas aritmatika menggunakan operator `/` akan selalu menghasilkan bilangan
pecahan, tapi jika ingin hasilnya bilangan bulat bisa menggunakan [floor division](https://docs.python.org/3/glossary.html#term-floor-division)
dengan operator `//` garis miring dua kali
```
>>> 15 / 2
7.5
>>> 15 // 4
3
>>> 15 / 4
3.75
```

Jika kita ingin mengetahui sisa dari pembagian maka gunakanlah operator modulus `%`
```
>>> 12 % 4
0
>>> 17 % 3
2
```

Bisa juga kita mengkalkulasi dengan eksponen (pemangkatan) menggunakan operator `**` istilanya _powers_ jika di Python
```
>>> 5 ** 2
25
>>> 10 ** 2
100
```

Operator `=` digunakan untuk memberikan nilai pada suatu variabel
```
>>> panjang = 30
>>> lebar = 25
>>> panjang * lebar
750
```

`_` digunakan untuk menyimpan nilai yang terakhir kali di print, namun nilainya tidak dapat diubah (read only)
```
>>> harga = 34.000
>>> satuan = 2
>>> harga * satuan
68.0
>>> total = 0
>>> total * _
213.0
>>> round(_, 3)
213.0
>>>
```
Python mendukung tipe data lainnya juga lihar [disini](https://docs.python.org/3/library/stdtypes.html#typesnumeric)

#### 3.1.2. [Strings](https://docs.python.org/3/tutorial/introduction.html#strings)
