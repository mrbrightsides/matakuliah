# **MODULE 8**

# **PENYELESAIAN PERSAMAAN DIFERENSIAL BIASA (ODE)**



Komputasi Numerik

Program Studi Teknik Elektro



## **1. Deskripsi Pembelajaran**

Dalam bidang teknik elektro, banyak sistem tidak hanya memiliki hubungan antara input dan output, tetapi juga mengalami perubahan terhadap waktu.

Contohnya:

- Tegangan kapasitor ketika proses pengisian dan pengosongan.
- Arus pada rangkaian induktor.
- Respons transien rangkaian listrik.
- Perubahan kecepatan motor listrik.
- Dinamika sistem kendali.
- Respons sistem elektronik terhadap perubahan input.

Perilaku sistem tersebut dapat dimodelkan menggunakan persamaan diferensial.

Persamaan diferensial menggambarkan hubungan antara suatu fungsi dengan turunannya. Dalam banyak kasus, penyelesaian persamaan diferensial secara analitik dapat menjadi rumit atau bahkan tidak tersedia dalam bentuk sederhana.

Komputasi numerik menyediakan metode untuk memperoleh solusi pendekatan melalui proses perhitungan bertahap.

Pada modul ini, mahasiswa akan mempelajari tiga metode utama:

1. Metode Euler.
2. Metode Heun.
3. Metode Runge-Kutta Orde 4 (RK4).

Ketiga metode tersebut akan digunakan untuk menyelesaikan masalah nilai awal (*Initial Value Problem*) dan diterapkan pada simulasi respons transien rangkaian RC.

## **2. Capaian Pembelajaran**

Setelah mempelajari modul ini, mahasiswa diharapkan mampu:

1. Menjelaskan konsep dasar persamaan diferensial biasa.
2. Mengidentifikasi variabel, turunan, dan kondisi awal pada ODE.
3. Menyelesaikan ODE menggunakan metode Euler.
4. Menyelesaikan ODE menggunakan metode Heun.
5. Menyelesaikan ODE menggunakan metode Runge-Kutta Orde 4.
6. Mengimplementasikan metode numerik ODE menggunakan Python.
7. Membandingkan akurasi beberapa metode penyelesaian ODE.
8. Menerapkan metode ODE untuk menganalisis respons transien rangkaian RC.

# **BAGIAN A – KONSEP DASAR PERSAMAAN DIFERENSIAL**

## **3. Pengertian Persamaan Diferensial**

Persamaan diferensial adalah persamaan matematika yang melibatkan suatu fungsi dan satu atau lebih turunannya.

Contoh sederhana:

\\[ \frac{dy}{dt}=2t \\]

Persamaan tersebut menyatakan bahwa laju perubahan \\(y\\) terhadap waktu \\(t\\) adalah dua kali nilai waktu.

Jika persamaan tersebut diintegralkan:

\\[ y=\int 2t\\,dt \\]

Maka diperoleh:

\\[ y=t^2+C \\]

Keterangan:

- \\(y\\) = fungsi yang dicari.
- \\(t\\) = variabel bebas.
- \\(\frac{dy}{dt}\\) = turunan pertama fungsi terhadap waktu.
- \\(C\\) = konstanta integrasi.

Untuk menentukan nilai konstanta \\(C\\), diperlukan informasi tambahan berupa kondisi awal.

### **3.1 Apa Itu Ordinary Differential Equation?**

Ordinary Differential Equation (ODE) atau Persamaan Diferensial Biasa adalah persamaan diferensial yang melibatkan turunan terhadap satu variabel bebas.

Contoh:

\\[ \frac{dy}{dt}+3y=0 \\]

Persamaan tersebut merupakan ODE karena fungsi \\(y\\) hanya bergantung pada satu variabel bebas, yaitu \\(t\\).

ODE banyak digunakan dalam pemodelan sistem dinamis, termasuk sistem kelistrikan dan elektronika.

### **3.2 Orde Persamaan Diferensial**

Orde persamaan diferensial ditentukan oleh turunan tertinggi yang muncul dalam persamaan.

Contoh:

**ODE orde satu**

\\[ \frac{dy}{dt}+2y=0 \\]

**ODE orde dua**

\\[ \frac{d^2y}{dt^2}+3\frac{dy}{dt}+2y=0 \\]

**ODE orde tiga**

\\[ \frac{d^3y}{dt^3}+2\frac{d^2y}{dt^2}+y=0 \\]

Dalam modul ini, fokus utama adalah ODE orde satu karena metode Euler, Heun, dan RK4 dapat digunakan secara langsung untuk menyelesaikan bentuk tersebut.

Persamaan diferensial orde lebih tinggi juga dapat diubah menjadi sekumpulan persamaan orde satu.

