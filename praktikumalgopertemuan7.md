# **MODULE 7**

# **ALGORITMA PENCARIAN DAN PENGURUTAN DATA PYTHON**

Pertemuan 7

Praktikum Algoritma dan Pemrograman

Program Studi Teknik Elektro

## **1. Deskripsi Materi**

Dalam pemrograman, data sering kali disimpan dalam jumlah yang cukup banyak. Data tersebut perlu diolah agar informasi yang dibutuhkan dapat ditemukan dengan cepat dan disajikan secara terstruktur.

Dua operasi dasar yang sering digunakan dalam pengolahan data adalah:

1. **Searching (pencarian):** proses menemukan data tertentu dari sekumpulan data.
2. **Sorting (pengurutan):** proses menyusun data berdasarkan urutan tertentu, misalnya dari nilai terkecil ke terbesar atau sebaliknya.

Pada pertemuan ini, mahasiswa akan mempelajari beberapa algoritma dasar, yaitu Linear Search, Binary Search, Bubble Sort, dan Selection Sort. Implementasinya menggunakan Python agar mahasiswa dapat memahami proses algoritma sekaligus melihat bagaimana setiap langkah bekerja.

## **2. Capaian Pembelajaran**

Setelah menyelesaikan materi ini, mahasiswa diharapkan mampu:

1. Menjelaskan konsep dasar algoritma pencarian dan pengurutan.
2. Mengimplementasikan Linear Search menggunakan Python.
3. Mengimplementasikan Binary Search pada data terurut.
4. Menjelaskan perbedaan Linear Search dan Binary Search.
5. Mengimplementasikan Bubble Sort.
6. Mengimplementasikan Selection Sort.
7. Membandingkan cara kerja dan efisiensi algoritma dasar.
8. Menerapkan algoritma pencarian dan pengurutan pada data pengukuran Teknik Elektro.

## **3. Konsep Dasar Searching**

### **3.1 Pengertian Searching**

Searching adalah proses mencari keberadaan suatu nilai atau elemen dalam kumpulan data.

Misalnya, sebuah sistem monitoring listrik memiliki data hasil pengukuran tegangan:

```
tegangan = [218, 220, 215, 225, 219, 230, 217]
```

Kita ingin mengetahui apakah nilai tegangan 225 terdapat dalam data tersebut.

Proses pencarian dapat dilakukan dengan membandingkan nilai yang dicari dengan setiap elemen data atau menggunakan algoritma tertentu.

Dua algoritma pencarian yang akan dipelajari adalah:

- Linear Search.
- Binary Search.

## **4. Linear Search**

### **4.1 Pengertian Linear Search**

Linear Search merupakan algoritma pencarian yang bekerja dengan memeriksa elemen data satu per satu, dimulai dari elemen pertama hingga nilai yang dicari ditemukan atau seluruh data selesai diperiksa.

Algoritma ini dapat digunakan pada data yang belum diurutkan.

### **4.2 Cara Kerja Linear Search**

Misalnya terdapat data:

```
data = [12, 18, 25, 30, 42, 50]
```

Kita ingin mencari nilai `30`.

Proses pencarian:

**Ilustrasi proses Linear Search**

Nilai yang dicari: 30

**12**

Indeks 0

Tidak cocok

**18**

Indeks 1

Tidak cocok

**25**

Indeks 2

Tidak cocok

**30**

Indeks 3

Ditemukan

**42**

Indeks 4

Tidak diperiksa

**50**

Indeks 5

Tidak diperiksa

Proses berhenti ketika nilai 30 ditemukan pada indeks ke-3.

Tahapan algoritma:

1. Mulai dari indeks pertama.
2. Bandingkan elemen dengan nilai yang dicari.
3. Jika sama, pencarian berhasil.
4. Jika berbeda, lanjutkan ke elemen berikutnya.
5. Jika seluruh data telah diperiksa dan tidak ditemukan, pencarian dinyatakan gagal.

### **4.3 Implementasi Linear Search**

```
def linear_search(data, target):    for i in range(len(data)):        if data[i] == target:            return i    return -1tegangan = [218, 220, 215, 225, 219, 230, 217]target = 225hasil = linear_search(tegangan, target)if hasil != -1:    print("Data ditemukan pada indeks:", hasil)else:    print("Data tidak ditemukan")
```

Output:

```
Data ditemukan pada indeks: 3
```

Penjelasan:

