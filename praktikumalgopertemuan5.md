# **MODULE 5 – STRUKTUR DATA DAN MANIPULASI DATA PYTHON**

**Learning Module 05**

Materi praktikum

**Mata Kuliah:** Praktikum Algoritma dan Pemrograman

**Program Studi:** Teknik Elektro

**Topik:** Python Data Structures and Data Manipulation

**Bahasa Pemrograman:** Python 3.x

**Prasyarat:** Variabel, tipe data, operator, percabangan, dan perulangan.

## **1. Deskripsi Pembelajaran**

Dalam pemrograman, data merupakan komponen utama yang digunakan untuk menjalankan proses komputasi. Pada aplikasi sederhana, data mungkin hanya terdiri dari satu atau dua variabel. Namun, dalam aplikasi yang lebih kompleks, program perlu mengelola banyak data sekaligus.

Sebagai contoh, sebuah sistem pengukuran listrik dapat menghasilkan puluhan hingga ribuan data tegangan, arus, suhu, dan resistansi. Menyimpan setiap hasil pengukuran dalam variabel yang berbeda tentu tidak efisien.

Python menyediakan beberapa struktur data untuk mengorganisasi sekumpulan nilai secara sistematis.

Pada materi ini, mahasiswa akan mempelajari empat struktur data utama:

1. List.
2. Tuple.
3. Dictionary.
4. Set.

Selain itu, mahasiswa akan mempelajari teknik manipulasi data, seperti indexing, slicing, iterasi, penambahan, penghapusan, pencarian, dan pengurutan data.

## **2. Capaian Pembelajaran**

Setelah mempelajari materi ini, mahasiswa diharapkan mampu:

1. Menjelaskan konsep dan fungsi struktur data dalam Python.
2. Membedakan karakteristik List, Tuple, Dictionary, dan Set.
3. Membuat dan mengakses elemen dalam struktur data.
4. Melakukan manipulasi data menggunakan berbagai metode Python.
5. Mengimplementasikan iterasi, pencarian, dan pengurutan data.
6. Mengolah kumpulan data hasil pengukuran dalam bidang Teknik Elektro.
7. Memilih struktur data yang tepat berdasarkan kebutuhan suatu program.

## **3. Konsep Dasar Struktur Data**

Struktur data merupakan cara untuk mengorganisasi dan menyimpan data agar dapat diakses serta dimanipulasi secara efektif.

Dalam Python, struktur data bawaan yang umum digunakan adalah:

| Struktur Data | Karakteristik                       | Mutable |
| ------------- | ----------------------------------- | ------- |
| List          | Berurutan, dapat memiliki duplikasi | Ya      |
| Tuple         | Berurutan, dapat memiliki duplikasi | Tidak   |
| Dictionary    | Menyimpan pasangan key-value        | Ya      |
| Set           | Menyimpan elemen unik               | Ya      |

*Mutable* berarti objek dapat diubah setelah dibuat, sedangkan *immutable* berarti objek tidak dapat diubah setelah dibuat.

Contoh sederhana:

```
tegangan = [220, 221, 219, 222]data_sensor = (220, 221, 219, 222)sensor = {    "tegangan": 220,    "arus": 5}kanal = {1, 2, 3, 3, 4}
```

Keempat variabel tersebut memiliki bentuk penyimpanan data yang berbeda.

## **4. List dalam Python**

### **4.1 Pengertian List**

List merupakan struktur data yang digunakan untuk menyimpan sekumpulan elemen dalam satu variabel.

List memiliki karakteristik:

- Memiliki urutan elemen.
- Dapat diakses menggunakan indeks.
- Dapat menyimpan data dengan tipe berbeda.
- Mengizinkan elemen duplikat.
- Dapat diubah setelah dibuat.

List ditulis menggunakan tanda kurung siku `[]`.

Contoh:

```
tegangan = [220, 221, 219, 222, 218]print(tegangan)
```

Output:

```
[220, 221, 219, 222, 218]
```

Variabel `tegangan` menyimpan lima nilai pengukuran dalam satu objek List.

