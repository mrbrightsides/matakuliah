# **Pertemuan 4 – Struktur Kontrol Program Python**

Praktikum Algoritma dan Pemrograman · Program Studi Teknik Elektro

**Learning Module 04**

Materi praktikum

**Topik:** Conditional Statement dan Looping Statement

**Fokus pembelajaran:** Mengembangkan kemampuan mahasiswa dalam mengendalikan alur eksekusi program menggunakan percabangan dan perulangan.

**Bahasa pemrograman:** Python 3.x

**Prasyarat:** Memahami variabel, tipe data, operator, input, dan output dasar Python.

## **1. Deskripsi Pembelajaran**

Dalam pemrograman, sebuah program tidak selalu dijalankan secara berurutan dari instruksi pertama hingga instruksi terakhir. Pada berbagai kondisi, program perlu mengambil keputusan, memilih instruksi tertentu, atau menjalankan proses yang sama secara berulang.

Sebagai contoh, dalam bidang Teknik Elektro, sebuah program dapat digunakan untuk:

- Menentukan kondisi tegangan berdasarkan nilai hasil pengukuran.
- Mengklasifikasikan kondisi arus listrik.
- Menghitung daya berdasarkan tegangan dan arus.
- Melakukan pengukuran berulang menggunakan sensor.
- Memeriksa apakah suatu nilai parameter listrik berada dalam rentang tertentu.
- Melakukan simulasi sederhana terhadap sistem kelistrikan.

Untuk membangun program dengan kemampuan tersebut, diperlukan pemahaman mengenai struktur kontrol atau *Control Structures*.

Struktur kontrol merupakan mekanisme dalam pemrograman yang mengatur bagaimana instruksi dieksekusi berdasarkan kondisi tertentu atau pengulangan proses.

Dalam Python, struktur kontrol yang akan dipelajari meliputi:

1. Conditional Statement (Percabangan).
2. Nested Conditional (Percabangan Bersarang).
3. Looping Statement (Perulangan).
4. Nested Loop (Perulangan Bersarang).
5. Break, Continue, dan Pass.

## **2. Capaian Pembelajaran**

Setelah mempelajari materi ini, mahasiswa diharapkan mampu:

1. Menjelaskan konsep dan fungsi struktur kontrol dalam pemrograman.
2. Mengimplementasikan percabangan menggunakan `if`, `elif`, dan `else`.
3. Menggunakan operator perbandingan dan logika dalam menentukan kondisi program.
4. Membuat percabangan bersarang untuk menangani beberapa kondisi.
5. Mengimplementasikan perulangan menggunakan `for` dan `while`.
6. Menggunakan `break`, `continue`, dan `pass` untuk mengatur alur perulangan.
7. Mengembangkan program sederhana berbasis kasus Teknik Elektro menggunakan struktur kontrol Python.

## **3. Conditional Statement (Struktur Percabangan)**

### **3.1 Pengertian Conditional Statement**

Conditional Statement merupakan struktur kontrol yang memungkinkan program mengambil keputusan berdasarkan kondisi tertentu.

Kondisi tersebut akan dievaluasi dan menghasilkan nilai Boolean, yaitu:

- `True`: Kondisi terpenuhi.
- `False`: Kondisi tidak terpenuhi.

Berdasarkan hasil evaluasi tersebut, program akan menentukan instruksi mana yang harus dijalankan.

Contoh sederhana:

```
tegangan = 220if tegangan > 200:    print("Tegangan memenuhi kondisi")
```

**Penjelasan kode:**

1. Variabel `tegangan` memiliki nilai 220.
2. Python memeriksa kondisi `tegangan > 200`.
3. Karena 220 lebih besar dari 200, kondisi bernilai `True`.
4. Instruksi `print()` dijalankan.

Output:

```
Tegangan memenuhi kondisi
```

Apabila nilai tegangan diubah menjadi 180, kondisi akan bernilai `False`, sehingga instruksi di dalam blok `if` tidak dijalankan.

### **3.2 Percabangan if**

Percabangan `if` digunakan ketika program hanya perlu menjalankan instruksi apabila suatu kondisi terpenuhi.

**Sintaks umum:**

```
if kondisi:    instruksi
```

Contoh penerapan:

```
arus = 15if arus > 10:    print("Arus melebihi batas simulasi")
```