- `data` merupakan kumpulan elemen yang akan diperiksa.
- `target` merupakan nilai yang ingin ditemukan.
- `range(len(data))` menghasilkan indeks seluruh elemen.
- `return i` mengembalikan indeks ketika nilai ditemukan.
- `return -1` menunjukkan bahwa nilai tidak ditemukan.

### **4.4 Linear Search Menggunakan Perulangan&#x20;**`for`

Alternatif lain adalah menggunakan perulangan langsung terhadap elemen data.

```
def linear_search(data, target):    for nilai in data:        if nilai == target:            return True    return Falsearus = [1.2, 1.5, 1.8, 2.1, 2.4]if linear_search(arus, 1.8):    print("Nilai arus ditemukan")else:    print("Nilai arus tidak ditemukan")
```

Output:

```
Nilai arus ditemukan
```

Pada implementasi ini, fungsi mengembalikan nilai Boolean (`True` atau `False`) untuk menunjukkan apakah data ditemukan.

### **4.5 Analisis Kompleksitas Linear Search**

Kompleksitas waktu Linear Search dapat dijelaskan sebagai berikut:

| Kondisi      | Jumlah pemeriksaan |
| ------------ | ------------------ |
| Best Case    | 1 kali             |
| Average Case | Sekitar n/2 kali   |
| Worst Case   | n kali             |

Notasi kompleksitas waktunya:

\\[ O(n) \\]

Artinya, jumlah pemeriksaan bertambah seiring dengan bertambahnya jumlah elemen data.

Jika terdapat 100 data, pada kondisi terburuk algoritma dapat melakukan hingga 100 kali pemeriksaan.

## **5. Binary Search**

### **5.1 Pengertian Binary Search**

Binary Search adalah algoritma pencarian yang bekerja dengan membagi ruang pencarian menjadi dua bagian secara berulang.

Berbeda dengan Linear Search, Binary Search **mensyaratkan data sudah dalam keadaan terurut**.

Algoritma ini membandingkan nilai target dengan elemen tengah (*middle element*). Berdasarkan hasil perbandingan, pencarian dilanjutkan hanya pada bagian kiri atau kanan.

### **5.2 Cara Kerja Binary Search**

Misalnya terdapat data terurut:

```
data = [10, 20, 30, 40, 50, 60, 70]
```

Kita ingin mencari nilai `60`.

**Ilustrasi pembagian ruang pencarian**

Target: 60

Langkah 1 — Periksa nilai tengah 40

**10**

**20**

**30**

**40**

**50**

**60**

**70**

60 lebih besar dari 40, lanjutkan ke bagian kanan.

Langkah 2 — Periksa bagian kanan, nilai tengah 60

**50**

**60**

**70**

Nilai 60 ditemukan.

Tahapan algoritma:

1. Tentukan batas kiri (*low*) dan batas kanan (*high*).
2. Hitung posisi tengah (*mid*).
3. Bandingkan nilai tengah dengan target.
4. Jika sama, pencarian berhasil.
5. Jika target lebih kecil, pindahkan batas kanan ke posisi sebelum tengah.
6. Jika target lebih besar, pindahkan batas kiri ke posisi setelah tengah.
7. Ulangi hingga nilai ditemukan atau ruang pencarian habis.

### **5.3 Implementasi Binary Search**

```
def binary_search(data, target):    low = 0    high = len(data) - 1    while low <= high:        mid = (low + high) // 2        if data[mid] == target:            return mid        elif data[mid] < target:            low = mid + 1        else:            high = mid - 1    return -1tegangan = [10, 20, 30, 40, 50, 60, 70]target = 60hasil = binary_search(tegangan, target)if hasil != -1:    print("Data ditemukan pada indeks:", hasil)else:    print("Data tidak ditemukan")
```

Output:

```
Data ditemukan pada indeks: 5
```

Penjelasan kode:

- `low` menyimpan batas awal pencarian.
- `high` menyimpan batas akhir pencarian.
- `mid` menyimpan posisi tengah.
- `//` merupakan operator pembagian bilangan bulat.
- `while low <= high` memastikan ruang pencarian masih tersedia.

### **5.4 Binary Search dengan Data Tidak Ditemukan**

```
data = [10, 20, 30, 40, 50, 60, 70]hasil = binary_search(data, 45)if hasil == -1:    print("Nilai tidak ditemukan")else:    print("Nilai ditemukan pada indeks:", hasil)
```

Output:

```
Nilai tidak ditemukan
```

### **5.5 Analisis Kompleksitas Binary Search**

Binary Search memiliki kompleksitas waktu:

\\[ O(\log n) \\]

