# **MODUL 7**

## **Metode Interpolasi dan Aproksimasi**

Pertemuan 7 · Program Studi Teknik Elektro

## **1. Deskripsi Pembelajaran**

Dalam bidang Teknik Elektro, proses pengukuran dan pengumpulan data sering menghasilkan sejumlah nilai diskrit. Data tersebut dapat berasal dari sensor, instrumen pengukuran, eksperimen laboratorium, maupun hasil simulasi sistem.

Namun, dalam kondisi tertentu, nilai yang dibutuhkan tidak tersedia secara langsung pada data pengukuran. Sebagai contoh, sebuah sensor hanya menghasilkan data tegangan pada temperatur 20°C dan 30°C, sedangkan sistem membutuhkan estimasi tegangan pada temperatur 25°C.

Metode interpolasi digunakan untuk memperkirakan nilai di antara titik-titik data yang telah diketahui. Sementara itu, metode aproksimasi digunakan untuk membangun pendekatan matematis terhadap sekumpulan data, termasuk ketika data memiliki variasi atau gangguan pengukuran.

Dalam pembelajaran ini, mahasiswa akan mempelajari metode interpolasi linear, interpolasi polinomial Lagrange, interpolasi Newton Divided Difference, serta pendekatan regresi menggunakan metode kuadrat terkecil (*least squares*).

## **2. Capaian Pembelajaran**

Setelah mengikuti pembelajaran ini, mahasiswa diharapkan mampu:

1. Menjelaskan konsep interpolasi dan aproksimasi data.
2. Membedakan interpolasi, ekstrapolasi, dan regresi.
3. Memahami prinsip interpolasi linear.
4. Menggunakan interpolasi polinomial Lagrange.
5. Menggunakan interpolasi Newton Divided Difference.
6. Menjelaskan prinsip pendekatan regresi linear menggunakan metode kuadrat terkecil.
7. Mengimplementasikan metode interpolasi dan aproksimasi menggunakan Python.
8. Menganalisis hasil estimasi data pada permasalahan Teknik Elektro.

## **3. Konsep Dasar Interpolasi dan Aproksimasi**

### **3.1 Pengertian interpolasi**

Interpolasi merupakan metode numerik untuk memperkirakan nilai suatu fungsi pada posisi tertentu berdasarkan sejumlah titik data yang telah diketahui.

Misalnya, diperoleh data hasil pengukuran:

| Temperatur (°C) | Tegangan sensor (V) |
| --------------- | ------------------- |
| 20              | 1,0                 |
| 30              | 2,0                 |
| 40              | 3,0                 |

Jika kita ingin mengetahui tegangan sensor pada temperatur 25°C, nilai tersebut dapat diperkirakan menggunakan metode interpolasi.

Interpolasi dilakukan pada rentang data yang telah tersedia.

### **3.2 Pengertian ekstrapolasi**

Ekstrapolasi merupakan proses memperkirakan nilai di luar rentang data yang tersedia.

Contohnya, jika data pengukuran hanya tersedia pada temperatur 20°C hingga 40°C, estimasi pada temperatur 50°C termasuk ekstrapolasi.

Ekstrapolasi umumnya memiliki risiko ketidakpastian lebih besar karena pola data di luar rentang pengamatan belum tentu mengikuti pola sebelumnya.

### **3.3 Pengertian regresi**

Regresi merupakan metode untuk membangun hubungan matematis yang paling sesuai dengan sekumpulan data berdasarkan kriteria tertentu.

Berbeda dengan interpolasi yang berusaha melewati seluruh titik data, regresi tidak harus melewati setiap titik pengamatan.

Regresi banyak digunakan ketika data pengukuran mengandung noise atau variasi yang tidak dapat dijelaskan secara sempurna oleh suatu fungsi.

### **3.4 Perbandingan interpolasi, ekstrapolasi, dan regresi**