Output:

```
Arus melebihi batas simulasi
```

Pada contoh tersebut, program hanya menampilkan pesan apabila nilai arus lebih besar dari 10 Ampere.

Jika kondisi tidak terpenuhi, program akan melewati instruksi tersebut dan melanjutkan eksekusi ke baris berikutnya.

### **3.3 Percabangan if-else**

Struktur `if-else` digunakan ketika terdapat dua kemungkinan hasil berdasarkan kondisi.

**Sintaks umum:**

```
if kondisi:    instruksi_jika_trueelse:    instruksi_jika_false
```

Contoh:

```
tegangan = float(input("Masukkan tegangan: "))if tegangan >= 200:    print("Kondisi tegangan memenuhi batas simulasi")else:    print("Kondisi tegangan di bawah batas simulasi")
```

Contoh output pertama:

```
Masukkan tegangan: 220
Kondisi tegangan memenuhi batas simulasi
```

Contoh output kedua:

```
Masukkan tegangan: 180
Kondisi tegangan di bawah batas simulasi
```

**Analisis:**

Pada struktur ini, salah satu dari dua blok instruksi akan dijalankan. Jika kondisi `if` bernilai True, blok `if` dijalankan. Sebaliknya, jika bernilai False, blok `else` yang dijalankan.

### **3.4 Percabangan if-elif-else**

Dalam beberapa permasalahan, program harus menangani lebih dari dua kemungkinan kondisi.

Python menyediakan `elif` (*else if*) untuk melakukan pemeriksaan terhadap beberapa kondisi secara berurutan.

**Sintaks umum:**

```
if kondisi_1:    instruksi_1elif kondisi_2:    instruksi_2elif kondisi_3:    instruksi_3else:    instruksi_lain
```

Contoh penerapan: klasifikasi tegangan listrik.

Ketentuan simulasi:

| Rentang tegangan | Kategori |
| ---------------- | -------- |
| Di bawah 200 V   | Rendah   |
| 200–240 V        | Normal   |
| Di atas 240 V    | Tinggi   |

Program:

```
tegangan = float(input("Masukkan tegangan (Volt): "))if tegangan < 200:    print("Kategori: Tegangan Rendah")elif tegangan <= 240:    print("Kategori: Tegangan Normal")else:    print("Kategori: Tegangan Tinggi")
```

Contoh output:

```
Masukkan tegangan (Volt): 220
Kategori: Tegangan Normal
```

**Analisis program:**

- Jika tegangan kurang dari 200, program menampilkan Tegangan Rendah.
- Jika kondisi pertama tidak terpenuhi dan tegangan kurang dari atau sama dengan 240, program menampilkan Tegangan Normal.
- Jika kedua kondisi sebelumnya tidak terpenuhi, program menampilkan Tegangan Tinggi.

Perlu diperhatikan bahwa batas pada contoh ini merupakan parameter simulasi pembelajaran, bukan standar tegangan operasional universal.

### **3.5 Nested If (Percabangan Bersarang)**

Nested If merupakan struktur percabangan yang menempatkan satu pernyataan `if` di dalam blok `if` lainnya.

Struktur ini digunakan ketika suatu keputusan membutuhkan pemeriksaan beberapa kondisi secara bertingkat.

Contoh kasus: pemeriksaan kondisi sistem kelistrikan.

```
tegangan = float(input("Masukkan tegangan: "))arus = float(input("Masukkan arus: "))if tegangan > 0:    if arus > 0:        print("Parameter listrik valid")    else:        print("Arus tidak valid")else:    print("Tegangan tidak valid")
```

Output:

```
Masukkan tegangan: 220
Masukkan arus: 5
Parameter listrik valid
```

**Cara kerja:**

1. Program memeriksa apakah tegangan lebih besar dari nol.
2. Jika terpenuhi, program melanjutkan pemeriksaan terhadap arus.
3. Jika arus juga lebih besar dari nol, program menampilkan bahwa parameter valid.
4. Jika salah satu kondisi tidak terpenuhi, program menampilkan pesan yang sesuai.

Nested If banyak digunakan pada sistem yang membutuhkan beberapa tahap validasi, seperti sistem monitoring dan kontrol.

## **4. Operator Perbandingan dan Logika**