Artinya, ruang pencarian berkurang sekitar setengah pada setiap iterasi.

Sebagai gambaran, jika terdapat 1.024 elemen, pencarian dapat selesai dalam sekitar 10 pembagian ruang pencarian pada kondisi terburuk.

Hal ini membuat Binary Search sangat efisien untuk data berukuran besar yang sudah terurut.

## **6. Perbandingan Linear Search dan Binary Search**

| Aspek              | Linear Search                 | Binary Search                    |
| ------------------ | ----------------------------- | -------------------------------- |
| Prinsip kerja      | Memeriksa satu per satu       | Membagi ruang pencarian          |
| Data harus terurut | Tidak                         | Ya                               |
| Kompleksitas waktu | O(n)                          | O(log n)                         |
| Implementasi       | Lebih sederhana               | Lebih kompleks                   |
| Cocok untuk        | Data kecil atau belum terurut | Data terurut dan berukuran besar |

**Kesimpulan:** Binary Search lebih efisien untuk pencarian pada data terurut, tetapi Linear Search lebih fleksibel karena tidak memerlukan proses pengurutan terlebih dahulu.

## **7. Konsep Dasar Sorting**

### **7.1 Pengertian Sorting**

Sorting merupakan proses mengurutkan elemen data berdasarkan aturan tertentu.

Pengurutan dapat dilakukan secara:

- **Ascending:** dari nilai terkecil ke terbesar.
- **Descending:** dari nilai terbesar ke terkecil.

Contoh:

```
data = [220, 215, 230, 218, 225]
```

Hasil ascending:

```
[215, 218, 220, 225, 230]
```

Hasil descending:

```
[230, 225, 220, 218, 215]
```

Dalam bidang Teknik Elektro, sorting dapat digunakan untuk:

- Mengurutkan hasil pengukuran tegangan.
- Menemukan nilai arus tertinggi dan terendah.
- Mengurutkan data sensor.
- Menyusun hasil pengujian komponen.
- Mengidentifikasi nilai pengukuran yang perlu dianalisis lebih lanjut.

## **8. Bubble Sort**

### **8.1 Pengertian Bubble Sort**

Bubble Sort adalah algoritma pengurutan sederhana yang bekerja dengan membandingkan dua elemen yang bersebelahan.

Jika urutannya tidak sesuai, kedua elemen tersebut akan ditukar (*swap*).

Proses ini dilakukan berulang kali sampai seluruh data berada dalam urutan yang benar.

### **8.2 Cara Kerja Bubble Sort**

Misalnya data:

```
data = [5, 3, 8, 2]
```

Proses pengurutan ascending:

**Ilustrasi Bubble Sort**

Data awal

**5**

**3**

**8**

**2**

Perbandingan pertama: 5 dan 3 → ditukar

**3**

**5**

**8**

**2**

Perbandingan berikutnya: 5 dan 8 → tidak ditukar

**3**

**5**

**8**

**2**

Perbandingan berikutnya: 8 dan 2 → ditukar

**3**

**5**

**2**

**8**

Setelah seluruh proses selesai

**2**

**3**

**5**

**8**

### **8.3 Implementasi Bubble Sort**

```
def bubble_sort(data):    n = len(data)    for i in range(n):        for j in range(0, n - i - 1):            if data[j] > data[j + 1]:                data[j], data[j + 1] = data[j + 1], data[j]    return datategangan = [220, 215, 230, 218, 225]hasil = bubble_sort(tegangan)print("Data setelah diurutkan:", hasil)
```

Output:

```
Data setelah diurutkan: [215, 218, 220, 225, 230]
```

Penjelasan:

- `n` merupakan jumlah elemen data.
- Perulangan luar menentukan jumlah putaran.
- Perulangan dalam membandingkan elemen yang bersebelahan.
- `data[j] > data[j + 1]` memeriksa apakah dua elemen perlu ditukar.
- `data[j], data[j + 1] = data[j + 1], data[j]` melakukan pertukaran nilai.

### **8.4 Bubble Sort Descending**

Untuk mengurutkan data dari terbesar ke terkecil, kondisi perbandingan dapat diubah.

```
def bubble_sort_desc(data):    n = len(data)    for i in range(n):        for j in range(0, n - i - 1):            if data[j] < data[j + 1]:                data[j], data[j + 1] = data[j + 1], data[j]    return dataarus = [2.1, 1.5, 3.2, 2.8, 1.9]print(bubble_sort_desc(arus))
```

Output:

```
[3.2, 2.8, 2.1, 1.9, 1.5]
```