### **4.2 Membuat List**

List dapat dibuat dengan berbagai tipe data.

**List numerik:**

```
arus = [2.5, 3.0, 4.2, 3.8]
```

**List string:**

```
nama_sensor = ["Sensor A", "Sensor B", "Sensor C"]
```

**List campuran:**

```
data = [220, 5.2, "Normal", True]
```

**List kosong:**

```
hasil_pengukuran = []
```

List kosong sering digunakan ketika data akan ditambahkan secara bertahap selama program berjalan.

### **4.3 Indexing**

Indexing merupakan teknik untuk mengakses elemen berdasarkan posisi indeks.

Dalam Python, indeks dimulai dari angka 0.

Contoh:

```
tegangan = [220, 221, 219, 222, 218]print(tegangan[0])print(tegangan[1])print(tegangan[2])
```

Output:

```
220
221
219
```

Ilustrasi indeks:

| Index | Nilai |
| ----- | ----- |
| 0     | 220   |
| 1     | 221   |
| 2     | 219   |
| 3     | 222   |
| 4     | 218   |

Python juga mendukung negative indexing.

```
print(tegangan[-1])print(tegangan[-2])
```

Output:

```
218
222
```

Indeks negatif dimulai dari belakang, dengan `-1` menunjukkan elemen terakhir.

### **4.4 Slicing**

Slicing digunakan untuk mengambil sebagian elemen dari sebuah List.

Sintaks:

```
list[start:stop:step]
```

Keterangan:

- `start`: Indeks awal.
- `stop`: Batas akhir yang tidak disertakan.
- `step`: Interval pengambilan elemen.

Contoh:

```
tegangan = [220, 221, 219, 222, 218]print(tegangan[1:4])
```

Output:

```
[221, 219, 222]
```

Contoh lainnya:

```
print(tegangan[:3])print(tegangan[2:])print(tegangan[::2])
```

Output:

```
[220, 221, 219]
[219, 222, 218]
[220, 219, 218]
```

### **4.5 Menambahkan Elemen List**

Python menyediakan beberapa metode untuk menambahkan elemen.

**Append()**

Menambahkan satu elemen pada akhir List.

```
tegangan = [220, 221, 219]tegangan.append(223)print(tegangan)
```

Output:

```
[220, 221, 219, 223]
```

**Insert()**

Menambahkan elemen pada posisi indeks tertentu.

```
tegangan = [220, 221, 219]tegangan.insert(1, 225)print(tegangan)
```

Output:

```
[220, 225, 221, 219]
```

**Extend()**

Menambahkan beberapa elemen dari iterable lain.

```
tegangan = [220, 221]data_baru = [219, 222, 218]tegangan.extend(data_baru)print(tegangan)
```

Output:

```
[220, 221, 219, 222, 218]
```

### **4.6 Menghapus Elemen List**

**Remove()**

Menghapus elemen berdasarkan nilainya.

```
arus = [2, 3, 4, 5]arus.remove(3)print(arus)
```

Output:

```
[2, 4, 5]
```

**Pop()**

Menghapus elemen berdasarkan indeks dan mengembalikan nilai yang dihapus.

```
arus = [2, 3, 4, 5]nilai = arus.pop(1)print("Nilai dihapus:", nilai)print("Data:", arus)
```

Output:

```
Nilai dihapus: 3
Data: [2, 4, 5]
```

**Del**

Menghapus elemen berdasarkan indeks.

```
arus = [2, 3, 4, 5]del arus[0]print(arus)
```

Output:

```
[3, 4, 5]
```

### **4.7 Mengolah List dengan Fungsi Bawaan**

Python memiliki sejumlah fungsi untuk membantu pengolahan data numerik.

| Fungsi     | Kegunaan                          |
| ---------- | --------------------------------- |
| `len()`    | Menghitung jumlah elemen          |
| `sum()`    | Menghitung total nilai numerik    |
| `min()`    | Mendapatkan nilai minimum         |
| `max()`    | Mendapatkan nilai maksimum        |
| `sorted()` | Menghasilkan data terurut         |
| `list()`   | Mengonversi iterable menjadi List |

