# **MODULE 8**

# **FILE HANDLING DAN EXCEPTION HANDLING PYTHON**

Pertemuan 8

Praktikum Algoritma dan Pemrograman

Program Studi Teknik Elektro

## **1. Deskripsi Materi**

Dalam pengembangan aplikasi, data tidak selalu ditulis secara langsung di dalam program. Sering kali data berasal dari file eksternal, seperti TXT, CSV, atau format lainnya.

Sebagai contoh, sebuah sistem monitoring kelistrikan dapat menghasilkan data pengukuran tegangan dan arus dalam jumlah besar. Data tersebut perlu disimpan agar dapat dibaca kembali, dianalisis, dan digunakan untuk menghasilkan laporan.

Python menyediakan mekanisme **File Handling** untuk membaca dan menulis file. Selain itu, Python menyediakan **Exception Handling** untuk menangani kesalahan yang mungkin terjadi ketika program dijalankan.

Pada pertemuan ini, mahasiswa akan mempelajari cara membaca dan menulis file teks, mengolah file CSV, serta menggunakan mekanisme penanganan kesalahan agar program lebih stabil.

## **2. Capaian Pembelajaran**

Setelah menyelesaikan materi ini, mahasiswa diharapkan mampu:

1. Menjelaskan konsep dasar File Handling dalam Python.
2. Membuka dan menutup file menggunakan `open()` dan `close()`.
3. Membaca isi file menggunakan `read()`, `readline()`, dan `readlines()`.
4. Menulis dan menambahkan data ke dalam file.
5. Mengolah data CSV menggunakan modul `csv`.
6. Memahami konsep Exception Handling.
7. Menggunakan `try`, `except`, `else`, dan `finally`.
8. Mengintegrasikan File Handling dan Exception Handling dalam program sederhana.
9. Mengembangkan program analisis data pengukuran kelistrikan berbasis file.

## **3. Konsep Dasar File Handling**

### **3.1 Apa itu File Handling?**

File Handling adalah mekanisme untuk melakukan operasi terhadap file melalui program komputer.

Operasi dasar File Handling meliputi:

- Membuat file.
- Membuka file.
- Membaca isi file.
- Menulis data ke dalam file.
- Menambahkan data ke dalam file.
- Menutup file.

Dalam Python, fungsi utama yang digunakan untuk membuka file adalah `open()`.

### **3.2 Sintaks Dasar&#x20;**`open()`

```
file = open("nama_file.txt", "mode")
```

Keterangan:

- `nama_file.txt` merupakan nama file yang akan diakses.
- `mode` menentukan jenis operasi terhadap file.

### **3.3 Mode File dalam Python**

| Mode | Fungsi                                                               |
| ---- | -------------------------------------------------------------------- |
| `r`  | Membaca file yang sudah tersedia                                     |
| `w`  | Menulis file, membuat file baru atau menimpa isi file yang sudah ada |
| `a`  | Menambahkan data di akhir file                                       |
| `x`  | Membuat file baru, gagal jika file sudah ada                         |
| `r+` | Membaca dan menulis file yang sudah ada                              |
| `w+` | Membaca dan menulis, tetapi mengosongkan isi file terlebih dahulu    |
| `a+` | Membaca dan menambahkan data pada akhir file                         |

Perlu diperhatikan bahwa mode `w` dapat menghapus isi file sebelumnya. Oleh karena itu, penggunaannya harus dilakukan dengan hati-hati.

## **4. Membaca File Teks**

### **4.1 Membaca File dengan&#x20;**`read()`

Method `read()` digunakan untuk membaca seluruh isi file sebagai satu string.

Misalnya terdapat file bernama `pengukuran.txt` dengan isi:

```
Pengukuran Tegangan Listrik
Sensor A: 220 Volt
Sensor B: 215 Volt
Sensor C: 225 Volt
Sensor D: 218 Volt
```

Program untuk membacanya:

```
file = open("pengukuran.txt", "r")isi = file.read()print(isi)file.close()
```

Output:

```
Pengukuran Tegangan Listrik
Sensor A: 220 Volt
Sensor B: 215 Volt
Sensor C: 225 Volt
Sensor D: 218 Volt
```

Penjelasan:

- `open()` membuka file.
- `read()` membaca seluruh isi file.
- `print()` menampilkan isi file.
- `close()` menutup file setelah selesai digunakan.

