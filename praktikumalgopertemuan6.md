# **MODULE 6**

# **FUNCTION DAN MODULARISASI PROGRAM PYTHON**

Pertemuan 6

Praktikum Algoritma dan Pemrograman

Program Studi Teknik Elektro

## **1. Deskripsi Materi**

Dalam pengembangan program komputer, terdapat banyak kondisi ketika suatu proses atau perhitungan harus dilakukan berulang kali. Jika seluruh instruksi ditulis secara langsung dalam satu bagian program, kode akan menjadi panjang, sulit dibaca, dan sulit dipelihara.

Python menyediakan fitur **function (fungsi)** untuk mengelompokkan sekumpulan instruksi ke dalam satu blok kode yang memiliki nama tertentu. Fungsi dapat dipanggil kapan saja selama program berjalan.

Dengan menggunakan fungsi, program dapat dibangun secara modular, sehingga setiap bagian memiliki tanggung jawab yang lebih jelas. Pendekatan ini sangat berguna dalam pemrograman aplikasi teknik, termasuk perhitungan parameter listrik, pengolahan hasil pengukuran, dan sistem monitoring.

## **2. Capaian Pembelajaran**

Setelah menyelesaikan materi ini, mahasiswa diharapkan mampu:

1. Menjelaskan konsep dan manfaat function dalam Python.
2. Membuat dan memanggil fungsi menggunakan `def`.
3. Menggunakan parameter dan argument dalam fungsi.
4. Menghasilkan nilai dari fungsi menggunakan `return`.
5. Menerapkan default argument dan keyword argument.
6. Memahami perbedaan variabel lokal dan global.
7. Membagi program menjadi beberapa fungsi yang saling terintegrasi.
8. Menerapkan fungsi untuk menyelesaikan permasalahan sederhana di bidang Teknik Elektro.

## **3. Konsep Dasar Function**

### **3.1 Apa itu Function?**

Function adalah sekumpulan instruksi yang dikelompokkan untuk menjalankan suatu tugas tertentu. Fungsi memiliki nama dan dapat dipanggil berulang kali dari bagian program lainnya.

Misalnya, kita ingin menghitung daya listrik menggunakan rumus:

\\[ P = V \times I \\]

Keterangan:

- \\(P\\) = daya listrik (Watt)
- \\(V\\) = tegangan (Volt)
- \\(I\\) = arus listrik (Ampere)

Tanpa fungsi, perhitungan tersebut mungkin harus ditulis berulang kali. Dengan fungsi, kita cukup membuat satu blok kode dan memanggilnya sesuai kebutuhan.

### **3.2 Membuat Function dengan&#x20;**`def`

Sintaks dasar:

```
def nama_fungsi():    # instruksi program    perintah
```

Contoh:

```
def tampilkan_identitas():    print("Praktikum Algoritma dan Pemrograman")    print("Program Studi Teknik Elektro")tampilkan_identitas()
```

Output:

```
Praktikum Algoritma dan Pemrograman
Program Studi Teknik Elektro
```

Penjelasan:

- `def` digunakan untuk mendefinisikan fungsi.
- `tampilkan_identitas` merupakan nama fungsi.
- Instruksi di dalam fungsi harus menggunakan indentasi.
- `tampilkan_identitas()` digunakan untuk memanggil fungsi.

**Hal penting:** Mendefinisikan fungsi tidak langsung menjalankan instruksi di dalamnya. Fungsi baru berjalan ketika dipanggil.

## **4. Parameter dan Argument**

Fungsi dapat menerima data dari luar melalui parameter.

### **4.1 Function dengan Parameter**

Parameter adalah variabel yang dituliskan pada saat fungsi didefinisikan.

Contoh:

```
def sapa_mahasiswa(nama):    print("Halo,", nama)    print("Selamat belajar Python!")sapa_mahasiswa("Andi")sapa_mahasiswa("Budi")
```

Output:

```
Halo, Andi
Selamat belajar Python!
Halo, Budi
Selamat belajar Python!
```

Pada contoh tersebut:

- `nama` adalah parameter.
- `"Andi"` dan `"Budi"` adalah argument.
- Satu fungsi dapat menerima nilai argument yang berbeda.

### **4.2 Function dengan Lebih dari Satu Parameter**

Contoh perhitungan daya listrik:

```
def hitung_daya(tegangan, arus):    daya = tegangan * arus    print("Daya listrik:", daya, "Watt")hitung_daya(220, 2)hitung_daya(12, 1.5)hitung_daya(24, 3)
```

Output:

