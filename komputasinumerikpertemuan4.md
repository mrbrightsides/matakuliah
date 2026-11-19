# **MODULE 4**

# **ANALISIS GALAT DAN METODE PENYELESAIAN PERSAMAAN NONLINEAR**

Pertemuan 4

Komputasi Numerik

Program Studi Teknik Elektro

## **1. Deskripsi Materi**

Dalam penyelesaian permasalahan teknik, tidak semua persamaan matematis dapat diselesaikan secara analitik atau menggunakan perhitungan eksak.

Beberapa permasalahan menghasilkan persamaan nonlinear yang cukup kompleks sehingga membutuhkan pendekatan numerik untuk memperoleh solusi.

Metode numerik merupakan teknik penyelesaian masalah matematis dengan menggunakan pendekatan perhitungan berulang untuk memperoleh nilai solusi yang mendekati nilai sebenarnya.

Dalam proses tersebut, hasil perhitungan dapat memiliki selisih terhadap nilai eksak. Selisih ini disebut sebagai *error* atau galat.

Pada pertemuan ini, mahasiswa akan mempelajari konsep analisis galat dan beberapa metode penyelesaian persamaan nonlinear, yaitu:

1. Metode Bisection.
2. Metode Regula Falsi.
3. Metode Newton-Raphson.

Implementasi akan menggunakan Python untuk membantu proses iterasi, perhitungan galat, dan analisis konvergensi.

## **2. Capaian Pembelajaran**

Setelah menyelesaikan materi ini, mahasiswa diharapkan mampu:

1. Menjelaskan konsep dasar komputasi numerik.
2. Memahami sumber dan jenis galat dalam perhitungan numerik.
3. Menghitung galat absolut, relatif, dan persentase galat.
4. Memahami konsep persamaan nonlinear dan akar persamaan.
5. Mengimplementasikan metode Bisection menggunakan Python.
6. Mengimplementasikan metode Regula Falsi menggunakan Python.
7. Mengimplementasikan metode Newton-Raphson menggunakan Python.
8. Membandingkan konvergensi dan akurasi metode numerik.
9. Menerapkan metode numerik pada permasalahan sederhana Teknik Elektro.

# **BAGIAN I — ANALISIS GALAT**

## **3. Pengantar Komputasi Numerik**

### **3.1 Apa Itu Komputasi Numerik?**

Komputasi numerik adalah bidang ilmu yang mempelajari metode matematis untuk memperoleh solusi pendekatan dari permasalahan numerik menggunakan proses komputasi.

Dalam bidang teknik, metode numerik digunakan ketika:

- Persamaan terlalu kompleks untuk diselesaikan secara analitik.
- Data diperoleh dari hasil pengukuran.
- Solusi eksak sulit diperoleh.
- Perhitungan membutuhkan proses iterasi.
- Sistem memiliki banyak variabel dan persamaan.

Contoh penerapan dalam Teknik Elektro:

| Permasalahan               | Penerapan Komputasi Numerik             |
| -------------------------- | --------------------------------------- |
| Analisis rangkaian listrik | Menentukan akar persamaan nonlinear     |
| Sistem tenaga listrik      | Menyelesaikan persamaan aliran daya     |
| Pengolahan sinyal          | Menghitung turunan dan integral numerik |
| Sistem kendali             | Menyelesaikan persamaan diferensial     |
| Instrumentasi              | Interpolasi data sensor                 |
| Elektronika                | Simulasi karakteristik komponen         |

### **3.2 Solusi Eksak dan Solusi Numerik**

Perhatikan persamaan berikut:

\\[ x^2-4=0 \\]

Persamaan tersebut dapat diselesaikan secara analitik:

\\[ x^2=4 \\]

\\[ x=\pm 2 \\]

Nilai 2 dan -2 merupakan solusi eksak.

Namun, pada persamaan yang lebih kompleks seperti:

\\[ f(x)=x^3-x-2=0 \\]

akar persamaan tidak mudah diperoleh menggunakan metode aljabar sederhana.