| Aspek                 | Interpolasi                        | Ekstrapolasi                     | Regresi                            |
| --------------------- | ---------------------------------- | -------------------------------- | ---------------------------------- |
| Tujuan                | Memperkirakan nilai di antara data | Memperkirakan nilai di luar data | Membentuk model hubungan data      |
| Posisi estimasi       | Dalam rentang data                 | Di luar rentang data             | Berdasarkan keseluruhan data       |
| Melalui semua titik   | Umumnya ya                         | Tidak harus                      | Tidak harus                        |
| Risiko ketidakpastian | Bergantung pola dan data           | Umumnya lebih tinggi             | Bergantung model dan kualitas data |

## **4. Metode Interpolasi Linear**

### **4.1 Prinsip dasar**

Interpolasi linear merupakan metode paling sederhana untuk memperkirakan nilai di antara dua titik data.

Metode ini mengasumsikan bahwa hubungan antara kedua titik dapat didekati menggunakan garis lurus.

Misalkan diketahui dua titik:

\\[ (x_0,y_0) \\]

dan

\\[ (x_1,y_1) \\]

Nilai interpolasi pada posisi \\(x\\) dapat dihitung menggunakan:

\\[ y=y_0+ \frac{x-x_0}{x_1-x_0} (y_1-y_0) \\]

Keterangan:

- \\(x_0,x_1\\) = nilai variabel bebas yang diketahui.
- \\(y_0,y_1\\) = nilai variabel terikat yang diketahui.
- \\(x\\) = posisi estimasi.
- \\(y\\) = hasil interpolasi.

### **4.2 Contoh perhitungan manual**

Diketahui data pengukuran sensor temperatur:

| Temperatur (°C) | Tegangan (V) |
| --------------- | ------------ |
| 20              | 1,0          |
| 30              | 2,0          |

Tentukan estimasi tegangan sensor pada temperatur 25°C.

Diketahui:

\\[ x_0=20,\quad y_0=1 \\]

\\[ x_1=30,\quad y_1=2 \\]

\\[ x=25 \\]

Substitusi ke rumus:

\\[ y=1+ \frac{25-20}{30-20}(2-1) \\]

\\[ y=1+\frac{5}{10} \\]

\\[ \boxed{y=1.5\text{ V}} \\]

Jadi, estimasi tegangan sensor pada temperatur 25°C adalah 1,5 V.

### **4.3 Implementasi Python**

```
def interpolasi_linear(x0, y0, x1, y1, x):    if x1 == x0:        raise ValueError("Nilai x0 dan x1 tidak boleh sama.")    y = y0 + ((x - x0) / (x1 - x0)) * (y1 - y0)    return yx0, y0 = 20, 1.0x1, y1 = 30, 2.0x = 25hasil = interpolasi_linear(x0, y0, x1, y1, x)print("Estimasi tegangan:", hasil, "V")
```

Hasil:

```
Estimasi tegangan: 1.5 V
```

### **4.4 Kelebihan dan keterbatasan**

Kelebihan:

- Perhitungan sederhana.
- Tidak membutuhkan banyak titik data.
- Mudah diimplementasikan.
- Cocok untuk hubungan yang relatif linear.

Keterbatasan:

- Tidak menggambarkan perubahan nonlinear secara akurat.
- Hanya menggunakan dua titik dalam setiap perhitungan.
- Hasil dapat kurang akurat ketika hubungan data memiliki kelengkungan yang signifikan.

## **5. Metode Interpolasi Polinomial Lagrange**

### **5.1 Prinsip dasar**

Interpolasi Lagrange merupakan metode interpolasi polinomial yang menggunakan sejumlah titik data untuk membentuk suatu fungsi polinomial.

Jika diketahui \\(n+1\\) titik data:

\\[ (x_0,y_0),\ldots,(x_n,y_n) \\]

maka polinomial interpolasi Lagrange dapat dinyatakan sebagai:

\\[ P_n(x)= \sum\_{i=0}^{n}y_iL_i(x) \\]

Dengan basis polinomial Lagrange:

\\[ L_i(x)= \prod\_{\substack{j=0\\\j\neq i}}^{n} \frac{x-x_j}{x_i-x_j} \\]

Setiap basis polinomial memiliki nilai satu pada titik datanya sendiri dan nol pada titik data lainnya.

Dengan demikian, polinomial yang dihasilkan melewati seluruh titik data yang digunakan.

### **5.2 Contoh perhitungan manual**

Diketahui tiga titik data:

| x | y |
| - | - |
| 1 | 1 |
| 2 | 4 |
| 3 | 9 |

Tentukan nilai fungsi pada:

\\[ x=2.5 \\]

Diketahui:

\\[ (x_0,y_0)=(1,1) \\]

\\[ (x_1,y_1)=(2,4) \\]

\\[ (x_2,y_2)=(3,9) \\]

Bentuk polinomial Lagrange:

\\[ P_2(x)=y_0L_0(x)+y_1L_1(x)+y_2L_2(x) \\]

Basis pertama:

\\[ L_0(x)= \frac{(x-2)(x-3)}{(1-2)(1-3)} \\]

Basis kedua:

\\[ L_1(x)= \frac{(x-1)(x-3)}{(2-1)(2-3)} \\]

Basis ketiga:

\\[ L_2(x)= \frac{(x-1)(x-2)}{(3-1)(3-2)} \\]

Substitusi \\(x=2.5\\):

\\[ L_0(2.5)= \frac{(0.5)(-0.5)}{2} =-0.125 \\]

\\[ L_1(2.5)= \frac{(1.5)(-0.5)}{-1} =0.75 \\]

\\[ L_2(2.5)= \frac{(1.5)(0.5)}{2} =0.375 \\]

Maka:

\\[ P_2(2.5)= 1(-0.125)+4(0.75)+9(0.375) \\]

\\[ P_2(2.5)=-0.125+3+3.375 \\]

\\[ \boxed{P_2(2.5)=6.25} \\]

### **5.3 Implementasi Python**

```
def lagrange_interpolation(x_data, y_data, x):    n = len(x_data)    if len(y_data) != n:        raise ValueError("Jumlah data x dan y harus sama.")    if len(set(x_data)) != n:        raise ValueError("Semua nilai x harus berbeda.")    hasil = 0.0    for i in range(n):        L = 1.0        for j in range(n):            if i != j:                L *= (                    (x - x_data[j]) /                    (x_data[i] - x_data[j])                )        hasil += y_data[i] * L    return hasilx_data = [1, 2, 3]y_data = [1, 4, 9]x = 2.5hasil = lagrange_interpolation(    x_data, y_data, x)print("Hasil interpolasi:", hasil)
```

Hasil:

```
Hasil interpolasi: 6.25
```

### **5.4 Kelebihan dan keterbatasan**

Kelebihan:

- Dapat menggunakan lebih dari dua titik data.
- Tidak membutuhkan penyusunan tabel selisih.
- Menghasilkan polinomial yang melewati seluruh titik data.
- Dapat digunakan untuk hubungan nonlinear.

Keterbatasan:

- Perhitungan menjadi semakin kompleks ketika jumlah titik bertambah.
- Penambahan data baru mengharuskan polinomial dihitung ulang.
- Polinomial berderajat tinggi dapat mengalami osilasi, khususnya pada interval tertentu.
- Sensitif terhadap distribusi titik data.

## **6. Metode Interpolasi Newton Divided Difference**

### **6.1 Prinsip dasar**

Newton Divided Difference merupakan metode interpolasi polinomial yang menggunakan tabel selisih terbagi (*divided difference*).

Metode ini membentuk polinomial berdasarkan nilai fungsi dan selisih terbagi dari titik-titik data.

Bentuk umum polinomial Newton:

\\[ \begin{aligned} P_n(x)=&f[x_0]\\\ &+f[x_0,x_1]\(x-x_0)\\\ &+f[x_0,x_1,x_2]\(x-x_0)(x-x_1)\\\ &+\cdots \end{aligned} \\]