```
Daya listrik: 440 Watt
Daya listrik: 18.0 Watt
Daya listrik: 72 Watt
```

Penjelasan:

Fungsi `hitung_daya()` menerima dua parameter, yaitu tegangan dan arus. Setiap kali dipanggil, fungsi menghitung hasil perkalian kedua parameter tersebut.

### **4.3 Urutan Argument**

Secara default, Python mengirimkan argument berdasarkan urutan parameter.

```
def data_pengukuran(tegangan, arus):    print("Tegangan:", tegangan, "Volt")    print("Arus:", arus, "Ampere")data_pengukuran(220, 5)
```

Output:

```
Tegangan: 220 Volt
Arus: 5 Ampere
```

Jika urutannya tertukar, hasil pemrosesan juga dapat menjadi tidak sesuai dengan maksud program.

## **5. Mengembalikan Nilai dengan&#x20;**`return`

Selain menampilkan hasil menggunakan `print()`, fungsi juga dapat mengembalikan nilai menggunakan `return`.

Perbedaan utamanya:

- `print()` menampilkan informasi ke layar.
- `return` mengirimkan hasil fungsi kembali ke bagian program yang memanggilnya.

Contoh:

```
def hitung_daya(tegangan, arus):    daya = tegangan * arus    return dayahasil = hitung_daya(220, 2)print("Hasil perhitungan:", hasil, "Watt")
```

Output:

```
Hasil perhitungan: 440 Watt
```

Nilai yang dikembalikan fungsi dapat disimpan ke variabel, digunakan dalam perhitungan berikutnya, atau diteruskan ke fungsi lain.

### **5.1 Menggunakan Return dalam Perhitungan Lanjutan**

```
def hitung_daya(tegangan, arus):    return tegangan * arusdaya_1 = hitung_daya(220, 2)daya_2 = hitung_daya(110, 3)total_daya = daya_1 + daya_2print("Daya perangkat 1:", daya_1, "Watt")print("Daya perangkat 2:", daya_2, "Watt")print("Total daya:", total_daya, "Watt")
```

Output:

```
Daya perangkat 1: 440 Watt
Daya perangkat 2: 330 Watt
Total daya: 770 Watt
```

### **5.2 Fungsi dengan Validasi**

Fungsi juga dapat digunakan untuk memvalidasi data sebelum melakukan perhitungan.

Contoh hukum Ohm:

\\[ I = \frac{V}{R} \\]

```
def hitung_arus(tegangan, resistansi):    if resistansi <= 0:        return None    arus = tegangan / resistansi    return arushasil = hitung_arus(12, 4)if hasil is not None:    print("Arus listrik:", hasil, "Ampere")else:    print("Resistansi tidak valid")
```

Output:

```
Arus listrik: 3.0 Ampere
```

Pada contoh tersebut, fungsi mengembalikan `None` jika resistansi tidak valid. Dengan demikian, program dapat mencegah pembagian dengan nol atau nilai resistansi negatif.

## **6. Default Argument dan Keyword Argument**

### **6.1 Default Argument**

Default argument merupakan nilai bawaan yang diberikan kepada parameter ketika fungsi didefinisikan.

Contoh:

```
def hitung_daya(tegangan, arus=1):    return tegangan * arusprint(hitung_daya(220))print(hitung_daya(220, 2))
```

Output:

```
220
440
```

Penjelasan:

- Ketika hanya memberikan nilai tegangan, arus menggunakan nilai default sebesar 1 Ampere.
- Ketika memberikan dua argument, nilai arus menggunakan argument yang diberikan.

### **6.2 Keyword Argument**

Keyword argument memungkinkan pemanggilan fungsi menggunakan nama parameternya.

Contoh:

```
def data_sensor(nama_sensor, tegangan, arus):    print("Sensor:", nama_sensor)    print("Tegangan:", tegangan, "Volt")    print("Arus:", arus, "Ampere")data_sensor(    nama_sensor="Sensor A",    tegangan=220,    arus=2.5)
```

Output:

```
Sensor: Sensor A
Tegangan: 220 Volt
Arus: 2.5 Ampere
```

Keyword argument membuat pemanggilan fungsi lebih mudah dibaca, terutama ketika jumlah parameter cukup banyak.

## **7. Variabel Lokal dan Global**

Dalam Python, variabel memiliki ruang lingkup (*scope*) yang menentukan bagian program tempat variabel dapat digunakan.

### **7.1 Variabel Lokal**

Variabel lokal dibuat di dalam fungsi dan hanya dapat diakses di dalam fungsi tersebut.