### **4.2 Membaca File dengan&#x20;**`readline()`

Method `readline()` digunakan untuk membaca satu baris setiap kali dipanggil.

```
file = open("pengukuran.txt", "r")baris_1 = file.readline()baris_2 = file.readline()print(baris_1)print(baris_2)file.close()
```

Output:

```
Pengukuran Tegangan Listrik

Sensor A: 220 Volt
```

Setiap pemanggilan `readline()` akan membaca baris berikutnya.

### **4.3 Membaca File dengan&#x20;**`readlines()`

Method `readlines()` membaca seluruh baris dan mengembalikannya dalam bentuk List.

```
file = open("pengukuran.txt", "r")data = file.readlines()print(data)file.close()
```

Hasilnya berupa List:

```
[    'Pengukuran Tegangan Listrik\n',    'Sensor A: 220 Volt\n',    'Sensor B: 215 Volt\n',    'Sensor C: 225 Volt\n',    'Sensor D: 218 Volt\n']
```

Karakter `\n` menunjukkan perpindahan baris atau *newline*.

### **4.4 Membaca File Menggunakan Perulangan**

Cara lain yang lebih praktis adalah menggunakan perulangan `for`.

```
file = open("pengukuran.txt", "r")for baris in file:    print(baris.strip())file.close()
```

Method `strip()` digunakan untuk menghilangkan karakter kosong di awal dan akhir string, termasuk karakter newline.

## **5. Menggunakan&#x20;**`with open()`

Dalam Python, cara yang direkomendasikan untuk mengakses file adalah menggunakan pernyataan `with`.

Contoh:

```
with open("pengukuran.txt", "r") as file:    isi = file.read()    print(isi)
```

Keuntungan menggunakan `with`:

1. File akan ditutup secara otomatis setelah blok program selesai.
2. Kode lebih ringkas.
3. Mengurangi risiko file lupa ditutup.
4. Lebih aman ketika terjadi kesalahan selama proses pembacaan.

Dengan demikian, untuk contoh-contoh berikutnya kita akan lebih banyak menggunakan `with open()`.

## **6. Menulis File Teks**

### **6.1 Menulis File dengan Mode&#x20;**`w`

Mode `w` digunakan untuk membuat file baru atau menimpa isi file yang sudah ada.

Contoh:

```
with open("hasil_analisis.txt", "w") as file:    file.write("LAPORAN PENGUKURAN LISTRIK\n")    file.write("Tegangan: 220 Volt\n")    file.write("Arus: 2 Ampere\n")    file.write("Daya: 440 Watt\n")print("File berhasil dibuat")
```

Output program:

```
File berhasil dibuat
```

Isi file `hasil_analisis.txt`:

```
LAPORAN PENGUKURAN LISTRIK
Tegangan: 220 Volt
Arus: 2 Ampere
Daya: 440 Watt
```

### **6.2 Menambahkan Data dengan Mode&#x20;**`a`

Mode `a` digunakan untuk menambahkan data pada akhir file tanpa menghapus isi sebelumnya.

```
with open("hasil_analisis.txt", "a") as file:    file.write("Status: Pengukuran selesai\n")print("Data berhasil ditambahkan")
```

Isi file setelah penambahan:

```
LAPORAN PENGUKURAN LISTRIK
Tegangan: 220 Volt
Arus: 2 Ampere
Daya: 440 Watt
Status: Pengukuran selesai
```

### **6.3 Menulis Banyak Baris dengan&#x20;**`writelines()`

Method `writelines()` dapat digunakan untuk menulis sekumpulan string ke dalam file.

```
data = [    "Sensor A: 220 Volt\n",    "Sensor B: 215 Volt\n",    "Sensor C: 225 Volt\n"]with open("data_sensor.txt", "w") as file:    file.writelines(data)print("Data sensor berhasil disimpan")
```

Perlu diingat bahwa `writelines()` tidak otomatis menambahkan karakter newline. Karena itu, setiap string perlu menyertakan `\n` jika ingin dipisahkan menjadi baris berbeda.

## **7. Bekerja dengan File CSV**

### **7.1 Pengertian CSV**

CSV merupakan singkatan dari *Comma-Separated Values*. CSV adalah format file yang digunakan untuk menyimpan data tabular dalam bentuk teks.

Data CSV umumnya memiliki:

- Baris sebagai record.
- Kolom sebagai atribut.
- Pemisah berupa koma atau delimiter lainnya.
- Baris pertama yang sering digunakan sebagai header.

Contoh isi file `data_sensor.csv`:

```
sensor,tegangan,arus
Sensor A,220,2.0
Sensor B,215,1.5
Sensor C,225,2.5
Sensor D,218,1.8
Sensor E,230,3.0
```

File CSV sangat umum digunakan untuk menyimpan hasil pengukuran, data sensor, dan hasil ekspor dari spreadsheet.

### **7.2 Membaca CSV dengan Modul&#x20;**`csv`

Python menyediakan modul bawaan bernama `csv`.

Untuk menggunakannya:

```
import csvwith open("data_sensor.csv", "r", newline="") as file:    reader = csv.reader(file)    for baris in reader:        print(baris)
```

Output:

```
['sensor', 'tegangan', 'arus']
['Sensor A', '220', '2.0']
['Sensor B', '215', '1.5']
['Sensor C', '225', '2.5']
['Sensor D', '218', '1.8']
['Sensor E', '230', '3.0']
```

Perhatikan bahwa data yang dibaca oleh `csv.reader()` secara default berupa string.

Jika ingin melakukan perhitungan matematis, data numerik harus dikonversi terlebih dahulu.

### **7.3 Membaca CSV dengan&#x20;**`csv.DictReader`

`DictReader` membaca setiap baris CSV sebagai Dictionary. Nama kolom digunakan sebagai key.

```
import csvwith open("data_sensor.csv", "r", newline="") as file:    reader = csv.DictReader(file)    for baris in reader:        print(            baris["sensor"],            baris["tegangan"],            baris["arus"]        )
```

Output:

```
Sensor A 220 2.0
Sensor B 215 1.5
Sensor C 225 2.5
Sensor D 218 1.8
Sensor E 230 3.0
```

Pendekatan ini lebih mudah digunakan ketika data CSV memiliki banyak kolom.

### **7.4 Menghitung Daya dari File CSV**

Berikutnya, kita akan membaca data CSV dan melakukan perhitungan daya.

Rumus:

\\[ P = V \times I \\]

Program:

```
import csvwith open("data_sensor.csv", "r", newline="") as file:    reader = csv.DictReader(file)    for baris in reader:        nama = baris["sensor"]        tegangan = float(baris["tegangan"])        arus = float(baris["arus"])        daya = tegangan * arus        print(nama)        print("Tegangan:", tegangan, "Volt")        print("Arus:", arus, "Ampere")        print("Daya:", daya, "Watt")        print("--------------------")
```

Output:

```
Sensor A
Tegangan: 220.0 Volt
Arus: 2.0 Ampere
Daya: 440.0 Watt
--------------------
Sensor B
Tegangan: 215.0 Volt
Arus: 1.5 Ampere
Daya: 322.5 Watt
--------------------
Sensor C
Tegangan: 225.0 Volt
Arus: 2.5 Ampere
Daya: 562.5 Watt
--------------------
Sensor D
Tegangan: 218.0 Volt
Arus: 1.8 Ampere
Daya: 392.4 Watt
--------------------
Sensor E
Tegangan: 230.0 Volt
Arus: 3.0 Ampere
Daya: 690.0 Watt
--------------------
```

## **8. Menulis Data ke File CSV**

Selain membaca file CSV, Python juga dapat membuat dan menyimpan data dalam format CSV menggunakan `csv.writer()`.

### **8.1 Membuat File CSV**

```
import csvdata = [    ["sensor", "tegangan", "arus"],    ["Sensor A", 220, 2.0],    ["Sensor B", 215, 1.5],    ["Sensor C", 225, 2.5]]with open("hasil_sensor.csv", "w", newline="") as file:    writer = csv.writer(file)    writer.writerows(data)print("File CSV berhasil dibuat")
```

Isi file `hasil_sensor.csv`:

```
sensor,tegangan,arus
Sensor A,220,2.0
Sensor B,215,1.5
Sensor C,225,2.5
```

### **8.2 Menambahkan Data ke CSV**

```
import csvdata_baru = ["Sensor D", 218, 1.8]with open("hasil_sensor.csv", "a", newline="") as file:    writer = csv.writer(file)    writer.writerow(data_baru)print("Data baru berhasil ditambahkan")
```