Selisih terbagi orde pertama:

\\[ f[x_i,x\_{i+1}] = \frac{f(x\_{i+1})-f(x_i)} {x\_{i+1}-x_i} \\]

Selisih terbagi orde kedua:

\\[ f[x_i,x\_{i+1},x\_{i+2}] = \frac{ f[x\_{i+1},x\_{i+2}] - f[x_i,x\_{i+1}] }{ x\_{i+2}-x_i } \\]

Proses dilanjutkan untuk orde selanjutnya.

### **6.2 Contoh perhitungan manual**

Gunakan data:

| x | f(x) |
| - | ---- |
| 1 | 1    |
| 2 | 4    |
| 3 | 9    |

**Langkah 1: Menghitung selisih terbagi orde pertama**

\\[ f[x_0,x_1]=\frac{4-1}{2-1}=3 \\]

\\[ f[x_1,x_2]=\frac{9-4}{3-2}=5 \\]

**Langkah 2: Menghitung selisih terbagi orde kedua**

\\[ f[x_0,x_1,x_2]= \frac{5-3}{3-1} \\]

\\[ f[x_0,x_1,x_2]=1 \\]

Tabel selisih terbagi:

| x | f(x) | Orde 1 | Orde 2 |
| - | ---- | ------ | ------ |
| 1 | 1    | 3      | 1      |
| 2 | 4    | 5      |        |
| 3 | 9    |        |        |

**Langkah 3: Membentuk polinomial Newton**

\\[ P_2(x)=1+3(x-1)+1(x-1)(x-2) \\]

Untuk \\(x=2.5\\):

\\[ P_2(2.5)= 1+3(1.5)+(1.5)(0.5) \\]

\\[ P_2(2.5)=1+4.5+0.75 \\]

\\[ \boxed{P_2(2.5)=6.25} \\]

Hasilnya sama dengan interpolasi Lagrange karena kedua metode membentuk polinomial interpolasi yang sama untuk kumpulan titik data yang sama.

### **6.3 Implementasi Python**

```
def newton_divided_difference(x_data, y_data):    n = len(x_data)    if len(y_data) != n:        raise ValueError("Jumlah data x dan y harus sama.")    if len(set(x_data)) != n:        raise ValueError("Semua nilai x harus berbeda.")    coef = [float(y) for y in y_data]    for j in range(1, n):        for i in range(n - 1, j - 1, -1):            coef[i] = (                (coef[i] - coef[i-1]) /                (x_data[i] - x_data[i-j])            )    return coefdef newton_evaluate(x_data, coef, x):    n = len(coef)    hasil = coef[n-1]    for i in range(n-2, -1, -1):        hasil = (            coef[i] +            (x - x_data[i]) * hasil        )
```

Hasil:

```
Koefisien Newton: [1.0, 3.0, 1.0]
Hasil interpolasi: 6.25
```

### **6.4 Kelebihan dan keterbatasan**

Kelebihan:

- Dapat menggunakan titik data yang tidak berjarak sama.
- Penambahan titik data dapat dilakukan dengan memperbarui tabel selisih.
- Bentuk polinomial mudah dievaluasi menggunakan skema bersarang.
- Cocok untuk pembelajaran interpolasi polinomial.

Keterbatasan:

- Memerlukan proses penyusunan tabel selisih terbagi.
- Perhitungan dapat menjadi kompleks untuk jumlah data besar.
- Menghadapi risiko osilasi pada polinomial berderajat tinggi.

## **7. Perbandingan Metode Interpolasi**

| Aspek                    | Linear             | Lagrange                      | Newton Divided Difference     |
| ------------------------ | ------------------ | ----------------------------- | ----------------------------- |
| Jumlah titik             | Dua titik          | Dua atau lebih                | Dua atau lebih                |
| Bentuk fungsi            | Garis lurus        | Polinomial                    | Polinomial                    |
| Prinsip                  | Interpolasi linear | Basis polinomial              | Selisih terbagi               |
| Data tidak berjarak sama | Bisa               | Bisa                          | Bisa                          |
| Penambahan data          | Perhitungan ulang  | Polinomial dihitung ulang     | Dapat memperbarui tabel       |
| Kompleksitas             | Rendah             | Meningkat dengan jumlah titik | Meningkat dengan jumlah titik |