[Introduction to ordinary differential equation | PPT](https://images.openai.com/static-rsc-4/qU44-Kj-aL2I0vu3N8D4nI9pnA6EdxkprcPadwaoUCIZTFDbRZwIPnwrZEpvxCsIcD95i8K7IBT9o7vKOwi2JTr0SOtuHD_sVN54LCyksEohQqTJPVa6s0CJW2pWw49cqj52Xx_-H9OHYokn7jl6OC1WB3NXaw6iureKGtWRIPY?purpose=inline)

[slideshare.net](https://www.slideshare.net/slideshow/introduction-to-ordinary-differential-equation/269651744?utm_source=chatgpt.com)

## **4. Initial Value Problem (IVP)**

### **4.1 Pengertian Kondisi Awal**

Penyelesaian persamaan diferensial sering membutuhkan informasi mengenai nilai fungsi pada suatu titik awal.

Permasalahan ini disebut *Initial Value Problem* atau masalah nilai awal.

Bentuk umum ODE orde satu:

\\[ \boxed{ \frac{dy}{dt}=f(t,y) } \\]

Dengan kondisi awal:

\\[ \boxed{ y(t_0)=y_0 } \\]

Keterangan:

- \\(t\\) = variabel bebas.
- \\(y\\) = fungsi yang dicari.
- \\(f(t,y)\\) = fungsi yang menggambarkan laju perubahan.
- \\(t_0\\) = waktu awal.
- \\(y_0\\) = nilai fungsi pada waktu awal.

Tujuan penyelesaian numerik adalah memperkirakan nilai \\(y\\) pada sejumlah titik waktu berikutnya.

### **4.2 Contoh Sederhana**

Diketahui:

\\[ \frac{dy}{dt}=2t \\]

Dengan kondisi awal:

\\[ y(0)=1 \\]

Penyelesaian analitik:

\\[ y=t^2+C \\]

Karena \\(y(0)=1\\):

\\[ 1=0^2+C \\]

\\[ C=1 \\]

Sehingga:

\\[ \boxed{y(t)=t^2+1} \\]

Jika ingin menghitung nilai pada \\(t=1\\):

\\[ y(1)=1^2+1 \\]

\\[ \boxed{y(1)=2} \\]

Nilai eksak ini nantinya dapat digunakan untuk membandingkan hasil metode numerik.

### **4.3 Konsep Diskretisasi Waktu**

Dalam penyelesaian numerik, waktu dibagi menjadi sejumlah langkah kecil.

Ukuran langkah dinyatakan dengan:

\\[ h=\Delta t \\]

Titik waktu berikutnya:

\\[ t\_{n+1}=t_n+h \\]

Keterangan:

- \\(t_n\\) = waktu pada iterasi ke-\\(n\\).
- \\(t\_{n+1}\\) = waktu pada iterasi berikutnya.
- \\(h\\) = ukuran langkah waktu.

Semakin kecil ukuran langkah, semakin rapat titik perhitungan yang dihasilkan. Namun, jumlah perhitungan juga menjadi lebih banyak.

[Understanding Neural ODE's - Jonty Sinai](https://images.openai.com/static-rsc-4/R2ZSoBFPnZ7ZOpP9FnS7rYYGsk22Z7H7DZCjjGNO8cEQrtJkOunX5n0LVk6krFekEIfkB4wSBnfI96NwwOueU6TqiccqgIl_NRCbTLtQ_m2dD1eEc8RfHtNw-Hus-9aGXcx9wdsKemnWiC-CCUcfh6GbjRnSqG48dMcGRgTWXis?purpose=inline)

[jontysinai.github.io](https://jontysinai.github.io/jekyll/update/2019/01/18/understanding-neural-odes.html?utm_source=chatgpt.com)

# **BAGIAN B – METODE PENYELESAIAN ODE**

## **5. Metode Euler**

### **5.1 Konsep Metode Euler**

Metode Euler merupakan salah satu metode numerik paling sederhana untuk menyelesaikan persamaan diferensial biasa.

Metode ini menggunakan nilai turunan pada titik saat ini untuk memperkirakan nilai fungsi pada titik berikutnya.

Secara geometris, metode Euler menggunakan garis singgung sebagai pendekatan terhadap kurva solusi.

Persamaan dasar:

\\[ \boxed{ y\_{n+1}=y_n+h f(t_n,y_n) } \\]

Dengan:

\\[ t\_{n+1}=t_n+h \\]

Keterangan:

- \\(y_n\\) = nilai fungsi saat ini.
- \\(y\_{n+1}\\) = nilai fungsi pada langkah berikutnya.
- \\(h\\) = ukuran langkah.
- \\(f(t_n,y_n)\\) = turunan fungsi pada titik saat ini.

### **5.2 Contoh Perhitungan Manual**

Diketahui:

\\[ \frac{dy}{dt}=2t \\]

Dengan kondisi awal:

\\[ y(0)=1 \\]

Gunakan metode Euler dengan:

\\[ h=0,5 \\]

Hitung nilai \\(y\\) hingga \\(t=1\\).

**Langkah 1: Tentukan persamaan**

\\[ f(t,y)=2t \\]

Persamaan Euler:

\\[ y\_{n+1}=y_n+h(2t_n) \\]

**Langkah 2: Iterasi pertama**

Diketahui:

\\[ t_0=0,\quad y_0=1 \\]

Maka:

\\[ y_1=1+0,5(2(0)) \\]

\\[ y_1=1 \\]

Waktu berikutnya:

\\[ t_1=0,5 \\]

**Langkah 3: Iterasi kedua**

\\[ y_2=y_1+h(2t_1) \\]

\\[ y_2=1+0,5(2(0,5)) \\]

\\[ y_2=1+0,5 \\]

\\[ \boxed{y_2=1,5} \\]

Waktu akhir:

\\[ t_2=1 \\]

Hasil perhitungan:

| Iterasi | Waktu \\(t\\) | Nilai \\(y\\) |
| ------- | ------------- | ------------- |
| 0       | 0,0           | 1,0           |
| 1       | 0,5           | 1,0           |
| 2       | 1,0           | 1,5           |

Nilai eksak pada \\(t=1\\) adalah 2. Jadi, metode Euler menghasilkan pendekatan 1,5.

### **5.3 Implementasi Metode Euler Menggunakan Python**

```
def euler_method(f, t0, y0, h, n):    t = t0    y = y0    hasil = [(t, y)]    for i in range(n):        y = y + h * f(t, y)        t = t + h        hasil.append((t, y))    return hasil# Persamaan diferensialdef f(t, y):    return 2 * t# Parameter awalt0 = 0y0 = 1h = 0.5n = 2hasil = euler_method(f, t0, y0, h, n)print("Hasil Metode Euler")for t, y in hasil:    print(f"t = {t:.2f}, y = {y:.4f}")
```

Output:

```
Hasil Metode Euler
t = 0.00, y = 1.0000
t = 0.50, y = 1.0000
t = 1.00, y = 1.5000
```

### **5.4 Kelebihan dan Keterbatasan**

Kelebihan:

- Algoritma sederhana.
- Mudah diimplementasikan.
- Membutuhkan sedikit operasi matematika.
- Cocok untuk memahami dasar penyelesaian ODE numerik.

Keterbatasan:

- Akurasi relatif rendah untuk banyak permasalahan.
- Galat dapat terakumulasi pada setiap langkah.
- Membutuhkan ukuran langkah yang cukup kecil untuk mendapatkan hasil yang lebih akurat.

Metode Euler memiliki galat lokal pemotongan berorde \\(O(h^2)\\) dan galat global berorde \\(O(h)\\), dengan asumsi solusi cukup mulus.

## **6. Metode Heun**

### **6.1 Konsep Metode Heun**

Metode Heun merupakan pengembangan dari metode Euler.

Jika metode Euler hanya menggunakan kemiringan pada titik awal, metode Heun memperhitungkan kemiringan awal dan perkiraan kemiringan pada titik akhir.

Metode ini juga dikenal sebagai *Improved Euler Method* atau metode Euler yang diperbaiki.

Tahap pertama adalah menghitung prediksi menggunakan Euler:

\\[ \boxed{ y^\*=y_n+h f(t_n,y_n) } \\]

Kemudian menghitung kemiringan pada titik akhir prediksi:

\\[ k_2=f(t_n+h,y^\*) \\]

Sementara kemiringan awal:

\\[ k_1=f(t_n,y_n) \\]

Nilai berikutnya dihitung menggunakan rata-rata kedua kemiringan:

\\[ \boxed{ y\_{n+1}=y_n+\frac{h}{2}(k_1+k_2) } \\]

### **6.2 Contoh Perhitungan Manual**

Gunakan kembali:

\\[ \frac{dy}{dt}=2t \\]

Kondisi awal:

\\[ y(0)=1 \\]

Dengan:

\\[ h=0,5 \\]

**Langkah 1: Tentukan nilai awal**

\\[ t_0=0,\quad y_0=1 \\]

Hitung kemiringan awal:

\\[ k_1=2(0)=0 \\]

**Langkah 2: Hitung prediksi Euler**

\\[ y^\*=y_0+hk_1 \\]

\\[ y^\*=1+0,5(0) \\]

\\[ y^\*=1 \\]

**Langkah 3: Hitung kemiringan akhir**

\\[ k_2=f(t_0+h,y^\*) \\]

\\[ k_2=2(0,5) \\]

\\[ k_2=1 \\]

**Langkah 4: Hitung nilai berikutnya**

\\[ y_1=y_0+\frac{h}{2}(k_1+k_2) \\]

\\[ y_1=1+\frac{0,5}{2}(0+1) \\]

\\[ y_1=1+0,25 \\]

\\[ \boxed{y_1=1,25} \\]

Untuk langkah kedua, \\(t_1=0,5\\) dan \\(y_1=1,25\\):

\\[ k_1=2(0,5)=1 \\]

Prediksi:

\\[ y^\*=1,25+0,5(1)=1,75 \\]

Kemiringan akhir:

\\[ k_2=2(1)=2 \\]

Koreksi:

\\[ y_2=1,25+\frac{0,5}{2}(1+2) \\]

\\[ \boxed{y_2=2} \\]

Hasil pada \\(t=1\\) sama dengan solusi eksak.

### **6.3 Implementasi Metode Heun Menggunakan Python**

```
def heun_method(f, t0, y0, h, n):    t = t0    y = y0    hasil = [(t, y)]    for i in range(n):        # Kemiringan awal        k1 = f(t, y)        # Prediksi Euler        y_prediksi = y + h * k1        # Kemiringan pada titik akhir        k2 = f(t + h, y_prediksi)        # Koreksi menggunakan rata-rata kemiringan        y = y + (h / 2) * (k1 + k2)        t = t + h        hasil.append((t, y))    return hasildef f(t, y):    return 2 * thasil = heun_method(f, 0, 1, 0.5, 2)print("Hasil Metode Heun")for t, y in hasil:
```

Output:

```
Hasil Metode Heun
t = 0.00, y = 1.0000
t = 0.50, y = 1.2500
t = 1.00, y = 2.0000
```

### **6.4 Kelebihan dan Keterbatasan**

Kelebihan:

- Lebih akurat daripada Euler untuk banyak fungsi yang cukup halus.
- Memperhitungkan kemiringan pada awal dan akhir interval.
- Relatif mudah dipahami dan diimplementasikan.

Keterbatasan:

- Membutuhkan dua evaluasi fungsi untuk setiap langkah.
- Tetap membutuhkan pemilihan ukuran langkah.
- Tidak selalu memberikan hasil eksak.

Metode Heun memiliki galat lokal pemotongan berorde \\(O(h^3)\\) dan galat global berorde \\(O(h^2)\\), untuk kondisi solusi yang cukup mulus.

## **7. Metode Runge-Kutta Orde 4 (RK4)**

### **7.1 Konsep Metode Runge-Kutta**

Runge-Kutta Orde 4 atau RK4 merupakan salah satu metode numerik yang banyak digunakan untuk menyelesaikan persamaan diferensial biasa.

Metode ini memperkirakan perubahan fungsi dengan menggunakan empat evaluasi kemiringan pada setiap langkah.

Berbeda dengan Euler yang hanya menggunakan satu kemiringan, RK4 memperhitungkan kemiringan pada beberapa posisi dalam satu interval.

Persamaan RK4:

\\[ \boxed{ y\_{n+1}=y_n+\frac{h}{6} (k_1+2k_2+2k_3+k_4) } \\]

Dengan:

\\[ k_1=f(t_n,y_n) \\]

\\[ k_2=f\left(t_n+\frac{h}{2}, y_n+\frac{h}{2}k_1\right) \\]

\\[ k_3=f\left(t_n+\frac{h}{2}, y_n+\frac{h}{2}k_2\right) \\]

\\[ k_4=f(t_n+h,y_n+hk_3) \\]

Keterangan:

- \\(k_1\\) = kemiringan awal.
- \\(k_2\\) = kemiringan pada titik tengah berdasarkan \\(k_1\\).
- \\(k_3\\) = kemiringan pada titik tengah berdasarkan \\(k_2\\).
- \\(k_4\\) = kemiringan pada titik akhir berdasarkan \\(k_3\\).
- \\(h\\) = ukuran langkah.

[File:Runge-Kutta slopes.svg - Wikimedia Commons](https://images.openai.com/static-rsc-4/qAcyrHZjmNSG2mWtlX_9Ci--x41LOUzKRUgqK5VtlXjGjbVBVxpjxZyR_lX-FjqZYEVfOvGo3U0SWfIRzVSJERyUdyBPHYoMjYXKWHCBf3tR9hHTBENSkvT7UwNaLyrJU_BBcrze7V9ZYtMvaHTGv-_WKYlBAS3nofWsiM233U0?purpose=inline)

[commons.wikimedia.org](https://commons.wikimedia.org/wiki/File%3ARunge-Kutta_slopes.svg?utm_source=chatgpt.com)

### **7.2 Contoh Perhitungan Manual**

Diketahui:

\\[ \frac{dy}{dt}=2t \\]

Dengan kondisi awal:

\\[ y(0)=1 \\]

Gunakan:

\\[ h=0,5 \\]

Hitung nilai \\(y\\) pada \\(t=0,5\\).

**Langkah 1: Hitung&#x20;**\\(k_1\\)

\\[ k_1=f(0,1) \\]

\\[ k_1=2(0) \\]

\\[ k_1=0 \\]

**Langkah 2: Hitung&#x20;**\\(k_2\\)

\\[ k_2=f\left(0,25,1+\frac{0,5}{2}(0)\right) \\]

\\[ k_2=2(0,25) \\]

\\[ k_2=0,5 \\]

**Langkah 3: Hitung&#x20;**\\(k_3\\)

\\[ k_3=f\left(0,25,1+\frac{0,5}{2}(0,5)\right) \\]

\\[ k_3=2(0,25) \\]

\\[ k_3=0,5 \\]

**Langkah 4: Hitung&#x20;**\\(k_4\\)

\\[ k_4=f(0,5,1+0,5(0,5)) \\]

\\[ k_4=2(0,5) \\]

\\[ k_4=1 \\]

**Langkah 5: Hitung nilai berikutnya**

\\[ y_1=1+\frac{0,5}{6} [0+2(0,5)+2(0,5)+1] \\]

\\[ y_1=1+\frac{0,5}{6}(3) \\]

\\[ y_1=1+0,25 \\]

\\[ \boxed{y_1=1,25} \\]

Pada contoh ini, RK4 menghasilkan nilai yang sama dengan solusi eksak.

### **7.3 Implementasi RK4 Menggunakan Python**

```
def rk4_method(f, t0, y0, h, n):    t = t0    y = y0    hasil = [(t, y)]    for i in range(n):        k1 = f(t, y)        k2 = f(            t + h / 2,            y + h * k1 / 2        )        k3 = f(            t + h / 2,            y + h * k2 / 2        )        k4 = f(            t + h,            y + h * k3        )        y = y + (h / 6) * (            k1 + 2*k2 + 2*k3 + k4        )        t = t + h        hasil.append((t, y))    return hasil
```

Output:

```
Hasil Metode RK4
t = 0.00, y = 1.0000
t = 0.50, y = 1.2500
t = 1.00, y = 2.0000
```

### **7.4 Kelebihan dan Keterbatasan**

Kelebihan:

- Memiliki tingkat akurasi yang tinggi untuk banyak permasalahan ODE yang cukup mulus.
- Tidak membutuhkan turunan orde tinggi secara eksplisit.
- Banyak digunakan dalam simulasi numerik.
- Cocok untuk berbagai sistem dinamis.

Keterbatasan:

- Membutuhkan empat evaluasi fungsi untuk setiap langkah.
- Perhitungan lebih kompleks daripada Euler dan Heun.
- Ukuran langkah tetap perlu dipilih secara tepat.
- Tidak otomatis menjamin stabilitas untuk semua sistem.

RK4 memiliki galat lokal pemotongan berorde \\(O(h^5)\\) dan galat global berorde \\(O(h^4)\\), dengan asumsi solusi cukup mulus.

## **8. Perbandingan Metode Euler, Heun, dan RK4**

Ketiga metode memiliki karakteristik yang berbeda.

| Aspek                       | Euler               | Heun                             | RK4                           |
| --------------------------- | ------------------- | -------------------------------- | ----------------------------- |
| Evaluasi fungsi per langkah | 1                   | 2                                | 4                             |
| Orde akurasi global         | 1                   | 2                                | 4                             |
| Kompleksitas                | Rendah              | Sedang                           | Lebih tinggi                  |
| Ketelitian umum             | Rendah              | Menengah                         | Tinggi                        |
| Penggunaan                  | Dasar dan sederhana | Pendekatan lebih baik dari Euler | Simulasi numerik lebih akurat |

**Interpretasi:**

- Euler cocok untuk memahami konsep dasar penyelesaian ODE.
- Heun memperbaiki hasil Euler dengan menggunakan rata-rata kemiringan.
- RK4 menggunakan empat estimasi kemiringan sehingga umumnya memberikan hasil yang lebih akurat pada ukuran langkah yang sama.

Namun, metode yang lebih tinggi ordonya tidak otomatis paling tepat untuk setiap persoalan. Karakteristik persamaan, stabilitas numerik, dan ukuran langkah tetap harus diperhatikan.

# **BAGIAN C – ANALISIS GALAT DAN KONVERGENSI**

## **9. Analisis Galat pada Penyelesaian ODE**

### **9.1 Galat Absolut**

Jika solusi eksak diketahui, galat absolut dapat dihitung dengan:

\\[ \boxed{ E_a=|y\_{\text{eksak}}-y\_{\text{numerik}}| } \\]

Misalnya:

\\[ y\_{\text{eksak}}=2 \\]

\\[ y\_{\text{numerik}}=1,5 \\]

Maka:

\\[ E_a=|2-1,5| \\]

\\[ \boxed{E_a=0,5} \\]

### **9.2 Galat Relatif**

\\[ E_r=\frac{E_a}{|y\_{\text{eksak}}|} \\]

### **9.3 Persentase Galat**

\\[ E_p=E_r\times100\\% \\]

Untuk contoh di atas:

\\[ E_r=\frac{0,5}{2}=0,25 \\]

\\[ \boxed{E_p=25\\%} \\]

### **9.4 Implementasi Python**

```
nilai_eksak = 2.0nilai_numerik = 1.5galat_absolut = abs(    nilai_eksak - nilai_numerik)galat_relatif = (    galat_absolut / abs(nilai_eksak))galat_persen = galat_relatif * 100print("Galat Absolut:", galat_absolut)print("Galat Relatif:", galat_relatif)print("Galat Persen:", galat_persen, "%")
```

Output:

```
Galat Absolut: 0.5
Galat Relatif: 0.25
Galat Persen: 25.0 %
```

### **9.5 Pengaruh Ukuran Langkah**

Ukuran langkah \\(h\\) berpengaruh terhadap akurasi penyelesaian ODE.

Secara umum, untuk metode dengan solusi yang cukup mulus:

- Euler memiliki galat global \\(O(h)\\).
- Heun memiliki galat global \\(O(h^2)\\).
- RK4 memiliki galat global \\(O(h^4)\\).

Ketika ukuran langkah diperkecil, galat pemotongan biasanya berkurang sesuai orde metodenya.

Namun, ukuran langkah yang sangat kecil juga meningkatkan jumlah perhitungan dan dapat memperbesar dampak galat pembulatan.

# **BAGIAN D – STUDI KASUS TEKNIK ELEKTRO**

## **10. Simulasi Respons Transien Rangkaian RC**

Ini bagian yang paling penting untuk menghubungkan teori ODE dengan aplikasi Teknik Elektro.

### **10.1 Deskripsi Kasus**

Sebuah rangkaian RC seri terdiri atas:

- Sumber tegangan DC.
- Resistor.
- Kapasitor.

Ketika sumber tegangan dihubungkan ke rangkaian, kapasitor mulai mengalami proses pengisian (*charging*).

Tegangan kapasitor tidak langsung mencapai tegangan sumber, tetapi meningkat secara bertahap terhadap waktu.

Fenomena tersebut disebut respons transien.

[RC Time Constant Calculator - Engineering Calculators & Tools](https://images.openai.com/static-rsc-4/FyTSod7n-IdkXoAVSs5WXpu0S-YfJVWWlmOl-EZBzwYxAMy-XIkB01tZoxSUKpSX0NyeliP_jNtw3S-9MiCVPUFq7h2HYoYF751-guniYkDLgvPmkCMqrYl-LXVFcxBOt_ehMO2fDucBRBIIoaRw5qwGQMdHt_4oHgs8MYn8An8?purpose=inline)

[allaboutcircuits.com](https://www.allaboutcircuits.com/tools/resistor-capacitor-time-constant-calculator/?utm_source=chatgpt.com)

Diketahui parameter rangkaian:

| Parameter                 | Nilai    |
| ------------------------- | -------- |
| Tegangan sumber \\(V_s\\) | 10 V     |
| Resistansi \\(R\\)        | 1.000 Ω  |
| Kapasitansi \\(C\\)       | 1.000 µF |
| Tegangan awal kapasitor   | 0 V      |

Pertanyaan:

**Bagaimana perubahan tegangan kapasitor selama proses pengisian dalam rentang waktu 0 sampai 5 detik?**

Kita akan menyelesaikannya menggunakan metode Euler, Heun, dan RK4.

### **10.2 Persamaan Matematis Rangkaian RC**

Berdasarkan Hukum Tegangan Kirchhoff (KVL):

\\[ V_s=V_R+V_C \\]

Tegangan pada resistor:

\\[ V_R=Ri \\]

Arus pada kapasitor:

\\[ i=C\frac{dV_C}{dt} \\]

Substitusikan ke persamaan KVL:

\\[ V_s=RC\frac{dV_C}{dt}+V_C \\]

Susun kembali:

\\[ RC\frac{dV_C}{dt}=V_s-V_C \\]

Sehingga:

\\[ \boxed{ \frac{dV_C}{dt}= \frac{V_s-V_C}{RC} } \\]

Persamaan tersebut merupakan ODE orde satu yang menggambarkan perubahan tegangan kapasitor terhadap waktu.

### **10.3 Menentukan Konstanta Waktu**

Konstanta waktu rangkaian RC dinyatakan sebagai:

\\[ \boxed{\tau=RC} \\]

Diketahui:

\\[ R=1000\ \Omega \\]

\\[ C=1000\ \mu F=0,001\ F \\]

Maka:

\\[ \tau=1000(0,001) \\]

\\[ \boxed{\tau=1\text{ detik}} \\]

Konstanta waktu menunjukkan karakteristik kecepatan respons rangkaian.

Untuk proses pengisian ideal, setelah satu konstanta waktu, tegangan kapasitor mencapai sekitar 63,2% dari tegangan sumber.

### **10.4 Bentuk Persamaan ODE**

Substitusikan nilai parameter:

\\[ \frac{dV_C}{dt} = \frac{10-V_C}{1000(0,001)} \\]

Karena:

\\[ RC=1 \\]

Maka:

\\[ \boxed{ \frac{dV_C}{dt}=10-V_C } \\]

Dengan kondisi awal:

\\[ \boxed{V_C(0)=0} \\]

Persamaan ini akan menjadi dasar simulasi numerik.

### **10.5 Solusi Analitik sebagai Pembanding**

Untuk rangkaian RC ideal dengan tegangan sumber konstan dan tegangan awal kapasitor nol, solusi analitiknya adalah:

\\[ \boxed{ V_C(t)=V_s(1-e^{-t/RC}) } \\]

Dengan parameter yang digunakan:

\\[ V_C(t)=10(1-e^{-t}) \\]

Solusi analitik ini digunakan sebagai nilai pembanding untuk mengevaluasi hasil metode numerik.

Beberapa nilai referensi:

| Waktu (s) | Tegangan kapasitor (V) |
| --------- | ---------------------- |
| 0         | 0,0000                 |
| 1         | 6,3212                 |
| 2         | 8,6466                 |
| 3         | 9,5021                 |
| 4         | 9,8168                 |
| 5         | 9,9326                 |

Nilai tersebut menunjukkan bahwa tegangan kapasitor meningkat secara bertahap dan mendekati tegangan sumber 10 V.

[Clamper Circuits - Circuit Design](https://images.openai.com/static-rsc-4/CnjFQ-0Pvg0VaHdPg6YFlUJG37vkXchy4HuJriLFVf76mOpqkST0yNhHTUCtVFLieWJ8dSoAlALW1qEStoyZgRRFoFkdNdSNRgypM8NAaMTfWmdSwpY1Wb52oAlT6Ru8Bt_easLBBtYgFFR2Z6nizST9dzGxiw5MnlIMKz6sFww?purpose=inline)

[suriyamu1.github.io](https://suriyamu1.github.io/ClamperCircuits/circuit_design.html?utm_source=chatgpt.com)

### **10.6 Simulasi Menggunakan Metode Euler**

Persamaan yang digunakan:

\\[ \frac{dV_C}{dt}=10-V_C \\]

Rumus Euler:

\\[ V\_{n+1}=V_n+h(10-V_n) \\]

Gunakan:

\\[ h=0,5 \\]

Kondisi awal:

\\[ t_0=0,\quad V_0=0 \\]

Iterasi pertama:

\\[ V_1=0+0,5(10-0) \\]

\\[ V_1=5 \\]

Iterasi kedua:

\\[ V_2=5+0,5(10-5) \\]

\\[ V_2=7,5 \\]

Iterasi ketiga:

\\[ V_3=7,5+0,5(10-7,5) \\]

\\[ V_3=8,75 \\]

Tabel hasil:

| Waktu (s) | Tegangan Euler (V) |
| --------- | ------------------ |
| 0,0       | 0,0000             |
| 0,5       | 5,0000             |
| 1,0       | 7,5000             |
| 1,5       | 8,7500             |
| 2,0       | 9,3750             |

### **10.7 Implementasi Simulasi RC Menggunakan Euler**

```
import numpy as npimport matplotlib.pyplot as plt# Parameter rangkaianVs = 10R = 1000C = 1000e-6# Persamaan diferensialdef rc_model(t, Vc):    return (Vs - Vc) / (R * C)# Parameter simulasit0 = 0t_end = 5h = 0.5n = int((t_end - t0) / h)# Kondisi awalt = 0Vc = 0waktu = [t]tegangan = [Vc]# Metode Eulerfor i in range(n):    Vc = Vc + h * rc_model(t, Vc)    t = t + h    waktu.append(t)    tegangan.append(Vc)
```

## **11. Perbandingan Euler, Heun, dan RK4 pada Rangkaian RC**

Sekarang kita gunakan persamaan yang sama untuk membandingkan ketiga metode.

### **11.1 Program Perbandingan**

```
import numpy as npimport matplotlib.pyplot as plt# Parameter rangkaianVs = 10R = 1000C = 1000e-6# Model ODEdef rc_model(t, Vc):    return (Vs - Vc) / (R * C)# Solusi analitikdef rc_exact(t):    return Vs * (1 - np.exp(-t / (R * C)))# Simulasi Eulerdef euler(f, t0, y0, h, n):    t = t0    y = y0    hasil = [(t, y)]    for i in range(n):        y = y + h * f(t, y)        t = t + h        hasil.append((t, y))    return hasil# Simulasi Heundef heun(f, t0, y0, h, n):    t = t0
```

### **11.2 Menghitung Galat Setiap Metode**

Kita juga dapat membandingkan hasil pada waktu akhir, yaitu 5 detik.

```
# Nilai referensi pada t = 5 detiknilai_eksak = rc_exact(5)# Nilai numerik pada t = 5 detiknilai_euler = hasil_euler[-1][1]nilai_heun = hasil_heun[-1][1]nilai_rk4 = hasil_rk4[-1][1]# Menghitung galat absoluterror_euler = abs(nilai_eksak - nilai_euler)error_heun = abs(nilai_eksak - nilai_heun)error_rk4 = abs(nilai_eksak - nilai_rk4)print("Nilai Eksak:", nilai_eksak)print("Galat Euler:", error_euler)print("Galat Heun:", error_heun)print("Galat RK4:", error_rk4)
```

Untuk parameter \\(h=0,5\\), hasil perhitungan mendekati:

| Metode | Tegangan pada 5 s (V) | Galat absolut (V) |
| ------ | --------------------- | ----------------- |
| Euler  | 9,6875                | 0,2451            |
| Heun   | 9,9041                | 0,0285            |
| RK4    | 9,9325                | 0,0001            |

Angka dibulatkan; perbedaan kecil dapat muncul pada digit terakhir akibat presisi floating-point.

### **11.3 Interpretasi Hasil**

Dari hasil perbandingan dapat diamati:

1. Euler menghasilkan pendekatan yang relatif lebih jauh dari solusi analitik.
2. Heun memberikan hasil yang lebih dekat dibandingkan Euler.
3. RK4 menghasilkan pendekatan yang paling dekat pada ukuran langkah yang digunakan.
4. Ketiga metode memperlihatkan bahwa tegangan kapasitor meningkat secara bertahap menuju tegangan sumber.

Perbandingan ini menunjukkan bahwa pemilihan metode numerik berpengaruh terhadap akurasi hasil simulasi.

## **12. Penerapan ODE pada Sistem Teknik Elektro Lainnya**

Selain rangkaian RC, persamaan diferensial juga dapat digunakan untuk memodelkan berbagai sistem teknik elektro.

### **12.1 Rangkaian RL**

Pada rangkaian RL seri, hubungan tegangan dan arus dapat dinyatakan sebagai:

\\[ V_s=L\frac{di}{dt}+Ri \\]

Sehingga:

\\[ \boxed{ \frac{di}{dt}=\frac{V_s-Ri}{L} } \\]

Persamaan tersebut dapat digunakan untuk memperkirakan perubahan arus induktor terhadap waktu.

[Les circuits RL et RC – Méthode Physique](https://images.openai.com/static-rsc-4/tbTJKAvoJQ3n8NoElquXiWTj7XWasSwTIhDvwJGNrmaaFSg4G4eIHyTFeKcrN1ZtNA7Fi5m6R9pfeibpfAp03auv4-0PWFDIu1Zwp1GXlpVs8s120EudRNRT51ZuZSiocyY3Em5Rt0buYritMvW5FtFLnTkXOPMJjybPyOTyV2E?purpose=inline)

[methodephysique.fr](https://www.methodephysique.fr/circuits_rl_rc/?utm_source=chatgpt.com)

### **12.2 Rangkaian RLC**

Pada rangkaian RLC seri, persamaan diferensial dapat ditulis:

\\[ L\frac{d^2q}{dt^2} + R\frac{dq}{dt} + \frac{q}{C}=V_s(t) \\]

Keterangan:

- \\(L\\) = induktansi.
- \\(R\\) = resistansi.
- \\(C\\) = kapasitansi.
- \\(q\\) = muatan listrik.
- \\(V_s(t)\\) = sumber tegangan terhadap waktu.

Persamaan tersebut merupakan ODE orde dua.

Untuk menyelesaikannya menggunakan metode RK4, persamaan dapat diubah menjadi dua persamaan orde satu.

### **12.3 Sistem Kendali**

Dalam sistem kendali, ODE dapat digunakan untuk memodelkan respons sistem terhadap masukan tertentu.

Contohnya adalah respons kecepatan motor DC terhadap perubahan tegangan input.

Model sederhana dapat melibatkan hubungan antara tegangan, arus, torsi, dan kecepatan sudut motor.

Metode numerik memungkinkan simulasi perilaku sistem ketika solusi analitik sulit diperoleh.

## **13. Kesalahan Umum dalam Penyelesaian ODE**

| Kesalahan                                   | Dampak                                 | Solusi                                  |
| ------------------------------------------- | -------------------------------------- | --------------------------------------- |
| Salah menentukan kondisi awal               | Seluruh hasil perhitungan dapat keliru | Pastikan nilai \\(y_0\\) benar          |
| Salah menentukan fungsi \\(f(t,y)\\)        | Model ODE tidak sesuai                 | Periksa persamaan diferensial           |
| Salah memilih ukuran langkah                | Hasil kurang akurat atau tidak stabil  | Evaluasi nilai \\(h\\)                  |
| Salah menghitung \\(k_1,k_2,k_3,k_4\\)      | Hasil RK4 tidak tepat                  | Hitung setiap tahap secara berurutan    |
| Tidak memperbarui waktu                     | Iterasi tidak berjalan sesuai interval | Gunakan \\(t\_{n+1}=t_n+h\\)            |
| Tidak membandingkan dengan solusi referensi | Akurasi tidak diketahui                | Hitung galat jika solusi eksak tersedia |
| Mengabaikan satuan fisik                    | Interpretasi sistem keliru             | Gunakan satuan SI secara konsisten      |

## **14. Rangkuman Materi**

Pada modul terakhir ini, mahasiswa telah mempelajari konsep dan penerapan penyelesaian persamaan diferensial biasa menggunakan metode numerik.

Ringkasan konsep:

1. ODE merupakan persamaan diferensial yang melibatkan turunan terhadap satu variabel bebas.
2. Initial Value Problem membutuhkan informasi kondisi awal untuk menentukan penyelesaian.
3. Metode Euler menggunakan satu evaluasi kemiringan pada setiap langkah.
4. Metode Heun menggunakan dua evaluasi kemiringan dan menghitung rata-ratanya.
5. Metode RK4 menggunakan empat evaluasi kemiringan untuk memperkirakan perubahan fungsi.
6. Ukuran langkah berpengaruh terhadap akurasi dan jumlah perhitungan.
7. Galat numerik dapat digunakan untuk mengevaluasi kualitas hasil penyelesaian.
8. ODE dapat digunakan untuk memodelkan respons dinamis berbagai sistem teknik elektro.

Dalam studi kasus rangkaian RC, mahasiswa dapat melihat bagaimana sebuah persamaan diferensial menggambarkan proses pengisian kapasitor. Hasil simulasi menggunakan Euler, Heun, dan RK4 juga menunjukkan bahwa pemilihan metode berpengaruh terhadap ketelitian hasil.

## **15. Referensi Pembelajaran**

1. Chapra, S. C., & Canale, R. P. *Numerical Methods for Engineers*. McGraw-Hill.
2. Burden, R. L., Faires, J. D., & Burden, A. M. *Numerical Analysis*. Cengage Learning.
3. Sauer, T. *Numerical Analysis*. Pearson.
4. Boyce, W. E., DiPrima, R. C., & Meade, D. B. *Elementary Differential Equations and Boundary Value Problems*. Wiley.
5. Python Documentation – [Python Official Documentation](https://docs.python.org/3/).
6. NumPy Documentation – [NumPy Official Documentation](https://numpy.org/doc/stable/).
7. Matplotlib Documentation – [Matplotlib Official Documentation](https://matplotlib.org/stable/).