### **8.3 Menggunakan&#x20;**`csv.DictWriter`

Jika data disimpan dalam bentuk Dictionary, kita dapat menggunakan `DictWriter`.

```
import csvdata = [    {"sensor": "Sensor A", "tegangan": 220, "arus": 2.0},    {"sensor": "Sensor B", "tegangan": 215, "arus": 1.5},    {"sensor": "Sensor C", "tegangan": 225, "arus": 2.5}]fieldnames = ["sensor", "tegangan", "arus"]with open("data_baru.csv", "w", newline="") as file:    writer = csv.DictWriter(file, fieldnames=fieldnames)    writer.writeheader()    writer.writerows(data)print("Data berhasil disimpan")
```

`writeheader()` digunakan untuk menuliskan nama kolom pada baris pertama file CSV.

## **9. Konsep Dasar Exception Handling**

### **9.1 Apa itu Exception?**

Exception merupakan kondisi kesalahan yang terjadi ketika program sedang dijalankan.

Contohnya:

- File yang ingin dibaca tidak ditemukan.
- Program mencoba membagi angka dengan nol.
- Data string dikonversi menjadi angka padahal formatnya tidak valid.
- Program mengakses indeks List yang tidak tersedia.
- Program mencoba mengakses key Dictionary yang tidak ada.

Tanpa penanganan kesalahan, exception yang tidak ditangani dapat menghentikan jalannya program.

### **9.2 Contoh Program Tanpa Exception Handling**

```
angka = int(input("Masukkan angka: "))hasil = 100 / angkaprint("Hasil:", hasil)
```

Jika pengguna memasukkan angka `0`, program menghasilkan:

```
ZeroDivisionError: division by zero
```

Jika pengguna memasukkan teks seperti `abc`, program menghasilkan:

```
ValueError: invalid literal for int()
```

Kondisi tersebut menunjukkan bahwa program perlu memiliki mekanisme untuk menangani kesalahan input.

## **10. Menggunakan&#x20;**`try`**&#x20;dan&#x20;**`except`

### **10.1 Struktur Dasar**

Sintaks:

```
try:    # kode yang berpotensi menghasilkan exceptionexcept:    # instruksi ketika terjadi exception
```

Contoh:

```
try:    angka = int(input("Masukkan angka: "))    hasil = 100 / angka    print("Hasil:", hasil)except:    print("Terjadi kesalahan pada input atau perhitungan")
```

Jika terjadi kesalahan, program akan menjalankan blok `except` daripada langsung berhenti karena exception tersebut.

Namun, penggunaan `except` tanpa menyebutkan jenis exception sebaiknya dihindari untuk penanganan kesalahan yang lebih terkontrol.

### **10.2 Menangani Exception Secara Spesifik**

Python menyediakan berbagai jenis exception.

| Exception           | Penyebab                                            |
| ------------------- | --------------------------------------------------- |
| `ValueError`        | Nilai tidak sesuai dengan tipe data yang diharapkan |
| `TypeError`         | Operasi tidak sesuai dengan tipe data               |
| `ZeroDivisionError` | Pembagian dengan nol                                |
| `FileNotFoundError` | File tidak ditemukan                                |
| `IndexError`        | Indeks List berada di luar jangkauan                |
| `KeyError`          | Key Dictionary tidak ditemukan                      |

Contoh:

```
try:    angka = int(input("Masukkan angka: "))    hasil = 100 / angka    print("Hasil:", hasil)except ValueError:    print("Input harus berupa angka")except ZeroDivisionError:    print("Angka tidak boleh nol")
```

Dengan menggunakan beberapa `except`, program dapat memberikan pesan kesalahan yang lebih spesifik.

## **11. Menggunakan&#x20;**`else`**&#x20;dan&#x20;**`finally`

Python menyediakan dua bagian tambahan dalam struktur Exception Handling.

### **11.1 Blok&#x20;**`else`

Blok `else` dijalankan ketika tidak terjadi exception pada blok `try`.

```
try:    tegangan = float(input("Masukkan tegangan: "))    arus = float(input("Masukkan arus: "))    daya = tegangan * arusexcept ValueError:    print("Input harus berupa angka")else:    print("Daya listrik:", daya, "Watt")
```

### **11.2 Blok&#x20;**`finally`

Blok `finally` akan dijalankan setelah proses `try` dan `except`, baik terjadi exception maupun tidak.

