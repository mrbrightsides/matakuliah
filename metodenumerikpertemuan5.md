# **MODUL 5**

## **Metode Numerik untuk Penyelesaian Persamaan Nonlinear**

Pertemuan 5 · Program Studi Teknik Elektro

## **1. Deskripsi Pembelajaran**

Persamaan nonlinear merupakan persamaan matematis yang variabelnya memiliki hubungan tidak linear. Persamaan jenis ini banyak ditemukan dalam berbagai persoalan Teknik Elektro, seperti analisis rangkaian dioda, karakteristik transistor, perhitungan impedansi, sistem tenaga listrik, serta pemodelan komponen elektronik.

Dalam kondisi tertentu, persamaan nonlinear sulit diselesaikan secara analitik. Oleh karena itu, diperlukan metode numerik untuk memperoleh nilai akar atau solusi pendekatan.

Akar persamaan merupakan nilai variabel yang menyebabkan suatu fungsi bernilai nol.

Secara umum, permasalahan pencarian akar dapat dituliskan sebagai:

\\[ f(x)=0 \\]

Metode numerik menyelesaikan persoalan tersebut melalui proses iterasi, yaitu pengulangan perhitungan untuk memperoleh nilai yang semakin mendekati akar persamaan.

## **2. Capaian Pembelajaran**

Setelah mengikuti pembelajaran ini, mahasiswa diharapkan mampu:

1. Menjelaskan karakteristik persamaan nonlinear.
2. Memahami konsep akar persamaan dan proses pencarian akar secara numerik.
3. Menjelaskan prinsip kerja metode Bisection, Regula Falsi, Newton-Raphson, dan Secant.
4. Melakukan perhitungan iterasi secara manual.
5. Mengimplementasikan algoritma pencarian akar menggunakan Python.
6. Membandingkan metode berdasarkan jumlah iterasi, ketelitian, dan karakteristik konvergensinya.
7. Menerapkan metode numerik untuk menyelesaikan persoalan nonlinear dalam bidang Teknik Elektro.

## **3. Konsep Persamaan Nonlinear**

Persamaan nonlinear merupakan persamaan yang tidak dapat dinyatakan dalam bentuk linear sederhana.

Contoh persamaan linear:

\\[ f(x)=2x-6 \\]

Contoh persamaan nonlinear:

\\[ f(x)=x^2-4 \\]

\\[ f(x)=x^3-2x-5 \\]

\\[ f(x)=e^x-3x \\]

Untuk memperoleh akar persamaan nonlinear, kita perlu mencari nilai \\(x\\) yang memenuhi:

\\[ f(x)=0 \\]

Sebagai contoh:

\\[ x^2-4=0 \\]

Maka:

\\[ x^2=4 \\]

\\[ x=\pm2 \\]

Pada contoh tersebut, akar dapat diperoleh secara analitik. Namun, pada persamaan yang lebih kompleks, penyelesaian analitik belum tentu tersedia atau praktis digunakan.

### **3.1 Konsep interval dan pendekatan awal**

Beberapa metode numerik membutuhkan nilai awal atau interval tertentu sebelum proses iterasi dilakukan.

Untuk metode berbasis interval, salah satu prinsip penting adalah perubahan tanda fungsi.

Jika:

\\[ f(a)\times f(b)<0 \\]

maka terdapat setidaknya satu akar pada interval \\([a,b]\\), dengan asumsi fungsi kontinu pada interval tersebut.

Namun, kondisi ini tidak menjamin bahwa akar hanya satu. Sebuah fungsi dapat memiliki lebih dari satu akar dalam suatu interval.

Contoh:

\\[ f(x)=x^2-4 \\]

Dengan interval \\([1,3]\\):

\\[ f(1)=1-4=-3 \\]

\\[ f(3)=9-4=5 \\]

Karena hasil perkalian kedua nilai tersebut negatif, terdapat setidaknya satu akar pada interval tersebut. Dalam hal ini, akar yang dimaksud adalah \\(x=2\\).

## **4. Metode Bisection**