Contoh:

```
tegangan = [220, 221, 219, 222, 218]print("Jumlah data:", len(tegangan))print("Total:", sum(tegangan))print("Minimum:", min(tegangan))print("Maksimum:", max(tegangan))print("Rata-rata:", sum(tegangan) / len(tegangan))
```

Output:

```
Jumlah data: 5
Total: 1100
Minimum: 218
Maksimum: 222
Rata-rata: 220.0
```

### **4.8 Sorting pada List**

Sorting merupakan proses mengurutkan elemen berdasarkan nilai tertentu.

Python menyediakan dua pendekatan utama.

**Sort()**

Mengurutkan List secara langsung.

```
tegangan = [220, 218, 223, 219, 221]tegangan.sort()print(tegangan)
```

Output:

```
[218, 219, 220, 221, 223]
```

Untuk mengurutkan secara menurun:

```
tegangan.sort(reverse=True)print(tegangan)
```

Output:

```
[223, 221, 220, 219, 218]
```

**Sorted()**

Menghasilkan List baru tanpa mengubah urutan objek asli.

```
tegangan = [220, 218, 223, 219, 221]hasil = sorted(tegangan)print("Data asli:", tegangan)print("Data terurut:", hasil)
```

Output:

```
Data asli: [220, 218, 223, 219, 221]
Data terurut: [218, 219, 220, 221, 223]
```

## **5. Tuple dalam Python**

### **5.1 Pengertian Tuple**

Tuple merupakan struktur data yang digunakan untuk menyimpan sekumpulan elemen secara berurutan, tetapi elemennya tidak dapat diubah setelah Tuple dibuat.

Karakteristik Tuple:

- Memiliki urutan.
- Dapat memiliki elemen duplikat.
- Mendukung indexing dan slicing.
- Tidak dapat dimodifikasi secara langsung.
- Ditulis menggunakan tanda kurung `()`.

Contoh:

```
data_sensor = (220, 5.2, 25.5)print(data_sensor)
```

Output:

```
(220, 5.2, 25.5)
```

### **5.2 Mengakses Elemen Tuple**

Sama seperti List, Tuple menggunakan indeks yang dimulai dari 0.

```
data = (220, 5.2, 25.5)print(data[0])print(data[1])print(data[2])
```

Output:

```
220
5.2
25.5
```

### **5.3 Tuple Tidak Dapat Diubah**

Contoh:

```
tegangan = (220, 221, 219)tegangan[0] = 230
```

Program akan menghasilkan `TypeError` karena elemen Tuple tidak dapat diubah.

Jika diperlukan perubahan, data dapat dikonversi menjadi List terlebih dahulu.

```
tegangan = (220, 221, 219)data_baru = list(tegangan)data_baru[0] = 230tegangan = tuple(data_baru)print(tegangan)
```

Output:

```
(230, 221, 219)
```

### **5.4 Kapan Menggunakan Tuple?**

Tuple cocok digunakan untuk menyimpan data yang sifatnya tetap atau tidak perlu dimodifikasi selama program berjalan.

Contoh:

```
parameter_sensor = ("Tegangan", "Volt", 0, 250)print("Nama parameter:", parameter_sensor[0])print("Satuan:", parameter_sensor[1])print("Batas minimum:", parameter_sensor[2])print("Batas maksimum:", parameter_sensor[3])
```

Tuple membantu menjaga sekumpulan informasi agar tidak berubah secara tidak sengaja.

## **6. Dictionary dalam Python**

### **6.1 Pengertian Dictionary**

Dictionary merupakan struktur data yang menyimpan data dalam bentuk pasangan `key-value`.

Berbeda dengan List yang mengakses data menggunakan indeks numerik, Dictionary menggunakan key sebagai identitas untuk mengakses nilai.

Dictionary ditulis menggunakan tanda kurung kurawal `{}`.

Contoh:

