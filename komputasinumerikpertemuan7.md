# **MODULE 7**

# **DIFERENSIASI DAN INTEGRASI NUMERIK**



Komputasi Numerik

Program Studi Teknik Elektro



## **1. Deskripsi Pembelajaran**

Dalam bidang teknik elektro, banyak fenomena fisik yang melibatkan perubahan suatu besaran terhadap waktu maupun akumulasi besaran selama periode tertentu.

Contohnya:

- Perubahan tegangan listrik terhadap waktu.
- Perubahan arus listrik dalam rangkaian.
- Kecepatan perubahan sinyal sensor.
- Perhitungan energi listrik berdasarkan daya.
- Perhitungan muatan listrik berdasarkan arus.
- Analisis sinyal analog yang diperoleh dari sistem pengukuran.

Secara matematis, diferensiasi digunakan untuk menghitung laju perubahan suatu fungsi, sedangkan integrasi digunakan untuk menghitung akumulasi atau luas di bawah kurva.

Dalam kondisi ideal, diferensiasi dan integrasi dapat dihitung menggunakan kalkulus analitik. Namun, pada sistem nyata, data sering diperoleh dalam bentuk sampel pengukuran yang terpisah-pisah.

Oleh karena itu, diperlukan metode numerik untuk memperkirakan nilai turunan dan integral berdasarkan data yang tersedia.

Pada modul ini, mahasiswa akan mempelajari metode diferensiasi numerik menggunakan pendekatan selisih hingga (*finite difference*) serta integrasi numerik menggunakan metode Trapesium dan Simpson.

## **2. Capaian Pembelajaran**

Setelah mempelajari materi ini, mahasiswa diharapkan mampu:

1. Menjelaskan konsep diferensiasi dan integrasi numerik.
2. Menghitung turunan fungsi menggunakan metode selisih maju, selisih mundur, dan selisih pusat.
3. Menghitung integral tentu menggunakan metode Trapesium.
4. Menghitung integral tentu menggunakan metode Simpson 1/3 dan Simpson 3/8.
5. Mengimplementasikan metode diferensiasi dan integrasi menggunakan Python.
6. Menganalisis galat hasil perhitungan numerik.
7. Menerapkan diferensiasi dan integrasi numerik pada permasalahan teknik elektro.

# **BAGIAN A – DIFERENSIASI NUMERIK**

## **3. Konsep Dasar Diferensiasi**

### **3.1 Pengertian Diferensiasi**

Diferensiasi merupakan proses matematika untuk menghitung laju perubahan suatu fungsi terhadap variabel bebasnya.

Jika suatu fungsi dinyatakan sebagai:

\\[ y=f(x) \\]

Maka turunan pertama fungsi tersebut dinyatakan sebagai:

\\[ f'(x)=\frac{dy}{dx} \\]

Turunan pertama menunjukkan seberapa cepat nilai \\(y\\) berubah ketika nilai \\(x\\) mengalami perubahan.

Secara geometris, turunan pertama dapat diartikan sebagai kemiringan garis singgung terhadap kurva pada suatu titik.

[Application Of Derivatives Revision Notes | Super Tutor](https://images.openai.com/static-rsc-4/i1v28zLqu0xOENs2En5K0jWWR4zeQrgVnPeUFzb9JBCDqodSF4NXbkqQB9_XHB_jvzE1vC_I65YD_kKbnq8bmc_5m3Eju5PsdBiEh0m7fhlUPdVHaSYhNjHa-bFeNUmMrEOhbapiSIpuAHJxs85HnNxYoLtm0H8oh5m6vBW8Oao?purpose=inline)

[supertutor.in](https://supertutor.in/resources/exams/wbjee/revision-notes/mathematics/application-of-derivatives/?utm_source=chatgpt.com)

Sebagai contoh, diketahui fungsi:

\\[ f(x)=x^2 \\]

Turunan pertama secara analitik adalah:

\\[ f'(x)=2x \\]

Jika ingin menghitung turunan pada \\(x=3\\), maka:

\\[ f'(3)=2(3) \\]

\\[ \boxed{f'(3)=6} \\]

Namun, bagaimana jika fungsi tersebut tidak diketahui secara matematis dan kita hanya memiliki sejumlah data hasil pengukuran?

Dalam kondisi tersebut, kita dapat menggunakan diferensiasi numerik.

### **3.2 Konsep Selisih Hingga (Finite Difference)**

Diferensiasi numerik menggunakan pendekatan perubahan nilai fungsi dalam interval yang relatif kecil.

Misalkan diketahui:

\\[ y=f(x) \\]

Dengan perubahan variabel sebesar:

\\[ h=\Delta x \\]

Maka pendekatan turunan dapat dihitung menggunakan perubahan nilai fungsi.

Terdapat tiga metode dasar:

1. Forward Difference.
2. Backward Difference.
3. Central Difference.

Ketiga metode ini menggunakan pendekatan yang berbeda untuk memperkirakan turunan pertama.

## **4. Metode Forward Difference**

### **4.1 Konsep**

Forward Difference atau metode selisih maju menggunakan nilai fungsi pada titik saat ini dan titik berikutnya.

Persamaan:

\\[ \boxed{ f'(x)\approx\frac{f(x+h)-f(x)}{h} } \\]

Keterangan:

- \\(f'(x)\\) = perkiraan turunan pertama.
- \\(f(x)\\) = nilai fungsi pada titik saat ini.
- \\(f(x+h)\\) = nilai fungsi pada titik berikutnya.
- \\(h\\) = ukuran langkah (*step size*).

Metode ini menggunakan data di depan titik yang sedang dihitung.

### **4.2 Contoh Perhitungan Manual**

Diketahui:

\\[ f(x)=x^2 \\]

Hitung perkiraan turunan pertama pada:

\\[ x=2 \\]

Dengan ukuran langkah:

\\[ h=0,1 \\]

**Langkah 1: Tentukan nilai fungsi**

\\[ f(2)=2^2=4 \\]

\\[ f(2+0,1)=f(2,1) \\]

\\[ f(2,1)=2,1^2=4,41 \\]

**Langkah 2: Gunakan persamaan Forward Difference**

\\[ f'(2)\approx\frac{4,41-4}{0,1} \\]

\\[ f'(2)\approx\frac{0,41}{0,1} \\]

\\[ \boxed{f'(2)\approx4,1} \\]

Sebagai pembanding, turunan analitik fungsi tersebut adalah:

\\[ f'(x)=2x \\]

Sehingga:

\\[ f'(2)=4 \\]

Hasil pendekatan Forward Difference adalah 4,1, sedangkan nilai eksaknya adalah 4.

### **4.3 Implementasi Python**

```
def forward_difference(f, x, h):    return (f(x + h) - f(x)) / h# Fungsi yang akan dihitungdef f(x):    return x**2x = 2h = 0.1hasil = forward_difference(f, x, h)print("Hasil Forward Difference:", hasil)
```

Output:

```
Hasil Forward Difference: 4.099999999999991
```

## **5. Metode Backward Difference**

### **5.1 Konsep**

Backward Difference atau metode selisih mundur menggunakan nilai fungsi pada titik saat ini dan titik sebelumnya.

Persamaannya:

\\[ \boxed{ f'(x)\approx\frac{f(x)-f(x-h)}{h} } \\]

Metode ini menggunakan informasi dari arah belakang terhadap titik yang sedang dihitung.

### **5.2 Contoh Perhitungan Manual**

Gunakan fungsi:

\\[ f(x)=x^2 \\]

Hitung turunan pada:

\\[ x=2 \\]

Dengan:

\\[ h=0,1 \\]

**Langkah 1: Hitung nilai fungsi**

\\[ f(2)=4 \\]

\\[ f(2-0,1)=f(1,9) \\]

\\[ f(1,9)=1,9^2=3,61 \\]

**Langkah 2: Substitusi ke persamaan**

\\[ f'(2)\approx\frac{4-3,61}{0,1} \\]

\\[ f'(2)\approx\frac{0,39}{0,1} \\]

\\[ \boxed{f'(2)\approx3,9} \\]

Hasil pendekatan adalah 3,9, sedangkan nilai turunan sebenarnya adalah 4.

### **5.3 Implementasi Python**

```
def backward_difference(f, x, h):    return (f(x) - f(x - h)) / hdef f(x):    return x**2x = 2h = 0.1hasil = backward_difference(f, x, h)print("Hasil Backward Difference:", hasil)
```

Output:

```
Hasil Backward Difference: 3.900000000000002
```

## **6. Metode Central Difference**

### **6.1 Konsep**

Central Difference atau metode selisih pusat menggunakan nilai fungsi pada dua sisi titik yang sedang dihitung.

Metode ini memperhitungkan nilai di depan dan di belakang titik.

Persamaannya:

\\[ \boxed{ f'(x)\approx \frac{f(x+h)-f(x-h)}{2h} } \\]

Metode ini umumnya memiliki tingkat akurasi yang lebih baik dibandingkan Forward Difference dan Backward Difference untuk fungsi yang cukup halus dan ukuran langkah yang sesuai.

### **6.2 Contoh Perhitungan Manual**

Diketahui:

\\[ f(x)=x^2 \\]

Hitung turunan pada:

\\[ x=2 \\]

Dengan:

\\[ h=0,1 \\]

**Langkah 1: Hitung nilai fungsi**

\\[ f(2,1)=4,41 \\]

\\[ f(1,9)=3,61 \\]

**Langkah 2: Gunakan persamaan Central Difference**

\\[ f'(2)\approx\frac{4,41-3,61}{2(0,1)} \\]

\\[ f'(2)\approx\frac{0,8}{0,2} \\]

\\[ \boxed{f'(2)\approx4} \\]

Hasilnya sama dengan nilai turunan analitik.

### **6.3 Implementasi Python**

```
def central_difference(f, x, h):    return (f(x + h) - f(x - h)) / (2 * h)def f(x):    return x**2x = 2h = 0.1hasil = central_difference(f, x, h)print("Hasil Central Difference:", hasil)
```

Output:

```
Hasil Central Difference: 4.0000000000000036
```

## **7. Perbandingan Metode Diferensiasi**

Ketiga metode memiliki karakteristik berbeda.

| Metode              | Persamaan                      | Orde galat pemotongan |
| ------------------- | ------------------------------ | --------------------- |
| Forward Difference  | \\(\frac{f(x+h)-f(x)}{h}\\)    | \\(O(h)\\)            |
| Backward Difference | \\(\frac{f(x)-f(x-h)}{h}\\)    | \\(O(h)\\)            |
| Central Difference  | \\(\frac{f(x+h)-f(x-h)}{2h}\\) | \\(O(h^2)\\)          |

Keterangan:

\\(O(h)\\) dan \\(O(h^2)\\) menunjukkan orde galat pemotongan (*truncation error*). Untuk fungsi yang cukup mulus, galat pemotongan Central Difference berkurang lebih cepat ketika \\(h\\) diperkecil.

**Interpretasi:**

- Forward Difference sesuai ketika data tersedia mulai dari titik saat ini ke arah depan.
- Backward Difference sesuai ketika data sebelumnya tersedia.
- Central Difference umumnya lebih akurat jika data tersedia pada kedua sisi titik yang dihitung.

Namun, ukuran langkah \\(h\\) tidak boleh diperkecil secara sembarangan. Jika terlalu kecil, kesalahan pembulatan (*round-off error*) dapat meningkat akibat pengurangan dua nilai fungsi yang hampir sama.

## **8. Diferensiasi Numerik Berdasarkan Data Pengukuran**

Dalam praktik teknik elektro, mahasiswa sering kali tidak memiliki persamaan fungsi yang diketahui. Data yang tersedia hanya berupa hasil pengukuran.

Contohnya:

| Waktu (s) | Tegangan (V) |
| --------- | ------------ |
| 0,0       | 0            |
| 0,1       | 1            |
| 0,2       | 4            |
| 0,3       | 9            |
| 0,4       | 16           |

Misalkan kita ingin memperkirakan laju perubahan tegangan pada waktu 0,2 detik.

Data sebelum titik tersebut:

\\[ V(0,1)=1 \\]

Data setelah titik tersebut:

\\[ V(0,3)=9 \\]

Dengan Central Difference:

\\[ \frac{dV}{dt}\bigg|\_{t=0,2} \approx \frac{V(0,3)-V(0,1)}{0,3-0,1} \\]

\\[ =\frac{9-1}{0,2} \\]

\\[ \boxed{\frac{dV}{dt}\approx40\text{ V/s}} \\]

Artinya, pada sekitar waktu 0,2 detik, tegangan mengalami perubahan dengan laju sekitar 40 volt per detik.

Contoh Python:

```
import numpy as npwaktu = np.array([0.0, 0.1, 0.2, 0.3, 0.4])tegangan = np.array([0, 1, 4, 9, 16])# Turunan pada titik tengahi = 2hasil = (    tegangan[i + 1] - tegangan[i - 1]) / (    waktu[i + 1] - waktu[i - 1])print("Laju perubahan tegangan:", hasil, "V/s")
```

Output:

```
Laju perubahan tegangan: 40.0 V/s
```

Perlu diperhatikan bahwa hasil tersebut adalah perkiraan turunan lokal berdasarkan data pengukuran, bukan bukti bahwa bentuk sinyal sebenarnya mengikuti fungsi tertentu.

# **BAGIAN B – INTEGRASI NUMERIK**

## **9. Konsep Dasar Integrasi**

### **9.1 Pengertian Integrasi**

Integrasi merupakan proses matematika untuk menghitung akumulasi suatu fungsi pada interval tertentu.

Jika diketahui fungsi:

\\[ y=f(x) \\]

Maka integral tentu pada interval \\(a\\) sampai \\(b\\) dinyatakan sebagai:

\\[ \boxed{ I=\int_a^b f(x)\\,dx } \\]

Secara geometris, integral tentu dapat diartikan sebagai luas bertanda di bawah kurva fungsi pada interval tersebut.

[Integral Operator](https://images.openai.com/static-rsc-4/UtVvMLnniVZ9tcvrsU4GH2hholpXtzt3F4EwxrCAsm3jY_66qsGq-PeFuqyWL2PUj4dw6YV37mZwvrcX_0dDwyUuMKZcyfY95ScSta2-rbUkNtUzmtAAAvjwefObsjc3qXBPEtF51x8N7105DN4pPF32O_q9eEgCq18oasaDz2E?purpose=inline)

[wumbo.net](https://wumbo.net/operators/integral/?utm_source=chatgpt.com)

Dalam teknik elektro, integrasi dapat digunakan untuk:

- Menghitung energi listrik dari daya terhadap waktu.
- Menghitung muatan listrik dari arus terhadap waktu.
- Menghitung nilai rata-rata sinyal.
- Menghitung akumulasi perubahan suatu besaran.
- Menganalisis respons sistem berdasarkan data pengukuran.

### **9.2 Mengapa Menggunakan Integrasi Numerik?**

Jika fungsi diketahui secara matematis, integral dapat dihitung menggunakan teknik kalkulus analitik.

Namun, pada sistem pengukuran, sering kali kita hanya memiliki sekumpulan titik data.

Misalnya, sensor daya mengirimkan data pengukuran setiap 0,1 detik.

Untuk menghitung energi selama periode pengamatan, kita perlu memperkirakan luas di bawah kurva daya terhadap waktu.

Integrasi numerik membantu melakukan perhitungan tersebut.

## **10. Metode Trapesium (Trapezoidal Rule)**

### **10.1 Konsep Metode Trapesium**

Metode Trapesium merupakan metode integrasi numerik yang memperkirakan luas di bawah kurva dengan membaginya menjadi beberapa bentuk trapesium.

Untuk satu interval, luas trapesium dihitung berdasarkan rata-rata tinggi kedua sisi dikalikan lebar interval.

Persamaan dasar:

\\[ \boxed{ I\approx\frac{b-a}{2}[f(a)+f(b)] } \\]

Jika interval dibagi menjadi \\(n\\) bagian dengan lebar sama:

\\[ h=\frac{b-a}{n} \\]

Maka persamaan komposit Trapesium menjadi:

\\[ \boxed{ I\approx\frac{h}{2} \left[ f(x_0)+2\sum\_{i=1}^{n-1}f(x_i)+f(x_n) \right] } \\]

Keterangan:

- \\(a\\) = batas bawah integral.
- \\(b\\) = batas atas integral.
- \\(n\\) = jumlah subinterval.
- \\(h\\) = lebar setiap subinterval.
- \\(x_i\\) = titik pembagian interval.
- \\(f(x_i)\\) = nilai fungsi pada titik ke-\\(i\\).

### **10.2 Contoh Perhitungan Manual**

Diketahui:

\\[ f(x)=x^2 \\]

Hitung integral:

\\[ I=\int_0^2 x^2\\,dx \\]

Gunakan metode Trapesium dengan:

\\[ n=4 \\]

**Langkah 1: Hitung ukuran langkah**

\\[ h=\frac{2-0}{4} \\]

\\[ h=0,5 \\]

**Langkah 2: Tentukan titik pembagian**

\\[ x_0=0 \\]

\\[ x_1=0,5 \\]

\\[ x_2=1 \\]

\\[ x_3=1,5 \\]

\\[ x_4=2 \\]

**Langkah 3: Hitung nilai fungsi**

| \\(x_i\\) | \\(f(x_i)=x_i^2\\) |
| --------- | ------------------ |
| 0         | 0                  |
| 0,5       | 0,25               |
| 1,0       | 1                  |
| 1,5       | 2,25               |
| 2,0       | 4                  |

**Langkah 4: Substitusikan ke persamaan Trapesium**

\\[ I\approx\frac{0,5}{2} [0+2(0,25+1+2,25)+4] \\]

\\[ I\approx0,25[0+7+4] \\]

\\[ I\approx0,25(11) \\]

\\[ \boxed{I\approx2,75} \\]

Sebagai pembanding, integral analitiknya adalah:

\\[ \int x^2dx=\frac{x^3}{3} \\]

Sehingga:

\\[ I=\left[\frac{x^3}{3}\right]\_0^2 \\]

\\[ I=\frac{8}{3} \\]

\\[ \boxed{I\approx2,6667} \\]

Jadi, metode Trapesium menghasilkan pendekatan 2,75.

### **10.3 Implementasi Python**

```
def trapezoidal_rule(f, a, b, n):    if n <= 0:        raise ValueError("Jumlah subinterval harus positif")    h = (b - a) / n    total = f(a) + f(b)    for i in range(1, n):        x = a + i * h        total += 2 * f(x)    return (h / 2) * totaldef f(x):    return x**2hasil = trapezoidal_rule(f, 0, 2, 4)print("Hasil integrasi Trapesium:", hasil)
```

Output:

```
Hasil integrasi Trapesium: 2.75
```

### **10.4 Kelebihan dan Keterbatasan**

Kelebihan:

- Relatif mudah dipahami dan diimplementasikan.
- Dapat digunakan pada data pengukuran.
- Tidak membutuhkan turunan fungsi.
- Dapat diterapkan pada fungsi yang sulit diintegralkan secara analitik.

Keterbatasan:

- Akurasi dipengaruhi jumlah subinterval.
- Pendekatan garis lurus kurang akurat untuk kurva yang sangat melengkung.
- Membutuhkan lebih banyak subinterval untuk meningkatkan ketelitian pada beberapa jenis fungsi.

## **11. Metode Simpson 1/3**

### **11.1 Konsep Metode Simpson 1/3**

Metode Simpson 1/3 memperkirakan luas di bawah kurva menggunakan polinomial kuadrat atau parabola.

Berbeda dengan metode Trapesium yang menggunakan garis lurus, Simpson 1/3 menggunakan pendekatan kurva parabola pada setiap dua subinterval.

Persamaan Simpson 1/3 untuk satu kelompok dua subinterval:

\\[ \boxed{ I\approx\frac{h}{3} [f(x_0)+4f(x_1)+f(x_2)] } \\]

Untuk banyak subinterval, persamaan kompositnya adalah:

\\[ \boxed{ I\approx\frac{h}{3} \left[ f(x_0) +4\sum\_{\text{indeks ganjil}}f(x_i) +2\sum\_{\substack{\text{indeks genap}\\\i\neq0,n}}f(x_i) +f(x_n) \right] } \\]

**Syarat penting:** Jumlah subinterval \\(n\\) harus genap dan jarak antar titik harus sama.

### **11.2 Contoh Perhitungan Manual**

Gunakan kembali fungsi:

\\[ f(x)=x^2 \\]

Hitung:

\\[ I=\int_0^2x^2\\,dx \\]

Dengan:

\\[ n=4 \\]

Ukuran langkah:

\\[ h=\frac{2-0}{4}=0,5 \\]

Data fungsi:

| \\(x_i\\) | \\(f(x_i)\\) |
| --------- | ------------ |
| 0         | 0            |
| 0,5       | 0,25         |
| 1,0       | 1            |
| 1,5       | 2,25         |
| 2,0       | 4            |

Substitusi ke persamaan Simpson 1/3:

\\[ I\approx\frac{0,5}{3} [ 0+4(0,25)+2(1)+4(2,25)+4 ] \\]

\\[ I\approx\frac{0,5}{3} [0+1+2+9+4] \\]

\\[ I\approx\frac{0,5}{3}(16) \\]

\\[ \boxed{I\approx2,6667} \\]

Hasil tersebut sama dengan nilai integral analitik karena Simpson 1/3 dapat mengintegralkan polinomial hingga derajat tiga secara tepat, dengan asumsi perhitungan aritmetika ideal.

### **11.3 Implementasi Python**

```
def simpson_13(f, a, b, n):    if n <= 0 or n % 2 != 0:        raise ValueError(            "Jumlah subinterval harus positif dan genap"        )    h = (b - a) / n    total = f(a) + f(b)    for i in range(1, n):        x = a + i * h        if i % 2 == 1:            total += 4 * f(x)        else:            total += 2 * f(x)    return (h / 3) * totaldef f(x):    return x**2hasil = simpson_13(f, 0, 2, 4)print("Hasil integrasi Simpson 1/3:", hasil)
```

Output:

```
Hasil integrasi Simpson 1/3: 2.6666666666666665
```

## **12. Metode Simpson 3/8**

### **12.1 Konsep Metode Simpson 3/8**

Simpson 3/8 merupakan metode integrasi numerik yang menggunakan pendekatan polinomial kubik pada tiga subinterval.

Metode ini membagi interval menjadi tiga bagian dengan panjang yang sama.

Persamaan untuk satu kelompok tiga subinterval:

\\[ \boxed{ I\approx\frac{3h}{8} [f(x_0)+3f(x_1)+3f(x_2)+f(x_3)] } \\]

Untuk banyak kelompok:

\\[ \boxed{ I\approx\frac{3h}{8} \left[ f(x_0)+f(x_n) +3\sum\_{\substack{i=1\\\i\not\equiv0\ (3)}}^{n-1}f(x_i) +2\sum\_{\substack{i=3\\\i\equiv0\ (3)}}^{n-3}f(x_i) \right] } \\]

**Syarat penting:** Jumlah subinterval \\(n\\) harus merupakan kelipatan tiga dan jarak antar titik harus sama.

### **12.2 Contoh Perhitungan Manual**

Diketahui:

\\[ f(x)=x^2 \\]

Hitung:

\\[ I=\int_0^3x^2\\,dx \\]

Dengan:

\\[ n=3 \\]

**Langkah 1: Hitung ukuran langkah**

\\[ h=\frac{3-0}{3}=1 \\]

**Langkah 2: Tentukan nilai fungsi**

| \\(x_i\\) | \\(f(x_i)=x_i^2\\) |
| --------- | ------------------ |
| 0         | 0                  |
| 1         | 1                  |
| 2         | 4                  |
| 3         | 9                  |

**Langkah 3: Gunakan Simpson 3/8**

\\[ I\approx\frac{3(1)}{8} [0+3(1)+3(4)+9] \\]

\\[ I\approx\frac{3}{8}[24] \\]

\\[ \boxed{I=9} \\]

Nilai integral analitik:

\\[ I=\left[\frac{x^3}{3}\right]\_0^3 \\]

\\[ I=9 \\]

Hasil Simpson 3/8 sama dengan hasil eksak.

### **12.3 Implementasi Python**

```
def simpson_38(f, a, b, n):    if n <= 0 or n % 3 != 0:        raise ValueError(            "Jumlah subinterval harus kelipatan 3"        )    h = (b - a) / n    total = f(a) + f(b)    for i in range(1, n):        x = a + i * h        if i % 3 == 0:            total += 2 * f(x)        else:            total += 3 * f(x)    return (3 * h / 8) * totaldef f(x):    return x**2hasil = simpson_38(f, 0, 3, 3)print("Hasil integrasi Simpson 3/8:", hasil)
```

Output:

```
Hasil integrasi Simpson 3/8: 9.0
```

## **13. Perbandingan Metode Integrasi Numerik**

| Aspek               | Trapesium      | Simpson 1/3               | Simpson 3/8                             |
| ------------------- | -------------- | ------------------------- | --------------------------------------- |
| Pendekatan          | Garis lurus    | Parabola                  | Polinomial kubik                        |
| Jumlah subinterval  | Bebas, positif | Genap                     | Kelipatan 3                             |
| Orde galat komposit | \\(O(h^2)\\)   | \\(O(h^4)\\)              | \\(O(h^4)\\)                            |
| Kompleksitas        | Rendah         | Sedang                    | Sedang                                  |
| Karakteristik       | Sederhana      | Akurat untuk fungsi halus | Alternatif untuk kelompok tiga interval |

Untuk fungsi yang cukup halus, metode Simpson umumnya memberikan akurasi lebih tinggi dibandingkan metode Trapesium pada ukuran langkah yang sama.

Namun, pemilihan metode tetap bergantung pada karakteristik data, jumlah sampel, interval, dan ketersediaan titik pengukuran.

# **BAGIAN C – ANALISIS GALAT**

## **14. Analisis Galat pada Diferensiasi dan Integrasi**

Hasil diferensiasi dan integrasi numerik merupakan pendekatan terhadap nilai matematis yang sebenarnya.

Oleh karena itu, kita perlu melakukan evaluasi galat.

### **14.1 Galat Absolut**

\\[ E_a=|I\_{\text{eksak}}-I\_{\text{numerik}}| \\]

Misalnya hasil integral eksak:

\\[ I\_{\text{eksak}}=2,6667 \\]

Hasil metode Trapesium:

\\[ I\_{\text{numerik}}=2,75 \\]

Maka:

\\[ E_a=|2,6667-2,75| \\]

\\[ \boxed{E_a\approx0,0833} \\]

### **14.2 Galat Relatif**

\\[ E_r= \frac{E_a}{|I\_{\text{eksak}}|} \\]

### **14.3 Persentase Galat**

\\[ E_p=E_r\times100\\% \\]

Contoh implementasi:

```
nilai_eksak = 8 / 3nilai_numerik = 2.75galat_absolut = abs(    nilai_eksak - nilai_numerik)galat_relatif = (    galat_absolut / abs(nilai_eksak))galat_persen = galat_relatif * 100print("Nilai Eksak:", nilai_eksak)print("Nilai Numerik:", nilai_numerik)print("Galat Absolut:", galat_absolut)print("Galat Relatif:", galat_relatif)print("Galat Persen:", galat_persen, "%")
```

### **14.4 Faktor yang Memengaruhi Galat**

Beberapa faktor yang memengaruhi akurasi metode diferensiasi dan integrasi adalah:

1. Ukuran langkah \\(h\\).
2. Jumlah titik pengukuran.
3. Karakteristik fungsi yang dihitung.
4. Tingkat perubahan fungsi.
5. Noise pada data pengukuran.
6. Kesalahan pembulatan komputer.

Khusus diferensiasi numerik, ukuran langkah yang terlalu besar dapat menghasilkan galat pemotongan yang besar. Sebaliknya, ukuran langkah yang terlalu kecil dapat memperbesar dampak galat pembulatan.

Dalam integrasi numerik, penambahan subinterval umumnya membantu meningkatkan ketelitian untuk fungsi yang cukup halus, tetapi kualitas data pengukuran tetap harus diperhatikan.

# **BAGIAN D – STUDI KASUS TEKNIK ELEKTRO**

## **15. Studi Kasus 1: Menghitung Energi Listrik dari Data Daya**

### **15.1 Deskripsi Kasus**

Sebuah sistem monitoring listrik mencatat daya listrik yang dikonsumsi oleh suatu perangkat setiap 0,1 detik.

Data pengukuran:

| Waktu (s) | Daya (W) |
| --------- | -------- |
| 0,0       | 10       |
| 0,1       | 12       |
| 0,2       | 15       |
| 0,3       | 14       |
| 0,4       | 11       |

Tujuan:

Menghitung estimasi energi listrik yang dikonsumsi selama 0,4 detik menggunakan metode Trapesium.

### **15.2 Konsep Matematis**

Energi listrik merupakan akumulasi daya terhadap waktu.

\\[ E=\int\_{t_0}^{t_1}P(t)\\,dt \\]

Keterangan:

- \\(E\\) = energi listrik dalam joule.
- \\(P(t)\\) = daya listrik dalam watt.
- \\(t\\) = waktu dalam sekon.

Karena data daya tersedia dalam bentuk sampel, kita gunakan metode integrasi numerik.

### **15.3 Perhitungan Manual**

Diketahui:

\\[ h=0,1 \\]

Gunakan persamaan Trapesium:

\\[ E\approx\frac{h}{2} [P_0+2(P_1+P_2+P_3)+P_4] \\]

Substitusi:

\\[ E\approx\frac{0,1}{2} [10+2(12+15+14)+11] \\]

\\[ E\approx0,05[10+82+11] \\]

\\[ E\approx0,05(103) \\]

\\[ \boxed{E=5,15\text{ J}} \\]

Jadi, estimasi energi yang dikonsumsi selama periode pengamatan adalah 5,15 joule.

### **15.4 Implementasi Python**

```
import numpy as np# Data pengukuranwaktu = np.array([0.0, 0.1, 0.2, 0.3, 0.4])daya = np.array([10, 12, 15, 14, 11])# Menghitung energi dengan metode Trapesiumenergi = np.trapezoid(daya, waktu)print("Estimasi energi:", energi, "Joule")
```

Output:

```
Estimasi energi: 5.15 Joule
```

Pada contoh ini, kita menggunakan `numpy.trapezoid()` untuk memverifikasi perhitungan. Dalam latihan algoritma, mahasiswa tetap perlu memahami dan mengimplementasikan metode Trapesium sendiri.

## **16. Studi Kasus 2: Menghitung Muatan Listrik dari Arus**

### **16.1 Deskripsi Kasus**

Sebuah rangkaian listrik memiliki arus yang berubah terhadap waktu.

Hasil pengukuran arus:

| Waktu (s) | Arus (A) |
| --------- | -------- |
| 0,0       | 0        |
| 0,1       | 2        |
| 0,2       | 4        |
| 0,3       | 6        |
| 0,4       | 8        |

Hitung muatan listrik yang mengalir selama 0,4 detik.

### **16.2 Konsep Matematis**

Muatan listrik merupakan integral arus terhadap waktu.

\\[ Q=\int\_{t_0}^{t_1}I(t)\\,dt \\]

Keterangan:

- \\(Q\\) = muatan listrik dalam coulomb.
- \\(I(t)\\) = arus listrik dalam ampere.
- \\(t\\) = waktu dalam sekon.

### **16.3 Penyelesaian Menggunakan Metode Simpson 1/3**

Diketahui:

\\[ h=0,1 \\]

Jumlah subinterval:

\\[ n=4 \\]

Gunakan persamaan Simpson 1/3:

\\[ Q\approx\frac{h}{3} [I_0+4(I_1+I_3)+2I_2+I_4] \\]

Substitusi:

\\[ Q\approx\frac{0,1}{3} [0+4(2+6)+2(4)+8] \\]

\\[ Q\approx\frac{0,1}{3} [0+32+8+8] \\]

\\[ Q\approx\frac{0,1}{3}(48) \\]

\\[ \boxed{Q=1,6\text{ C}} \\]

Jadi, muatan listrik yang mengalir selama 0,4 detik adalah 1,6 coulomb.

### **16.4 Implementasi Python**

```
import numpy as npwaktu = np.array([0.0, 0.1, 0.2, 0.3, 0.4])arus = np.array([0, 2, 4, 6, 8])h = 0.1muatan = (h / 3) * (    arus[0]    + 4 * (arus[1] + arus[3])    + 2 * arus[2]    + arus[4])print("Muatan listrik:", muatan, "Coulomb")
```

Output:

```
Muatan listrik: 1.6 Coulomb
```

## **17. Studi Kasus 3: Analisis Perubahan Tegangan terhadap Waktu**

### **17.1 Deskripsi Kasus**

Sebuah sistem monitoring mencatat perubahan tegangan pada suatu rangkaian selama proses pengujian.

Data pengukuran:

| Waktu (s) | Tegangan (V) |
| --------- | ------------ |
| 0,0       | 0            |
| 0,1       | 1            |
| 0,2       | 4            |
| 0,3       | 9            |
| 0,4       | 16           |

Hitung laju perubahan tegangan pada waktu 0,2 detik menggunakan metode Central Difference.

### **17.2 Penyelesaian**

Persamaan:

\\[ \frac{dV}{dt}\approx \frac{V(t+h)-V(t-h)}{2h} \\]

Diketahui:

\\[ t=0,2,\quad h=0,1 \\]

\\[ V(0,3)=9 \\]

\\[ V(0,1)=1 \\]

Maka:

\\[ \frac{dV}{dt}\approx \frac{9-1}{2(0,1)} \\]

\\[ \boxed{\frac{dV}{dt}=40\text{ V/s}} \\]

### **17.3 Interpretasi**

Nilai 40 V/s menunjukkan perkiraan laju perubahan tegangan pada sekitar waktu 0,2 detik.

Dalam analisis rangkaian, informasi perubahan tegangan terhadap waktu dapat membantu memahami karakteristik respons sistem, khususnya ketika terjadi perubahan kondisi operasi atau transien.

## **18. Visualisasi Data Pengukuran Menggunakan Python**

Agar mahasiswa dapat melihat hubungan antara data pengukuran dan hasil perhitungan numerik, kita dapat membuat grafik sederhana.

Contoh berikut memperlihatkan daya listrik terhadap waktu.

```
import numpy as npimport matplotlib.pyplot as plt# Data pengukuranwaktu = np.array([0.0, 0.1, 0.2, 0.3, 0.4])daya = np.array([10, 12, 15, 14, 11])# Menghitung energienergi = np.trapezoid(daya, waktu)# Membuat grafikplt.figure(figsize=(8, 5))plt.plot(    waktu,    daya,    marker="o",    label="Data Daya")plt.fill_between(    waktu,    daya,    alpha=0.2)plt.xlabel("Waktu (s)")plt.ylabel("Daya (W)")plt.title("Pengukuran Daya terhadap Waktu")plt.grid(True)plt.legend()plt.show()print("Estimasi Energi:", energi, "J")
```

[BEN: Měření práce elektrického proudu          —         Elektrika.cz, reportážní portál instalační elektrotechniky, vyhlášky, schémata zapojení .](https://images.openai.com/static-rsc-4/PcFkid2tj8-OxAabf51xl65hzqkl0eyNbCjcLUM_Ogsp0f4XbXsOHYgsscq_qrXJxF7VcHFEaTDmcEhfUg33OHTZ0xqZNB-NBidvj9AQTyeid6g459SbKSJI2fg8NxFpVBmv2KRO8o6xwbmiQzwZbx13u29Vv98jHNujK8W4dho?purpose=inline)

[elektrika.cz](https://elektrika.cz/data/clanky/ben-mereni-prace-elektrickeho-proudu?utm_source=chatgpt.com)

Area di bawah kurva daya terhadap waktu merepresentasikan energi yang dikonsumsi selama periode pengamatan.

Dengan demikian, mahasiswa dapat menghubungkan konsep integral dengan interpretasi fisik suatu sistem listrik.

## **19. Ringkasan Metode dan Rumus Penting**

Berikut rangkuman rumus yang perlu dipahami mahasiswa.

### **Diferensiasi Numerik**

| Metode              | Rumus                          |
| ------------------- | ------------------------------ |
| Forward Difference  | \\(\frac{f(x+h)-f(x)}{h}\\)    |
| Backward Difference | \\(\frac{f(x)-f(x-h)}{h}\\)    |
| Central Difference  | \\(\frac{f(x+h)-f(x-h)}{2h}\\) |

### **Integrasi Numerik**

| Metode      | Rumus                                                                               |
| ----------- | ----------------------------------------------------------------------------------- |
| Trapesium   | \\(\frac{h}{2}[f_0+2\sum f_i+f_n]\\)                                                |
| Simpson 1/3 | \\(\frac{h}{3}[f_0+4\sum\_{\text{ganjil}}f_i+2\sum\_{\text{genap}}f_i+f_n]\\)       |
| Simpson 3/8 | \\(\frac{3h}{8}[f_0+f_n+3\sum\_{i\not\equiv0\ (3)}f_i+2\sum\_{i\equiv0\ (3)}f_i]\\) |

### **Konsep Evaluasi Galat**

\\[ E_a=|I\_{\text{eksak}}-I\_{\text{numerik}}| \\]

\\[ E_r=\frac{E_a}{|I\_{\text{eksak}}|} \\]

\\[ E_p=E_r\times100\\% \\]

## **20. Kesalahan Umum yang Perlu Dihindari**

| Kesalahan                                        | Dampak                                        | Solusi                                                        |
| ------------------------------------------------ | --------------------------------------------- | ------------------------------------------------------------- |
| Salah menentukan nilai \\(h\\)                   | Hasil turunan atau integral tidak tepat       | Hitung interval dengan benar                                  |
| Salah memilih Forward atau Backward              | Menggunakan data yang tidak sesuai            | Perhatikan posisi titik pengukuran                            |
| Mengabaikan Central Difference                   | Kehilangan potensi akurasi                    | Gunakan jika data tersedia di kedua sisi                      |
| Jumlah subinterval Simpson 1/3 ganjil            | Metode tidak memenuhi syarat                  | Gunakan jumlah subinterval genap                              |
| Jumlah subinterval Simpson 3/8 bukan kelipatan 3 | Metode tidak memenuhi syarat                  | Gunakan kelipatan tiga                                        |
| Data waktu tidak seragam                         | Rumus komposit standar tidak berlaku langsung | Gunakan formula untuk interval tidak seragam atau metode lain |
| Mengabaikan satuan                               | Interpretasi hasil keliru                     | Periksa dimensi fisik                                         |
| Mengabaikan noise sensor                         | Turunan dapat menjadi sangat tidak stabil     | Lakukan pemeriksaan dan pengolahan data                       |

**Catatan khusus untuk diferensiasi:** Turunan numerik sangat sensitif terhadap noise pengukuran karena menghitung perubahan antara nilai yang berdekatan. Pada data sensor yang berisik, diperlukan pertimbangan filtering atau pendekatan pengolahan data sebelum menghitung turunan.

## **21. Kesimpulan Pembelajaran**

Diferensiasi dan integrasi numerik merupakan metode penting dalam penyelesaian berbagai persoalan teknik elektro.

Diferensiasi numerik memungkinkan kita memperkirakan laju perubahan suatu besaran berdasarkan data pengukuran, sedangkan integrasi numerik memungkinkan kita menghitung akumulasi besaran selama interval tertentu.

Metode Forward Difference, Backward Difference, dan Central Difference digunakan untuk menghitung turunan numerik.

Sementara itu, metode Trapesium, Simpson 1/3, dan Simpson 3/8 digunakan untuk memperkirakan nilai integral tentu.

Pemilihan metode perlu mempertimbangkan karakteristik fungsi, jumlah titik data, ukuran langkah, dan ketelitian yang dibutuhkan.

Mahasiswa diharapkan tidak hanya mampu menjalankan program Python, tetapi juga memahami prinsip matematis dan makna fisik hasil perhitungan dalam konteks sistem kelistrikan.

## **22. Referensi Pembelajaran**

1. Chapra, S. C., & Canale, R. P. *Numerical Methods for Engineers*. McGraw-Hill.
2. Burden, R. L., Faires, J. D., & Burden, A. M. *Numerical Analysis*. Cengage Learning.
3. Sauer, T. *Numerical Analysis*. Pearson.
4. Python Documentation – [Python Official Documentation](https://docs.python.org/3/).
5. NumPy Documentation – [NumPy Official Documentation](https://numpy.org/doc/stable/).
6. Matplotlib Documentation – [Matplotlib Official Documentation](https://matplotlib.org/stable/?utm_source=chatgpt.com).