### **4.1 Prinsip dasar**

Metode Bisection atau metode bagi dua merupakan metode pencarian akar dengan membagi interval menjadi dua bagian secara berulang.

Metode ini menggunakan dua batas interval, yaitu \\(a\\) dan \\(b\\), yang memiliki nilai fungsi dengan tanda berbeda.

Titik tengah interval dihitung menggunakan:

\\[ x_r=\frac{a+b}{2} \\]

Selanjutnya, nilai fungsi pada titik tengah diperiksa.

- Jika \\(f(x_r)=0\\), akar telah ditemukan.
- Jika \\(f(a)\times f(x_r)<0\\), interval baru adalah \\([a,x_r]\\).
- Jika \\(f(x_r)\times f(b)<0\\), interval baru adalah \\([x_r,b]\\).

Proses dilakukan berulang sampai memenuhi kriteria penghentian.

### **4.2 Algoritma Bisection**

1. Tentukan fungsi \\(f(x)\\).
2. Tentukan batas bawah \\(a\\) dan batas atas \\(b\\).
3. Pastikan \\(f(a)\times f(b)<0\\).
4. Hitung titik tengah \\(x_r\\).
5. Evaluasi nilai \\(f(x_r)\\).
6. Tentukan interval baru berdasarkan perubahan tanda.
7. Ulangi sampai toleransi galat atau jumlah iterasi terpenuhi.

### **4.3 Contoh perhitungan manual**

Tentukan akar persamaan:

\\[ f(x)=x^2-4=0 \\]

Gunakan interval awal:

\\[ a=1,\quad b=3 \\]

Diperoleh:

\\[ f(1)=-3 \\]

\\[ f(3)=5 \\]

Karena terjadi perubahan tanda, proses Bisection dapat dilakukan.

**Iterasi pertama**

\\[ x_r=\frac{1+3}{2}=2 \\]

\\[ f(2)=2^2-4=0 \\]

Akar langsung ditemukan, yaitu:

\\[ \boxed{x=2} \\]

Untuk melihat proses pembagian interval secara bertahap, kita gunakan persamaan lain:

\\[ f(x)=x^3-2x-5 \\]

Interval awal:

\\[ a=2,\quad b=3 \\]

| Iterasi | a      | b      | \\(x_r\\) | \\(f(x_r)\\) |
| ------- | ------ | ------ | --------- | ------------ |
| 1       | 2,0000 | 3,0000 | 2,5000    | 5,6250       |
| 2       | 2,0000 | 2,5000 | 2,2500    | 1,8906       |
| 3       | 2,0000 | 2,2500 | 2,1250    | 0,3457       |
| 4       | 2,0000 | 2,1250 | 2,0625    | -0,3513      |
| 5       | 2,0625 | 2,1250 | 2,0938    | -0,0089      |

Pada iterasi kelima, nilai fungsi sudah mendekati nol. Interval terus dipersempit sampai toleransi yang ditentukan tercapai.

### **4.4 Implementasi Python**

```
def f(x):    return x**3 - 2*x - 5def bisection(a, b, tol=1e-6, max_iter=100):    if f(a) * f(b) >= 0:        raise ValueError(            "Interval harus memiliki perubahan tanda."        )    print("Iterasi | a | b | xr | f(xr)")    for i in range(1, max_iter + 1):        xr = (a + b) / 2        fxr = f(xr)        print(            f"{i:3d} | {a:.6f} | "            f"{b:.6f} | {xr:.6f} | {fxr:.6f}"        )        if abs(fxr) < tol or (b-a)/2 < tol:            return xr        if f(a) * fxr < 0:            b = xr        else:            a = xr    return xrakar = bisection(2, 3)print("\nAkar persamaan:", akar)print("Nilai fungsi:", f(akar))
```

Metode Bisection memiliki keunggulan berupa kestabilan dan jaminan konvergensi menuju suatu akar pada interval yang memenuhi syarat kontinuitas dan perubahan tanda. Kekurangannya adalah konvergensi relatif lambat.