Untuk membangun kondisi yang lebih kompleks, Python menyediakan operator perbandingan dan operator logika.

### **4.1 Operator Perbandingan**

Operator perbandingan digunakan untuk membandingkan dua nilai.

| Operator | Fungsi                       | Contoh   |
| -------- | ---------------------------- | -------- |
| `==`     | Sama dengan                  | `a == b` |
| `!=`     | Tidak sama dengan            | `a != b` |
| `>`      | Lebih besar                  | `a > b`  |
| `<`      | Lebih kecil                  | `a < b`  |
| `>=`     | Lebih besar atau sama dengan | `a >= b` |
| `<=`     | Lebih kecil atau sama dengan | `a <= b` |

Contoh:

```
tegangan = 220print(tegangan == 220)print(tegangan > 200)print(tegangan < 200)
```

Output:

```
True
True
False
```

### **4.2 Operator Logika**

Operator logika digunakan untuk menggabungkan beberapa kondisi.

| Operator | Fungsi                    |
| -------- | ------------------------- |
| `and`    | Semua kondisi harus True  |
| `or`     | Minimal satu kondisi True |
| `not`    | Membalik nilai Boolean    |

**Contoh penggunaan AND:**

```
tegangan = 220arus = 5if tegangan >= 200 and arus <= 10:    print("Parameter berada dalam rentang simulasi")else:    print("Parameter di luar rentang simulasi")
```

Kedua kondisi harus terpenuhi agar program menjalankan blok `if`.

**Contoh penggunaan OR:**

```
suhu = 45arus = 12if suhu > 40 or arus > 10:    print("Peringatan: Parameter melewati batas simulasi")
```

Program akan memberikan peringatan apabila salah satu kondisi terpenuhi.

**Contoh penggunaan NOT:**

```
sensor_aktif = Falseif not sensor_aktif:    print("Sensor belum aktif")
```

Operator `not` membalik nilai Boolean dari False menjadi True.

## **5. Looping Statement (Struktur Perulangan)**

### **5.1 Pengertian Looping**

Looping merupakan struktur kontrol yang digunakan untuk menjalankan satu atau beberapa instruksi secara berulang.

Perulangan sangat berguna ketika suatu proses harus dilakukan berkali-kali.

Dalam bidang Teknik Elektro, perulangan dapat digunakan untuk:

- Melakukan pembacaan sensor secara berulang.
- Menghitung beberapa hasil pengukuran.
- Mengumpulkan data tegangan dan arus.
- Melakukan simulasi perubahan parameter.
- Menghitung nilai rata-rata dari sejumlah pengukuran.

Python memiliki dua struktur perulangan utama, yaitu:

1. `for`
2. `while`

### **5.2 Perulangan for**

Perulangan `for` digunakan untuk melakukan iterasi terhadap suatu urutan data atau objek yang dapat diiterasi (*iterable*).

**Sintaks umum:**

```
for variabel in iterable:    instruksi
```

Contoh:

```
for i in range(1, 6):    print("Pengukuran ke-", i)
```

Output:

```
Pengukuran ke- 1
Pengukuran ke- 2
Pengukuran ke- 3
Pengukuran ke- 4
Pengukuran ke- 5
```

Pada contoh tersebut, `range(1, 6)` menghasilkan bilangan 1 sampai 5.

Nilai batas akhir pada `range()` tidak ikut dimasukkan.

### **5.3 Fungsi range()**

Fungsi `range()` digunakan untuk menghasilkan urutan bilangan yang dapat dimanfaatkan dalam perulangan.

Bentuk umum:

```
range(start, stop, step)
```

Keterangan:

- `start`: Nilai awal.
- `stop`: Batas akhir yang tidak ikut dimasukkan.
- `step`: Jarak atau kenaikan setiap iterasi.

Contoh 1 – Urutan bilangan:

```
for i in range(1, 6):    print(i)
```

Output:

```
1
2
3
4
5
```

Contoh 2 – Bilangan genap:

```
for i in range(2, 11, 2):    print(i)
```

Output:

```
2
4
6
8
10
```

Contoh 3 – Perulangan menurun:

```
for i in range(5, 0, -1):    print(i)
```

Output:

```
5
4
3
2
1
```

### **5.4 Perulangan while**

Perulangan `while` digunakan untuk menjalankan instruksi selama kondisi tertentu masih bernilai True.