```
def hitung_daya():    tegangan = 220    arus = 2    daya = tegangan * arus    print("Daya:", daya, "Watt")hitung_daya()
```

Output:

```
Daya: 440 Watt
```

Variabel `tegangan`, `arus`, dan `daya` merupakan variabel lokal.

### **7.2 Variabel Global**

Variabel global didefinisikan di luar fungsi sehingga dapat dibaca dari berbagai bagian program.

```
tegangan = 220def hitung_daya(arus):    daya = tegangan * arus    return dayahasil = hitung_daya(2)print("Tegangan:", tegangan, "Volt")print("Daya:", hasil, "Watt")
```

Output:

```
Tegangan: 220 Volt
Daya: 440 Watt
```

### **7.3 Penggunaan&#x20;**`global`

Keyword `global` digunakan apabila sebuah fungsi perlu mengubah nilai variabel global.

```
jumlah_pengukuran = 0def tambah_pengukuran():    global jumlah_pengukuran    jumlah_pengukuran += 1tambah_pengukuran()tambah_pengukuran()tambah_pengukuran()print("Jumlah pengukuran:", jumlah_pengukuran)
```

Output:

```
Jumlah pengukuran: 3
```

**Catatan:** Penggunaan variabel global sebaiknya dibatasi. Untuk program yang lebih terstruktur, lebih baik mengirimkan data melalui parameter dan mengembalikan hasil melalui `return`.

## **8. Function dengan Struktur Data**

Fungsi dapat menerima dan mengolah struktur data seperti List, Tuple, dan Dictionary yang telah dipelajari pada pertemuan sebelumnya.

### **8.1 Fungsi untuk Menghitung Rata-Rata**

```
def hitung_rata_rata(data):    if len(data) == 0:        return None    rata_rata = sum(data) / len(data)    return rata_ratategangan = [218, 220, 221, 219, 223]hasil = hitung_rata_rata(tegangan)print("Rata-rata tegangan:", hasil, "Volt")
```

Output:

```
Rata-rata tegangan: 220.2 Volt
```

### **8.2 Fungsi untuk Mencari Nilai Tertinggi dan Terendah**

```
def analisis_pengukuran(data):    if len(data) == 0:        return None    hasil = {        "minimum": min(data),        "maksimum": max(data),        "rata_rata": sum(data) / len(data)    }    return hasilarus = [1.2, 1.5, 1.8, 1.4, 2.0]hasil = analisis_pengukuran(arus)print("Arus minimum:", hasil["minimum"], "A")print("Arus maksimum:", hasil["maksimum"], "A")print("Rata-rata arus:", hasil["rata_rata"], "A")
```

Output:

```
Arus minimum: 1.2 A
Arus maksimum: 2.0 A
Rata-rata arus: 1.58 A
```

Fungsi mengembalikan Dictionary yang berisi beberapa hasil analisis sekaligus.

## **9. Modularisasi Program**

### **9.1 Pengertian Modularisasi**

Modularisasi adalah teknik membagi program menjadi beberapa bagian atau modul yang memiliki tugas tertentu.

Sebagai contoh, program analisis kelistrikan dapat dibagi menjadi:

1. Fungsi untuk menghitung arus.
2. Fungsi untuk menghitung daya.
3. Fungsi untuk mengklasifikasikan hasil pengukuran.
4. Fungsi untuk menampilkan laporan.

Setiap fungsi dapat dikembangkan dan diuji secara terpisah.

### **9.2 Menggabungkan Beberapa Function**

Contoh program:

```
def hitung_arus(tegangan, resistansi):    if resistansi <= 0:        return None    return tegangan / resistansidef hitung_daya(tegangan, arus):    return tegangan * arusdef klasifikasi_arus(arus):    if arus is None:        return "Data tidak valid"    elif arus < 1:        return "Arus rendah"    elif arus <= 5:        return "Arus normal"    else:        return "Arus tinggi"def tampilkan_laporan(tegangan, resistansi):    arus = hitung_arus(tegangan, resistansi)    if arus is None:        print("Resistansi tidak valid")        return    daya = hitung_daya(tegangan, arus)    status = klasifikasi_arus(arus)    print("=== LAPORAN ANALISIS LISTRIK ===")    print("Tegangan:", tegangan, "Volt")    print("Resistansi:", resistansi, "Ohm")    print("Arus:", arus, "Ampere")
```

Output:

```
=== LAPORAN ANALISIS LISTRIK ===
Tegangan: 12 Volt
Resistansi: 4 Ohm
Arus: 3.0 Ampere
Daya: 36.0 Watt
Status: Arus normal
```