### **8.5 Analisis Kompleksitas Bubble Sort**

Kompleksitas waktu Bubble Sort pada implementasi dasar:

\\[ O(n^2) \\]

Artinya, jumlah operasi perbandingan dapat meningkat secara kuadratik ketika jumlah data bertambah.

Bubble Sort mudah dipahami untuk pembelajaran algoritma, tetapi tidak efisien untuk mengurutkan data dalam jumlah besar.

## **9. Selection Sort**

### **9.1 Pengertian Selection Sort**

Selection Sort merupakan algoritma pengurutan yang bekerja dengan mencari elemen terkecil dari bagian data yang belum terurut, kemudian menempatkannya pada posisi yang benar.

Proses tersebut dilakukan berulang kali hingga seluruh data terurut.

### **9.2 Cara Kerja Selection Sort**

Misalnya terdapat data:

```
data = [64, 25, 12, 22, 11]
```

Langkah-langkah:

1. Cari nilai terkecil dari seluruh data, yaitu 11.
2. Tukar 11 dengan elemen pertama.
3. Cari nilai terkecil dari bagian data yang belum terurut.
4. Tempatkan nilai terkecil tersebut pada posisi berikutnya.
5. Ulangi hingga seluruh data terurut.

Ilustrasi:

**Proses Selection Sort**

Data awal

**64**

**25**

**12**

**22**

**11**

Putaran 1: nilai terkecil 11

**11**

**25**

**12**

**22**

**64**

Putaran 2: nilai terkecil 12

**11**

**12**

**25**

**22**

**64**

Putaran 3: nilai terkecil 22

**11**

**12**

**22**

**25**

**64**

Hasil akhir

**11**

**12**

**22**

**25**

**64**

Bagian berwarna hijau menunjukkan posisi yang sudah terurut.

### **9.3 Implementasi Selection Sort**

```
def selection_sort(data):    n = len(data)    for i in range(n):        min_index = i        for j in range(i + 1, n):            if data[j] < data[min_index]:                min_index = j        data[i], data[min_index] = data[min_index], data[i]    return datategangan = [220, 215, 230, 218, 225]hasil = selection_sort(tegangan)print("Data setelah diurutkan:", hasil)
```

Output:

```
Data setelah diurutkan: [215, 218, 220, 225, 230]
```

Penjelasan:

- `min_index` menyimpan posisi elemen terkecil sementara.
- Perulangan bagian dalam mencari elemen terkecil.
- Setelah ditemukan, elemen terkecil ditukar dengan elemen pada posisi `i`.
- Proses dilanjutkan ke posisi berikutnya.

### **9.4 Selection Sort Descending**

```
def selection_sort_desc(data):    n = len(data)    for i in range(n):        max_index = i        for j in range(i + 1, n):            if data[j] > data[max_index]:                max_index = j        data[i], data[max_index] = data[max_index], data[i]    return dataarus = [2.1, 1.5, 3.2, 2.8, 1.9]print(selection_sort_desc(arus))
```

Output:

```
[3.2, 2.8, 2.1, 1.9, 1.5]
```

### **9.5 Analisis Kompleksitas Selection Sort**

Kompleksitas waktu Selection Sort:

\\[ O(n^2) \\]

Selection Sort tetap melakukan pencarian elemen minimum pada bagian data yang belum terurut. Jumlah perbandingannya relatif konsisten, meskipun data awal sudah terurut.

## **10. Perbandingan Algoritma Sorting**

| Aspek              | Bubble Sort                       | Selection Sort                 |
| ------------------ | --------------------------------- | ------------------------------ |
| Prinsip kerja      | Membandingkan elemen bersebelahan | Mencari elemen terkecil        |
| Proses pertukaran  | Dapat terjadi berkali-kali        | Umumnya satu kali per putaran  |
| Kompleksitas waktu | O(n²)                             | O(n²)                          |
| Tingkat pemahaman  | Mudah                             | Mudah                          |
| Cocok untuk        | Pembelajaran proses pertukaran    | Pembelajaran pencarian minimum |

Perlu diketahui, Python sebenarnya telah menyediakan fungsi pengurutan bawaan yang jauh lebih praktis dan efisien untuk penggunaan sehari-hari, yaitu `sorted()` dan `list.sort()`.

Namun, Bubble Sort dan Selection Sort tetap perlu dipahami agar mahasiswa mengerti bagaimana algoritma pengurutan bekerja di balik sebuah program.

## **11. Fungsi Sorting Bawaan Python**