Berbeda dengan `for` yang umumnya digunakan untuk jumlah iterasi atau urutan data yang telah diketahui, `while` sering digunakan ketika jumlah pengulangan bergantung pada kondisi.

**Sintaks umum:**

```
while kondisi:    instruksi
```

Contoh:

```
counter = 1while counter <= 5:    print("Pengukuran ke-", counter)    counter += 1
```

Output:

```
Pengukuran ke- 1
Pengukuran ke- 2
Pengukuran ke- 3
Pengukuran ke- 4
Pengukuran ke- 5
```

**Analisis program:**

1. Variabel `counter` dimulai dari 1.
2. Program memeriksa apakah `counter` kurang dari atau sama dengan 5.
3. Jika kondisi True, instruksi dijalankan.
4. Nilai `counter` ditambah satu.
5. Proses diulang hingga kondisi bernilai False.

### **5.5 Infinite Loop**

Infinite Loop merupakan perulangan yang tidak pernah berhenti karena kondisi perulangan selalu bernilai True.

Contoh:

```
counter = 1while counter <= 5:    print(counter)
```

Pada kode tersebut, nilai `counter` tidak pernah berubah. Akibatnya, kondisi `counter <= 5` selalu True.

Untuk menghindari kondisi tersebut, pastikan terdapat mekanisme yang mengubah nilai variabel atau menghentikan perulangan.

Contoh perbaikan:

```
counter = 1while counter <= 5:    print(counter)    counter += 1
```

## **6. Nested Loop (Perulangan Bersarang)**

Nested Loop merupakan perulangan yang ditempatkan di dalam perulangan lainnya.

Struktur ini dapat digunakan untuk menangani data multidimensi atau melakukan proses berulang dengan beberapa tingkatan.

Contoh:

```
for i in range(1, 4):    for j in range(1, 4):        print("Baris:", i, "Kolom:", j)
```

Output:

```
Baris: 1 Kolom: 1
Baris: 1 Kolom: 2
Baris: 1 Kolom: 3
Baris: 2 Kolom: 1
Baris: 2 Kolom: 2
Baris: 2 Kolom: 3
Baris: 3 Kolom: 1
Baris: 3 Kolom: 2
Baris: 3 Kolom: 3
```

Perulangan bagian dalam akan menyelesaikan seluruh iterasinya untuk setiap satu iterasi perulangan bagian luar.

### **Contoh Penerapan: Simulasi Pengukuran Multikanal**

Sebuah sistem memiliki tiga kanal pengukuran. Setiap kanal melakukan tiga kali pengukuran tegangan.

```
for kanal in range(1, 4):    print("Kanal:", kanal)    for pengukuran in range(1, 4):        print("Pengukuran ke-", pengukuran)
```

Struktur ini dapat digunakan sebagai dasar pemahaman proses akuisisi data dari beberapa kanal sensor.

## **7. Penggunaan break, continue, dan pass**

Python menyediakan beberapa instruksi tambahan untuk mengatur jalannya perulangan dan percabangan.

### **7.1 Break**

`break` digunakan untuk menghentikan perulangan secara langsung.

Contoh:

```
for i in range(1, 10):    if i == 5:        break    print(i)
```

Output:

```
1
2
3
4
```

Ketika nilai `i` mencapai 5, perulangan langsung dihentikan.

### **7.2 Continue**

`continue` digunakan untuk melewati iterasi yang sedang berlangsung dan melanjutkan ke iterasi berikutnya.

Contoh:

```
for i in range(1, 6):    if i == 3:        continue    print(i)
```

Output:

```
1
2
4
5
```

Nilai 3 tidak ditampilkan karena iterasi tersebut dilewati.

### **7.3 Pass**

`pass` merupakan instruksi kosong yang tidak melakukan tindakan apa pun ketika dieksekusi.

Instruksi ini biasanya digunakan sebagai placeholder ketika struktur program sudah dibuat tetapi implementasinya belum ditulis.

Contoh:

```
tegangan = 220if tegangan > 200:    passelse:    print("Tegangan di bawah batas")
```

Pada contoh tersebut, blok `if` belum memiliki instruksi yang akan dijalankan.

## **8. Studi Kasus Penerapan dalam Teknik Elektro**

Bagian ini menggabungkan berbagai konsep yang telah dipelajari sebelumnya.

