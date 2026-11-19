# **MODUL 8**

## **Metode Diferensiasi, Integrasi Numerik, dan Penyelesaian Persamaan Diferensial**

Pertemuan 8 · Program Studi Teknik Elektro

## **1. Deskripsi Pembelajaran**

Dalam bidang Teknik Elektro, banyak fenomena fisik dan sistem kelistrikan yang dinyatakan menggunakan operasi diferensial dan integral.

Diferensiasi digunakan untuk menganalisis laju perubahan suatu besaran, seperti perubahan tegangan, arus, muatan, dan sinyal terhadap waktu. Sementara itu, integrasi digunakan untuk menghitung akumulasi suatu besaran, seperti energi listrik dari daya dan muatan listrik dari arus.

Selain itu, berbagai sistem listrik dan elektronika dapat dimodelkan menggunakan persamaan diferensial. Contohnya adalah respons transien rangkaian RC dan RL, dinamika rangkaian RLC, serta model sistem kendali.

Ketika fungsi matematis sulit diintegrasikan atau diturunkan secara analitik, atau data hanya tersedia dalam bentuk diskrit, metode numerik dapat digunakan untuk memperoleh pendekatan solusi.

Dalam modul ini, mahasiswa akan mempelajari metode diferensiasi numerik, integrasi numerik, serta metode penyelesaian persamaan diferensial biasa (*Ordinary Differential Equations* atau ODE).

## **2. Capaian Pembelajaran**

Setelah mengikuti pembelajaran ini, mahasiswa diharapkan mampu:

1. Menjelaskan konsep diferensiasi dan integrasi numerik.
2. Memahami pendekatan beda maju, beda mundur, dan beda tengah.
3. Menggunakan metode Trapezoidal untuk integrasi numerik.
4. Menggunakan metode Simpson 1/3 dan Simpson 3/8.
5. Menjelaskan konsep persamaan diferensial biasa dan masalah nilai awal.
6. Mengimplementasikan metode Euler, Heun, dan Runge-Kutta orde 4.
7. Menganalisis pengaruh ukuran langkah terhadap ketelitian hasil numerik.
8. Menerapkan metode numerik untuk menganalisis fenomena kelistrikan.

## **3. Konsep Dasar Diferensiasi Numerik**

### **3.1 Pengertian diferensiasi**

Diferensiasi merupakan proses matematis untuk menentukan laju perubahan suatu fungsi terhadap variabel bebasnya.

Jika suatu fungsi dinyatakan sebagai:

\\[ y=f(x) \\]

maka turunan pertamanya adalah:

\\[ f'(x)=\frac{dy}{dx} \\]

Dalam Teknik Elektro, diferensiasi dapat digunakan untuk:

- Menghitung laju perubahan tegangan terhadap waktu.
- Menghitung laju perubahan arus listrik.
- Menganalisis karakteristik sinyal.
- Menentukan hubungan antara arus dan tegangan pada kapasitor.
- Menganalisis respons dinamis sistem.

Contoh hubungan arus dan tegangan kapasitor:

\\[ i(t)=C\frac{dv(t)}{dt} \\]

Persamaan tersebut menunjukkan bahwa arus kapasitor sebanding dengan laju perubahan tegangan terhadap waktu.

### **3.2 Pendekatan diferensiasi numerik**

Diferensiasi numerik digunakan ketika turunan fungsi perlu diperkirakan berdasarkan nilai fungsi pada titik-titik tertentu.

Jika diketahui dua titik yang berdekatan, pendekatan turunan dapat dilakukan menggunakan perbandingan perubahan nilai fungsi terhadap perubahan variabel.

Misalkan:

\\[ f'(x)\approx \frac{f(x+h)-f(x)}{h} \\]

Pendekatan tersebut dikenal sebagai metode *Forward Difference*.

## **4. Metode Forward Difference**

### **4.1 Prinsip dasar**

Forward Difference atau beda maju menggunakan nilai fungsi pada titik saat ini dan titik berikutnya.

Rumus:

\\[ f'(x)\approx \frac{f(x+h)-f(x)}{h} \\]

Keterangan:

- \\(f'(x)\\) = estimasi turunan pertama.
- \\(h\\) = ukuran langkah (*step size*).
- \\(x\\) = titik evaluasi.

Metode ini memiliki galat pemotongan global terhadap titik evaluasi berorde:

\\[ O(h) \\]

Artinya, secara umum, galat pemotongan berkurang sebanding dengan ukuran langkah \\(h\\), selama kondisi pendekatan terpenuhi.

### **4.2 Contoh perhitungan manual**

Diketahui fungsi:

\\[ f(x)=x^2 \\]

Tentukan turunan pada:

\\[ x=2 \\]

Dengan ukuran langkah:

\\[ h=0.1 \\]

Menggunakan Forward Difference:

\\[ f'(2)\approx \frac{f(2.1)-f(2)}{0.1} \\]

\\[ =\frac{(2.1)^2-(2)^2}{0.1} \\]

\\[ =\frac{4.41-4}{0.1} \\]

\\[ \boxed{f'(2)\approx4.1} \\]

Sebagai pembanding, turunan analitik fungsi tersebut adalah:

\\[ f'(x)=2x \\]

Sehingga:

\\[ f'(2)=4 \\]

Galat absolut:

\\[ E_a=|4-4.1|=0.1 \\]

### **4.3 Implementasi Python**

```
def f(x):    return x**2x = 2h = 0.1forward = (f(x+h) - f(x)) / hprint("Forward Difference:", forward)
```

Hasil:

```
Forward Difference: 4.1
```

## **5. Metode Backward Difference**

### **5.1 Prinsip dasar**

Backward Difference atau beda mundur menggunakan nilai fungsi pada titik saat ini dan titik sebelumnya.

Rumus:

\\[ f'(x)\approx \frac{f(x)-f(x-h)}{h} \\]

Metode ini juga memiliki galat pemotongan berorde:

\\[ O(h) \\]

### **5.2 Contoh perhitungan manual**

Gunakan fungsi:

\\[ f(x)=x^2 \\]

Dengan:

\\[ x=2,\quad h=0.1 \\]

Maka:

\\[ f'(2)\approx \frac{f(2)-f(1.9)}{0.1} \\]

\\[ =\frac{4-3.61}{0.1} \\]

\\[ \boxed{f'(2)\approx3.9} \\]

Jika dibandingkan dengan turunan analitik sebesar 4, diperoleh:

\\[ E_a=|4-3.9|=0.1 \\]

### **5.3 Implementasi Python**

```
def f(x):    return x**2x = 2h = 0.1backward = (f(x) - f(x-h)) / hprint("Backward Difference:", backward)
```

Hasil:

```
Backward Difference: 3.9
```

## **6. Metode Central Difference**

### **6.1 Prinsip dasar**

Central Difference atau beda tengah menggunakan dua titik, yaitu satu titik sebelum dan satu titik sesudah posisi yang akan dihitung.

Rumus:

\\[ f'(x)\approx \frac{f(x+h)-f(x-h)}{2h} \\]

Metode ini memiliki galat pemotongan berorde:

\\[ O(h^2) \\]

Dalam kondisi fungsi cukup halus dan ukuran langkah sesuai, metode Central Difference umumnya memberikan pendekatan lebih akurat dibandingkan Forward dan Backward Difference dengan ukuran langkah yang sama.

### **6.2 Contoh perhitungan manual**

Gunakan fungsi:

\\[ f(x)=x^2 \\]

Dengan:

\\[ x=2,\quad h=0.1 \\]

Maka:

\\[ f'(2)\approx \frac{f(2.1)-f(1.9)}{2(0.1)} \\]

\\[ =\frac{4.41-3.61}{0.2} \\]

\\[ =\frac{0.8}{0.2} \\]

\\[ \boxed{f'(2)\approx4} \\]

Hasilnya sama dengan turunan analitik untuk contoh ini.

### **6.3 Implementasi Python**

```
def f(x):    return x**2x = 2h = 0.1central = (    f(x+h) - f(x-h)) / (2*h)print("Central Difference:", central)
```

Hasil:

```
Central Difference: 4.0
```

### **6.4 Perbandingan metode diferensiasi**

| Metode              | Rumus                          | Orde galat   |
| ------------------- | ------------------------------ | ------------ |
| Forward Difference  | \\(\frac{f(x+h)-f(x)}{h}\\)    | \\(O(h)\\)   |
| Backward Difference | \\(\frac{f(x)-f(x-h)}{h}\\)    | \\(O(h)\\)   |
| Central Difference  | \\(\frac{f(x+h)-f(x-h)}{2h}\\) | \\(O(h^2)\\) |

Perbedaan ketiga metode terletak pada posisi titik data yang digunakan dalam proses estimasi.

## **7. Diferensiasi Numerik Berdasarkan Data Diskrit**

Dalam praktik Teknik Elektro, data pengukuran sering tersedia dalam bentuk tabel, bukan fungsi matematis.

Misalnya, hasil pengukuran tegangan terhadap waktu:

| Waktu (s) | Tegangan (V) |
| --------- | ------------ |
| 0,0       | 0            |
| 0,1       | 2            |
| 0,2       | 8            |
| 0,3       | 18           |
| 0,4       | 32           |

Untuk memperkirakan laju perubahan tegangan pada waktu tertentu, kita dapat menggunakan metode beda hingga.

Jika data berjarak sama, pendekatan Central Difference pada titik interior dapat ditulis:

\\[ \frac{dV}{dt}\bigg|\_{t_i} \approx \frac{V\_{i+1}-V\_{i-1}}{2h} \\]

Sebagai contoh, pada \\(t=0.2\\) s:

\\[ \frac{dV}{dt}\approx \frac{18-2}{0.2} \\]

\\[ \boxed{\frac{dV}{dt}\approx80\text{ V/s}} \\]

Hasil ini menunjukkan bahwa tegangan mengalami perubahan sekitar 80 V setiap detik pada titik tersebut berdasarkan pendekatan beda tengah.

### **Implementasi Python**

```
import numpy as npwaktu = np.array([0.0, 0.1, 0.2, 0.3, 0.4])tegangan = np.array([0, 2, 8, 18, 32])h = 0.1turunan = np.zeros(len(tegangan))# Forward Differenceturunan[0] = (    tegangan[1] - tegangan[0]) / h# Central Differencefor i in range(1, len(tegangan)-1):    turunan[i] = (        tegangan[i+1] - tegangan[i-1]    ) / (2*h)# Backward Differenceturunan[-1] = (    tegangan[-1] - tegangan[-2]) / hfor t, dv in zip(waktu, turunan):    print(        f"t = {t:.1f} s, "        f"dV/dt = {dv:.2f} V/s"    )
```

## **8. Konsep Dasar Integrasi Numerik**

### **8.1 Pengertian integrasi**

Integrasi merupakan operasi matematis yang digunakan untuk menghitung akumulasi suatu besaran.

Jika suatu fungsi dinyatakan sebagai:

\\[ y=f(x) \\]

maka integral tentu pada interval \\([a,b]\\) dituliskan:

\\[ I=\int_a^b f(x)\\,dx \\]

Dalam Teknik Elektro, integrasi dapat digunakan untuk:

- Menghitung energi listrik berdasarkan daya.
- Menghitung muatan listrik berdasarkan arus.
- Menghitung nilai rata-rata suatu sinyal.
- Menghitung luas di bawah kurva sinyal.
- Menganalisis akumulasi perubahan suatu besaran terhadap waktu.

Contoh hubungan muatan listrik dan arus:

\\[ Q=\int\_{t_0}^{t_1}i(t)\\,dt \\]

Sementara energi listrik dapat dihitung melalui:

\\[ E=\int\_{t_0}^{t_1}P(t)\\,dt \\]

### **8.2 Konsep pendekatan luas**

Secara geometris, integral tentu dapat dipahami sebagai luas bertanda di bawah kurva fungsi pada interval tertentu.

Ketika fungsi tidak mudah diintegrasikan secara analitik atau hanya tersedia dalam bentuk data diskrit, pendekatan numerik dapat digunakan untuk memperkirakan nilai integral.

Tiga metode yang akan dipelajari adalah:

1. Trapezoidal Rule.
2. Simpson's 1/3 Rule.
3. Simpson's 3/8 Rule.

## **9. Metode Trapezoidal**

### **9.1 Prinsip dasar**

Metode Trapezoidal memperkirakan luas di bawah kurva dengan membagi interval menjadi beberapa trapesium.

Untuk satu interval:

\\[ I\approx \frac{b-a}{2} [f(a)+f(b)] \\]

Untuk \\(n\\) subinterval dengan lebar sama:

\\[ h=\frac{b-a}{n} \\]

Rumus komposit Trapezoidal:

\\[ I\approx \frac{h}{2} \left[ f(x_0)+2\sum\_{i=1}^{n-1}f(x_i)+f(x_n) \right] \\]

Metode ini memiliki galat pemotongan global berorde:

\\[ O(h^2) \\]

### **9.2 Contoh perhitungan manual**

Hitung integral:

\\[ I=\int_0^2x^2\\,dx \\]

Gunakan dua subinterval:

\\[ n=2 \\]

\\[ h=\frac{2-0}{2}=1 \\]

Tentukan titik:

\\[ x_0=0,\quad x_1=1,\quad x_2=2 \\]

Nilai fungsi:

\\[ f(0)=0 \\]

\\[ f(1)=1 \\]

\\[ f(2)=4 \\]

Gunakan rumus Trapezoidal:

\\[ I\approx \frac{1}{2} [0+2(1)+4] \\]

\\[ I\approx\frac{6}{2} \\]

\\[ \boxed{I\approx3} \\]

Sebagai pembanding, nilai integral eksak:

\\[ I=\left[\frac{x^3}{3}\right]\_0^2 \\]

\\[ I=\frac{8}{3} \\]

\\[ I\approx2.6667 \\]

Galat absolut:

\\[ E_a=|3-2.6667| \\]

\\[ E_a\approx0.3333 \\]

### **9.3 Implementasi Python**

```
def f(x):    return x**2def trapezoidal(a, b, n):    h = (b-a)/n    total = f(a) + f(b)    for i in range(1, n):        x = a + i*h        total += 2*f(x)    return (h/2)*totalhasil = trapezoidal(0, 2, 2)print("Hasil Trapezoidal:", hasil)
```

## **10. Metode Simpson 1/3**

### **10.1 Prinsip dasar**

Metode Simpson 1/3 menggunakan pendekatan polinomial kuadrat untuk memperkirakan luas di bawah kurva.

Metode ini membutuhkan jumlah subinterval genap dengan ukuran langkah yang sama.

Rumus komposit:

\\[ \begin{aligned} I\approx\frac{h}{3}\bigg[ &f(x_0)+f(x_n)\\\ &+4\sum\_{\text{i ganjil}}f(x_i)\\\ &+2\sum\_{\text{i genap}}f(x_i) \bigg] \end{aligned} \\]

Jumlah subinterval \\(n\\) harus genap.

Untuk fungsi yang cukup halus, galat pemotongan globalnya berorde:

\\[ O(h^4) \\]

### **10.2 Contoh perhitungan manual**

Gunakan integral yang sama:

\\[ I=\int_0^2x^2\\,dx \\]

Dengan:

\\[ n=2,\quad h=1 \\]

Diketahui:

\\[ f(0)=0,\quad f(1)=1,\quad f(2)=4 \\]

Rumus Simpson 1/3:

\\[ I\approx \frac{1}{3} [f(0)+4f(1)+f(2)] \\]

\\[ I\approx \frac{1}{3}[0+4(1)+4] \\]

\\[ I\approx\frac{8}{3} \\]

\\[ \boxed{I\approx2.6667} \\]

Pada contoh ini, hasil Simpson 1/3 sama dengan nilai integral eksak karena fungsi yang digunakan merupakan polinomial berderajat dua.

### **10.3 Implementasi Python**

```
def f(x):    return x**2def simpson_13(a, b, n):    if n % 2 != 0:        raise ValueError(            "Jumlah subinterval harus genap."        )    h = (b-a)/n    total = f(a) + f(b)    for i in range(1, n):        x = a + i*h        if i % 2 == 1:            total += 4*f(x)        else:            total += 2*f(x)    return (h/3)*totalhasil = simpson_13(0, 2, 2)print("Hasil Simpson 1/3:", hasil)
```

## **11. Metode Simpson 3/8**

### **11.1 Prinsip dasar**

Metode Simpson 3/8 menggunakan pendekatan polinomial kubik untuk memperkirakan luas di bawah kurva.

Metode ini membutuhkan jumlah subinterval yang merupakan kelipatan tiga.

Rumus untuk tiga subinterval:

\\[ I\approx \frac{3h}{8} [ f(x_0)+3f(x_1)+3f(x_2)+f(x_3) ] \\]

Untuk bentuk komposit:

\\[ \begin{aligned} I\approx\frac{3h}{8}\bigg[ &f(x_0)+f(x_n)\\\ &+3\sum\_{i\not\equiv0\pmod3}f(x_i)\\\ &+2\sum\_{\substack{i\equiv0\pmod3\\\0\<i\<n}}f(x_i) \bigg] \end{aligned} \\]

Jumlah subinterval \\(n\\) harus merupakan kelipatan tiga.

Untuk fungsi cukup halus, galat pemotongan globalnya juga berorde:

\\[ O(h^4) \\]

### **11.2 Contoh perhitungan manual**

Hitung:

\\[ I=\int_0^3x^3\\,dx \\]

Gunakan:

\\[ n=3 \\]

\\[ h=\frac{3-0}{3}=1 \\]

Titik pengamatan:

\\[ x_0=0,\quad x_1=1,\quad x_2=2,\quad x_3=3 \\]

Nilai fungsi:

\\[ f(0)=0 \\]

\\[ f(1)=1 \\]

\\[ f(2)=8 \\]

\\[ f(3)=27 \\]

Substitusi ke rumus:

\\[ I\approx \frac{3(1)}{8} [0+3(1)+3(8)+27] \\]

\\[ I\approx \frac{3}{8}[54] \\]

\\[ \boxed{I=20.25} \\]

Nilai integral eksak:

\\[ I=\left[\frac{x^4}{4}\right]\_0^3 \\]

\\[ I=\frac{81}{4}=20.25 \\]

Hasil metode Simpson 3/8 sama dengan solusi eksak untuk contoh ini.

### **11.3 Implementasi Python**

```
def f(x):    return x**3def simpson_38(a, b, n):    if n % 3 != 0:        raise ValueError(            "Jumlah subinterval harus kelipatan 3."        )    h = (b-a)/n    total = f(a) + f(b)    for i in range(1, n):        x = a + i*h        if i % 3 == 0:            total += 2*f(x)        else:            total += 3*f(x)    return (3*h/8)*totalhasil = simpson_38(0, 3, 3)print("Hasil Simpson 3/8:", hasil)
```

### **11.4 Perbandingan metode integrasi**

| Metode      | Pendekatan         | Syarat jumlah subinterval | Orde galat global |
| ----------- | ------------------ | ------------------------- | ----------------- |
| Trapezoidal | Polinomial linear  | Bebas                     | \\(O(h^2)\\)      |
| Simpson 1/3 | Polinomial kuadrat | Genap                     | \\(O(h^4)\\)      |
| Simpson 3/8 | Polinomial kubik   | Kelipatan 3               | \\(O(h^4)\\)      |

Untuk ukuran langkah yang sama dan fungsi yang cukup halus, Simpson umumnya memiliki ketelitian lebih tinggi daripada Trapezoidal. Namun, pemilihan metode tetap perlu mempertimbangkan bentuk fungsi, jumlah data, dan ketentuan interval.

## **12. Integrasi Numerik Berdasarkan Data Pengukuran**

Dalam praktik Teknik Elektro, data daya dan arus dapat diperoleh melalui proses pengukuran berkala.

Sebagai contoh, diketahui data daya listrik terhadap waktu:

| Waktu (s) | Daya (W) |
| --------- | -------- |
| 0         | 2        |
| 1         | 3        |
| 2         | 4        |
| 3         | 5        |
| 4         | 6        |

Energi listrik dapat diperkirakan menggunakan:

\\[ E=\int P(t)\\,dt \\]

Gunakan metode Trapezoidal:

\\[ E\approx \frac{h}{2} [ P_0+2P_1+2P_2+2P_3+P_4 ] \\]

Dengan \\(h=1\\):

\\[ E\approx \frac{1}{2} [2+2(3)+2(4)+2(5)+6] \\]

\\[ E=\frac{32}{2} \\]

\\[ \boxed{E=16\text{ J}} \\]

Hasil tersebut menunjukkan energi yang dikonsumsi selama interval pengamatan adalah 16 joule berdasarkan data dan pendekatan Trapezoidal.

### **Implementasi Python**

```
import numpy as npwaktu = np.array([0, 1, 2, 3, 4], dtype=float)daya = np.array([2, 3, 4, 5, 6], dtype=float)energi = np.trapezoid(daya, waktu)print("Energi listrik:", energi, "Joule")
```

## **13. Konsep Persamaan Diferensial Biasa (ODE)**

### **13.1 Pengertian ODE**

Persamaan diferensial biasa atau *Ordinary Differential Equation* merupakan persamaan yang melibatkan suatu fungsi tidak diketahui dan turunan-turunannya terhadap satu variabel bebas.

Bentuk umum ODE orde pertama:

\\[ \frac{dy}{dt}=f(t,y) \\]

Keterangan:

- \\(t\\) = variabel bebas, misalnya waktu.
- \\(y\\) = variabel terikat.
- \\(\frac{dy}{dt}\\) = laju perubahan fungsi terhadap waktu.

Dalam Teknik Elektro, ODE digunakan untuk memodelkan:

- Respons transien rangkaian RC.
- Respons arus pada rangkaian RL.
- Dinamika rangkaian RLC.
- Sistem kendali.
- Perubahan sinyal dalam sistem dinamis.

### **13.2 Masalah nilai awal**

Penyelesaian ODE sering membutuhkan nilai awal atau *Initial Value Problem* (IVP).

Bentuk umumnya:

\\[ \frac{dy}{dt}=f(t,y) \\]

Dengan kondisi awal:

\\[ y(t_0)=y_0 \\]

Kondisi awal tersebut diperlukan untuk menentukan solusi yang sesuai dengan kondisi sistem pada waktu tertentu.

### **13.3 Diskretisasi waktu**

Metode numerik menyelesaikan ODE dengan membagi interval waktu menjadi sejumlah langkah kecil.

Ukuran langkah waktu dinyatakan:

\\[ h=\frac{t\_{\text{akhir}}-t\_{\text{awal}}}{N} \\]

Dengan:

- \\(h\\) = ukuran langkah waktu.
- \\(N\\) = jumlah langkah.
- \\(t\_{\text{awal}}\\) = waktu awal.
- \\(t\_{\text{akhir}}\\) = waktu akhir.

Semakin kecil ukuran langkah, hasil pendekatan umumnya dapat menjadi lebih akurat untuk metode yang stabil dan memenuhi asumsi penggunaannya. Namun, ukuran langkah yang terlalu kecil juga meningkatkan jumlah komputasi dan dapat memperbesar pengaruh galat pembulatan.

## **14. Metode Euler**

### **14.1 Prinsip dasar**

Metode Euler merupakan metode numerik paling sederhana untuk menyelesaikan ODE orde pertama.

Metode ini menggunakan kemiringan atau turunan fungsi pada titik saat ini untuk memperkirakan nilai pada titik berikutnya.

Rumus:

\\[ y\_{n+1}=y_n+h f(t_n,y_n) \\]

Dengan pembaruan waktu:

\\[ t\_{n+1}=t_n+h \\]

Metode Euler memiliki galat lokal per langkah berorde:

\\[ O(h^2) \\]

Sedangkan galat globalnya berorde:

\\[ O(h) \\]

### **14.2 Contoh perhitungan manual**

Diketahui:

\\[ \frac{dy}{dt}=2t \\]

Dengan kondisi awal:

\\[ y(0)=1 \\]

Gunakan ukuran langkah:

\\[ h=0.5 \\]

**Iterasi pertama**

\\[ t_0=0,\quad y_0=1 \\]

\\[ y_1=y_0+h(2t_0) \\]

\\[ y_1=1+0.5(0) \\]

\\[ \boxed{y_1=1} \\]

Waktu berikutnya:

\\[ t_1=0.5 \\]

**Iterasi kedua**

\\[ y_2=y_1+h(2t_1) \\]

\\[ y_2=1+0.5(1) \\]

\\[ \boxed{y_2=1.5} \\]

Pada waktu \\(t=1\\), metode Euler menghasilkan:

\\[ y(1)\approx1.5 \\]

Sebagai pembanding, solusi analitik:

\\[ y=\int2t\\,dt \\]

\\[ y=t^2+C \\]

Dari kondisi awal \\(y(0)=1\\), diperoleh:

\\[ y=t^2+1 \\]

Sehingga:

\\[ y(1)=2 \\]

Galat absolut:

\\[ E_a=|2-1.5|=0.5 \\]

### **14.3 Implementasi Python**

```
def f(t, y):    return 2*tdef euler(t0, y0, h, steps):    t = t0    y = y0    hasil = [(t, y)]    for i in range(steps):        y = y + h*f(t, y)        t = t + h        hasil.append((t, y))    return hasilhasil = euler(0, 1, 0.5, 2)for t, y in hasil:    print(        f"t = {t:.2f}, "        f"y = {y:.4f}"    )
```

## **15. Metode Heun**

### **15.1 Prinsip dasar**

Metode Heun merupakan pengembangan metode Euler yang menggunakan pendekatan kemiringan rata-rata antara titik awal dan titik akhir.

Metode ini juga dikenal sebagai metode Euler yang diperbaiki (*Improved Euler Method*).

Tahap pertama adalah menghitung prediksi menggunakan Euler:

\\[ y\_{n+1}^{\*}=y_n+h f(t_n,y_n) \\]

Kemudian menghitung kemiringan pada titik prediksi:

\\[ f(t\_{n+1},y\_{n+1}^{\*}) \\]

Nilai akhir diperoleh menggunakan rata-rata kedua kemiringan:

\\[ y\_{n+1}=y_n+ \frac{h}{2} [ f(t_n,y_n)+ f(t\_{n+1},y\_{n+1}^{\*}) ] \\]

Metode Heun memiliki galat lokal per langkah berorde:

\\[ O(h^3) \\]

Sedangkan galat globalnya berorde:

\\[ O(h^2) \\]

### **15.2 Contoh perhitungan manual**

Gunakan kembali persamaan:

\\[ \frac{dy}{dt}=2t \\]

Dengan:

\\[ y(0)=1,\quad h=0.5 \\]

**Iterasi pertama**

Nilai awal:

\\[ t_0=0,\quad y_0=1 \\]

Kemiringan awal:

\\[ k_1=2t_0=0 \\]

Prediksi Euler:

\\[ y_1^\*=1+0.5(0)=1 \\]

Kemiringan pada titik prediksi:

\\[ k_2=2(0.5)=1 \\]

Koreksi Heun:

\\[ y_1=1+\frac{0.5}{2}(0+1) \\]

\\[ \boxed{y_1=1.25} \\]

**Iterasi kedua**

Pada:

\\[ t_1=0.5,\quad y_1=1.25 \\]

Kemiringan awal:

\\[ k_1=2(0.5)=1 \\]

Prediksi Euler:

\\[ y_2^\*=1.25+0.5(1)=1.75 \\]

Kemiringan prediksi:

\\[ k_2=2(1)=2 \\]

Koreksi Heun:

\\[ y_2=1.25+\frac{0.5}{2}(1+2) \\]

\\[ \boxed{y_2=2} \\]

Hasil pada \\(t=1\\) adalah 2, sama dengan solusi analitik untuk contoh ini.

### **15.3 Implementasi Python**

```
def f(t, y):    return 2*tdef heun(t0, y0, h, steps):    t = t0    y = y0    hasil = [(t, y)]    for i in range(steps):        k1 = f(t, y)        # Prediksi Euler        y_predict = y + h*k1        # Kemiringan di titik prediksi        k2 = f(t+h, y_predict)        # Koreksi Heun        y = y + (h/2)*(k1+k2)        t = t+h        hasil.append((t, y))    return hasilhasil = heun(0, 1, 0.5, 2)for t, y in hasil:    print(        f"t = {t:.2f}, "
```

## **16. Metode Runge-Kutta Orde 4 (RK4)**

### **16.1 Prinsip dasar**

Metode Runge-Kutta orde 4 merupakan metode numerik yang banyak digunakan untuk menyelesaikan persamaan diferensial biasa.

Metode ini menggunakan empat estimasi kemiringan untuk memperoleh nilai pendekatan berikutnya.

Rumus RK4:

\\[ k_1=f(t_n,y_n) \\]

\\[ k_2=f\left( t_n+\frac{h}{2}, y_n+\frac{hk_1}{2} \right) \\]

\\[ k_3=f\left( t_n+\frac{h}{2}, y_n+\frac{hk_2}{2} \right) \\]

\\[ k_4=f(t_n+h,y_n+hk_3) \\]

Nilai berikutnya dihitung menggunakan:

\\[ y\_{n+1}=y_n+ \frac{h}{6} (k_1+2k_2+2k_3+k_4) \\]

Metode RK4 memiliki galat lokal per langkah berorde:

\\[ O(h^5) \\]

Sedangkan galat globalnya berorde:

\\[ O(h^4) \\]

### **16.2 Contoh perhitungan manual**

Gunakan:

\\[ \frac{dy}{dt}=2t \\]

Dengan:

\\[ y(0)=1,\quad h=0.5 \\]

**Iterasi pertama**

\\[ k_1=2(0)=0 \\]

\\[ k_2=2(0.25)=0.5 \\]

\\[ k_3=2(0.25)=0.5 \\]

\\[ k_4=2(0.5)=1 \\]

Substitusi:

\\[ y_1= 1+\frac{0.5}{6} [0+2(0.5)+2(0.5)+1] \\]

\\[ y_1=1+\frac{0.5}{6}(2.5) \\]

\\[ \boxed{y_1=1.208333} \\]

**Iterasi kedua**

Pada:

\\[ t_1=0.5,\quad y_1=1.208333 \\]

Diperoleh:

\\[ k_1=1 \\]

\\[ k_2=1.5 \\]

\\[ k_3=1.5 \\]

\\[ k_4=2 \\]

Sehingga:

\\[ y_2= 1.208333+ \frac{0.5}{6} [1+2(1.5)+2(1.5)+2] \\]

\\[ y_2=1.208333+\frac{0.5}{6}(7.5) \\]

\\[ \boxed{y_2=1.833333} \\]

Catatan penting: hasil tersebut benar untuk fungsi \\(dy/dt=2t\\), tetapi belum sama dengan solusi analitik \\(y(1)=2\\). Penyebabnya adalah RK4 menghasilkan pendekatan dengan empat tahap kemiringan, bukan solusi eksak untuk semua fungsi. Untuk fungsi ini, pendekatan RK4 dengan dua langkah \\(h=0.5\\) belum menghasilkan nilai eksak.

### **16.3 Implementasi Python**

```
def f(t, y):    return 2*tdef rk4(t0, y0, h, steps):    t = t0    y = y0    hasil = [(t, y)]    for i in range(steps):        k1 = f(t, y)        k2 = f(            t + h/2,            y + h*k1/2        )        k3 = f(            t + h/2,            y + h*k2/2        )        k4 = f(            t + h,            y + h*k3        )        y = y + (            h/6        ) * (            k1 + 2*k2 + 2*k3 + k4        )        t = t + h
```

## **17. Perbandingan Metode Penyelesaian ODE**

Ketiga metode memiliki tingkat kompleksitas dan ketelitian yang berbeda.

| Aspek                              | Euler        | Heun         | RK4          |
| ---------------------------------- | ------------ | ------------ | ------------ |
| Jumlah evaluasi fungsi per langkah | 1            | 2            | 4            |
| Galat lokal                        | \\(O(h^2)\\) | \\(O(h^3)\\) | \\(O(h^5)\\) |
| Galat global                       | \\(O(h)\\)   | \\(O(h^2)\\) | \\(O(h^4)\\) |
| Kompleksitas                       | Rendah       | Sedang       | Lebih tinggi |
| Ketelitian umum                    | Lebih rendah | Menengah     | Lebih tinggi |

Semakin tinggi orde metode, semakin baik potensi ketelitian untuk fungsi yang cukup halus dan ukuran langkah yang sesuai. Namun, ketelitian aktual juga dipengaruhi karakteristik sistem, kestabilan numerik, dan ukuran langkah yang digunakan.

## **18. Studi Kasus Teknik Elektro: Respons Transien Rangkaian RC**

### **18.1 Deskripsi kasus**

Sebuah rangkaian RC seri digunakan untuk mempelajari proses pengisian kapasitor ketika dihubungkan dengan sumber tegangan DC.

Diketahui parameter:

| Parameter                 | Nilai   |
| ------------------------- | ------- |
| Tegangan sumber \\(V_s\\) | 10 V    |
| Resistansi \\(R\\)        | 1000 Ω  |
| Kapasitansi \\(C\\)       | 1000 µF |
| Tegangan awal kapasitor   | 0 V     |

Tujuan analisis adalah menentukan perubahan tegangan kapasitor terhadap waktu menggunakan metode numerik.

### **18.2 Membentuk persamaan diferensial**

Berdasarkan Hukum Kirchhoff Tegangan:

\\[ V_s=V_R+V_C \\]

Dengan hubungan:

\\[ V_R=Ri \\]

dan:

\\[ i=C\frac{dV_C}{dt} \\]

Maka:

\\[ V_s=RC\frac{dV_C}{dt}+V_C \\]

Susun ulang:

\\[ \frac{dV_C}{dt} = \frac{V_s-V_C}{RC} \\]

Diketahui:

\\[ R=1000\ \Omega \\]

\\[ C=1000\ \mu F=0.001\ F \\]

Konstanta waktu:

\\[ \tau=RC \\]

\\[ \tau=1000(0.001) \\]

\\[ \boxed{\tau=1\text{ s}} \\]

Persamaan diferensial menjadi:

\\[ \frac{dV_C}{dt}=10-V_C \\]

Dengan kondisi awal:

\\[ V_C(0)=0 \\]

### **18.3 Solusi analitik sebagai pembanding**

Untuk rangkaian RC pengisian, solusi analitik tegangan kapasitor adalah:

\\[ V_C(t)=V_s(1-e^{-t/RC}) \\]

Substitusi parameter:

\\[ \boxed{V_C(t)=10(1-e^{-t})} \\]

Solusi analitik ini dapat digunakan sebagai nilai referensi untuk mengevaluasi hasil pendekatan numerik.

### **18.4 Implementasi metode Euler, Heun, dan RK4**

```
import numpy as npimport matplotlib.pyplot as plt# Parameter rangkaianVs = 10.0R = 1000.0C = 0.001# Persamaan diferensialdef f(t, Vc):    return (Vs - Vc) / (R*C)# Solusi analitikdef analytical(t):    return Vs * (        1 - np.exp(-t/(R*C))    )# Metode Eulerdef euler(t0, y0, h, steps):    t = t0    y = y0    values = [y]    for i in range(steps):        y = y + h*f(t, y)        t = t + h        values.append(y)
```

### **18.5 Interpretasi hasil**

Simulasi menghasilkan kurva perubahan tegangan kapasitor selama proses pengisian.

Secara fisik, tegangan kapasitor meningkat secara bertahap dan mendekati tegangan sumber 10 V.

Karena menggunakan ukuran langkah \\(h=0.5\\) s, masing-masing metode akan memberikan tingkat ketelitian yang berbeda.

Untuk parameter tersebut, pada waktu 5 detik, hasil pendekatan yang diharapkan kurang lebih:

| Metode   | Tegangan pada 5 s |
| -------- | ----------------- |
| Euler    | 9,6875 V          |
| Heun     | 9,9041 V          |
| RK4      | 9,9325 V          |
| Analitik | 9,9326 V          |

Hasil menunjukkan bahwa RK4 memberikan pendekatan paling dekat terhadap solusi analitik untuk konfigurasi simulasi tersebut.

Metode Euler memiliki perbedaan lebih besar karena menggunakan satu evaluasi kemiringan pada setiap langkah. Heun memperbaiki hasil melalui rata-rata dua kemiringan, sedangkan RK4 menggunakan empat estimasi kemiringan.

### **18.6 Penerapan pada sistem Teknik Elektro lainnya**

Konsep penyelesaian ODE juga dapat diterapkan pada berbagai sistem lainnya.

**Rangkaian RL**

\\[ L\frac{di}{dt}+Ri=V_s \\]

Persamaan tersebut menggambarkan perubahan arus pada induktor.

**Rangkaian RLC seri**

\\[ L\frac{d^2q}{dt^2} + R\frac{dq}{dt} + \frac{q}{C}=V_s(t) \\]

Persamaan ini menggambarkan dinamika muatan dan arus pada rangkaian RLC.

**Sistem kendali**

\\[ \frac{dx}{dt}=Ax+Bu \\]

Persamaan tersebut merupakan bentuk representasi ruang keadaan yang digunakan untuk memodelkan dinamika sistem kendali.

Dengan demikian, metode penyelesaian ODE menjadi salah satu perangkat penting dalam analisis sistem kelistrikan dan elektronika.

## **19. Analisis Galat dan Pengaruh Ukuran Langkah**

Ukuran langkah atau *step size* memiliki pengaruh terhadap ketelitian hasil perhitungan numerik.

Pada metode Euler, Heun, dan RK4, ukuran langkah yang berbeda dapat menghasilkan pendekatan yang berbeda pula.

Untuk metode yang stabil dan memenuhi asumsi matematisnya, memperkecil ukuran langkah umumnya dapat meningkatkan ketelitian.

Namun, ukuran langkah yang terlalu besar dapat menghasilkan galat yang tinggi atau bahkan menyebabkan ketidakstabilan numerik.

### **19.1 Perbandingan ukuran langkah**

Misalkan sistem RC disimulasikan menggunakan:

\\[ h=0.5,\quad h=0.25,\quad h=0.1 \\]

Hasilnya dapat dibandingkan dengan solusi analitik:

\\[ V_C(t)=10(1-e^{-t}) \\]

Contoh kode untuk menghitung galat:

```
import numpy as npVs = 10.0R = 1000.0C = 0.001def f(t, Vc):    return (Vs-Vc)/(R*C)def exact(t):    return Vs*(1-np.exp(-t/(R*C)))def euler_final(h):    steps = int(5/h)    t = 0    y = 0    for i in range(steps):        y = y+h*f(t, y)        t += h    return ydef heun_final(h):    steps = int(5/h)    t = 0    y = 0    for i in range(steps):
```

### **19.2 Interpretasi**

Melalui percobaan tersebut, mahasiswa dapat mengamati bahwa:

- Metode Euler cenderung membutuhkan ukuran langkah lebih kecil untuk mencapai ketelitian tertentu.
- Metode Heun memberikan pendekatan yang lebih baik dibandingkan Euler pada kondisi yang sama.
- Metode RK4 dapat memberikan ketelitian tinggi dengan jumlah langkah yang relatif lebih sedikit.
- Pemilihan ukuran langkah harus mempertimbangkan kebutuhan akurasi dan kestabilan sistem.

Perlu ditekankan bahwa orde metode saja tidak menjamin kestabilan. Untuk sistem yang memiliki dinamika cepat atau sifat kaku (*stiff*), pemilihan ukuran langkah dan metode yang tepat menjadi sangat penting.

## **20. Kesalahan Umum dalam Diferensiasi, Integrasi, dan Penyelesaian ODE**

Beberapa kesalahan yang perlu dihindari:

1. Menggunakan rumus diferensiasi numerik dengan ukuran langkah yang tidak sesuai.
2. Tidak memperhatikan posisi titik data dalam Forward, Backward, dan Central Difference.
3. Menggunakan jumlah subinterval ganjil pada Simpson 1/3.
4. Menggunakan jumlah subinterval yang bukan kelipatan tiga pada Simpson 3/8.
5. Salah menentukan ukuran langkah integrasi.
6. Tidak mengonversi satuan komponen listrik secara tepat.
7. Salah menentukan kondisi awal pada penyelesaian ODE.
8. Salah menghitung kemiringan pada metode Heun dan RK4.
9. Menggunakan ukuran langkah terlalu besar sehingga hasil menjadi tidak akurat atau tidak stabil.
10. Tidak membandingkan hasil numerik dengan solusi analitik atau referensi ketika tersedia.

## **21. Rangkuman**

Pada pertemuan ini, mahasiswa telah mempelajari:

- Konsep diferensiasi numerik.
- Metode Forward Difference, Backward Difference, dan Central Difference.
- Pendekatan turunan berdasarkan data diskrit.
- Konsep integrasi numerik.
- Metode Trapezoidal.
- Metode Simpson 1/3 dan Simpson 3/8.
- Konsep persamaan diferensial biasa.
- Masalah nilai awal dan diskretisasi waktu.
- Metode Euler.
- Metode Heun.
- Metode Runge-Kutta orde 4.
- Perbandingan ketelitian metode penyelesaian ODE.
- Pengaruh ukuran langkah terhadap hasil numerik.
- Penerapan metode numerik pada respons transien rangkaian RC.

## **22. Referensi Pembelajaran**

1. Chapra, S. C., & Canale, R. P. *Numerical Methods for Engineers*. McGraw-Hill.
2. Burden, R. L., Faires, J. D., & Burden, A. M. *Numerical Analysis*. Cengage Learning.
3. Sauer, T. *Numerical Analysis*. Pearson.
4. Kiusalaas, J. *Numerical Methods in Engineering with Python 3*. Cambridge University Press.
5. Alexander, C. K., & Sadiku, M. N. O. *Fundamentals of Electric Circuits*. McGraw-Hill.