```
sensor = {    "tegangan": 220,    "arus": 5.2,    "resistansi": 42.3}print(sensor)
```

Output:

```
{'tegangan': 220, 'arus': 5.2, 'resistansi': 42.3}
```

### **6.2 Mengakses Data Dictionary**

Data dapat diakses menggunakan key.

```
sensor = {    "tegangan": 220,    "arus": 5.2,    "resistansi": 42.3}print(sensor["tegangan"])print(sensor["arus"])
```

Output:

```
220
5.2
```

Alternatif lainnya adalah menggunakan metode `get()`.

```
print(sensor.get("tegangan"))print(sensor.get("daya", "Data tidak tersedia"))
```

Metode `get()` dapat memberikan nilai default jika key tidak ditemukan.

### **6.3 Menambahkan dan Mengubah Data**

Menambahkan elemen baru:

```
sensor = {    "tegangan": 220,    "arus": 5.2}sensor["daya"] = 1144print(sensor)
```

Output:

```
{'tegangan': 220, 'arus': 5.2, 'daya': 1144}
```

Mengubah nilai:

```
sensor["tegangan"] = 230print(sensor)
```

Output:

```
{'tegangan': 230, 'arus': 5.2, 'daya': 1144}
```

### **6.4 Menghapus Data Dictionary**

Menggunakan `pop()`:

```
sensor = {    "tegangan": 220,    "arus": 5.2,    "daya": 1144}sensor.pop("daya")print(sensor)
```

Menggunakan `del`:

```
del sensor["arus"]print(sensor)
```

### **6.5 Iterasi Dictionary**

Python menyediakan metode untuk melakukan iterasi terhadap Dictionary.

**keys():**

```
sensor = {    "tegangan": 220,    "arus": 5.2,    "daya": 1144}for key in sensor.keys():    print(key)
```

**values():**

```
for nilai in sensor.values():    print(nilai)
```

**items():**

```
for key, nilai in sensor.items():    print(key, ":", nilai)
```

Output:

```
tegangan : 220
arus : 5.2
daya : 1144
```

### **6.6 Nested Dictionary**

Dictionary dapat berisi Dictionary lainnya.

Contoh:

```
data_sensor = {    "sensor_1": {        "tegangan": 220,        "arus": 5.2    },    "sensor_2": {        "tegangan": 230,        "arus": 4.8    }}print(data_sensor["sensor_1"]["tegangan"])print(data_sensor["sensor_2"]["arus"])
```

Output:

```
220
4.8
```

Struktur ini berguna untuk mengelola banyak sensor dengan atribut yang berbeda.

## **7. Set dalam Python**

### **7.1 Pengertian Set**

Set merupakan struktur data yang digunakan untuk menyimpan kumpulan elemen unik.

Karakteristik Set:

- Tidak menyimpan elemen duplikat.
- Tidak memiliki indeks.
- Tidak menjamin urutan elemen.
- Mendukung operasi himpunan.
- Dapat ditambah dan dikurangi elemennya.

Set ditulis menggunakan tanda kurung kurawal `{}`.

Contoh:

```
sensor_id = {1, 2, 3, 3, 4, 4}print(sensor_id)
```

Output:

```
{1, 2, 3, 4}
```

Elemen yang sama secara otomatis hanya disimpan satu kali.

### **7.2 Menambahkan Elemen Set**

Menggunakan `add()`:

```
sensor_id = {1, 2, 3}sensor_id.add(4)print(sensor_id)
```

Menggunakan `update()`:

```
sensor_id.update([5, 6, 7])print(sensor_id)
```

### **7.3 Menghapus Elemen Set**

Menggunakan `remove()`:

```
sensor_id = {1, 2, 3, 4}sensor_id.remove(2)print(sensor_id)
```

Perlu diperhatikan bahwa `remove()` menghasilkan `KeyError` jika elemen yang dicari tidak ditemukan.

Alternatifnya, gunakan `discard()` yang tidak menghasilkan error jika elemen tidak ada.

### **7.4 Operasi Himpunan pada Set**