### **Studi Kasus 1: Sistem Klasifikasi Tegangan**

Sebuah program digunakan untuk mengklasifikasikan hasil pengukuran tegangan berdasarkan parameter simulasi.

Ketentuan:

| Tegangan       | Kategori |
| -------------- | -------- |
| Di bawah 200 V | Rendah   |
| 200–240 V      | Normal   |
| Di atas 240 V  | Tinggi   |

Program:

```
tegangan = float(input("Masukkan tegangan: "))if tegangan < 200:    kategori = "Rendah"elif tegangan <= 240:    kategori = "Normal"else:    kategori = "Tinggi"print("Hasil klasifikasi:", kategori)
```

Konsep yang digunakan:

- Input data.
- Operator perbandingan.
- Conditional Statement.
- Variabel dan output.

### **Studi Kasus 2: Perhitungan Arus Menggunakan Hukum Ohm**

Hukum Ohm menyatakan bahwa hubungan antara tegangan, arus, dan hambatan dapat dinyatakan sebagai:

\\[ I = \frac{V}{R} \\]

Keterangan:

- \\(I\\) = Arus listrik (Ampere).
- \\(V\\) = Tegangan listrik (Volt).
- \\(R\\) = Hambatan listrik (Ohm).

Program:

```
tegangan = float(input("Masukkan tegangan (V): "))hambatan = float(input("Masukkan hambatan (Ohm): "))if hambatan > 0:    arus = tegangan / hambatan    print("Tegangan:", tegangan, "Volt")    print("Hambatan:", hambatan, "Ohm")    print("Arus:", arus, "Ampere")else:    print("Error: Hambatan harus lebih besar dari nol")
```

Contoh output:

```
Masukkan tegangan (V): 12
Masukkan hambatan (Ohm): 6

Tegangan: 12.0 Volt
Hambatan: 6.0 Ohm
Arus: 2.0 Ampere
```

Program menggunakan percabangan untuk mencegah pembagian dengan nol.

### **Studi Kasus 3: Menghitung Rata-Rata Pengukuran Tegangan**

Sebuah alat ukur melakukan lima kali pengukuran tegangan. Program digunakan untuk menghitung nilai rata-rata hasil pengukuran.

Rumus:

\\[ V\_{\text{rata-rata}} = \frac{\sum V_i}{n} \\]

Program:

```
total = 0jumlah = 5for i in range(1, jumlah + 1):    tegangan = float(        input(f"Pengukuran ke-{i}: ")    )    total += teganganrata_rata = total / jumlahprint("Total pengukuran:", total)print("Rata-rata tegangan:", rata_rata, "Volt")
```

Contoh input:

```
Pengukuran ke-1: 218
Pengukuran ke-2: 220
Pengukuran ke-3: 221
Pengukuran ke-4: 219
Pengukuran ke-5: 222
```

Output:

```
Total pengukuran: 1100.0
Rata-rata tegangan: 220.0 Volt
```

Konsep yang digunakan:

- Variabel akumulator.
- Perulangan `for`.
- Fungsi `range()`.
- Operasi aritmatika.
- Perhitungan rata-rata.

### **Studi Kasus 4: Simulasi Monitoring Parameter Listrik**

Sebuah sistem monitoring sederhana menerima data tegangan dan arus secara berulang. Program akan menampilkan status berdasarkan kondisi pengukuran.

```
jumlah_data = 5for i in range(1, jumlah_data + 1):    print("\nData pengukuran ke-", i)    tegangan = float(input("Tegangan (V): "))    arus = float(input("Arus (A): "))    daya = tegangan * arus    if tegangan < 200:        status = "Tegangan Rendah"    elif tegangan <= 240:        status = "Tegangan Normal"    else:        status = "Tegangan Tinggi"    print("Status:", status)    print("Daya:", daya, "Watt")
```

Program tersebut menggabungkan perulangan, percabangan, input, dan perhitungan parameter listrik.

Catatan: Perhitungan daya dengan \\(P=VI\\) pada contoh ini merupakan model sederhana untuk beban DC atau asumsi faktor daya satu. Untuk analisis sistem AC, perhitungan daya aktif dapat memerlukan faktor daya dan parameter tambahan.

## **9. Perbandingan for dan while**

