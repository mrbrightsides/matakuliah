# **MODULE 6**

# **INTERPOLASI DAN APROKSIMASI DATA**



Komputasi Numerik

Program Studi Teknik Elektro



## **1. Deskripsi Pembelajaran**

Dalam berbagai aplikasi teknik elektro, hasil pengukuran sering kali hanya tersedia dalam sejumlah titik data tertentu. Sebagai contoh, sebuah sensor suhu mungkin memberikan data tegangan keluaran pada beberapa nilai suhu yang telah diketahui.

Namun, dalam kondisi nyata, sistem dapat menghasilkan nilai yang berada di antara titik-titik pengukuran tersebut.

Misalnya, hasil kalibrasi sensor menunjukkan:

| Suhu (°C) | Tegangan keluaran (V) |
| --------- | --------------------- |
| 10        | 0,5                   |
| 20        | 1,0                   |
| 30        | 1,5                   |
| 40        | 2,0                   |

Jika sensor menghasilkan tegangan 1,3 V, berapakah suhu yang terukur?

Nilai tersebut tidak tersedia secara langsung dalam tabel. Untuk memperkirakannya, kita dapat menggunakan metode interpolasi.

Interpolasi merupakan salah satu metode komputasi numerik yang digunakan untuk memperkirakan nilai di antara titik-titik data yang telah diketahui.

Dalam modul ini kita akan mempelajari:

1. Konsep dasar interpolasi dan aproksimasi.
2. Interpolasi linear.
3. Interpolasi polinomial Lagrange.
4. Interpolasi Newton Divided Difference.
5. Penerapan interpolasi dalam teknik elektro.
6. Implementasi metode interpolasi menggunakan Python.
7. Analisis hasil dan kesalahan interpolasi.

## **2. Capaian Pembelajaran**

Setelah mempelajari modul ini, mahasiswa diharapkan mampu:

- Menjelaskan konsep interpolasi dan aproksimasi data.
- Membedakan interpolasi dan ekstrapolasi.
- Menghitung nilai menggunakan interpolasi linear.
- Menyusun polinomial interpolasi Lagrange.
- Menggunakan metode Newton Divided Difference.
- Mengimplementasikan metode interpolasi menggunakan Python.
- Menganalisis hasil interpolasi berdasarkan data pengukuran.
- Mengidentifikasi keterbatasan dan potensi kesalahan metode interpolasi.

## **3. Konsep Dasar Interpolasi dan Aproksimasi**

### **3.1 Pengertian Interpolasi**

Interpolasi adalah metode numerik untuk memperkirakan nilai suatu fungsi pada posisi tertentu berdasarkan sejumlah titik data yang telah diketahui.

Misalkan terdapat sekumpulan data:

\\[ (x_0,y_0),(x_1,y_1),\ldots,(x_n,y_n) \\]

Keterangan:

- \\(x_i\\) = variabel bebas atau input.
- \\(y_i\\) = nilai fungsi atau output.
- \\(n\\) = orde tertinggi polinomial interpolasi.

Tujuan interpolasi adalah membentuk fungsi pendekatan \\(P(x)\\) yang melewati titik-titik data tersebut.

Secara matematis:

\\[ P(x_i)=y_i \\]

Artinya, fungsi interpolasi harus menghasilkan nilai yang sama dengan data yang diketahui pada setiap titik interpolasi.