```
try:    angka = int(input("Masukkan angka: "))    hasil = 100 / angka    print("Hasil:", hasil)except ValueError:    print("Input tidak valid")except ZeroDivisionError:    print("Tidak dapat membagi dengan nol")finally:    print("Program selesai dijalankan")
```

### **11.3 Struktur Lengkap Exception Handling**

```
try:    # kode utamaexcept ValueError:    # penanganan ValueErrorexcept ZeroDivisionError:    # penanganan ZeroDivisionErrorelse:    # dijalankan jika tidak terjadi exceptionfinally:    # selalu dijalankan pada akhir proses
```

## **12. Menggunakan&#x20;**`raise`**&#x20;untuk Membuat Exception**

Selain menangani exception yang muncul secara otomatis, programmer juga dapat membuat exception sendiri menggunakan keyword `raise`.

Contoh:

```
def hitung_arus(tegangan, resistansi):    if resistansi <= 0:        raise ValueError("Resistansi harus lebih besar dari nol")    return tegangan / resistansitry:    hasil = hitung_arus(12, 0)    print("Arus:", hasil)except ValueError as error:    print("Kesalahan:", error)
```

Output:

```
Kesalahan: Resistansi harus lebih besar dari nol
```

Pada contoh tersebut:

- Fungsi memeriksa nilai resistansi.
- Jika resistansi tidak valid, fungsi menghasilkan exception dengan `raise`.
- Blok `except` menangkap exception tersebut.
- Program menampilkan pesan kesalahan yang lebih informatif.

## **13. Studi Kasus Teknik Elektro: Membaca dan Menganalisis Data Sensor dari CSV**

Sekarang kita gabungkan materi File Handling, Exception Handling, Function, dan Struktur Data dalam satu program.

### **13.1 Deskripsi Kasus**

Sebuah sistem monitoring kelistrikan menyimpan data pengukuran beberapa sensor dalam file CSV.

Data yang tersedia:

| Sensor   | Tegangan (V) | Arus (A) |
| -------- | ------------ | -------- |
| Sensor A | 220          | 2.0      |
| Sensor B | 215          | 1.5      |
| Sensor C | 225          | 2.5      |
| Sensor D | 218          | 1.8      |
| Sensor E | 230          | 3.0      |

Program akan melakukan:

1. Membaca data dari file CSV.
2. Memvalidasi nilai tegangan dan arus.
3. Menghitung daya setiap sensor.
4. Menghitung rata-rata tegangan.
5. Menghitung total daya.
6. Menyimpan hasil analisis ke file CSV baru.
7. Menangani kesalahan yang mungkin terjadi selama pemrosesan.

### **13.2 Persiapan File Input**

Buat file bernama `data_sensor.csv`.

Isi file:

```
sensor,tegangan,arus
Sensor A,220,2.0
Sensor B,215,1.5
Sensor C,225,2.5
Sensor D,218,1.8
Sensor E,230,3.0
```

Simpan file tersebut dalam direktori yang sama dengan program Python.

### **13.3 Implementasi Program**

```
import csv# Fungsi menghitung dayadef hitung_daya(tegangan, arus):    if tegangan < 0 or arus < 0:        raise ValueError("Nilai tidak boleh negatif")    return tegangan * arus# Fungsi membaca data CSVdef baca_data(filename):    data = []    with open(filename, "r", newline="") as file:        reader = csv.DictReader(file)        for baris in reader:            tegangan = float(baris["tegangan"])            arus = float(baris["arus"])            if tegangan < 0 or arus < 0:                raise ValueError("Nilai pengukuran negatif")            data.append({                "sensor": baris["sensor"],                "tegangan": tegangan,                "arus": arus            })    return data# Fungsi analisis datadef analisis_data(data):
```

### **13.4 Output Program**

```
=== LAPORAN ANALISIS SENSOR ===

 Sensor A
Tegangan: 220.0 Volt
Arus: 2.0 Ampere
Daya: 440.0 Watt

 Sensor B
Tegangan: 215.0 Volt
Arus: 1.5 Ampere
Daya: 322.5 Watt

 Sensor C
Tegangan: 225.0 Volt
Arus: 2.5 Ampere
Daya: 562.5 Watt

 Sensor D
Tegangan: 218.0 Volt
Arus: 1.8 Ampere
Daya: 392.4 Watt

 Sensor E
Tegangan: 230.0 Volt
Arus: 3.0 Ampere
Daya: 690.0 Watt

Rata-rata tegangan: 221.6 Volt
Total daya: 2407.4 Watt

Hasil analisis berhasil disimpan
```