## **5. Metode Regula Falsi**

### **5.1 Prinsip dasar**

Metode Regula Falsi atau *False Position Method* merupakan metode pencarian akar yang menggunakan pendekatan garis lurus antara dua titik batas interval.

Berbeda dari Bisection yang selalu menggunakan titik tengah, Regula Falsi memperkirakan posisi akar berdasarkan interpolasi linear.

Rumus yang digunakan:

\\[ x_r=b-\frac{f(b)(a-b)}{f(a)-f(b)} \\]

Nilai \\(x_r\\) merupakan perkiraan akar yang diperoleh dari perpotongan garis interpolasi dengan sumbu \\(x\\).

### **5.2 Algoritma Regula Falsi**

1. Tentukan fungsi \\(f(x)\\).
2. Tentukan interval awal \\(a\\) dan \\(b\\).
3. Pastikan \\(f(a)\times f(b)<0\\).
4. Hitung perkiraan akar menggunakan rumus Regula Falsi.
5. Evaluasi nilai fungsi pada perkiraan akar.
6. Perbarui batas interval berdasarkan perubahan tanda.
7. Ulangi sampai kriteria penghentian terpenuhi.

### **5.3 Contoh perhitungan manual**

Gunakan persamaan:

\\[ f(x)=x^3-2x-5 \\]

Dengan interval awal:

\\[ a=2,\quad b=3 \\]

Diketahui:

\\[ f(2)=-1 \\]

\\[ f(3)=16 \\]

**Iterasi pertama**

\\[ x_r=3-\frac{16(2-3)}{-1-16} \\]

\\[ x_r=3-\frac{-16}{-17} \\]

\\[ x_r=2.058824 \\]

Kemudian:

\\[ f(2.058824)\approx-0.3908 \\]

Karena \\(f(a)\\) dan \\(f(x_r)\\) memiliki tanda yang sama, batas bawah diperbarui menjadi:

\\[ a=2.058824 \\]

Sementara batas atas tetap:

\\[ b=3 \\]

**Iterasi kedua**

Gunakan kembali rumus:

\\[ x_r=b-\frac{f(b)(a-b)}{f(a)-f(b)} \\]

Dengan nilai interval yang baru, diperoleh perkiraan akar berikutnya.

| Iterasi | a      | b      | \\(x_r\\) |
| ------- | ------ | ------ | --------- |
| 1       | 2,0000 | 3,0000 | 2,0588    |
| 2       | 2,0588 | 3,0000 | 2,0813    |
| 3       | 2,0813 | 3,0000 | 2,0896    |
| 4       | 2,0896 | 3,0000 | 2,0926    |
| 5       | 2,0926 | 3,0000 | 2,0937    |

Hasil pendekatan semakin mendekati akar persamaan.

### **5.4 Implementasi Python**

```
def f(x):    return x**3 - 2*x - 5def regula_falsi(a, b, tol=1e-6, max_iter=100):    if f(a) * f(b) >= 0:        raise ValueError(            "Interval harus memiliki perubahan tanda."        )    print("Iterasi | a | b | xr | f(xr)")    for i in range(1, max_iter + 1):        fa = f(a)        fb = f(b)        xr = b - (fb * (a-b)) / (fa-fb)        fxr = f(xr)        print(            f"{i:3d} | {a:.6f} | "            f"{b:.6f} | {xr:.6f} | {fxr:.6f}"        )        if abs(fxr) < tol:            return xr        if fa * fxr < 0:            b = xr        else:            a = xr    return xrakar = regula_falsi(2, 3)
```

Metode Regula Falsi biasanya memberikan pendekatan yang lebih terarah daripada Bisection pada beberapa fungsi. Namun, salah satu kelemahannya adalah salah satu batas interval dapat tetap tidak berubah selama banyak iterasi sehingga konvergensi menjadi lambat.

## **6. Metode Newton-Raphson**

### **6.1 Prinsip dasar**

Metode Newton-Raphson merupakan metode iteratif yang menggunakan turunan pertama fungsi untuk memperkirakan akar persamaan.