[Interpolation — The Science of Machine Learning & AI](https://images.openai.com/static-rsc-4/-IwzmmXeOPhViyluPzox4w5HG-P85gpiO0YL_qSnWP7JWuHfWhWu2GgikaOJyMiFokPnPi5UabfMaGYOz1tET9JrUkikKs5VbdDIh4or6VkuJB9c151qC0Uub8WqynqWEHr5L87Lkt6mUyop-qfVPDnL5GvJKoRMzTs5zUQ1rwY?purpose=inline)

[ml-science.com](https://www.ml-science.com/interpolation?utm_source=chatgpt.com)

### **3.2 Interpolasi, Ekstrapolasi, dan Regresi**

Ketiga istilah ini sering dianggap sama, padahal memiliki tujuan berbeda.

| Metode       | Tujuan                                    | Karakteristik                                        |
| ------------ | ----------------------------------------- | ---------------------------------------------------- |
| Interpolasi  | Memperkirakan nilai di antara data        | Melewati titik data yang diketahui                   |
| Ekstrapolasi | Memperkirakan nilai di luar rentang data  | Lebih berisiko karena berada di luar data pengamatan |
| Regresi      | Membentuk model hubungan berdasarkan data | Tidak harus melewati seluruh titik data              |

Contoh:

Jika data pengukuran tersedia dari 10°C sampai 40°C:

- Memperkirakan suhu pada 25°C merupakan interpolasi.
- Memperkirakan suhu pada 55°C merupakan ekstrapolasi.
- Membentuk model hubungan tegangan dan suhu dari sejumlah pengukuran merupakan regresi jika model tersebut dicari untuk menyesuaikan pola data secara keseluruhan.

[Standard Curve Interpolation at Gary Delariva blog](https://images.openai.com/static-rsc-4/hHuvo6YSWUyqJbWAVez7lorWn2a-r6H5k0cSZAfa0vc4MasEOe2nQw3fDZb92Jcab9ZJTScAKjKawkZZswNiyYL7e8SHDuvyuGJGovwIiJmalPNjqpqbyqaOqsVXwC7UoKD7jrHqY7MhulQv4FcbZwx4XIwES7qu9J4vbfzF1js?purpose=inline)

[storage.googleapis.com](https://storage.googleapis.com/dwgsqgkzonoyke/standard-curve-interpolation.html?utm_source=chatgpt.com)

**Hal penting:** Interpolasi biasanya digunakan ketika nilai yang ingin diperkirakan masih berada di dalam rentang data yang tersedia. Ekstrapolasi perlu dilakukan dengan lebih hati-hati karena pola di luar rentang pengamatan belum tentu mengikuti pola data sebelumnya.

### **3.3 Mengapa Interpolasi Dibutuhkan dalam Teknik Elektro?**

Interpolasi dapat digunakan dalam berbagai permasalahan teknik elektro, misalnya:

- Kalibrasi sensor suhu berdasarkan tegangan keluaran.
- Memperkirakan nilai tegangan pada karakteristik komponen elektronik.
- Memperkirakan arus pada titik operasi tertentu.
- Mengolah data hasil pengukuran laboratorium.
- Membaca tabel karakteristik motor listrik.
- Memperkirakan parameter sistem berdasarkan data eksperimen.

Dengan demikian, interpolasi membantu mengubah data pengukuran yang terbatas menjadi informasi numerik yang lebih bermanfaat.

## **4. Interpolasi Linear**

### **4.1 Konsep Interpolasi Linear**

Interpolasi linear merupakan metode paling sederhana untuk memperkirakan nilai di antara dua titik data.

Metode ini mengasumsikan bahwa hubungan antara dua titik tersebut dapat didekati dengan garis lurus.

Misalkan diketahui dua titik:

\\[ (x_0,y_0) \\]

dan

\\[ (x_1,y_1) \\]

Persamaan garis lurus yang menghubungkan kedua titik tersebut adalah:

\\[ y(x)=y_0+ \frac{x-x_0}{x_1-x_0}(y_1-y_0) \\]

Keterangan:

- \\(x_0\\) = nilai input pertama.
- \\(x_1\\) = nilai input kedua.
- \\(y_0\\) = nilai output pertama.
- \\(y_1\\) = nilai output kedua.
- \\(x\\) = nilai input yang ingin diperkirakan.
- \\(y(x)\\) = hasil interpolasi.

### **4.2 Contoh Perhitungan Manual**

Diketahui hasil pengukuran sensor suhu:

| Suhu (°C) | Tegangan (V) |
| --------- | ------------ |
| 10        | 0,5          |
| 20        | 1,0          |

Jika tegangan keluaran sensor adalah 0,8 V, perkirakan suhu yang bersesuaian.

**Langkah 1: Identifikasi data**

Karena kita ingin mencari suhu berdasarkan tegangan, posisi variabel perlu disesuaikan:

\\[ x_0=0,5,\quad y_0=10 \\]

\\[ x_1=1,0,\quad y_1=20 \\]

Tegangan yang diketahui:

\\[ x=0,8 \\]

**Langkah 2: Masukkan ke persamaan**

\\[ y(x)=y_0+ \frac{x-x_0}{x_1-x_0}(y_1-y_0) \\]

\\[ y(0,8)=10+ \frac{0,8-0,5}{1,0-0,5}(20-10) \\]

\\[ y(0,8)=10+ \frac{0,3}{0,5}(10) \\]

\\[ y(0,8)=10+6 \\]

\\[ \boxed{y(0,8)=16^\circ C} \\]

Jadi, berdasarkan interpolasi linear, suhu yang diperkirakan adalah **16°C**.

### **4.3 Implementasi Interpolasi Linear Menggunakan Python**

```
def interpolasi_linear(x0, y0, x1, y1, x):    if x0 == x1:        raise ValueError("x0 dan x1 tidak boleh sama")    if not min(x0, x1) <= x <= max(x0, x1):        raise ValueError("Nilai x berada di luar rentang interpolasi")    y = y0 + ((x - x0) / (x1 - x0)) * (y1 - y0)    return y# Data pengukuran sensorx0 = 0.5y0 = 10x1 = 1.0y1 = 20# Nilai tegangan yang ingin diperkirakanx = 0.8hasil = interpolasi_linear(x0, y0, x1, y1, x)print("Tegangan Sensor:", x, "V")print("Estimasi Suhu:", hasil, "°C")
```

**Output program:**

```
Tegangan Sensor: 0.8 V
Estimasi Suhu: 16.0 °C
```

### **4.4 Kelebihan dan Keterbatasan**

Kelebihan:

- Perhitungan sederhana.
- Mudah diterapkan menggunakan Python.
- Cocok untuk data yang memiliki perubahan relatif linear.
- Tidak membutuhkan banyak titik data.

Keterbatasan:

- Hanya menggunakan dua titik data untuk satu segmen interpolasi.
- Kurang akurat jika hubungan antarvariabel sangat nonlinear.
- Hasil dapat berbeda apabila rentang titik pengukuran terlalu lebar.

## **5. Interpolasi Polinomial Lagrange**

### **5.1 Konsep Metode Lagrange**

Interpolasi linear hanya menggunakan dua titik data. Jika tersedia lebih banyak titik pengukuran, kita dapat menggunakan interpolasi polinomial.

Salah satu metode yang dapat digunakan adalah interpolasi Lagrange.

Metode Lagrange membentuk polinomial yang melewati seluruh titik data yang diketahui.

Jika terdapat \\(n+1\\) titik data, maka polinomial interpolasi yang dibentuk memiliki derajat paling tinggi \\(n\\), dengan syarat seluruh nilai \\(x_i\\) berbeda.

Persamaan umum polinomial Lagrange:

\\[ P_n(x)=\sum\_{i=0}^{n}y_iL_i(x) \\]

Dengan:

\\[ L_i(x)= \prod\_{\substack{j=0\\\j\neq i}}^{n} \frac{x-x_j}{x_i-x_j} \\]

Keterangan:

- \\(P_n(x)\\) = polinomial interpolasi.
- \\(y_i\\) = nilai fungsi pada titik ke-\\(i\\).
- \\(L_i(x)\\) = basis polinomial Lagrange.
- \\(x_i\\) = titik data ke-\\(i\\).
- \\(n\\) = derajat maksimum polinomial.

Basis Lagrange memiliki sifat:

\\[ L_i(x_j)= \begin{cases} 1, & i=j\\\ 0, & i\neq j \end{cases} \\]

Sifat tersebut menyebabkan polinomial yang dibentuk akan melewati semua titik data.

### **5.2 Contoh Perhitungan Manual**

Diketahui data pengukuran:

| \\(x\\) | \\(y\\) |
| ------- | ------- |
| 1       | 1       |
| 2       | 4       |
| 3       | 9       |

Tentukan nilai interpolasi pada:

\\[ x=2,5 \\]

Karena terdapat tiga titik data, polinomial yang digunakan memiliki derajat paling tinggi dua.

**Langkah 1: Bentuk basis Lagrange pertama**

\\[ L_0(x)= \frac{(x-2)(x-3)} {(1-2)(1-3)} \\]

\\[ L_0(x)=\frac{(x-2)(x-3)}{2} \\]

**Langkah 2: Bentuk basis kedua**

\\[ L_1(x)= \frac{(x-1)(x-3)} {(2-1)(2-3)} \\]

\\[ L_1(x)=-(x-1)(x-3) \\]

**Langkah 3: Bentuk basis ketiga**

\\[ L_2(x)= \frac{(x-1)(x-2)} {(3-1)(3-2)} \\]

\\[ L_2(x)=\frac{(x-1)(x-2)}{2} \\]

**Langkah 4: Susun polinomial Lagrange**

\\[ P_2(x)=1L_0(x)+4L_1(x)+9L_2(x) \\]

Substitusikan \\(x=2,5\\).

\\[ L_0(2,5)= \frac{(0,5)(-0,5)}{2} =-0,125 \\]

\\[ L_1(2,5)= -(1,5)(-0,5)=0,75 \\]

\\[ L_2(2,5)= \frac{(1,5)(0,5)}{2} =0,375 \\]

Maka:

\\[ P_2(2,5)= 1(-0,125)+4(0,75)+9(0,375) \\]

\\[ P_2(2,5)=-0,125+3+3,375 \\]

\\[ \boxed{P_2(2,5)=6,25} \\]

Jadi, hasil interpolasi Lagrange adalah **6,25**.

### **5.3 Implementasi Lagrange Menggunakan Python**

```
def lagrange_interpolation(x_data, y_data, x):    n = len(x_data)    if n != len(y_data) or n == 0:        raise ValueError("Jumlah data x dan y harus sama dan tidak kosong")    if len(set(x_data)) != n:        raise ValueError("Semua nilai x harus berbeda")    if not min(x_data) <= x <= max(x_data):        raise ValueError("Nilai x berada di luar rentang interpolasi")    hasil = 0.0    for i in range(n):        L = 1.0        for j in range(n):            if i != j:                L *= (x - x_data[j]) / (x_data[i] - x_data[j])        hasil += y_data[i] * L    return hasil# Datax_data = [1, 2, 3]y_data = [1, 4, 9]# Titik yang dicarix = 2.5hasil = lagrange_interpolation(x_data, y_data, x)print("Hasil interpolasi Lagrange:", hasil)
```

**Output:**

```
Hasil interpolasi Lagrange: 6.25
```

### **5.4 Analisis Metode Lagrange**

Metode Lagrange memiliki kelebihan:

- Dapat menggunakan lebih dari dua titik data.
- Tidak membutuhkan penyusunan tabel selisih.
- Bentuk matematisnya relatif mudah dipahami.
- Cocok untuk data dengan titik input yang tidak harus berjarak sama.

Namun, metode ini memiliki keterbatasan:

- Perhitungan dapat menjadi panjang jika jumlah data bertambah.
- Jika satu titik data berubah, keseluruhan polinomial perlu dihitung kembali.
- Polinomial berderajat tinggi dapat menghasilkan osilasi yang tidak diinginkan.

Fenomena osilasi pada interpolasi polinomial berderajat tinggi dikenal sebagai *Runge phenomenon* dalam kondisi tertentu.

## **6. Interpolasi Newton Divided Difference**

### **6.1 Konsep Metode Newton**

Metode Newton Divided Difference merupakan metode interpolasi polinomial yang menggunakan tabel selisih terbagi (*divided difference table*).

Seperti Lagrange, metode Newton juga membentuk polinomial yang melewati seluruh titik data.

Perbedaannya terletak pada cara menyusun koefisien polinomial.

Metode Newton menggunakan koefisien yang diperoleh dari perhitungan selisih terbagi secara bertahap.

### **6.2 Persamaan Selisih Terbagi**

Selisih terbagi orde pertama:

\\[ f[x_i,x\_{i+1}] = \frac{f[x\_{i+1}]-f[x_i]} {x\_{i+1}-x_i} \\]

Selisih terbagi orde kedua:

\\[ f[x_i,x\_{i+1},x\_{i+2}] = \frac{ f[x\_{i+1},x\_{i+2}] - f[x_i,x\_{i+1}] }{ x\_{i+2}-x_i } \\]

Secara umum:

\\[ f[x_i,\ldots,x\_{i+k}] = \frac{ f[x\_{i+1},\ldots,x\_{i+k}] - f[x_i,\ldots,x\_{i+k-1}] }{ x\_{i+k}-x_i } \\]

Polinomial Newton kemudian ditulis sebagai:

\\[ \begin{aligned} P_n(x)={}&f[x_0]\\\ &+f[x_0,x_1]\(x-x_0)\\\ &+f[x_0,x_1,x_2]\(x-x_0)(x-x_1)\\\ &+\cdots \end{aligned} \\]

Bentuk umumnya:

\\[ P_n(x)=f[x_0]+ \sum\_{k=1}^{n} f[x_0,\ldots,x_k] \prod\_{j=0}^{k-1}(x-x_j) \\]

### **6.3 Contoh Perhitungan Manual**

Gunakan data yang sama:

| \\(x\\) | \\(f(x)\\) |
| ------- | ---------- |
| 1       | 1          |
| 2       | 4          |
| 3       | 9          |

**Langkah 1: Hitung selisih terbagi orde pertama**

\\[ f[1,2]=\frac{4-1}{2-1}=3 \\]

\\[ f[2,3]=\frac{9-4}{3-2}=5 \\]

**Langkah 2: Hitung selisih terbagi orde kedua**

\\[ f[1,2,3]=\frac{5-3}{3-1} \\]

\\[ f[1,2,3]=1 \\]

Tabel selisih terbagi:

| \\(x\\) | \\(f(x)\\) | Orde 1 | Orde 2 |
| ------- | ---------- | ------ | ------ |
| 1       | 1          | 3      | 1      |
| 2       | 4          | 5      |        |
| 3       | 9          |        |        |

**Langkah 3: Bentuk polinomial Newton**

\\[ P_2(x)=1+3(x-1)+1(x-1)(x-2) \\]

**Langkah 4: Hitung pada&#x20;**\\(x=2,5\\)

\\[ P_2(2,5)= 1+3(2,5-1) +(2,5-1)(2,5-2) \\]

\\[ P_2(2,5)=1+4,5+(1,5)(0,5) \\]

\\[ P_2(2,5)=1+4,5+0,75 \\]

\\[ \boxed{P_2(2,5)=6,25} \\]

Hasilnya sama dengan metode Lagrange karena kedua metode membentuk polinomial interpolasi yang sama untuk titik-titik data tersebut.

### **6.4 Implementasi Newton Divided Difference Menggunakan Python**

```
def newton_divided_difference(x_data, y_data):    n = len(x_data)    if n != len(y_data) or n == 0:        raise ValueError("Jumlah data x dan y harus sama dan tidak kosong")    if len(set(x_data)) != n:        raise ValueError("Semua nilai x harus berbeda")    # Membuat tabel selisih terbagi    table = [[0.0 for _ in range(n)] for _ in range(n)]    for i in range(n):        table[i][0] = float(y_data[i])    for j in range(1, n):        for i in range(n - j):            table[i][j] = (                table[i + 1][j - 1] - table[i][j - 1]            ) / (x_data[i + j] - x_data[i])    # Koefisien polinomial    coefficients = [table[0][j] for j in range(n)]    return coefficientsdef newton_evaluate(x_data, coefficients, x):    n = len(coefficients)    if not min(x_data) <= x <= max(x_data):        raise ValueError("Nilai x berada di luar rentang interpolasi")    hasil = coefficients[0]    product = 1.0
```

**Output:**

```
Koefisien Newton: [1.0, 3.0, 1.0]
Hasil interpolasi: 6.25
```

### **6.5 Kelebihan dan Keterbatasan Newton**

Kelebihan:

- Koefisien diperoleh secara sistematis melalui tabel.
- Relatif mudah menambahkan titik data baru.
- Cocok untuk implementasi algoritma numerik.
- Dapat digunakan pada titik data yang tidak berjarak sama.

Keterbatasan:

- Membutuhkan proses penyusunan tabel selisih terbagi.
- Tetap berpotensi menghasilkan osilasi jika polinomial berderajat tinggi.
- Semua nilai input harus berbeda agar pembagian tidak menghasilkan penyebut nol.

## **7. Perbandingan Metode Interpolasi**

Ketiga metode yang telah dipelajari memiliki karakteristik berbeda.

| Aspek                    | Linear                  | Lagrange              | Newton                |
| ------------------------ | ----------------------- | --------------------- | --------------------- |
| Jumlah titik             | Dua per segmen          | Banyak                | Banyak                |
| Bentuk fungsi            | Garis lurus             | Polinomial            | Polinomial            |
| Perhitungan              | Sederhana               | Basis polinomial      | Tabel selisih         |
| Penambahan data          | Mengubah segmen terkait | Hitung ulang          | Dapat diperbarui      |
| Kompleksitas             | Rendah                  | Meningkat dengan data | Meningkat dengan data |
| Hasil melalui titik data | Ya                      | Ya                    | Ya                    |

**Kesimpulan perbandingan:**

- Gunakan interpolasi linear jika hubungan data relatif linear dan membutuhkan perhitungan sederhana.
- Gunakan Lagrange jika ingin membentuk polinomial dari sejumlah titik data.
- Gunakan Newton Divided Difference jika ingin memperoleh koefisien polinomial secara bertahap dan sistematis.

Perlu diingat, penggunaan polinomial dengan derajat semakin tinggi tidak otomatis menghasilkan perkiraan yang semakin baik.

## **8. Studi Kasus Teknik Elektro: Kalibrasi Sensor Suhu**

Sekarang kita terapkan ketiga metode pada kasus yang lebih dekat dengan bidang Teknik Elektro.

### **8.1 Deskripsi Kasus**

Sebuah sensor suhu menghasilkan tegangan keluaran yang berubah sesuai temperatur lingkungan.

Hasil pengukuran kalibrasi awal diperoleh sebagai berikut:

| Tegangan Sensor (V) | Suhu (°C) |
| ------------------- | --------- |
| 0,5                 | 10        |
| 1,0                 | 20        |
| 1,5                 | 30        |
| 2,0                 | 40        |

Pada saat pengujian, sensor menghasilkan tegangan sebesar 1,3 V.

Permasalahan:

**Berapa suhu yang diperkirakan berdasarkan tegangan keluaran sensor tersebut?**

### **8.2 Penyelesaian Menggunakan Interpolasi Linear**

Nilai 1,3 V berada di antara 1,0 V dan 1,5 V.

Dengan demikian:

\\[ x_0=1,0,\quad y_0=20 \\]

\\[ x_1=1,5,\quad y_1=30 \\]

\\[ x=1,3 \\]

Substitusi:

\\[ T=20+ \frac{1,3-1,0}{1,5-1,0}(30-20) \\]

\\[ T=20+\frac{0,3}{0,5}(10) \\]

\\[ T=20+6 \\]

\\[ \boxed{T=26^\circ C} \\]

### **8.3 Implementasi Menggunakan Python**

```
# Data kalibrasi sensortegangan = [0.5, 1.0, 1.5, 2.0]suhu = [10, 20, 30, 40]# Tegangan pengujianV_sensor = 1.3# Mencari interval datafor i in range(len(tegangan) - 1):    if tegangan[i] <= V_sensor <= tegangan[i + 1]:        T = interpolasi_linear(            tegangan[i],            suhu[i],            tegangan[i + 1],            suhu[i + 1],            V_sensor        )        print("Tegangan Sensor:", V_sensor, "V")        print("Estimasi Suhu:", T, "°C")        breakelse:    print("Tegangan berada di luar rentang data kalibrasi")
```

**Output:**

```
Tegangan Sensor: 1.3 V
Estimasi Suhu: 26.0 °C
```

### **8.4 Menggunakan Lagrange dan Newton**

Sekarang kita gunakan seluruh data kalibrasi.

```
# Data kalibrasix_data = [0.5, 1.0, 1.5, 2.0]y_data = [10, 20, 30, 40]# Tegangan yang akan dihitungx = 1.3# Metode Lagrangehasil_lagrange = lagrange_interpolation(    x_data, y_data, x)# Metode Newtonkoefisien = newton_divided_difference(    x_data, y_data)hasil_newton = newton_evaluate(    x_data, koefisien, x)print("Lagrange:", hasil_lagrange, "°C")print("Newton:", hasil_newton, "°C")
```

Hasil yang diperoleh:

```
Lagrange: 26.0 °C
Newton: 26.0 °C
```

Mengapa hasil ketiganya sama?

Karena data kalibrasi yang digunakan memiliki hubungan linear:

\\[ T=20V \\]

Ketiga metode dapat merepresentasikan hubungan tersebut dengan tepat pada contoh ini.

Namun, pada data sensor yang memiliki karakteristik nonlinear, hasil interpolasi linear dan polinomial dapat berbeda.

### **8.5 Visualisasi Data Menggunakan Matplotlib**

Untuk membantu memahami hasil interpolasi, kita dapat menggambarkan titik data kalibrasi dan kurva interpolasinya.

```
import numpy as npimport matplotlib.pyplot as plt# Data kalibrasix_data = [0.5, 1.0, 1.5, 2.0]y_data = [10, 20, 30, 40]# Membuat rentang teganganx_plot = np.linspace(0.5, 2.0, 100)# Menghitung interpolasiy_plot = [    lagrange_interpolation(x_data, y_data, x)    for x in x_plot]# Membuat grafikplt.figure(figsize=(8, 5))plt.scatter(    x_data,    y_data,    label="Data Kalibrasi")plt.plot(    x_plot,    y_plot,    label="Kurva Interpolasi")plt.scatter(    [1.3],    [26],    label="Estimasi pada 1.3 V")plt.xlabel("Tegangan Sensor (V)")plt.ylabel("Suhu (°C)")plt.title("Interpolasi Data Kalibrasi Sensor Suhu")plt.grid(True)plt.legend()plt.show()
```

[MSP430FR4133: Correct usage of TLV values for internal temperature sensor. - MSP low-power microcontroller forum - MSP low-power microcontrollers - TI E2E support forums](https://images.openai.com/static-rsc-4/-qe0Ap9AJTEWdQUdtoAyWsjipeSuDbEWlEheBP0TOEzUmQZtNHOnQkL4RPh1_l7jbRaVQa85O8xlh95IE85QzyQ6eT7H6iYuUKiCwfCj3mQ9wyIsZBtKx5uMwfZRSPu6JiT8biPJuaXZAAW_lSvFNG60q2mwdmevDIpL9hAtGao?purpose=inline)

[e2e.ti.com](https://e2e.ti.com/support/microcontrollers/msp-low-power-microcontrollers-group/msp430/f/msp-low-power-microcontroller-forum/589045/msp430fr4133-correct-usage-of-tlv-values-for-internal-temperature-sensor?utm_source=chatgpt.com)

Visualisasi tersebut membantu memperlihatkan bagaimana fungsi interpolasi menghubungkan titik-titik pengukuran dan memperkirakan nilai di antaranya.

## **9. Analisis Galat dan Kualitas Interpolasi**

Hasil interpolasi merupakan nilai perkiraan. Oleh karena itu, kita perlu memahami bagaimana mengevaluasi ketepatannya.

### **9.1 Galat Absolut**

Jika nilai sebenarnya diketahui, galat absolut dihitung dengan:

\\[ E_a=|y\_{\text{sebenarnya}}-y\_{\text{aproksimasi}}| \\]

Misalkan:

- Suhu referensi = 25,8°C.
- Hasil interpolasi = 26°C.

Maka:

\\[ E_a=|25,8-26| \\]

\\[ \boxed{E_a=0,2^\circ C} \\]

### **9.2 Galat Relatif**

\\[ E_r= \frac{E_a}{|y\_{\text{sebenarnya}}|} \\]

\\[ E_r=\frac{0,2}{25,8} \\]

\\[ E_r=0,00775 \\]

### **9.3 Persentase Galat**

\\[ E_p=E_r\times100\\% \\]

\\[ E_p=0,775\\% \\]

Jadi, persentase galat hasil interpolasi adalah sekitar **0,775%**.

Contoh implementasi Python:

```
nilai_sebenarnya = 25.8nilai_interpolasi = 26.0galat_absolut = abs(    nilai_sebenarnya - nilai_interpolasi)galat_relatif = (    galat_absolut / abs(nilai_sebenarnya))galat_persen = galat_relatif * 100print("Galat Absolut:", galat_absolut)print("Galat Relatif:", galat_relatif)print("Galat Persen:", galat_persen, "%")
```

Output:

```
Galat Absolut: 0.2
Galat Relatif: 0.007751937984496124
Galat Persen: 0.7751937984496124 %
```

**Catatan:** Dalam praktik, nilai sebenarnya tidak selalu diketahui. Jika tidak tersedia, kita tidak dapat menghitung galat sebenarnya secara langsung. Kita perlu menggunakan pendekatan evaluasi lain, seperti membandingkan hasil dengan pengukuran tambahan, validasi pada titik yang tidak digunakan dalam pembentukan interpolasi, atau menganalisis karakteristik data.

### **9.4 Faktor yang Memengaruhi Akurasi Interpolasi**

Beberapa faktor yang perlu diperhatikan:

1. **Jumlah titik data:** Lebih banyak titik tidak selalu berarti hasil lebih baik.
2. **Jarak antar titik:** Titik yang terlalu berjauhan dapat menyebabkan pendekatan lokal kurang akurat.
3. **Karakteristik fungsi:** Hubungan nonlinear mungkin tidak dapat direpresentasikan dengan baik oleh garis lurus.
4. **Noise pengukuran:** Data sensor dapat mengandung gangguan atau ketidakpastian.
5. **Derajat polinomial:** Polinomial berderajat tinggi dapat mengalami osilasi, khususnya pada rentang yang lebar.

Dalam aplikasi teknik elektro, kualitas data pengukuran sama pentingnya dengan pemilihan metode numerik.

## **10. Pengantar Aproksimasi Data Menggunakan Regresi Linear**

Selain interpolasi, kita juga perlu memahami konsep aproksimasi data.

Pada interpolasi, fungsi dibentuk agar melewati seluruh titik data yang diketahui.

Namun, dalam pengukuran nyata, data sering mengandung noise. Jika kita memaksa sebuah fungsi melewati seluruh titik pengukuran, fungsi tersebut bisa saja mengikuti noise, bukan pola hubungan yang sebenarnya.

Salah satu pendekatan yang dapat digunakan adalah regresi linear dengan metode kuadrat terkecil (*Least Squares*).

### **10.1 Konsep Regresi Linear**

Regresi linear membentuk hubungan:

\\[ y=a+bx \\]

Keterangan:

- \\(a\\) = konstanta atau intersep.
- \\(b\\) = kemiringan garis atau slope.
- \\(x\\) = variabel bebas.
- \\(y\\) = nilai prediksi.

Koefisien \\(a\\) dan \\(b\\) dipilih agar jumlah kuadrat selisih antara nilai pengukuran dan nilai prediksi menjadi minimum.

\\[ SSE=\sum\_{i=1}^{n}(y_i-\hat{y}\_i)^2 \\]

Dengan:

\\[ \hat{y}\_i=a+bx_i \\]

### **10.2 Persamaan Koefisien Regresi**

Kemiringan garis:

\\[ b= \frac{ n\sum x_iy_i-(\sum x_i)(\sum y_i) }{ n\sum x_i^2-(\sum x_i)^2 } \\]

Intersep:

\\[ a=\frac{\sum y_i-b\sum x_i}{n} \\]

### **10.3 Contoh Data**

Misalkan hasil pengukuran sensor menghasilkan data:

| Tegangan (V) | Suhu (°C) |
| ------------ | --------- |
| 0,5          | 10,2      |
| 1,0          | 19,8      |
| 1,5          | 30,4      |
| 2,0          | 39,7      |

Data tersebut memiliki sedikit variasi yang mungkin disebabkan oleh noise pengukuran.

Kita dapat membentuk garis regresi untuk mendapatkan pola hubungan umum antara tegangan dan suhu.

### **10.4 Implementasi Regresi Linear Menggunakan Python**

```
import numpy as npimport matplotlib.pyplot as plt# Data pengukuranx = np.array([0.5, 1.0, 1.5, 2.0])y = np.array([10.2, 19.8, 30.4, 39.7])# Menghitung koefisien regresib, a = np.polyfit(x, y, 1)# Membentuk persamaan regresiprint("Intersep (a):", a)print("Slope (b):", b)# Prediksi pada tegangan 1.3 Vx_baru = 1.3y_prediksi = a + b * x_baruprint("Estimasi suhu:", y_prediksi, "°C")# Visualisasix_plot = np.linspace(min(x), max(x), 100)y_plot = a + b * x_plotplt.scatter(x, y, label="Data Pengukuran")plt.plot(x_plot, y_plot, label="Regresi Linear")plt.xlabel("Tegangan (V)")plt.ylabel("Suhu (°C)")plt.title("Regresi Linear Kalibrasi Sensor")plt.grid(True)plt.legend()plt.show()
```

Metode ini tidak menjamin garis melewati seluruh titik pengukuran. Tujuannya adalah memperoleh model hubungan yang paling sesuai menurut kriteria kuadrat terkecil.

**Perbedaan mendasar:**

- Interpolasi cocok ketika kita ingin mereproduksi titik data yang diketahui dan memperkirakan nilai di antaranya.
- Regresi cocok ketika kita ingin membangun model umum dari data yang mungkin mengandung noise.

Dalam pengembangan sistem instrumentasi, kedua pendekatan ini dapat digunakan sesuai karakteristik data dan tujuan pengukuran.

## **11. Kesalahan Umum dalam Interpolasi dan Aproksimasi**

Beberapa kesalahan yang sering terjadi ketika mahasiswa menerapkan metode interpolasi adalah:

| Kesalahan                               | Dampak                       | Solusi                                     |
| --------------------------------------- | ---------------------------- | ------------------------------------------ |
| Nilai \\(x\\) duplikat                  | Pembagian dengan nol         | Pastikan setiap \\(x_i\\) berbeda          |
| Salah menentukan variabel               | Hasil tidak sesuai konteks   | Tentukan input dan output secara jelas     |
| Menggunakan interpolasi di luar rentang | Berubah menjadi ekstrapolasi | Periksa rentang data                       |
| Salah menghitung basis Lagrange         | Polinomial keliru            | Periksa penyebut dan indeks                |
| Salah menyusun tabel Newton             | Koefisien tidak tepat        | Hitung selisih secara berurutan            |
| Menggunakan polinomial terlalu tinggi   | Potensi osilasi              | Pilih metode dan jumlah titik secara bijak |
| Mengabaikan noise                       | Model tidak representatif    | Pertimbangkan regresi atau metode lain     |

## **12. Rangkuman Materi**

Pada modul ini kita telah mempelajari beberapa konsep penting dalam komputasi numerik.

1. Interpolasi digunakan untuk memperkirakan nilai di antara titik data yang telah diketahui.
2. Ekstrapolasi digunakan untuk memperkirakan nilai di luar rentang data.
3. Regresi digunakan untuk membentuk model hubungan berdasarkan pola data.
4. Interpolasi linear menggunakan dua titik data dan mengasumsikan hubungan garis lurus.
5. Interpolasi Lagrange membentuk polinomial berdasarkan basis Lagrange.
6. Newton Divided Difference membentuk polinomial melalui tabel selisih terbagi.
7. Galat interpolasi dapat dianalisis jika tersedia nilai referensi.
8. Regresi linear dapat digunakan ketika data pengukuran mengandung variasi atau noise.

Dalam teknik elektro, interpolasi dan aproksimasi dapat diterapkan untuk kalibrasi sensor, pengolahan data pengukuran, analisis karakteristik komponen, serta pengembangan sistem instrumentasi.

Hal yang paling penting adalah mahasiswa tidak hanya memperoleh nilai hasil perhitungan, tetapi juga mampu menjelaskan bagaimana nilai tersebut diperoleh dan apakah hasilnya masuk akal secara teknis.

## **13. Referensi Pembelajaran**

Beberapa referensi yang dapat digunakan untuk memperdalam materi:

1. Chapra, S. C., & Canale, R. P. *Numerical Methods for Engineers*. McGraw-Hill.
2. Burden, R. L., Faires, J. D., & Burden, A. M. *Numerical Analysis*. Cengage Learning.
3. Sauer, T. *Numerical Analysis*. Pearson.
4. Python Documentation – [Python Official Documentation](https://docs.python.org/3/).
5. NumPy Documentation – [NumPy Official Documentation](https://numpy.org/doc/stable/).
6. Matplotlib Documentation – [Matplotlib Official Documentation](https://matplotlib.org/stable/).