### **13.5 Hasil File Output**

Program menghasilkan file baru bernama `hasil_analisis.csv`.

Isi file:

```
sensor,tegangan,arus,daya
Sensor A,220.0,2.0,440.0
Sensor B,215.0,1.5,322.5
Sensor C,225.0,2.5,562.5
Sensor D,218.0,1.8,392.4
Sensor E,230.0,3.0,690.0
```

### **13.6 Analisis Program**

Program tersebut memperlihatkan bagaimana beberapa konsep Python dapat digunakan secara bersama-sama:

| Komponen                | Fungsi                         |
| ----------------------- | ------------------------------ |
| `import csv`            | Mengakses fitur pengolahan CSV |
| `baca_data()`           | Membaca dan memvalidasi data   |
| `hitung_daya()`         | Melakukan perhitungan daya     |
| `analisis_data()`       | Mengolah data sensor           |
| `simpan_hasil()`        | Menyimpan hasil analisis       |
| `try-except`            | Menangani kesalahan            |
| `List` dan `Dictionary` | Menyimpan data pengukuran      |

Program juga menunjukkan bahwa pemisahan fungsi membuat kode lebih mudah dipahami dan dikembangkan.

Catatan: perhitungan daya pada contoh ini menggunakan model sederhana \\(P=V \times I\\), sesuai ilustrasi beban DC atau resistif. Pada pengukuran daya aktif AC, faktor daya perlu diperhitungkan.

## **14. Validasi Data dan Penanganan Kesalahan File**

Dalam praktik pengolahan data, tidak semua file yang diterima memiliki format yang benar. Bisa saja terdapat data kosong, nilai nonnumerik, atau nama kolom yang berbeda.

Sebagai contoh, file CSV berikut memiliki satu baris yang tidak valid:

```
sensor,tegangan,arus
Sensor A,220,2.0
Sensor B,215,1.5
Sensor C,ABC,2.5
Sensor D,218,1.8
```

Ketika program mencoba mengubah `ABC` menjadi `float`, Python akan menghasilkan `ValueError`.

Kita dapat menangani kesalahan per baris agar satu data yang bermasalah tidak langsung menghentikan seluruh proses.

```
import csvdata_valid = []data_error = []with open("data_sensor.csv", "r", newline="") as file:    reader = csv.DictReader(file)    for nomor, baris in enumerate(reader, start=2):        try:            tegangan = float(baris["tegangan"])            arus = float(baris["arus"])            if tegangan < 0 or arus < 0:                raise ValueError("Nilai tidak boleh negatif")            data_valid.append({                "sensor": baris["sensor"],                "tegangan": tegangan,                "arus": arus            })        except (ValueError, KeyError) as error:            data_error.append({                "baris": nomor,                "kesalahan": str(error)            })print("Data valid:", len(data_valid))print("Data bermasalah:", len(data_error))for error in data_error:    print(error)
```

Contoh output ketika file memiliki satu baris bermasalah:

```
Data valid: 3
Data bermasalah: 1
{'baris': 4, 'kesalahan': "could not convert string to float: 'ABC'"}
```

Dengan pendekatan ini, program dapat memisahkan data yang valid dan data yang perlu diperiksa lebih lanjut.

## **15. Pengembangan Lanjutan: Visualisasi Data Pengukuran**

Setelah data CSV berhasil dibaca dan dianalisis, hasilnya dapat divisualisasikan menggunakan Matplotlib.

Contoh berikut membaca data sensor dan membuat grafik tegangan.

```
import csvimport matplotlib.pyplot as pltnama_sensor = []tegangan = []with open("data_sensor.csv", "r", newline="") as file:    reader = csv.DictReader(file)    for baris in reader:        nama_sensor.append(baris["sensor"])        tegangan.append(float(baris["tegangan"]))plt.bar(nama_sensor, tegangan)plt.title("Hasil Pengukuran Tegangan")plt.xlabel("Nama Sensor")plt.ylabel("Tegangan (Volt)")plt.grid(axis="y")plt.show()
```