Ketiga metode dapat menghasilkan nilai yang sama apabila menggunakan kumpulan titik data yang sama dan membentuk polinomial interpolasi dengan derajat yang sama.

Perbedaannya terutama terletak pada cara membangun dan mengevaluasi polinomial tersebut.

## **8. Metode Regresi Linear (Least Squares)**

### **8.1 Prinsip dasar**

Interpolasi bertujuan membangun fungsi yang melewati titik-titik data, sedangkan regresi bertujuan memperoleh model yang paling sesuai terhadap keseluruhan data berdasarkan kriteria tertentu.

Salah satu metode regresi yang umum digunakan adalah metode kuadrat terkecil (*least squares*).

Regresi linear menggunakan model:

\\[ y=a+bx \\]

Keterangan:

- \\(a\\) = konstanta atau intercept.
- \\(b\\) = koefisien kemiringan atau slope.
- \\(x\\) = variabel bebas.
- \\(y\\) = nilai prediksi.

Koefisien regresi dapat dihitung menggunakan:

\\[ b= \frac{ n\sum xy-\sum x\sum y }{ n\sum x^2-(\sum x)^2 } \\]

\\[ a=\frac{\sum y-b\sum x}{n} \\]

Metode kuadrat terkecil memilih parameter \\(a\\) dan \\(b\\) dengan meminimalkan jumlah kuadrat residual:

\\[ SSE=\sum\_{i=1}^{n}(y_i-\hat y_i)^2 \\]

### **8.2 Contoh perhitungan manual**

Diketahui data pengukuran sensor:

| x | y   |
| - | --- |
| 1 | 2,1 |
| 2 | 3,9 |
| 3 | 6,2 |
| 4 | 7,8 |

Buat model regresi linear:

\\[ y=a+bx \\]

Tabel perhitungan:

| x      | y        | \\(x^2\\) | \\(xy\\) |
| ------ | -------- | --------- | -------- |
| 1      | 2,1      | 1         | 2,1      |
| 2      | 3,9      | 4         | 7,8      |
| 3      | 6,2      | 9         | 18,6     |
| 4      | 7,8      | 16        | 31,2     |
| **10** | **20,0** | **30**    | **59,7** |

Diketahui:

\\[ n=4 \\]

\\[ \sum x=10,\quad \sum y=20 \\]

\\[ \sum x^2=30,\quad \sum xy=59.7 \\]

Menghitung slope:

\\[ b= \frac{4(59.7)-(10)(20)} {4(30)-10^2} \\]

\\[ b=\frac{238.8-200}{120-100} \\]

\\[ b=\frac{38.8}{20} \\]

\\[ b=1.94 \\]

Menghitung intercept:

\\[ a=\frac{20-(1.94)(10)}{4} \\]

\\[ a=0.15 \\]

Dengan demikian, model regresi linear:

\\[ \boxed{y=0.15+1.94x} \\]

Jika ingin memperkirakan nilai \\(y\\) pada \\(x=2.5\\):

\\[ y=0.15+1.94(2.5) \\]

\\[ \boxed{y=5.00} \\]

### **8.3 Implementasi Python**

```
import numpy as npx = np.array([1, 2, 3, 4], dtype=float)y = np.array([2.1, 3.9, 6.2, 7.8], dtype=float)n = len(x)# Menghitung slopeb = (    n * np.sum(x*y) - np.sum(x)*np.sum(y)) / (    n * np.sum(x**2) - np.sum(x)**2)# Menghitung intercepta = (np.sum(y) - b*np.sum(x)) / n# Prediksix_pred = 2.5y_pred = a + b*x_predprint("Intercept:", a)print("Slope:", b)print("Model: y =", a, "+", b, "x")print("Prediksi pada x=2.5:", y_pred)
```