Perhatikan bahwa fungsi `tampilkan_laporan()` tidak melakukan seluruh perhitungan sendiri. Fungsi tersebut memanggil fungsi lain sesuai kebutuhan.

Inilah salah satu manfaat utama modularisasi: setiap bagian program memiliki tugas yang jelas.

## **10. Studi Kasus Teknik Elektro: Program Analisis Pengukuran Beberapa Kanal**

Pada bagian ini, mahasiswa akan mempelajari penerapan fungsi dalam sebuah kasus yang lebih terintegrasi.

### **10.1 Deskripsi Kasus**

Sebuah sistem monitoring kelistrikan memiliki tiga kanal pengukuran. Setiap kanal memiliki nilai tegangan dan resistansi yang berbeda.

Program harus melakukan:

1. Menghitung arus setiap kanal berdasarkan hukum Ohm.
2. Menghitung daya setiap kanal.
3. Menghitung total daya seluruh kanal.
4. Menampilkan laporan hasil analisis.

### **10.2 Implementasi Program**

```
# Fungsi menghitung arusdef hitung_arus(tegangan, resistansi):    if resistansi <= 0:        return None    return tegangan / resistansi# Fungsi menghitung dayadef hitung_daya(tegangan, arus):    return tegangan * arus# Fungsi menghitung data satu kanaldef analisis_kanal(nama, tegangan, resistansi):    arus = hitung_arus(tegangan, resistansi)    if arus is None:        return None    daya = hitung_daya(tegangan, arus)    return {        "nama": nama,        "tegangan": tegangan,        "resistansi": resistansi,        "arus": arus,        "daya": daya    }# Data pengukurankanal = [    {"nama": "Kanal 1", "tegangan": 12, "resistansi": 4},    {"nama": "Kanal 2", "tegangan": 24, "resistansi": 8},    {"nama": "Kanal 3", "tegangan": 9, "resistansi": 3}
```

### **10.3 Hasil Program**

```
=== HASIL ANALISIS SISTEM KELISTRIKAN ===

 Kanal 1
Tegangan: 12 Volt
Resistansi: 4 Ohm
Arus: 3.0 Ampere
Daya: 36.0 Watt

 Kanal 2
Tegangan: 24 Volt
Resistansi: 8 Ohm
Arus: 3.0 Ampere
Daya: 72.0 Watt

 Kanal 3
Tegangan: 9 Volt
Resistansi: 3 Ohm
Arus: 3.0 Ampere
Daya: 27.0 Watt

Total daya seluruh kanal: 135.0 Watt
```

### **10.4 Analisis Program**

Dari program tersebut dapat diamati:

- Fungsi `hitung_arus()` digunakan untuk menghitung arus berdasarkan hukum Ohm.
- Fungsi `hitung_daya()` digunakan untuk menghitung daya listrik.
- Fungsi `analisis_kanal()` menggabungkan proses perhitungan menjadi satu kesatuan.
- Struktur List dan Dictionary digunakan untuk menyimpan data beberapa kanal.
- Perulangan `for` digunakan untuk memproses setiap kanal.
- Variabel `total_daya` digunakan untuk mengakumulasi hasil perhitungan.

Contoh ini menggambarkan bagaimana function, struktur data, dan perulangan dapat digunakan bersama untuk membangun program analisis sederhana.

Catatan teknis: perhitungan daya di atas menggunakan model sederhana DC atau beban resistif. Untuk sistem AC sinusoidal satu fasa, daya aktif juga mempertimbangkan faktor daya, yaitu P = V × I × cos φ.

## **11. Function sebagai Modul Terpisah**

Pada program yang lebih besar, fungsi dapat dikelompokkan ke dalam file Python terpisah. File tersebut dapat diimpor dan digunakan oleh program utama.

Misalnya, kita memiliki dua file:

**perhitungan.py**

```
def hitung_arus(tegangan, resistansi):    if resistansi <= 0:        return None    return tegangan / resistansidef hitung_daya(tegangan, arus):    return tegangan * arus
```

**main.py**

```
import perhitunganarus = perhitungan.hitung_arus(12, 4)daya = perhitungan.hitung_daya(12, arus)print("Arus:", arus, "Ampere")print("Daya:", daya, "Watt")
```

Output:

```
Arus: 3.0 Ampere
Daya: 36.0 Watt
```

Kedua file harus berada dalam direktori yang sama agar contoh sederhana tersebut dapat dijalankan tanpa konfigurasi tambahan.