Dalam kondisi seperti ini, metode numerik dapat digunakan untuk mencari nilai pendekatan akar persamaan.

Contohnya:

\\[ x\approx 1.52138 \\]

Nilai tersebut merupakan pendekatan akar positif persamaan tersebut.

**Perbedaan utama:**

- Solusi analitik menghasilkan nilai berdasarkan manipulasi matematis.
- Solusi numerik menghasilkan nilai pendekatan melalui proses perhitungan.

## **4. Konsep Galat (Error)**

### **4.1 Pengertian Galat**

Galat adalah selisih antara nilai pendekatan yang diperoleh melalui perhitungan dengan nilai sebenarnya atau nilai acuan.

Dalam komputasi numerik, galat merupakan hal yang tidak dapat dihindari sepenuhnya.

Misalnya:

- Nilai eksak: 10.
- Nilai hasil perhitungan: 9,8.

Maka terdapat selisih sebesar 0,2.

### **4.2 Sumber Galat**

Beberapa sumber galat dalam komputasi numerik:

**1. Galat pembulatan (Round-off Error)**

Terjadi karena komputer memiliki keterbatasan dalam merepresentasikan angka desimal.

Contoh:

```
a = 0.1b = 0.2print(a + b)
```

Output:

```
0.30000000000000004
```

Secara matematis, 0,1 + 0,2 = 0,3. Namun, representasi bilangan floating-point pada komputer dapat menghasilkan nilai yang sedikit berbeda.

**2. Galat pemotongan (Truncation Error)**

Terjadi ketika suatu proses matematis dihentikan atau disederhanakan dengan hanya menggunakan sejumlah suku atau langkah tertentu.

Contohnya, pendekatan deret Taylor yang hanya menggunakan beberapa suku.

**3. Galat pengukuran (Measurement Error)**

Terjadi karena keterbatasan alat ukur atau kondisi pengukuran.

Contoh:

- Tegangan sebenarnya: 220 V.
- Hasil pembacaan alat: 219,7 V.

Selisih tersebut dapat berasal dari ketelitian alat ukur, kondisi lingkungan, atau ketidakpastian pengukuran.

## **5. Jenis-Jenis Galat**

### **5.1 Galat Absolut**

Galat absolut merupakan nilai mutlak dari selisih antara nilai eksak dan nilai pendekatan.

Rumus:

\\[ E_a=|x\_{\text{eksak}}-x\_{\text{aproksimasi}}| \\]

Contoh:

Nilai eksak suatu parameter adalah 100, sedangkan hasil perhitungan numerik adalah 98.

\\[ E_a=|100-98| \\]

\\[ E_a=2 \\]

Jadi, galat absolutnya adalah 2.

### **5.2 Galat Relatif**

Galat relatif merupakan perbandingan antara galat absolut dengan nilai eksak.

Rumus:

\\[ E_r=\frac{|x\_{\text{eksak}}-x\_{\text{aproksimasi}}|} {|x\_{\text{eksak}}|} \\]

Contoh:

\\[ E_r=\frac{2}{100}=0.02 \\]

Galat relatifnya adalah 0,02.

### **5.3 Galat Persentase**

Galat persentase merupakan galat relatif yang dinyatakan dalam persen.

Rumus:

\\[ E_p=E_r\times 100\\% \\]

\\[ E_p=0.02\times100\\%=2\\% \\]

**Ringkasan contoh perhitungan**

# **2**

Galat absolut

# **0,02**

Galat relatif

# **2%**

Galat persentase

### **5.4 Implementasi Perhitungan Galat dengan Python**

```
nilai_eksak = 100nilai_pendekatan = 98galat_absolut = abs(nilai_eksak - nilai_pendekatan)galat_relatif = galat_absolut / abs(nilai_eksak)galat_persen = galat_relatif * 100print("Nilai eksak:", nilai_eksak)print("Nilai pendekatan:", nilai_pendekatan)print("Galat absolut:", galat_absolut)print("Galat relatif:", galat_relatif)print("Galat persentase:", galat_persen, "%")
```