Hasil:

```
Intercept: 0.15
Slope: 1.94
Model: y = 0.15 + 1.94 x
Prediksi pada x=2.5: 5.0
```

### **8.4 Evaluasi model regresi**

Salah satu ukuran evaluasi yang dapat digunakan adalah koefisien determinasi:

\\[ R^2= 1-\frac{SSE}{SST} \\]

Dengan:

\\[ SST=\sum\_{i=1}^{n}(y_i-\bar y)^2 \\]

Nilai \\(R^2\\) menggambarkan proporsi variasi data yang dapat dijelaskan oleh model regresi.

Nilai \\(R^2\\) yang semakin mendekati satu menunjukkan kecocokan model yang semakin tinggi terhadap data pada sampel yang dianalisis. Namun, nilai tersebut tidak otomatis menjamin model cocok untuk prediksi di luar rentang data.

Implementasi Python:

```
import numpy as npy_actual = yy_predicted = a + b*xSSE = np.sum((y_actual - y_predicted)**2)SST = np.sum((y_actual - np.mean(y_actual))**2)R_squared = 1 - SSE/SSTprint("SSE:", SSE)print("R-squared:", R_squared)
```

## **9. Studi Kasus Teknik Elektro: Kalibrasi Sensor Temperatur**

### **9.1 Deskripsi kasus**

Sebuah sensor temperatur digunakan untuk mengukur perubahan temperatur pada suatu sistem elektronik.

Sensor menghasilkan tegangan keluaran yang berubah mengikuti temperatur lingkungan.

Berdasarkan proses pengukuran, diperoleh data:

| Temperatur (°C) | Tegangan sensor (V) |
| --------------- | ------------------- |
| 10              | 0,5                 |
| 20              | 1,0                 |
| 30              | 1,5                 |
| 40              | 2,0                 |

Tujuan analisis adalah memperkirakan tegangan sensor ketika temperatur berada pada 25°C.

### **9.2 Penyelesaian menggunakan interpolasi linear**

Gunakan dua titik terdekat:

\\[ (x_0,y_0)=(20,1.0) \\]

\\[ (x_1,y_1)=(30,1.5) \\]

Nilai estimasi:

\\[ x=25 \\]

Substitusi:

\\[ y=1.0+ \frac{25-20}{30-20}(1.5-1.0) \\]

\\[ y=1.0+0.5(0.5) \\]

\\[ \boxed{y=1.25\text{ V}} \\]

### **9.3 Penyelesaian menggunakan Lagrange dan Newton**

Dengan menggunakan seluruh empat titik data, kedua metode interpolasi polinomial juga menghasilkan:

\\[ \boxed{y=1.25\text{ V}} \\]

Hal ini terjadi karena seluruh data memiliki hubungan linear yang konsisten.

Dalam kasus data yang memiliki pola nonlinear, interpolasi polinomial dapat menghasilkan bentuk fungsi yang berbeda dari interpolasi linear.

### **9.4 Implementasi Python dan visualisasi**

```
import numpy as npimport matplotlib.pyplot as plt# Data pengukurantemperatur = np.array([10, 20, 30, 40], dtype=float)tegangan = np.array([0.5, 1.0, 1.5, 2.0], dtype=float)# Titik estimasix_estimasi = 25# Interpolasi lineary_estimasi = np.interp(    x_estimasi,    temperatur,    tegangan)print("Temperatur:", x_estimasi, "°C")print("Estimasi tegangan:", y_estimasi, "V")# Visualisasix_plot = np.linspace(10, 40, 100)y_plot = np.interp(x_plot, temperatur, tegangan)plt.figure(figsize=(8, 5))plt.plot(    temperatur,    tegangan,    'o',    label="Data Pengukuran")plt.plot(    x_plot,    y_plot,
```