Metode ini bekerja berdasarkan pendekatan garis singgung terhadap kurva fungsi.

Rumus iterasinya adalah:

\\[ x\_{n+1}=x_n-\frac{f(x_n)}{f'(x_n)} \\]

Keterangan:

- \\(x_n\\) = nilai pendekatan pada iterasi ke-\\(n\\).
- \\(x\_{n+1}\\) = nilai pendekatan berikutnya.
- \\(f(x_n)\\) = nilai fungsi pada \\(x_n\\).
- \\(f'(x_n)\\) = turunan pertama fungsi pada \\(x_n\\).

Metode ini membutuhkan nilai awal dan turunan fungsi.

### **6.2 Algoritma Newton-Raphson**

1. Tentukan fungsi \\(f(x)\\).
2. Tentukan turunan pertama \\(f'(x)\\).
3. Tentukan nilai awal \\(x_0\\).
4. Hitung nilai berikutnya menggunakan rumus Newton-Raphson.
5. Evaluasi perubahan nilai iterasi atau residual fungsi.
6. Ulangi sampai memenuhi kriteria penghentian.

### **6.3 Contoh perhitungan manual**

Gunakan persamaan:

\\[ f(x)=x^3-2x-5 \\]

Turunan pertamanya:

\\[ f'(x)=3x^2-2 \\]

Gunakan nilai awal:

\\[ x_0=2 \\]

**Iterasi pertama**

\\[ x_1=2-\frac{2^3-2(2)-5}{3(2)^2-2} \\]

\\[ x_1=2-\frac{-1}{10} \\]

\\[ x_1=2.1 \\]

**Iterasi kedua**

\\[ x_2=2.1-\frac{(2.1)^3-2(2.1)-5}{3(2.1)^2-2} \\]

\\[ x_2\approx2.094568 \\]

**Iterasi ketiga**

\\[ x_3=2.094568- \frac{f(2.094568)}{f'(2.094568)} \\]

\\[ x_3\approx2.094551 \\]

Dengan demikian, akar persamaan dapat diperkirakan:

\\[ \boxed{x\approx2.094551} \\]

### **6.4 Implementasi Python**

```
def f(x):    return x**3 - 2*x - 5def df(x):    return 3*x**2 - 2def newton_raphson(x0, tol=1e-6, max_iter=100):    x = x0    print("Iterasi | x | f(x)")    for i in range(1, max_iter + 1):        fx = f(x)        dfx = df(x)        print(f"{i:3d} | {x:.8f} | {fx:.8f}")        if abs(fx) < tol:            return x        if abs(dfx) < 1e-12:            raise ValueError(                "Turunan terlalu dekat dengan nol."            )        x_new = x - fx / dfx        x = x_new    return xakar = newton_raphson(2)print("\nAkar persamaan:", akar)
```

Metode Newton-Raphson memiliki konvergensi kuadratik di sekitar akar sederhana jika memenuhi kondisi tertentu. Artinya, ketika iterasi sudah cukup dekat dengan akar dan asumsi metode terpenuhi, jumlah digit akurat dapat bertambah dengan cepat.

Namun, metode ini sensitif terhadap pemilihan nilai awal. Jika turunan mendekati nol atau nilai awal tidak sesuai, metode dapat gagal konvergen.

## **7. Metode Secant**

### **7.1 Prinsip dasar**

Metode Secant merupakan metode pencarian akar yang memiliki prinsip mirip Newton-Raphson, tetapi tidak memerlukan perhitungan turunan secara eksplisit.

Metode ini menggunakan dua nilai pendekatan sebelumnya untuk membentuk garis secant atau garis yang menghubungkan dua titik pada kurva fungsi.

Rumus iterasinya:

\\[ x\_{n+1}=x_n- \frac{f(x_n)(x_n-x\_{n-1})} {f(x_n)-f(x\_{n-1})} \\]

Keterangan:

- \\(x_n\\) = pendekatan saat ini.
- \\(x\_{n-1}\\) = pendekatan sebelumnya.
- \\(x\_{n+1}\\) = pendekatan berikutnya.

### **7.2 Algoritma Secant**

1. Tentukan fungsi \\(f(x)\\).
2. Tentukan dua nilai awal \\(x_0\\) dan \\(x_1\\).
3. Hitung nilai pendekatan baru menggunakan rumus Secant.
4. Geser nilai sebelumnya menjadi nilai saat ini.
5. Ulangi proses sampai memenuhi kriteria penghentian.

### **7.3 Contoh perhitungan manual**

Gunakan persamaan:

\\[ f(x)=x^3-2x-5 \\]

Pilih dua nilai awal:

\\[ x_0=2,\quad x_1=3 \\]

Diketahui:

\\[ f(2)=-1 \\]

\\[ f(3)=16 \\]

**Iterasi pertama**

\\[ x_2=3- \frac{16(3-2)}{16-(-1)} \\]

\\[ x_2=3-\frac{16}{17} \\]

\\[ x_2\approx2.058824 \\]

**Iterasi kedua**

Gunakan \\(x_1=3\\) dan \\(x_2=2.058824\\):

\\[ x_3=x_2- \frac{f(x_2)(x_2-x_1)} {f(x_2)-f(x_1)} \\]

Hasilnya:

\\[ x_3\approx2.081264 \\]

Proses dilanjutkan sampai nilai pendekatan semakin stabil dan nilai fungsi mendekati nol.

### **7.4 Implementasi Python**

```
def f(x):    return x**3 - 2*x - 5def secant(x0, x1, tol=1e-6, max_iter=100):    print("Iterasi | x | f(x)")    for i in range(1, max_iter + 1):        f0 = f(x0)        f1 = f(x1)        if abs(f1 - f0) < 1e-12:            raise ValueError(                "Penyebut terlalu dekat dengan nol."            )        x2 = x1 - f1 * (x1-x0) / (f1-f0)        fx2 = f(x2)        print(f"{i:3d} | {x2:.8f} | {fx2:.8f}")        if abs(fx2) < tol:            return x2        x0 = x1        x1 = x2    return x2akar = secant(2, 3)print("\nAkar persamaan:", akar)print("Nilai fungsi:", f(akar))
```

Metode Secant tidak membutuhkan turunan analitik sehingga dapat lebih praktis untuk fungsi yang turunannya sulit dihitung.

Namun, metode ini tidak selalu konvergen dan pemilihan dua nilai awal sangat memengaruhi hasilnya.

## **8. Perbandingan Keempat Metode**

Keempat metode memiliki karakteristik yang berbeda. Pemilihan metode perlu disesuaikan dengan bentuk fungsi, ketersediaan turunan, nilai awal, dan kebutuhan ketelitian.

| Aspek               | Bisection                 | Regula Falsi              | Newton-Raphson  | Secant            |
| ------------------- | ------------------------- | ------------------------- | --------------- | ----------------- |
| Nilai awal          | Dua batas                 | Dua batas                 | Satu nilai      | Dua nilai         |
| Turunan             | Tidak                     | Tidak                     | Ya              | Tidak             |
| Prinsip             | Pembagian interval        | Interpolasi linear        | Garis singgung  | Garis secant      |
| Konvergensi         | Linear                    | Umumnya linear            | Kuadratik lokal | Superlinear lokal |
| Jaminan konvergensi | Ya, jika syarat terpenuhi | Ya, jika syarat terpenuhi | Tidak umum      | Tidak umum        |
| Kompleksitas        | Rendah                    | Rendah                    | Sedang          | Sedang            |

Catatan: konvergensi Regula Falsi dapat sangat lambat pada fungsi tertentu. Konvergensi Newton-Raphson dan Secant juga bergantung pada kedekatan nilai awal dengan akar dan karakteristik fungsi.

### **8.1 Perbandingan hasil menggunakan Python**

Kita dapat menggunakan persamaan yang sama untuk membandingkan hasil keempat metode.

```
def f(x):    return x**3 - 2*x - 5def df(x):    return 3*x**2 - 2# Nilai akar referensiakar_referensi = 2.0945514815# Hasil dari masing-masing metodehasil = {    "Bisection": bisection(2, 3),    "Regula Falsi": regula_falsi(2, 3),    "Newton-Raphson": newton_raphson(2),    "Secant": secant(2, 3)}print("\nPERBANDINGAN HASIL")for nama, akar in hasil.items():    galat = abs(akar_referensi - akar)    print(        f"{nama:18s} "        f"Akar = {akar:.8f} "        f"Galat = {galat:.8e}"    )
```

Sebelum menjalankan kode perbandingan, pastikan fungsi-fungsi metode sudah didefinisikan pada sesi Python yang sama. Untuk laporan perbandingan yang adil, gunakan toleransi dan kriteria penghentian yang sama serta catat jumlah evaluasi fungsi, bukan hanya jumlah iterasi.

## **9. Studi Kasus Teknik Elektro: Analisis Karakteristik Dioda**

### **9.1 Deskripsi kasus**

Sebuah rangkaian menggunakan dioda semikonduktor yang memiliki karakteristik arus dan tegangan nonlinear.

Hubungan arus dan tegangan dioda dapat dimodelkan menggunakan persamaan Shockley:

\\[ I_D=I_S \left( e^{\frac{V_D}{nV_T}}-1 \right) \\]

Keterangan:

- \\(I_D\\) = arus dioda.
- \\(I_S\\) = arus saturasi balik.
- \\(V_D\\) = tegangan dioda.
- \\(n\\) = faktor idealitas dioda.
- \\(V_T\\) = tegangan termal.

Untuk rangkaian sumber tegangan \\(V_S\\) dan resistor \\(R\\) yang terhubung seri dengan dioda, berdasarkan hukum Kirchhoff tegangan:

\\[ V_S=I_DR+V_D \\]

Dengan memasukkan persamaan Shockley:

\\[ V_S= RI_S \left( e^{\frac{V_D}{nV_T}}-1 \right) +V_D \\]

Persamaan tersebut merupakan persamaan nonlinear yang perlu diselesaikan untuk memperoleh nilai tegangan dioda.

### **9.2 Menentukan persamaan akar**

Persamaan dapat diubah menjadi:

\\[ f(V_D)= RI_S \left( e^{\frac{V_D}{nV_T}}-1 \right) +V_D-V_S \\]

Nilai \\(V_D\\) yang membuat \\(f(V_D)=0\\) merupakan tegangan dioda yang dicari.

### **9.3 Parameter simulasi**

Gunakan parameter berikut sebagai contoh simulasi:

| Parameter                 | Nilai            |
| ------------------------- | ---------------- |
| Tegangan sumber \\(V_S\\) | 5 V              |
| Resistansi \\(R\\)        | 1000 Ω           |
| Arus saturasi \\(I_S\\)   | \\(10^{-12}\\) A |
| Faktor idealitas \\(n\\)  | 1                |
| Tegangan termal \\(V_T\\) | 0,02585 V        |

### **9.4 Implementasi menggunakan Python**

```
import math# Parameter rangkaianVs = 5.0R = 1000.0Is = 1e-12n = 1.0Vt = 0.02585# Persamaan nonlineardef f(Vd):    exponent = Vd / (n * Vt)    return (        R * Is * (math.exp(exponent) - 1)        + Vd - Vs    )# Metode Bisectiondef bisection(a, b, tol=1e-8):    if f(a) * f(b) >= 0:        raise ValueError("Interval tidak valid")    for i in range(100):        xr = (a+b)/2        if abs(f(xr)) < tol:            return xr        if f(a) * f(xr) < 0:            b = xr        else:            a = xr    return xrVd = bisection(0, 1)# Menghitung arus diodaId = (Vs - Vd) / Rprint("Tegangan Dioda :", Vd, "V")print("Arus Dioda     :", Id, "A")print("Residual       :", f(Vd), "V")
```

### **9.5 Interpretasi hasil**

Dari simulasi, mahasiswa akan memperoleh nilai pendekatan tegangan dioda dan arus yang mengalir pada rangkaian.

Hasil tersebut dapat digunakan untuk memahami bagaimana metode numerik menyelesaikan model komponen elektronik yang memiliki karakteristik nonlinear.

Mahasiswa juga perlu memperhatikan bahwa model Shockley merupakan model idealisasi. Hasil simulasi bergantung pada parameter dioda, temperatur, dan asumsi model yang digunakan.

## **10. Evaluasi Kinerja Metode Numerik**

Keberhasilan metode numerik tidak hanya ditentukan oleh nilai akar yang diperoleh. Ada beberapa aspek yang perlu diperhatikan.

**10.1 Residual**

Residual merupakan nilai fungsi pada akar pendekatan:

\\[ r=|f(x_r)| \\]

Semakin kecil residual, semakin dekat nilai pendekatan terhadap pemenuhan persamaan.

**10.2 Galat pendekatan**

Jika nilai akar referensi diketahui, galat absolut dapat dihitung menggunakan:

\\[ E_a=|x\_{\text{referensi}}-x_r| \\]

**10.3 Jumlah iterasi**

Jumlah iterasi dapat digunakan untuk membandingkan efisiensi metode, tetapi perlu memperhatikan bahwa satu iterasi pada setiap metode belum tentu membutuhkan jumlah evaluasi fungsi yang sama.

**10.4 Kriteria penghentian**

Proses iterasi dapat dihentikan ketika salah satu kondisi berikut terpenuhi:

\\[ |f(x_r)|<\varepsilon \\]

atau

\\[ |x\_{n+1}-x_n|<\varepsilon \\]

dengan \\(\varepsilon\\) merupakan toleransi yang ditentukan.

Kedua kriteria tersebut tidak selalu setara. Perubahan nilai iterasi yang kecil belum tentu menjamin residual juga kecil. Oleh karena itu, pemeriksaan residual sangat dianjurkan.

## **11. Kesalahan Umum dalam Penyelesaian Persamaan Nonlinear**

Beberapa kesalahan yang sering terjadi antara lain:

1. Menggunakan metode Bisection atau Regula Falsi tanpa memastikan perubahan tanda pada interval.
2. Memilih nilai awal Newton-Raphson yang tidak sesuai.
3. Mengabaikan kemungkinan turunan bernilai nol atau mendekati nol.
4. Tidak memperhatikan penyebut yang mendekati nol pada metode Secant.
5. Menghentikan iterasi hanya berdasarkan jumlah iterasi tanpa mengevaluasi hasil.
6. Menganggap semua metode selalu konvergen.
7. Membandingkan metode dengan kriteria penghentian yang berbeda.
8. Tidak memeriksa residual setelah mendapatkan akar pendekatan.

## **12. Rangkuman**

Pada pertemuan ini, mahasiswa telah mempelajari:

- Pengertian persamaan nonlinear dan akar persamaan.
- Prinsip metode Bisection.
- Prinsip metode Regula Falsi.
- Prinsip metode Newton-Raphson.
- Prinsip metode Secant.
- Perhitungan iterasi secara manual.
- Implementasi algoritma menggunakan Python.
- Perbandingan karakteristik dan konvergensi metode.
- Penerapan metode numerik pada analisis rangkaian dioda.
- Evaluasi hasil melalui residual, galat, dan jumlah iterasi.

## **13. Referensi Pembelajaran**

1. Chapra, S. C., & Canale, R. P. *Numerical Methods for Engineers*. McGraw-Hill.
2. Burden, R. L., Faires, J. D., & Burden, A. M. *Numerical Analysis*. Cengage Learning.
3. Sauer, T. *Numerical Analysis*. Pearson.
4. Kiusalaas, J. *Numerical Methods in Engineering with Python 3*. Cambridge University Press.
5. Boylestad, R. L., & Nashelsky, L. *Electronic Devices and Circuit Theory*. Pearson.