Output:

```
Nilai eksak: 100
Nilai pendekatan: 98
Galat absolut: 2
Galat relatif: 0.02
Galat persentase: 2.0 %
```

### **5.5 Implementasi Galat untuk Data Pengukuran**

Misalnya sebuah alat ukur tegangan dibandingkan dengan alat referensi.

```
tegangan_referensi = 220.0tegangan_sensor = 219.5galat_absolut = abs(    tegangan_referensi - tegangan_sensor)galat_relatif = (    galat_absolut / abs(tegangan_referensi))galat_persen = galat_relatif * 100print("Tegangan referensi:", tegangan_referensi, "V")print("Tegangan sensor:", tegangan_sensor, "V")print("Galat absolut:", galat_absolut, "V")print("Galat persentase:", galat_persen, "%")
```

Output:

```
Tegangan referensi: 220.0 V
Tegangan sensor: 219.5 V
Galat absolut: 0.5 V
Galat persentase: 0.22727272727272727 %
```

Galat persentase dapat dibulatkan menjadi:

\\[ E_p\approx 0.2273\\% \\]

Catatan: untuk nilai acuan nol, galat relatif tidak terdefinisi. Dalam kondisi tersebut, galat absolut dapat digunakan atau diperlukan metrik alternatif.

# **BAGIAN II — PERSAMAAN NONLINEAR**

## **6. Pengertian Persamaan Nonlinear**

Persamaan nonlinear adalah persamaan matematis yang tidak dapat dinyatakan sebagai persamaan linear terhadap variabelnya.

Contoh persamaan nonlinear:

\\[ f(x)=x^2-4 \\]

\\[ f(x)=x^3-x-2 \\]

\\[ f(x)=e^{-x}-x \\]

\\[ f(x)=\sin(x)-0.5 \\]

Persamaan nonlinear sering muncul dalam berbagai permasalahan Teknik Elektro, misalnya karakteristik dioda, persamaan rangkaian dengan komponen nonlinear, dan model sistem tertentu.

### **6.1 Akar Persamaan**

Akar persamaan adalah nilai variabel yang menyebabkan fungsi menghasilkan nilai nol.

Secara matematis:

\\[ f(x)=0 \\]

Misalnya:

\\[ f(x)=x^2-9 \\]

Akar persamaannya:

\\[ x=-3 \quad \text{atau} \quad x=3 \\]

Karena:

\\[ f(3)=3^2-9=0 \\]

dan

\\[ f(-3)=(-3)^2-9=0 \\]

### **6.2 Mengapa Membutuhkan Metode Numerik?**

Tidak semua persamaan nonlinear dapat diselesaikan secara sederhana menggunakan manipulasi aljabar.

Metode numerik memungkinkan kita memperoleh pendekatan akar dengan melakukan iterasi.

Dalam pembelajaran ini, kita akan menggunakan tiga metode:

1. Bisection.
2. Regula Falsi.
3. Newton-Raphson.

# **BAGIAN III — METODE BISECTION**

## **7. Konsep Metode Bisection**

Metode Bisection merupakan metode pencarian akar persamaan nonlinear dengan cara membagi interval menjadi dua bagian secara berulang.

Metode ini menggunakan prinsip perubahan tanda fungsi.

Jika:

\\[ f(a)\times f(b)<0 \\]

maka terdapat setidaknya satu akar pada interval \\([a,b]\\), dengan asumsi fungsi kontinu pada interval tersebut.

Metode Bisection bekerja dengan mencari titik tengah interval:

\\[ x_r=\frac{a+b}{2} \\]

Kemudian mengevaluasi nilai fungsi pada titik tersebut.

### **7.1 Langkah-Langkah Metode Bisection**

Misalnya:

\\[ f(x)=x^3-x-2 \\]

Kita ingin mencari akar persamaan tersebut.

Tentukan interval awal:

\\[ a=1,\quad b=2 \\]

Evaluasi fungsi:

\\[ f(1)=1-1-2=-2 \\]