Set mendukung beberapa operasi matematis.

Misalnya:

```
sensor_a = {1, 2, 3, 4}sensor_b = {3, 4, 5, 6}
```

**Union (Gabungan):**

```
print(sensor_a | sensor_b)
```

Hasilnya adalah seluruh elemen unik dari kedua himpunan.

**Intersection (Irisan):**

```
print(sensor_a & sensor_b)
```

Hasilnya adalah elemen yang terdapat pada kedua himpunan.

**Difference (Selisih):**

```
print(sensor_a - sensor_b)
```

Hasilnya adalah elemen yang terdapat pada `sensor_a`, tetapi tidak terdapat pada `sensor_b`.

**Symmetric Difference:**

```
print(sensor_a ^ sensor_b)
```

Hasilnya adalah elemen yang hanya terdapat pada salah satu himpunan.

## **8. Perbandingan List, Tuple, Dictionary, dan Set**

| Aspek        | List          | Tuple      | Dictionary                        | Set           |
| ------------ | ------------- | ---------- | --------------------------------- | ------------- |
| Simbol       | `[]`          | `()`       | `{key: value}`                    | `{}`          |
| Berurutan    | Ya            | Ya         | Ya, berdasarkan urutan penyisipan | Tidak dijamin |
| Mutable      | Ya            | Tidak      | Ya                                | Ya            |
| Duplikasi    | Ya            | Ya         | Key tidak boleh duplikat          | Tidak         |
| Akses indeks | Ya            | Ya         | Tidak menggunakan indeks          | Tidak         |
| Penggunaan   | Kumpulan data | Data tetap | Data berpasangan                  | Data unik     |

Catatan: Dictionary pada Python modern mempertahankan urutan penyisipan key. Set tidak menjamin urutan elemen.

**Pedoman pemilihan struktur data:**

- Gunakan List ketika data perlu disimpan dan dimodifikasi secara berurutan.
- Gunakan Tuple ketika data bersifat tetap.
- Gunakan Dictionary ketika data memiliki atribut atau pasangan key-value.
- Gunakan Set ketika membutuhkan elemen unik atau operasi himpunan.

## **9. Manipulasi dan Pengolahan Data**

Setelah memahami berbagai struktur data, langkah selanjutnya adalah mengolah data tersebut.

### **9.1 Iterasi Data**

Iterasi digunakan untuk membaca setiap elemen dalam struktur data.

Contoh:

```
tegangan = [220, 221, 219, 222, 218]for nilai in tegangan:    print(nilai)
```

### **9.2 Menghitung Rata-Rata**

```
tegangan = [220, 221, 219, 222, 218]total = 0for nilai in tegangan:    total += nilairata_rata = total / len(tegangan)print("Rata-rata:", rata_rata)
```

Output:

```
Rata-rata: 220.0
```

### **9.3 Filtering Data**

Filtering merupakan proses memilih data yang memenuhi kondisi tertentu.

Contoh: mengambil nilai tegangan di atas 220 V.

```
tegangan = [218, 220, 225, 230, 215, 222]hasil = []for nilai in tegangan:    if nilai > 220:        hasil.append(nilai)print(hasil)
```

Output:

```
[225, 230, 222]
```

Python juga mendukung List Comprehension.

```
hasil = [nilai for nilai in tegangan if nilai > 220]print(hasil)
```

Hasilnya sama, tetapi penulisannya lebih ringkas.

### **9.4 Menghitung Frekuensi Kemunculan**

Metode `count()` dapat digunakan untuk menghitung berapa kali nilai tertentu muncul.

```
status = ["Normal", "Normal", "Tinggi", "Rendah", "Normal"]jumlah_normal = status.count("Normal")print("Jumlah status normal:", jumlah_normal)
```

Output:

```
Jumlah status normal: 3
```

### **9.5 Menggunakan Enumerate()**

`enumerate()` digunakan untuk mendapatkan indeks dan nilai sekaligus ketika melakukan iterasi.