### **11.1 Menggunakan&#x20;**`sorted()`

Fungsi `sorted()` menghasilkan List baru yang sudah terurut tanpa mengubah List aslinya.

```
tegangan = [220, 215, 230, 218, 225]hasil = sorted(tegangan)print("Data asli:", tegangan)print("Data terurut:", hasil)
```

Output:

```
Data asli: [220, 215, 230, 218, 225]
Data terurut: [215, 218, 220, 225, 230]
```

### **11.2 Menggunakan&#x20;**`sort()`

Method `sort()` mengurutkan List secara langsung.

```
arus = [2.1, 1.5, 3.2, 2.8, 1.9]arus.sort()print(arus)
```

Output:

```
[1.5, 1.9, 2.1, 2.8, 3.2]
```

### **11.3 Mengurutkan Secara Descending**

Kita dapat menggunakan parameter `reverse=True`.

```
tegangan = [220, 215, 230, 218, 225]hasil = sorted(tegangan, reverse=True)print(hasil)
```

Output:

```
[230, 225, 220, 218, 215]
```

### **11.4 Mengurutkan Dictionary Berdasarkan Nilai**

Misalnya kita memiliki data pengukuran dari beberapa sensor:

```
sensor = {    "Sensor A": 220,    "Sensor B": 215,    "Sensor C": 230,    "Sensor D": 218}hasil = sorted(    sensor.items(),    key=lambda item: item[1])print(hasil)
```

Output:

```
[
    ('Sensor B', 215),
    ('Sensor D', 218),
    ('Sensor A', 220),
    ('Sensor C', 230)
]
```

Pada contoh tersebut:

- `sensor.items()` menghasilkan pasangan key dan value.
- `key=lambda item: item[1]` menentukan bahwa pengurutan dilakukan berdasarkan nilai pengukuran.
- Hasilnya berupa List berisi pasangan data sensor dan nilai tegangannya.

## **12. Studi Kasus Teknik Elektro: Analisis dan Pengurutan Data Tegangan**

### **12.1 Deskripsi Kasus**

Sebuah sistem monitoring listrik melakukan pengukuran tegangan pada beberapa titik. Data hasil pengukuran perlu dianalisis untuk mengetahui:

1. Nilai tegangan terendah.
2. Nilai tegangan tertinggi.
3. Urutan data tegangan dari terendah ke tertinggi.
4. Posisi pengukuran dengan nilai tertentu.
5. Jumlah data yang berada di atas nilai ambang yang ditentukan.

### **12.2 Implementasi Program**

```
def linear_search(data, target):    for i in range(len(data)):        if data[i] == target:            return i    return -1def bubble_sort(data):    data = data.copy()    n = len(data)    for i in range(n):        for j in range(n - i - 1):            if data[j] > data[j + 1]:                data[j], data[j + 1] = data[j + 1], data[j]    return datadef analisis_tegangan(data):    print("=== ANALISIS DATA TEGANGAN ===")    print("Data awal:", data)    print("Tegangan minimum:", min(data), "Volt")    print("Tegangan maksimum:", max(data), "Volt")    hasil_sort = bubble_sort(data)    print("Data terurut:", hasil_sort)    target = 225    posisi = linear_search(data, target)    if posisi != -1:
```

### **12.3 Output Program**

```
=== ANALISIS DATA TEGANGAN ===
Data awal: [220, 215, 230, 218, 225, 235, 210, 228]
Tegangan minimum: 210 Volt
Tegangan maksimum: 235 Volt
Data terurut: [210, 215, 218, 220, 225, 228, 230, 235]
Tegangan 225 Volt ditemukan pada indeks: 4
Jumlah pengukuran di atas 225 Volt: 3
```

### **12.4 Analisis Program**

Program tersebut menggabungkan beberapa konsep yang telah dipelajari:

- Function digunakan untuk membagi program menjadi beberapa bagian.
- Linear Search digunakan untuk mencari nilai pengukuran.
- Bubble Sort digunakan untuk mengurutkan data.
- Perulangan digunakan untuk menghitung jumlah data berdasarkan kondisi tertentu.
- List digunakan sebagai tempat penyimpanan hasil pengukuran.

Perlu diperhatikan bahwa nilai ambang 225 Volt pada contoh ini hanya digunakan sebagai parameter simulasi pembelajaran, bukan standar universal untuk menentukan keamanan atau kualitas tegangan listrik.

## **13. Praktik Eksperimen Algoritma**