[Student Hostel Electricity Usage Analysis Using Python (MINOR PROJECT) | by Prachi Arya | Medium](https://images.openai.com/static-rsc-4/aUEZMcpn51MEUFGIm2TQ6DsI1GD-INzDLOrLgWvFuLUjRuO5R2faIo_Mt4MQMi3v7zNNs-6RSTQfIDN-r8zBl4EC0I5uGjgEuWD6UTrJnecCT8VZgwEJLNk43px9i6nuvHVsjTVyyA6LgCNv9X_uJuHpSpOc7vVHGVgZ_whKJkg?purpose=inline)

[medium.com](https://medium.com/%40prachiarya206/student-hostel-electricity-usage-analysis-using-python-minor-project-86d2a99e281e?utm_source=chatgpt.com)

Visualisasi tersebut membantu pengguna membandingkan hasil pengukuran antar-sensor dengan lebih mudah.

Catatan: Matplotlib merupakan library tambahan. Instalasi dapat dilakukan melalui terminal:

```
pip install matplotlib
```

## **16. Kesalahan Umum dalam File Handling dan Exception Handling**

| Kesalahan                           | Penyebab                               | Solusi                                  |
| ----------------------------------- | -------------------------------------- | --------------------------------------- |
| `FileNotFoundError`                 | File tidak ditemukan                   | Periksa nama dan lokasi file            |
| `PermissionError`                   | Tidak memiliki izin mengakses file     | Periksa hak akses                       |
| `ValueError`                        | Data tidak sesuai tipe yang diharapkan | Validasi sebelum konversi               |
| `KeyError`                          | Nama kolom CSV tidak sesuai            | Periksa header file                     |
| `UnicodeDecodeError`                | Encoding file tidak sesuai             | Tentukan encoding yang tepat            |
| File tertimpa                       | Menggunakan mode `w`                   | Gunakan mode `a` jika ingin menambahkan |
| Data CSV tidak terbaca dengan benar | Struktur atau delimiter tidak sesuai   | Periksa format file                     |

Beberapa praktik baik yang perlu diterapkan:

1. Gunakan `with open()` untuk mengakses file.
2. Periksa keberadaan file sebelum diproses jika diperlukan.
3. Validasi data sebelum melakukan perhitungan.
4. Tangani exception secara spesifik.
5. Hindari penggunaan `except` kosong tanpa alasan.
6. Gunakan nama file dan lokasi penyimpanan yang jelas.

## **17. Ringkasan Materi**

Pada pertemuan ini, mahasiswa telah mempelajari:

1. File Handling merupakan mekanisme untuk membaca dan menulis file menggunakan Python.
2. Fungsi `open()` digunakan untuk membuka file.
3. Mode `r`, `w`, `a`, dan `x` menentukan jenis operasi file.
4. `read()`, `readline()`, dan `readlines()` digunakan untuk membaca file.
5. `write()` dan `writelines()` digunakan untuk menulis data.
6. Pernyataan `with open()` membantu mengelola file secara otomatis.
7. Modul `csv` digunakan untuk membaca dan menulis file CSV.
8. `DictReader` dan `DictWriter` mempermudah pengolahan data berdasarkan nama kolom.
9. Exception Handling digunakan untuk menangani kesalahan ketika program berjalan.
10. `try`, `except`, `else`, dan `finally` merupakan bagian dari mekanisme Exception Handling.
11. Keyword `raise` digunakan untuk menghasilkan exception secara manual.
12. File Handling dapat dikombinasikan dengan Function, List, Dictionary, dan perulangan untuk membangun aplikasi pengolahan data.

**Inti pembelajaran:** Program yang baik tidak hanya mampu mengolah data, tetapi juga mampu membaca data eksternal, menyimpan hasil pemrosesan, dan menangani kondisi kesalahan secara terstruktur.

## **18. Referensi Pembelajaran**

1. Python Software Foundation. *Reading and Writing Files*. [Python Official Documentation](https://docs.python.org/3/tutorial/inputoutput.html).
2. Python Software Foundation. *CSV File Reading and Writing*. [Python CSV Documentation](https://docs.python.org/3/library/csv.html).
3. Python Software Foundation. *Errors and Exceptions*. [Python Exception Handling Documentation](https://docs.python.org/3/tutorial/errors.html).
4. Matthes, E. (2023). *Python Crash Course*, 3rd Edition. No Starch Press.