```
tegangan = [220, 221, 219, 222]for index, nilai in enumerate(tegangan):    print("Data ke-", index + 1, ":", nilai)
```

Output:

```
Data ke- 1 : 220
Data ke- 2 : 221
Data ke- 3 : 219
Data ke- 4 : 222
```

### **9.6 Menggunakan Zip()**

`zip()` digunakan untuk menggabungkan beberapa iterable berdasarkan posisi elemennya.

Contoh:

```
tegangan = [220, 221, 219]arus = [2.5, 3.0, 2.8]for v, i in zip(tegangan, arus):    daya = v * i    print("Tegangan:", v)    print("Arus:", i)    print("Daya:", daya)    print("----------------")
```

Contoh ini menunjukkan bagaimana dua kumpulan data dapat diproses secara bersamaan.

## **10. Studi Kasus Penerapan dalam Teknik Elektro**

Bagian ini menggabungkan konsep struktur data dan manipulasi data untuk menyelesaikan permasalahan sederhana dalam bidang Teknik Elektro.

### **Studi Kasus 1: Pengolahan Data Pengukuran Tegangan**

Sebuah eksperimen menghasilkan data pengukuran tegangan sebanyak sepuluh kali.

Data yang diperoleh:

```
tegangan = [218, 220, 221, 219, 223,            225, 217, 222, 224, 220]
```

Program diminta untuk menghitung:

1. Jumlah data pengukuran.
2. Nilai rata-rata.
3. Nilai minimum.
4. Nilai maksimum.
5. Data yang memiliki nilai di atas rata-rata.

Implementasi:

```
tegangan = [218, 220, 221, 219, 223,            225, 217, 222, 224, 220]jumlah = len(tegangan)rata_rata = sum(tegangan) / jumlahminimum = min(tegangan)maksimum = max(tegangan)di_atas_rata = []for nilai in tegangan:    if nilai > rata_rata:        di_atas_rata.append(nilai)print("Jumlah pengukuran:", jumlah)print("Rata-rata:", rata_rata)print("Minimum:", minimum)print("Maksimum:", maksimum)print("Di atas rata-rata:", di_atas_rata)
```

Output:

```
Jumlah pengukuran: 10
Rata-rata: 220.9
Minimum: 217
Maksimum: 225
Di atas rata-rata: [221, 223, 225, 222, 224]
```

**Analisis:**

Program menggunakan List untuk menyimpan data, fungsi bawaan untuk menghitung statistik sederhana, serta perulangan dan percabangan untuk melakukan filtering.

### **Studi Kasus 2: Pengelolaan Data Beberapa Sensor**

Sebuah sistem monitoring memiliki tiga sensor dengan masing-masing data tegangan, arus, dan suhu.

Data disimpan menggunakan Dictionary.

```
sensor = {    "sensor_1": {        "tegangan": 220,        "arus": 2.5,        "suhu": 30    },    "sensor_2": {        "tegangan": 225,        "arus": 3.0,        "suhu": 35    },    "sensor_3": {        "tegangan": 218,        "arus": 2.8,        "suhu": 32    }}for nama, data in sensor.items():    daya = data["tegangan"] * data["arus"]    print("Nama:", nama)    print("Tegangan:", data["tegangan"], "Volt")    print("Arus:", data["arus"], "Ampere")    print("Suhu:", data["suhu"], "Celsius")    print("Daya:", daya, "Watt")    print("----------------------")
```

Output:

```
Nama: sensor_1
Tegangan: 220 Volt
Arus: 2.5 Ampere
Suhu: 30 Celsius
Daya: 550.0 Watt
----------------------
Nama: sensor_2
Tegangan: 225 Volt
Arus: 3.0 Ampere
Suhu: 35 Celsius
Daya: 675.0 Watt
----------------------
Nama: sensor_3
Tegangan: 218 Volt
Arus: 2.8 Ampere
Suhu: 32 Celsius
Daya: 610.4 Watt
----------------------
```

**Analisis:**