### **11.1 Mengimpor Fungsi Tertentu**

Selain mengimpor seluruh modul, kita juga dapat mengimpor fungsi tertentu.

```
from perhitungan import hitung_arus, hitung_dayaarus = hitung_arus(24, 8)daya = hitung_daya(24, arus)print("Arus:", arus)print("Daya:", daya)
```

Dengan cara ini, fungsi dapat dipanggil langsung tanpa menuliskan nama modul di depannya.

## **12. Lambda Function (Pengenalan)**

Python juga menyediakan fungsi anonim menggunakan keyword `lambda`.

Lambda cocok digunakan untuk fungsi sederhana yang hanya membutuhkan satu ekspresi.

Sintaks:

```
lambda parameter: ekspresi
```

Contoh:

```
hitung_daya = lambda tegangan, arus: tegangan * arushasil = hitung_daya(220, 2)print("Daya:", hasil, "Watt")
```

Output:

```
Daya: 440 Watt
```

Contoh lain:

```
konversi_kilowatt = lambda watt: watt / 1000print(konversi_kilowatt(1500), "kW")
```

Output:

```
1.5 kW
```

Lambda bukan pengganti seluruh function. Untuk proses yang memiliki banyak instruksi, validasi, atau percabangan, penggunaan `def` biasanya lebih tepat dan mudah dibaca.

## **13. Kesalahan Umum dalam Penggunaan Function**

| Kesalahan                | Penyebab                                   | Solusi                                                 |
| ------------------------ | ------------------------------------------ | ------------------------------------------------------ |
| `NameError`              | Fungsi belum didefinisikan atau nama salah | Periksa nama dan urutan definisi                       |
| `TypeError`              | Jumlah argument tidak sesuai               | Periksa parameter fungsi                               |
| `IndentationError`       | Indentasi tidak konsisten                  | Gunakan indentasi yang benar                           |
| Hasil `None`             | Fungsi tidak mengembalikan nilai           | Gunakan `return` jika diperlukan                       |
| `ZeroDivisionError`      | Pembagian dengan nol                       | Lakukan validasi sebelum pembagian                     |
| Hasil perhitungan keliru | Urutan argument tertukar                   | Periksa urutan parameter atau gunakan keyword argument |

Contoh kesalahan yang sering terjadi:

```
def hitung_daya(tegangan, arus):    daya = tegangan * arushasil = hitung_daya(220, 2)print(hasil)
```

Output:

```
None
```

Mengapa? Karena fungsi tidak memiliki `return`. Variabel `daya` hanya dibuat di dalam fungsi dan tidak dikembalikan ke pemanggil.

Perbaikannya:

```
def hitung_daya(tegangan, arus):    daya = tegangan * arus    return dayahasil = hitung_daya(220, 2)print(hasil)
```

Output:

```
440
```

## **14. Ringkasan Materi**

Pada pertemuan ini, mahasiswa telah mempelajari:

1. Function merupakan blok kode yang dibuat untuk menjalankan tugas tertentu.
2. Keyword `def` digunakan untuk mendefinisikan fungsi.
3. Parameter digunakan untuk menerima data dari luar fungsi.
4. `return` digunakan untuk mengembalikan nilai hasil pemrosesan.
5. Default argument memberikan nilai bawaan pada parameter.
6. Keyword argument memungkinkan pemanggilan fungsi berdasarkan nama parameter.
7. Variabel lokal hanya berlaku di dalam fungsi, sedangkan variabel global dapat diakses dari lingkup program yang lebih luas.
8. Modularisasi membagi program menjadi bagian-bagian yang lebih terstruktur.
9. Fungsi dapat menerima dan mengolah List maupun Dictionary.
10. Lambda merupakan alternatif untuk fungsi sederhana dengan satu ekspresi.

**Inti pembelajaran:** Program yang baik tidak hanya menghasilkan output yang benar, tetapi juga harus terstruktur, mudah dipahami, dapat digunakan kembali, dan mudah dikembangkan.

## **15. Referensi Pembelajaran**

1. Python Software Foundation. *Python Tutorial – Defining Functions*. [Python Official Documentation](https://docs.python.org/3/tutorial/controlflow.html).
2. Python Software Foundation. *Python Tutorial – Modules*. [Python Modules Documentation](https://docs.python.org/3/tutorial/modules.html).
3. Python Software Foundation. *Built-in Functions*. [Python Built-in Functions](https://docs.python.org/3/library/functions.html).
4. Matthes, E. (2023). *Python Crash Course*, 3rd Edition. No Starch Press.