\\[ f(2)=8-2-2=4 \\]

Karena hasilnya berbeda tanda, interval tersebut memenuhi syarat perubahan tanda.

Langkah pertama:

\\[ x_r=\frac{1+2}{2}=1.5 \\]

Evaluasi:

\\[ f(1.5)=1.5^3-1.5-2=-0.125 \\]

Karena \\(f(1.5)\\) dan \\(f(2)\\) berbeda tanda, interval baru adalah:

\\[ [1.5,2] \\]

Proses tersebut dilanjutkan sampai diperoleh nilai yang memenuhi toleransi galat.

### **7.2 Ilustrasi Pembagian Interval**

**Visualisasi pencarian akar Bisection**

Karena f(xr) negatif, interval berikutnya adalah [1.5, 2]. Ilustrasi ini menunjukkan pembagian interval, bukan skala grafik fungsi.

### **7.3 Implementasi Bisection Menggunakan Python**

```
def f(x):    return x**3 - x - 2def bisection(a, b, toleransi, max_iterasi):    if f(a) * f(b) >= 0:        print("Interval tidak memenuhi syarat perubahan tanda")        return None    print("Iterasi | a | b | xr | f(xr)")    for i in range(1, max_iterasi + 1):        xr = (a + b) / 2        hasil = f(xr)        print(i, a, b, xr, hasil)        if abs(hasil) < toleransi:            return xr        if f(a) * hasil < 0:            b = xr        else:            a = xr    return xrakar = bisection(1, 2, 0.0001, 100)print("\nAkar persamaan:", akar)
```

Contoh hasil akhir:

```
Akar persamaan: 1.521...
```

Nilai akhir bergantung pada toleransi dan jumlah iterasi yang digunakan.

### **7.4 Analisis Metode Bisection**

Kelebihan:

- Algoritma relatif sederhana.
- Tidak membutuhkan turunan fungsi.
- Konvergen untuk fungsi kontinu dengan interval yang memiliki perubahan tanda.
- Mudah diterapkan menggunakan Python.

Kekurangan:

- Konvergensinya relatif lambat.
- Membutuhkan interval awal yang memenuhi syarat.
- Tidak dapat langsung menemukan akar jika interval tidak menunjukkan perubahan tanda, meskipun akar mungkin berada di dalam interval dengan akar berulang atau beberapa akar.

# **BAGIAN IV — METODE REGULA FALSI**

## **8. Konsep Metode Regula Falsi**

Metode Regula Falsi atau *False Position Method* merupakan metode pencarian akar persamaan nonlinear yang juga menggunakan interval dengan perubahan tanda.

Berbeda dengan Bisection yang menggunakan titik tengah, Regula Falsi menentukan titik pendekatan berdasarkan garis lurus yang menghubungkan dua titik pada kurva fungsi.

Rumus:

\\[ x_r = \frac{a f(b)-b f(a)} {f(b)-f(a)} \\]

Keterangan:

- \\(a\\) = batas bawah interval.
- \\(b\\) = batas atas interval.
- \\(f(a)\\) = nilai fungsi pada batas bawah.
- \\(f(b)\\) = nilai fungsi pada batas atas.
- \\(x_r\\) = titik pendekatan akar.

### **8.1 Contoh Perhitungan Manual**

Gunakan persamaan:

\\[ f(x)=x^3-x-2 \\]

Interval awal:

\\[ a=1,\quad b=2 \\]

Nilai fungsi:

\\[ f(1)=-2 \\]

\\[ f(2)=4 \\]

Substitusi ke rumus:

\\[ x_r=\frac{1(4)-2(-2)}{4-(-2)} \\]

\\[ x_r=\frac{8}{6} \\]

\\[ x_r=1.3333 \\]

Nilai ini menjadi pendekatan akar pada iterasi pertama.

### **8.2 Implementasi Regula Falsi dengan Python**