Penggunaan Nested Dictionary memungkinkan setiap sensor memiliki sejumlah atribut yang berbeda. Pendekatan ini cocok untuk aplikasi monitoring yang mengelola beberapa perangkat sekaligus.

### **Studi Kasus 3: Identifikasi Sensor Unik**

Sebuah sistem menerima daftar ID sensor dari beberapa perangkat. Beberapa ID tercatat lebih dari satu kali.

Program diminta mengidentifikasi jumlah sensor unik.

```
daftar_sensor = [    "S001", "S002", "S003",    "S001", "S004", "S002",    "S005", "S003"]sensor_unik = set(daftar_sensor)print("Seluruh data:", daftar_sensor)print("Sensor unik:", sensor_unik)print("Jumlah data:", len(daftar_sensor))print("Jumlah sensor unik:", len(sensor_unik))
```

Output jumlah:

```
Jumlah data: 8
Jumlah sensor unik: 5
```

**Analisis:**

Struktur Set secara otomatis menghilangkan duplikasi sehingga cocok digunakan untuk identifikasi elemen unik.

### **Studi Kasus 4: Pengolahan Data Pengukuran Terintegrasi**

Sebuah sistem melakukan pengukuran listrik menggunakan beberapa kanal. Data setiap kanal disimpan menggunakan Dictionary yang berisi List hasil pengukuran.

Program akan menghitung nilai rata-rata, minimum, maksimum, dan daya rata-rata setiap kanal.

```
data_kanal = {    "Kanal A": {        "tegangan": [220, 221, 219, 222],        "arus": [2.5, 2.6, 2.4, 2.5]    },    "Kanal B": {        "tegangan": [225, 226, 224, 223],        "arus": [3.0, 2.9, 3.1, 3.0]    }}for nama, data in data_kanal.items():    tegangan = data["tegangan"]    arus = data["arus"]    rata_v = sum(tegangan) / len(tegangan)    rata_i = sum(arus) / len(arus)    daya_rata = rata_v * rata_i    print("\n", nama)    print("Rata-rata tegangan:", rata_v)    print("Rata-rata arus:", rata_i)    print("Tegangan minimum:", min(tegangan))    print("Tegangan maksimum:", max(tegangan))    print("Estimasi daya:", daya_rata, "Watt")
```

**Analisis:**

Kasus ini menggabungkan beberapa konsep sekaligus:

- Dictionary untuk mengelompokkan data berdasarkan kanal.
- List untuk menyimpan hasil pengukuran.
- Iterasi untuk memproses setiap kanal.
- Fungsi `sum()`, `len()`, `min()`, dan `max()` untuk pengolahan data.
- Operasi aritmatika untuk menghitung estimasi daya.

Catatan: Perkalian rata-rata tegangan dan rata-rata arus merupakan estimasi berdasarkan nilai rata-rata masing-masing, bukan selalu sama dengan rata-rata daya sesaat. Untuk pengukuran daya yang lebih akurat, hitung daya pada setiap pasangan pengukuran terlebih dahulu.

## **11. Visualisasi Sederhana Data Pengukuran**

Struktur data Python dapat menjadi dasar pengolahan data sebelum divisualisasikan.

Salah satu pustaka yang dapat digunakan adalah Matplotlib.

Instalasi jika menggunakan lingkungan lokal:

```
pip install matplotlib
```

Contoh program:

```
import matplotlib.pyplot as pltwaktu = [1, 2, 3, 4, 5, 6]tegangan = [220, 221, 219, 222, 218, 223]plt.plot(waktu, tegangan, marker="o")plt.title("Grafik Pengukuran Tegangan")plt.xlabel("Pengukuran ke-")plt.ylabel("Tegangan (Volt)")plt.grid(True)plt.show()
```