Untuk membantu mahasiswa memahami perbedaan algoritma, kita dapat menambahkan pencatatan jumlah perbandingan.

### **13.1 Menghitung Perbandingan Linear Search**

```
def linear_search_count(data, target):    jumlah_perbandingan = 0    for i in range(len(data)):        jumlah_perbandingan += 1        if data[i] == target:            return i, jumlah_perbandingan    return -1, jumlah_perbandingandata = [10, 20, 30, 40, 50, 60, 70, 80]posisi, jumlah = linear_search_count(data, 80)print("Posisi:", posisi)print("Jumlah perbandingan:", jumlah)
```

Output:

```
Posisi: 7
Jumlah perbandingan: 8
```

### **13.2 Menghitung Perbandingan Binary Search**

```
def binary_search_count(data, target):    low = 0    high = len(data) - 1    jumlah_perbandingan = 0    while low <= high:        mid = (low + high) // 2        jumlah_perbandingan += 1        if data[mid] == target:            return mid, jumlah_perbandingan        elif data[mid] < target:            low = mid + 1        else:            high = mid - 1    return -1, jumlah_perbandingandata = [10, 20, 30, 40, 50, 60, 70, 80]posisi, jumlah = binary_search_count(data, 80)print("Posisi:", posisi)print("Jumlah perbandingan:", jumlah)
```

Output:

```
Posisi: 7
Jumlah perbandingan: 4
```

### **13.3 Analisis Eksperimen**

Pada contoh tersebut, Linear Search membutuhkan delapan kali perbandingan untuk menemukan nilai 80, sedangkan Binary Search hanya membutuhkan empat kali perbandingan.

Hasil ini memperlihatkan bagaimana pemilihan algoritma dapat memengaruhi jumlah operasi yang dilakukan oleh program.

Jumlah perbandingan tersebut merupakan hasil untuk data dan target pada contoh, bukan angka yang selalu berlaku untuk setiap kondisi.

## **14. Kesalahan Umum dalam Searching dan Sorting**

| Kesalahan                          | Penyebab                     | Solusi                                      |
| ---------------------------------- | ---------------------------- | ------------------------------------------- |
| Binary Search tidak menemukan data | Data belum terurut           | Urutkan data terlebih dahulu                |
| Indeks hasil tidak sesuai          | Salah memahami indeks Python | Ingat indeks dimulai dari 0                 |
| Sorting mengubah data asli         | Menggunakan `sort()`         | Gunakan `sorted()` atau salin List          |
| Hasil pencarian `-1`               | Data tidak ditemukan         | Periksa target dan isi data                 |
| Proses sorting tidak selesai       | Kesalahan kondisi perulangan | Periksa batas indeks dan kondisi pertukaran |
| Nilai tidak sesuai urutan          | Operator perbandingan salah  | Periksa penggunaan `>` atau `<`             |

## **15. Ringkasan Materi**

Pada pertemuan ini, mahasiswa telah mempelajari:

1. Searching adalah proses menemukan nilai tertentu dalam kumpulan data.
2. Linear Search memeriksa data satu per satu dan dapat digunakan pada data yang belum terurut.
3. Binary Search membagi ruang pencarian menjadi dua bagian dan membutuhkan data terurut.
4. Linear Search memiliki kompleksitas waktu O(n).
5. Binary Search memiliki kompleksitas waktu O(log n).
6. Sorting adalah proses menyusun data berdasarkan urutan tertentu.
7. Bubble Sort mengurutkan data dengan membandingkan elemen yang bersebelahan.
8. Selection Sort mengurutkan data dengan mencari elemen terkecil atau terbesar.
9. Bubble Sort dan Selection Sort memiliki kompleksitas waktu dasar O(n²).
10. Python menyediakan `sorted()` dan `sort()` untuk pengurutan data secara praktis.

**Inti pembelajaran:** Pemilihan algoritma pencarian dan pengurutan yang tepat dapat memengaruhi efisiensi program, terutama ketika jumlah data yang diproses semakin besar.

## **16. Referensi Pembelajaran**

1. Python Software Foundation. *Python Tutorial – Data Structures*. [Python Official Documentation](https://docs.python.org/3/tutorial/datastructures.html).
2. Python Software Foundation. *Built-in Functions – sorted()*. [Python sorted() Documentation](https://docs.python.org/3/library/functions.html).
3. Cormen, T. H., et al. (2022). *Introduction to Algorithms*, 4th Edition. MIT Press.
4. Matthes, E. (2023). *Python Crash Course*, 3rd Edition. No Starch Press.