Kedua struktur perulangan memiliki fungsi yang serupa, tetapi penggunaannya berbeda.

| Aspek                | for                              | while                                       |
| -------------------- | -------------------------------- | ------------------------------------------- |
| Dasar perulangan     | Iterasi terhadap iterable        | Kondisi Boolean                             |
| Jumlah iterasi       | Sering diketahui                 | Dapat bergantung pada kondisi               |
| Pengelolaan variabel | Umumnya otomatis                 | Sering diperbarui manual                    |
| Risiko infinite loop | Lebih kecil pada penggunaan umum | Lebih tinggi jika kondisi tidak berubah     |
| Contoh               | Lima kali pengukuran             | Pengukuran sampai kondisi tertentu tercapai |

Contoh penggunaan `for`:

```
for i in range(5):    print("Membaca sensor")
```

Contoh penggunaan `while`:

```
nilai = 0while nilai < 5:    print("Membaca sensor")    nilai += 1
```

Keduanya dapat menghasilkan lima kali proses, tetapi pendekatan pengendalian iterasinya berbeda.

## **10. Kesalahan Umum dalam Penggunaan Struktur Kontrol**

Beberapa kesalahan yang sering terjadi ketika mahasiswa menggunakan struktur kontrol Python adalah:

| Kesalahan               | Penyebab                      | Solusi                                     |
| ----------------------- | ----------------------------- | ------------------------------------------ |
| IndentationError        | Indentasi tidak konsisten     | Gunakan indentasi 4 spasi                  |
| SyntaxError             | Penulisan sintaks tidak tepat | Periksa titik dua dan struktur kode        |
| Kondisi tidak berjalan  | Operator perbandingan salah   | Periksa penggunaan `==`, `>=`, dan lainnya |
| Infinite Loop           | Kondisi while tidak berubah   | Perbarui variabel kondisi                  |
| Hasil klasifikasi salah | Urutan kondisi tidak tepat    | Susun kondisi dari rentang yang sesuai     |
| TypeError               | Tipe data tidak sesuai        | Gunakan konversi tipe data yang tepat      |

**Catatan penting:** Python menggunakan indentasi untuk menentukan blok program. Berbeda dengan beberapa bahasa pemrograman lain, Python tidak menggunakan tanda kurung kurawal `{}` sebagai pembatas blok percabangan dan perulangan.

Contoh:

```
if tegangan > 200:    print("Tegangan memenuhi kondisi")    print("Proses dilanjutkan")
```

Kedua instruksi `print()` merupakan bagian dari blok `if` karena memiliki indentasi yang sama.

## **11. Rangkuman Materi**

Struktur kontrol merupakan bagian fundamental dalam algoritma dan pemrograman. Melalui struktur kontrol, program dapat menjalankan instruksi berdasarkan kondisi tertentu maupun melakukan pengulangan proses.

Konsep utama yang telah dipelajari meliputi:

1. `if`: menjalankan instruksi berdasarkan kondisi.
2. `if-else`: memilih satu dari dua kemungkinan.
3. `if-elif-else`: menangani beberapa kemungkinan kondisi.
4. Nested If: melakukan pemeriksaan kondisi secara bertingkat.
5. `for`: melakukan iterasi terhadap iterable.
6. `while`: melakukan pengulangan selama kondisi terpenuhi.
7. Nested Loop: menjalankan perulangan di dalam perulangan.
8. `break`: menghentikan perulangan.
9. `continue`: melewati iterasi tertentu.
10. `pass`: menyediakan blok kosong sebagai placeholder.

Penguasaan struktur kontrol menjadi fondasi untuk mempelajari pengolahan data, modularisasi program, algoritma pencarian, pengurutan data, dan pengembangan aplikasi berbasis Python.

### **Referensi Pembelajaran**

1. Python Software Foundation. *The Python Tutorial – More Control Flow Tools*. [https://docs.python.org/3/tutorial/controlflow.html](https://docs.python.org/3/tutorial/controlflow.html?utm_source=chatgpt.com)
2. Python Software Foundation. *Built-in Functions – range()*. [https://docs.python.org/3/library/functions.html#func-range](https://docs.python.org/3/library/functions.html?utm_source=chatgpt.com#func-range)
3. Matthes, E. (2023). *Python Crash Course*, 3rd Edition. No Starch Press.