[iAWE](https://images.openai.com/static-rsc-4/vYpd_CYHl_iAejO1rUqxMyK7zpzjE6oXJudzYftZmT55MH2SY2SKluK7sUkPFYF7fGR5uSh9wytAa6QGC4PUlGHMJ2PVBTrOztp-EIaP33G_5xAsoSWM31uNEZQRDaOnmuvCn8SbyvUovVZ8_IMEqo5L4wQ9fJOwYYigGjl2h3s?purpose=inline)

[iawe.github.io](https://iawe.github.io/?utm_source=chatgpt.com)

**Penjelasan:**

- `waktu` menyimpan urutan pengukuran.
- `tegangan` menyimpan nilai hasil pengukuran.
- `plt.plot()` digunakan untuk membentuk grafik.
- `plt.xlabel()` dan `plt.ylabel()` memberikan label sumbu.
- `plt.show()` menampilkan grafik.

Visualisasi membantu pengguna memahami perubahan nilai pengukuran berdasarkan waktu atau urutan pengambilan data.

## **12. Kesalahan Umum dalam Penggunaan Struktur Data**

| Kesalahan          | Penyebab                                  | Solusi                                    |
| ------------------ | ----------------------------------------- | ----------------------------------------- |
| IndexError         | Mengakses indeks yang tidak tersedia      | Periksa panjang List                      |
| KeyError           | Key Dictionary tidak ditemukan            | Gunakan `get()` atau validasi key         |
| TypeError          | Mengubah elemen Tuple                     | Gunakan List jika data perlu dimodifikasi |
| ValueError         | Data tidak sesuai dengan operasi          | Periksa tipe dan isi data                 |
| Key duplikat       | Menggunakan key yang sama pada Dictionary | Gunakan key yang unik                     |
| Data tidak terurut | Menganggap Set memiliki urutan tetap      | Gunakan List jika urutan diperlukan       |

### **Perhatian: Shallow Copy dan Aliasing**

Dalam Python, penugasan List ke variabel lain tidak otomatis membuat salinan independen.

Contoh:

```
data_a = [220, 221, 222]data_b = data_adata_b[0] = 230print(data_a)print(data_b)
```

Output:

```
[230, 221, 222]
[230, 221, 222]
```

Kedua variabel merujuk pada objek List yang sama.

Jika ingin membuat salinan sederhana:

```
data_a = [220, 221, 222]data_b = data_a.copy()data_b[0] = 230print(data_a)print(data_b)
```

Output:

```
[220, 221, 222]
[230, 221, 222]
```

Pemahaman ini penting agar mahasiswa tidak mengalami perubahan data yang tidak disengaja ketika mengembangkan program.

## **13. Rangkuman Materi**

Struktur data merupakan bagian penting dalam pengembangan program karena memungkinkan pengelolaan sekumpulan data secara sistematis.

Materi ini membahas empat struktur data utama:

1. **List:** menyimpan data berurutan dan dapat dimodifikasi.
2. **Tuple:** menyimpan data berurutan yang tidak dapat dimodifikasi.
3. **Dictionary:** menyimpan data dalam bentuk pasangan key-value.
4. **Set:** menyimpan elemen unik tanpa menjamin urutan.

Selain itu, mahasiswa telah mempelajari berbagai teknik manipulasi data, seperti indexing, slicing, iterasi, filtering, sorting, dan operasi himpunan.

Dalam bidang Teknik Elektro, struktur data dapat digunakan untuk mengelola hasil pengukuran, mengorganisasi data sensor, melakukan analisis parameter listrik, dan menyiapkan data untuk visualisasi.

Penguasaan materi ini menjadi dasar untuk mempelajari Function dan Modularisasi Program pada pertemuan selanjutnya.

## **14. Referensi Pembelajaran**

1. Python Software Foundation. *Data Structures – Python Tutorial*. [https://docs.python.org/3/tutorial/datastructures.html](https://docs.python.org/3/tutorial/datastructures.html)
2. Python Software Foundation. *Built-in Types*. [https://docs.python.org/3/library/stdtypes.html](https://docs.python.org/3/library/stdtypes.html)
3. Python Software Foundation. *Built-in Functions*. [https://docs.python.org/3/library/functions.html](https://docs.python.org/3/library/functions.html)
4. McKinney, W. (2022). *Python for Data Analysis*, 3rd Edition. O'Reilly Media.