### **9.5 Interpretasi hasil**

Berdasarkan hasil perhitungan, ketika temperatur berada pada 25°C, tegangan keluaran sensor diperkirakan sebesar 1,25 V.

Nilai tersebut merupakan hasil estimasi berdasarkan hubungan data pengukuran yang tersedia.

Dalam penerapan sebenarnya, kualitas estimasi dipengaruhi oleh karakteristik sensor, ketelitian alat ukur, kondisi lingkungan, serta jumlah dan distribusi titik kalibrasi.

## **10. Analisis Galat dan Evaluasi Interpolasi**

Hasil interpolasi dan aproksimasi perlu dievaluasi agar dapat diketahui tingkat ketelitian model.

Jika nilai sebenarnya tersedia, galat absolut dapat dihitung:

\\[ E_a=|y\_{\text{sebenarnya}}-y\_{\text{estimasi}}| \\]

Galat relatif:

\\[ E_r= \frac{ |y\_{\text{sebenarnya}}-y\_{\text{estimasi}}| }{ |y\_{\text{sebenarnya}}| } \\]

Persentase galat:

\\[ E_p=E_r\times100\\% \\]

Namun, dalam praktik pengukuran sensor, nilai sebenarnya sering tidak diketahui secara pasti. Oleh karena itu, evaluasi dapat menggunakan:

- Residual terhadap data pengamatan.
- SSE dan RMSE untuk model regresi.
- Perbandingan dengan alat ukur referensi.
- Validasi menggunakan data pengukuran tambahan.
- Analisis perilaku model pada rentang interpolasi.

Perlu diperhatikan bahwa interpolasi polinomial melewati seluruh titik data yang digunakan, sehingga residual pada titik-titik tersebut secara matematis bernilai nol. Hal ini bukan berarti model pasti akurat pada titik lain atau bebas dari kesalahan pengukuran.

## **11. Kesalahan Umum dalam Interpolasi dan Aproksimasi**

Beberapa kesalahan yang perlu dihindari:

1. Menganggap interpolasi dan regresi merupakan metode yang sama.
2. Menggunakan interpolasi untuk memperkirakan nilai jauh di luar rentang data.
3. Salah memasukkan koordinat titik data.
4. Menggunakan titik data dengan nilai \\(x\\) yang sama pada interpolasi polinomial.
5. Mengabaikan pengaruh noise dan ketidakpastian pengukuran.
6. Menggunakan polinomial berderajat tinggi tanpa mempertimbangkan kemungkinan osilasi.
7. Menganggap nilai \\(R^2\\) tinggi selalu menjamin kemampuan prediksi yang baik.
8. Tidak melakukan evaluasi terhadap model yang dihasilkan.

## **12. Rangkuman**

Pada pertemuan ini, mahasiswa telah mempelajari:

- Konsep interpolasi dan aproksimasi.
- Perbedaan interpolasi, ekstrapolasi, dan regresi.
- Metode interpolasi linear.
- Metode interpolasi polinomial Lagrange.
- Metode Newton Divided Difference.
- Metode regresi linear menggunakan least squares.
- Implementasi metode interpolasi dan regresi menggunakan Python.
- Visualisasi hasil interpolasi.
- Evaluasi model menggunakan galat, residual, SSE, dan \\(R^2\\).
- Penerapan interpolasi untuk kalibrasi sensor temperatur dalam bidang Teknik Elektro.

## **13. Referensi Pembelajaran**

1. Chapra, S. C., & Canale, R. P. *Numerical Methods for Engineers*. McGraw-Hill.
2. Burden, R. L., Faires, J. D., & Burden, A. M. *Numerical Analysis*. Cengage Learning.
3. Sauer, T. *Numerical Analysis*. Pearson.
4. Kiusalaas, J. *Numerical Methods in Engineering with Python 3*. Cambridge University Press.
5. Montgomery, D. C., Peck, E. A., & Vining, G. G. *Introduction to Linear Regression Analysis*. Wiley.