```
def f(x):    return x**3 - x - 2def regula_falsi(a, b, toleransi, max_iterasi):    if f(a) * f(b) >= 0:        print("Interval tidak memenuhi syarat perubahan tanda")        return None    print("Iterasi | a | b | xr | f(xr)")    for i in range(1, max_iterasi + 1):        xr = (            a * f(b) - b * f(a)        ) / (            f(b) - f(a)        )        hasil = f(xr)        print(i, a, b, xr, hasil)        if abs(hasil) < toleransi:            return xr        if f(a) * hasil < 0:            b = xr        else:            a = xr    return xrakar = regula_falsi(1, 2, 0.0001, 100)print("\nAkar persamaan:", akar)
```

### **8.3 Analisis Metode Regula Falsi**

Kelebihan:

- Tidak membutuhkan turunan fungsi.
- Menggunakan informasi nilai fungsi pada kedua batas interval.
- Sering kali memberikan pendekatan yang lebih cepat daripada Bisection pada kasus tertentu.

Kekurangan:

- Salah satu batas interval dapat tetap tidak berubah selama beberapa iterasi.
- Konvergensi tidak selalu cepat.
- Kinerja sangat dipengaruhi oleh bentuk fungsi.

# **BAGIAN V — METODE NEWTON-RAPHSON**

## **9. Konsep Metode Newton-Raphson**

Newton-Raphson merupakan metode numerik untuk mencari akar persamaan nonlinear dengan memanfaatkan turunan pertama fungsi.

Metode ini menggunakan garis singgung pada kurva fungsi untuk memperkirakan posisi akar berikutnya.

Rumus:

\\[ x\_{n+1}=x_n-\frac{f(x_n)}{f'(x_n)} \\]

Keterangan:

- \\(x_n\\) = nilai pendekatan pada iterasi saat ini.
- \\(x\_{n+1}\\) = nilai pendekatan berikutnya.
- \\(f(x_n)\\) = nilai fungsi.
- \\(f'(x_n)\\) = turunan pertama fungsi.

### **9.1 Contoh Perhitungan Manual**

Gunakan persamaan:

\\[ f(x)=x^3-x-2 \\]

Turunan pertamanya:

\\[ f'(x)=3x^2-1 \\]

Tentukan nilai awal:

\\[ x_0=1.5 \\]

Substitusi ke rumus Newton-Raphson:

\\[ x_1=1.5-\frac{f(1.5)}{f'(1.5)} \\]

Diketahui:

\\[ f(1.5)=-0.125 \\]

\\[ f'(1.5)=3(1.5)^2-1=5.75 \\]

Maka:

\\[ x_1=1.5-\frac{-0.125}{5.75} \\]

\\[ x_1\approx1.521739 \\]

Hasil tersebut menjadi nilai pendekatan akar pada iterasi pertama.

### **9.2 Implementasi Newton-Raphson Menggunakan Python**

```
def f(x):    return x**3 - x - 2def df(x):    return 3*x**2 - 1def newton_raphson(x0, toleransi, max_iterasi):    x = x0    print("Iterasi | x | f(x)")    for i in range(1, max_iterasi + 1):        if df(x) == 0:            print("Turunan bernilai nol")            return None        x_baru = x - f(x) / df(x)        print(i, x_baru, f(x_baru))        if abs(x_baru - x) < toleransi:            return x_baru        x = x_baru    return xakar = newton_raphson(1.5, 0.0001, 100)print("\nAkar persamaan:", akar)
```

### **9.3 Analisis Metode Newton-Raphson**

Kelebihan:

- Konvergensi dapat sangat cepat ketika nilai awal cukup dekat dengan akar dan akar memenuhi kondisi yang sesuai.
- Cocok untuk persamaan nonlinear yang memiliki turunan.
- Efisien pada banyak permasalahan numerik.

Kekurangan:

- Membutuhkan turunan pertama fungsi.
- Memerlukan nilai awal.
- Dapat gagal jika turunan mendekati nol.
- Dapat divergen jika nilai awal tidak sesuai.

# **BAGIAN VI — PERBANDINGAN METODE**

## **10. Perbandingan Bisection, Regula Falsi, dan Newton-Raphson**

| Aspek                | Bisection          | Regula Falsi            | Newton-Raphson               |
| -------------------- | ------------------ | ----------------------- | ---------------------------- |
| Dasar metode         | Pembagian interval | Interpolasi garis lurus | Garis singgung               |
| Membutuhkan turunan  | Tidak              | Tidak                   | Ya                           |
| Membutuhkan interval | Ya                 | Ya                      | Tidak                        |
| Nilai awal           | Dua batas          | Dua batas               | Satu titik                   |
| Konvergensi          | Linear             | Umumnya linear          | Kuadratik pada kondisi ideal |
| Implementasi         | Sederhana          | Sedang                  | Sedang                       |

### **10.1 Kriteria Penghentian Iterasi**

Iterasi perlu dihentikan ketika solusi telah memenuhi tingkat ketelitian yang ditentukan.

Beberapa kriteria yang umum digunakan:

**1. Berdasarkan nilai fungsi**

\\[ |f(x_n)|<\varepsilon \\]

**2. Berdasarkan perubahan nilai pendekatan**

\\[ |x\_{n+1}-x_n|<\varepsilon \\]

**3. Berdasarkan galat relatif**

\\[ \left|\frac{x\_{n+1}-x_n}{x\_{n+1}}\right|<\varepsilon \\]

dengan asumsi penyebut tidak nol.

Keterangan:

- \\(\varepsilon\\) adalah toleransi yang ditentukan.
- \\(x_n\\) adalah nilai pendekatan saat ini.
- \\(x\_{n+1}\\) adalah nilai pendekatan berikutnya.

Perlu diperhatikan bahwa perubahan nilai yang kecil tidak selalu berarti residual fungsi juga kecil. Untuk evaluasi yang lebih baik, periksa residual dan kriteria perubahan pendekatan sesuai kebutuhan.

### **10.2 Konsep Konvergensi**

Konvergensi adalah kondisi ketika hasil iterasi semakin mendekati solusi yang diharapkan.

Jika:

\\[ \lim\_{n\to\infty}x_n=x^\* \\]

maka barisan iterasi konvergen menuju nilai \\(x^\*\\).

Dalam metode numerik, konvergensi menjadi salah satu indikator keberhasilan algoritma.

# **BAGIAN VII — STUDI KASUS TEKNIK ELEKTRO**

## **11. Studi Kasus: Menentukan Tegangan pada Rangkaian Dioda**

[Diode Voltage Drop: Values, Formula, and How to Measure It](https://images.openai.com/static-rsc-4/umE73YviJaJIhkNlbSYDnfnQrGoCevvt1LZh9NgkmyWng3M38fmJCmcqd_Z66TLmvSrdP4ytzDSKKSHc1P8v5kyAuXlc9s1VmvtvXDjO-A6k6sgkiGzw0_mJAPgR1dTm2FYEJ0p_xHgVIBU5Ue21GWyGlNKL6NenbtW6zDWyG2s?purpose=inline)

[jlcpcb.com](https://jlcpcb.com/blog/diode-voltage-drop-guide?utm_source=chatgpt.com)

### **11.1 Deskripsi Permasalahan**

Sebuah rangkaian DC terdiri atas sumber tegangan, resistor, dan dioda silikon.

Hubungan arus dan tegangan dioda dapat didekati menggunakan persamaan Shockley:

\\[ I_D=I_S\left(e^{\frac{V_D}{nV_T}}-1\right) \\]

Keterangan:

- \\(I_D\\) = arus dioda.
- \\(I_S\\) = arus saturasi balik.
- \\(V_D\\) = tegangan dioda.
- \\(n\\) = faktor idealitas dioda.
- \\(V_T\\) = tegangan termal.

Arus yang melalui resistor adalah:

\\[ I_R=\frac{V_S-V_D}{R} \\]

Berdasarkan hukum arus Kirchhoff:

\\[ I_R=I_D \\]

Sehingga:

\\[ \frac{V_S-V_D}{R} = I_S\left(e^{\frac{V_D}{nV_T}}-1\right) \\]

Persamaan tersebut dapat ditulis sebagai:

\\[ f(V_D)= \frac{V_S-V_D}{R} -I_S\left(e^{\frac{V_D}{nV_T}}-1\right)=0 \\]

Persamaan ini merupakan persamaan nonlinear yang dapat diselesaikan menggunakan metode numerik.

### **11.2 Parameter Simulasi**

Gunakan parameter berikut:

| Parameter                 | Nilai            |
| ------------------------- | ---------------- |
| Tegangan sumber \\(V_S\\) | 5 V              |
| Resistansi \\(R\\)        | 1.000 Ω          |
| Arus saturasi \\(I_S\\)   | \\(10^{-12}\\) A |
| Faktor idealitas \\(n\\)  | 1                |
| Tegangan termal \\(V_T\\) | 0,02585 V        |

Tujuan simulasi adalah menentukan nilai tegangan dioda \\(V_D\\) yang memenuhi persamaan rangkaian.

### **11.3 Implementasi Metode Bisection**

```
import math# Parameter rangkaianVs = 5.0R = 1000Is = 1e-12n = 1Vt = 0.02585# Persamaan nonlineardef f(Vd):    arus_resistor = (Vs - Vd) / R    arus_dioda = Is * (        math.exp(Vd / (n * Vt)) - 1    )    return arus_resistor - arus_dioda# Metode Bisectiondef bisection(a, b, toleransi, max_iterasi):    if f(a) * f(b) >= 0:        print("Interval tidak valid")        return None    for i in range(max_iterasi):        xr = (a + b) / 2        if abs(f(xr)) < toleransi:            return xr        if f(a) * f(xr) < 0:            b = xr        else:            a = xr    return xrtegangan_dioda = bisection(    0,    1,    1e-10,    200)arus_dioda = (    (Vs - tegangan_dioda) / R)print("Tegangan dioda:", tegangan_dioda, "V")print("Arus rangkaian:", arus_dioda, "A")print("Residual:", f(tegangan_dioda))
```

### **11.4 Interpretasi Hasil**

Program mencari nilai tegangan dioda yang membuat arus pada resistor sama dengan arus pada dioda.

Dengan demikian, solusi numerik yang diperoleh memenuhi kondisi kerja rangkaian berdasarkan model matematis yang digunakan.

Nilai hasil simulasi bukan angka universal untuk semua dioda. Hasilnya bergantung pada parameter model, suhu, dan karakteristik komponen.

# **BAGIAN VIII — IMPLEMENTASI DAN ANALISIS DENGAN PYTHON**

## **12. Membandingkan Ketiga Metode dalam Satu Program**

Sekarang kita buat program yang menggunakan persamaan yang sama untuk membandingkan Bisection, Regula Falsi, dan Newton-Raphson.

Persamaan:

\\[ f(x)=x^3-x-2 \\]

Nilai akar pendekatan yang akan digunakan sebagai acuan:

\\[ x^\*\approx1.5213797068 \\]

Contoh program:

```
def f(x):    return x**3 - x - 2def df(x):    return 3*x**2 - 1def bisection(a, b, tol):    iterasi = 0    while abs(b - a) > tol:        xr = (a + b) / 2        iterasi += 1        if f(a) * f(xr) < 0:            b = xr        else:            a = xr    return xr, iterasidef regula_falsi(a, b, tol):    iterasi = 0    xr_lama = None    while iterasi < 1000:        xr = (            a * f(b) - b * f(a)        ) / (            f(b) - f(a)        )        iterasi += 1        if xr_lama is not None:            if abs(xr - xr_lama) < tol:                break        if f(a) * f(xr) < 0:            b = xr        else:            a = xr        xr_lama = xr    return xr, iterasidef newton_raphson(x0, tol):    iterasi = 0    while iterasi < 1000:        if df(x0) == 0:            return None, iterasi        x1 = x0 - f(x0) / df(x0)        iterasi += 1        if abs(x1 - x0) < tol:            return x1, iterasi        x0 = x1    return x0, iterasitoleransi = 1e-6hasil_bis, iter_bis = bisection(1, 2, toleransi)hasil_rf, iter_rf = regula_falsi(1, 2, toleransi)hasil_nr, iter_nr = newton_raphson(1.5, toleransi)print("=== PERBANDINGAN METODE NUMERIK ===")print("Bisection:", hasil_bis)print("Iterasi:", iter_bis)print("Residual:", abs(f(hasil_bis)))print("\nRegula Falsi:", hasil_rf)print("Iterasi:", iter_rf)print("Residual:", abs(f(hasil_rf)))print("\nNewton-Raphson:", hasil_nr)print("Iterasi:", iter_nr)print("Residual:", abs(f(hasil_nr)))
```

**Catatan interpretasi:** program di atas menggunakan kriteria penghentian yang berbeda untuk setiap metode: lebar interval pada Bisection, perubahan pendekatan pada Regula Falsi dan Newton-Raphson. Karena itu, jumlah iterasinya tidak boleh dibandingkan sebagai ukuran efisiensi yang sepenuhnya setara tanpa menyamakan kriteria konvergensinya.

## **13. Kesalahan Umum dalam Komputasi Numerik**

| Kesalahan                               | Penyebab                                   | Solusi                               |
| --------------------------------------- | ------------------------------------------ | ------------------------------------ |
| Bisection tidak berjalan                | Interval tidak menunjukkan perubahan tanda | Periksa nilai fungsi di kedua batas  |
| Regula Falsi menghasilkan pembagian nol | Nilai fungsi kedua batas sama              | Validasi penyebut                    |
| Newton-Raphson gagal                    | Turunan bernilai nol                       | Periksa turunan dan nilai awal       |
| Iterasi terlalu banyak                  | Toleransi terlalu kecil                    | Sesuaikan toleransi dengan kebutuhan |
| Hasil tidak konvergen                   | Nilai awal atau metode tidak sesuai        | Evaluasi karakteristik fungsi        |
| Hasil numerik kurang akurat             | Pembulatan terlalu dini                    | Pertahankan presisi selama iterasi   |

## **14. Ringkasan Materi**

Pada pertemuan ini, mahasiswa telah mempelajari:

1. Komputasi numerik digunakan untuk memperoleh solusi pendekatan permasalahan matematis.
2. Galat merupakan selisih antara nilai pendekatan dan nilai acuan.
3. Galat dapat berupa galat absolut, relatif, dan persentase.
4. Persamaan nonlinear merupakan persamaan yang tidak bersifat linear terhadap variabelnya.
5. Akar persamaan merupakan nilai yang menyebabkan fungsi bernilai nol.
6. Metode Bisection menggunakan pembagian interval menjadi dua bagian.
7. Metode Regula Falsi menggunakan pendekatan garis lurus antara dua titik.
8. Metode Newton-Raphson menggunakan turunan pertama fungsi.
9. Toleransi digunakan untuk menentukan tingkat ketelitian solusi.
10. Konvergensi menunjukkan kecenderungan iterasi menuju solusi.
11. Metode numerik dapat diterapkan pada permasalahan Teknik Elektro, termasuk analisis rangkaian dioda.

**Inti pembelajaran:** Keberhasilan komputasi numerik tidak hanya ditentukan oleh nilai akhir yang diperoleh, tetapi juga oleh ketepatan metode, proses iterasi, tingkat galat, dan kemampuan menginterpretasikan hasil.

## **15. Referensi Pembelajaran**

1. Chapra, S. C., & Canale, R. P. (2021). *Numerical Methods for Engineers*, 8th Edition. McGraw-Hill.
2. Burden, R. L., Faires, J. D., & Burden, A. M. (2016). *Numerical Analysis*, 10th Edition. Cengage Learning.
3. Sauer, T. (2018). *Numerical Analysis*, 3rd Edition. Pearson.
4. Python Software Foundation. [Python Math Module Documentation](https://docs.python.org/3/library/math.html?utm_source=chatgpt.com).
