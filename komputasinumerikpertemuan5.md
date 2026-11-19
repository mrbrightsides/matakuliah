# **MODULE 5**

# **PENYELESAIAN SISTEM PERSAMAAN LINEAR**

Pertemuan 5

Komputasi Numerik

Program Studi Teknik Elektro

## **1. Deskripsi Materi**

Sistem persamaan linear merupakan kumpulan dua atau lebih persamaan yang memiliki variabel-variabel yang saling berkaitan.

Dalam bidang Teknik Elektro, sistem persamaan linear sering digunakan untuk menyelesaikan permasalahan seperti:

- Menentukan arus pada beberapa cabang rangkaian.
- Menentukan tegangan pada beberapa node.
- Menganalisis jaringan listrik berdasarkan Hukum Kirchhoff.
- Menghitung distribusi arus dan tegangan.
- Menyelesaikan model matematis sistem tenaga listrik.

Untuk sistem persamaan dengan banyak variabel, penyelesaian secara manual dapat menjadi kompleks. Oleh karena itu, diperlukan metode numerik yang dapat menyelesaikan sistem persamaan secara sistematis.

Pada pertemuan ini, mahasiswa akan mempelajari metode Eliminasi Gauss, Gauss-Jordan, dan Gauss-Seidel serta membandingkan karakteristik ketiganya.

## **2. Capaian Pembelajaran**

Setelah menyelesaikan materi ini, mahasiswa diharapkan mampu:

1. Menjelaskan konsep sistem persamaan linear.
2. Merepresentasikan sistem persamaan linear dalam bentuk matriks.
3. Memahami konsep matriks koefisien dan vektor konstanta.
4. Menyelesaikan sistem persamaan linear menggunakan Eliminasi Gauss.
5. Menyelesaikan sistem persamaan linear menggunakan Gauss-Jordan.
6. Mengimplementasikan metode Gauss-Seidel.
7. Menghitung residual dan mengevaluasi ketelitian hasil.
8. Memahami kondisi konvergensi metode iteratif.
9. Menerapkan metode numerik pada permasalahan rangkaian listrik.

# **BAGIAN I — KONSEP SISTEM PERSAMAAN LINEAR**

## **3. Pengertian Sistem Persamaan Linear**

Sistem persamaan linear adalah sekumpulan persamaan yang setiap variabelnya memiliki pangkat satu dan tidak dikalikan dengan variabel lainnya.

Contoh sistem persamaan linear dengan dua variabel:

\\[ 2x+3y=13 \\]

\\[ x+y=5 \\]

Tujuannya adalah menentukan nilai \\(x\\) dan \\(y\\) yang memenuhi kedua persamaan tersebut secara bersamaan.

Dari persamaan kedua:

\\[ x=5-y \\]

Substitusikan ke persamaan pertama:

\\[ 2(5-y)+3y=13 \\]

\\[ 10-2y+3y=13 \\]

\\[ y=3 \\]

Sehingga:

\\[ x=2 \\]

Jadi, solusi sistem persamaan tersebut adalah:

\\[ \boxed{x=2,\quad y=3} \\]

### **3.1 Sistem Persamaan Linear dengan Tiga Variabel**

Contoh:

\\[ 2x+y+z=7 \\]

\\[ x+2y+z=8 \\]

\\[ x+y+2z=9 \\]

Sistem tersebut memiliki tiga variabel, yaitu \\(x\\), \\(y\\), dan \\(z\\).

Semakin banyak variabel dan persamaan, semakin kompleks proses penyelesaiannya. Metode matriks membantu menyusun dan menyelesaikan sistem tersebut secara terstruktur.

## **4. Representasi Matriks**

Sistem persamaan linear dapat ditulis dalam bentuk:

\\[ AX=B \\]

Keterangan:

- \\(A\\) = matriks koefisien.
- \\(X\\) = vektor variabel.
- \\(B\\) = vektor konstanta.

Untuk contoh tiga variabel sebelumnya:

\\[ \begin{bmatrix} 2&1&1\\\ 1&2&1\\\ 1&1&2 \end{bmatrix} \begin{bmatrix} x\\\y\\\z \end{bmatrix} = \begin{bmatrix} 7\\\8\\\9 \end{bmatrix} \\]

Dengan demikian:

\\[ A= \begin{bmatrix} 2&1&1\\\ 1&2&1\\\ 1&1&2 \end{bmatrix} \\]

\\[ X= \begin{bmatrix} x\\\y\\\z \end{bmatrix} \\]

\\[ B= \begin{bmatrix} 7\\\8\\\9 \end{bmatrix} \\]

### **4.1 Matriks Augmented**

Dalam metode eliminasi, sistem persamaan sering ditulis dalam bentuk matriks augmented.

Matriks augmented merupakan penggabungan matriks koefisien dengan vektor konstanta.

\\[ \left[ \begin{array}{ccc|c} 2&1&1&7\\\ 1&2&1&8\\\ 1&1&2&9 \end{array} \right] \\]

Representasi ini akan digunakan pada metode Eliminasi Gauss dan Gauss-Jordan.

# **BAGIAN II — METODE ELIMINASI GAUSS**

## **5. Konsep Metode Eliminasi Gauss**

Metode Eliminasi Gauss merupakan metode penyelesaian sistem persamaan linear dengan mengubah matriks augmented menjadi bentuk segitiga atas (*upper triangular matrix*).

Setelah bentuk segitiga atas diperoleh, nilai setiap variabel dihitung menggunakan proses substitusi mundur (*back substitution*).

Tujuan eliminasi adalah menghilangkan variabel pada bagian bawah diagonal utama matriks.

### **5.1 Operasi Baris Elementer**

Dalam proses Eliminasi Gauss, terdapat tiga operasi baris elementer:

1. Menukar dua baris.
2. Mengalikan satu baris dengan konstanta bukan nol.
3. Menambahkan atau mengurangi suatu baris dengan kelipatan baris lainnya.

Operasi tersebut digunakan untuk mengubah bentuk matriks tanpa mengubah solusi sistem persamaan.

### **5.2 Contoh Penyelesaian Manual**

Gunakan sistem persamaan:

\\[ 2x+y+z=7 \\]

\\[ x+2y+z=8 \\]

\\[ x+y+2z=9 \\]

Matriks augmented:

\\[ \left[ \begin{array}{ccc|c} 2&1&1&7\\\ 1&2&1&8\\\ 1&1&2&9 \end{array} \right] \\]

**Langkah 1 — Eliminasi variabel x pada baris kedua dan ketiga.**

Gunakan operasi:

\\[ R_2\leftarrow 2R_2-R_1 \\]

\\[ R_3\leftarrow 2R_3-R_1 \\]

Hasil:

\\[ \left[ \begin{array}{ccc|c} 2&1&1&7\\\ 0&3&1&9\\\ 0&1&3&11 \end{array} \right] \\]

**Langkah 2 — Eliminasi variabel y pada baris ketiga.**

Gunakan operasi:

\\[ R_3\leftarrow 3R_3-R_2 \\]

Hasil:

\\[ \left[ \begin{array}{ccc|c} 2&1&1&7\\\ 0&3&1&9\\\ 0&0&8&24 \end{array} \right] \\]

Matriks sekarang berbentuk segitiga atas.

**Langkah 3 — Substitusi mundur.**

Dari baris ketiga:

\\[ 8z=24 \\]

\\[ z=3 \\]

Dari baris kedua:

\\[ 3y+z=9 \\]

\\[ 3y+3=9 \\]

\\[ y=2 \\]

Dari baris pertama:

\\[ 2x+y+z=7 \\]

\\[ 2x+2+3=7 \\]

\\[ x=1 \\]

Maka solusi sistem adalah:

\\[ \boxed{x=1,\quad y=2,\quad z=3} \\]

### **5.3 Implementasi Eliminasi Gauss Menggunakan Python**

Untuk implementasi dasar, kita menggunakan List dua dimensi sebagai representasi matriks augmented.

```
def gauss_elimination(A, b):    n = len(b)    # Membuat matriks augmented    M = [        A[i][:] + [b[i]]        for i in range(n)    ]    # Proses eliminasi maju    for i in range(n):        # Pivoting sederhana        max_row = max(            range(i, n),            key=lambda r: abs(M[r][i])        )        M[i], M[max_row] = M[max_row], M[i]        if abs(M[i][i]) < 1e-12:            raise ValueError("Matriks singular atau hampir singular")        for j in range(i + 1, n):            faktor = M[j][i] / M[i][i]            for k in range(i, n + 1):                M[j][k] -= faktor * M[i][k]    # Substitusi mundur    x = [0.0] * n    for i in range(n - 1, -1, -1):
```

Output:

```
Hasil Eliminasi Gauss:
Variabel 1 = 1.0
Variabel 2 = 2.0
Variabel 3 = 3.0
```

### **5.4 Analisis Program**

Program tersebut memiliki dua tahapan utama:

- Eliminasi maju: mengubah matriks menjadi bentuk segitiga atas.
- Substitusi mundur: menghitung nilai variabel dari baris terakhir ke baris pertama.

Program juga menerapkan *partial pivoting*, yaitu memilih elemen dengan nilai absolut terbesar pada kolom pivot dari baris yang tersedia. Teknik ini membantu mengurangi risiko pembagian dengan nilai pivot yang sangat kecil.

**Kompleksitas waktu:** untuk sistem berukuran \\(n \times n\\), Eliminasi Gauss secara umum membutuhkan operasi berorde:

\\[ O(n^3) \\]

# **BAGIAN III — METODE GAUSS-JORDAN**

## **6. Konsep Metode Gauss-Jordan**

Metode Gauss-Jordan merupakan pengembangan dari Eliminasi Gauss.

Jika Eliminasi Gauss mengubah matriks menjadi bentuk segitiga atas, Gauss-Jordan melanjutkan proses eliminasi hingga menghasilkan bentuk *reduced row echelon form* (RREF).

Pada bentuk RREF:

- Elemen diagonal utama bernilai 1.
- Elemen di atas diagonal utama bernilai 0.
- Elemen di bawah diagonal utama bernilai 0.

Dengan demikian, nilai variabel dapat langsung diperoleh tanpa substitusi mundur.

### **6.1 Contoh Penyelesaian Manual**

Gunakan kembali sistem persamaan:

\\[ 2x+y+z=7 \\]

\\[ x+2y+z=8 \\]

\\[ x+y+2z=9 \\]

Matriks augmented awal:

\\[ \left[ \begin{array}{ccc|c} 2&1&1&7\\\ 1&2&1&8\\\ 1&1&2&9 \end{array} \right] \\]

Melalui pertukaran dan operasi baris elementer, matriks diubah menjadi bentuk RREF:

\\[ \left[ \begin{array}{ccc|c} 1&0&0&1\\\ 0&1&0&2\\\ 0&0&1&3 \end{array} \right] \\]

Dari matriks tersebut langsung diperoleh:

\\[ x=1,\quad y=2,\quad z=3 \\]

### **6.2 Implementasi Gauss-Jordan Menggunakan Python**

```
def gauss_jordan(A, b):    n = len(b)    M = [        A[i][:] + [b[i]]        for i in range(n)    ]    for i in range(n):        # Memilih pivot        max_row = max(            range(i, n),            key=lambda r: abs(M[r][i])        )        M[i], M[max_row] = M[max_row], M[i]        pivot = M[i][i]        if abs(pivot) < 1e-12:            raise ValueError("Matriks singular atau hampir singular")        # Membuat pivot menjadi 1        for j in range(n + 1):            M[i][j] /= pivot        # Menghilangkan elemen lain pada kolom pivot        for k in range(n):            if k != i:                faktor = M[k][i]                for j in range(n + 1):
```

Output:

```
Hasil Gauss-Jordan:
Variabel 1 = 1.0
Variabel 2 = 2.0
Variabel 3 = 3.0
```

### **6.3 Analisis Metode Gauss-Jordan**

Kelebihan:

- Solusi dapat diperoleh langsung dari matriks hasil.
- Tidak memerlukan substitusi mundur.
- Konsep operasi baris mudah diamati.
- Dapat digunakan untuk mencari invers matriks melalui proses augmented dengan matriks identitas.

Kekurangan:

- Jumlah operasi umumnya lebih banyak dibandingkan Eliminasi Gauss.
- Membutuhkan pengelolaan matriks yang teliti.
- Tetap memerlukan perhatian terhadap pivot yang mendekati nol.

Untuk sistem persamaan berukuran besar, Eliminasi Gauss dengan pivoting atau metode faktorisasi matriks sering lebih efisien daripada Gauss-Jordan.

# **BAGIAN IV — METODE GAUSS-SEIDEL**

## **7. Konsep Metode Gauss-Seidel**

Berbeda dari Eliminasi Gauss dan Gauss-Jordan yang merupakan metode langsung, Gauss-Seidel merupakan metode iteratif.

Metode ini memperoleh solusi melalui perhitungan berulang dengan menggunakan nilai terbaru yang telah dihitung pada iterasi yang sama.

Metode Gauss-Seidel sering digunakan untuk menyelesaikan sistem persamaan linear berukuran besar, khususnya ketika struktur matriksnya sesuai untuk metode iteratif.

### **7.1 Bentuk Umum Sistem Persamaan**

Misalkan sistem persamaan:

\\[ a\_{11}x_1+a\_{12}x_2+\cdots+a\_{1n}x_n=b_1 \\]

\\[ a\_{21}x_1+a\_{22}x_2+\cdots+a\_{2n}x_n=b_2 \\]

\\[ \vdots \\]

\\[ a\_{n1}x_1+a\_{n2}x_2+\cdots+a\_{nn}x_n=b_n \\]

Setiap persamaan diubah sehingga variabel diagonalnya berada di ruas kiri.

Rumus umum Gauss-Seidel:

\\[ x_i^{(k+1)} = \frac{1}{a\_{ii}} \left[ b_i- \sum\_{j=1}^{i-1}a\_{ij}x_j^{(k+1)} - \sum\_{j=i+1}^{n}a\_{ij}x_j^{(k)} \right] \\]

Keterangan:

- \\(x_i^{(k+1)}\\) = nilai variabel baru.
- \\(x_j^{(k+1)}\\) = nilai terbaru pada iterasi saat ini.
- \\(x_j^{(k)}\\) = nilai dari iterasi sebelumnya.
- \\(k\\) = nomor iterasi.

### **7.2 Contoh Sistem Persamaan**

Gunakan sistem berikut:

\\[ 10x+y+z=12 \\]

\\[ 2x+10y+z=13 \\]

\\[ 2x+2y+10z=14 \\]

Ubah menjadi:

\\[ x=\frac{12-y-z}{10} \\]

\\[ y=\frac{13-2x-z}{10} \\]

\\[ z=\frac{14-2x-2y}{10} \\]

Gunakan nilai awal:

\\[ x_0=0,\quad y_0=0,\quad z_0=0 \\]

**Iterasi pertama**

Menghitung \\(x_1\\):

\\[ x_1=\frac{12-0-0}{10}=1.2 \\]

Menghitung \\(y_1\\):

\\[ y_1=\frac{13-2(1.2)-0}{10}=1.06 \\]

Menghitung \\(z_1\\):

\\[ z_1=\frac{14-2(1.2)-2(1.06)}{10}=0.948 \\]

Hasil iterasi pertama:

\\[ x_1=1.2,\quad y_1=1.06,\quad z_1=0.948 \\]

Pada iterasi berikutnya, nilai baru tersebut digunakan kembali. Proses dilakukan hingga memenuhi toleransi yang telah ditentukan.

### **7.3 Implementasi Gauss-Seidel dengan Python**

```
def gauss_seidel(A, b, x0, toleransi, max_iterasi):    n = len(b)    x = x0.copy()    for iterasi in range(1, max_iterasi + 1):        x_lama = x.copy()        for i in range(n):            if abs(A[i][i]) < 1e-12:                raise ValueError("Elemen diagonal tidak boleh nol")            jumlah = 0            for j in range(n):                if j != i:                    jumlah += A[i][j] * x[j]            x[i] = (b[i] - jumlah) / A[i][i]        galat = max(            abs(x[i] - x_lama[i])            for i in range(n)        )        print(            f"Iterasi {iterasi}: {x}, Galat = {galat}"        )        if galat < toleransi:            return x, iterasi
```

### **7.4 Analisis Metode Gauss-Seidel**

Kelebihan:

- Cocok untuk sistem dengan banyak variabel apabila struktur matriks mendukung konvergensi.
- Tidak membutuhkan proses eliminasi matriks secara penuh.
- Dapat menghasilkan solusi dengan iterasi bertahap.
- Nilai terbaru langsung digunakan pada perhitungan berikutnya.

Kekurangan:

- Membutuhkan nilai awal.
- Tidak selalu konvergen.
- Hasil bergantung pada karakteristik matriks dan susunan persamaan.
- Membutuhkan kriteria penghentian yang tepat.

### **7.5 Syarat Konvergensi Gauss-Seidel**

Salah satu kondisi yang cukup untuk menjamin konvergensi adalah matriks koefisien bersifat dominan diagonal secara ketat.

Artinya:

\\[ |a\_{ii}|>\sum\_{j\neq i}|a\_{ij}| \\]

untuk setiap baris \\(i\\).

Matriks yang dominan diagonal secara ketat akan memenuhi kondisi konvergensi Gauss-Seidel.

Namun, kondisi tersebut bukan satu-satunya cara agar metode dapat konvergen. Terdapat kondisi matematis lain, seperti matriks simetris positif definit.

# **BAGIAN V — PERBANDINGAN METODE**

## **8. Perbandingan Eliminasi Gauss, Gauss-Jordan, dan Gauss-Seidel**

| Aspek                | Eliminasi Gauss                       | Gauss-Jordan                          | Gauss-Seidel                             |
| -------------------- | ------------------------------------- | ------------------------------------- | ---------------------------------------- |
| Jenis metode         | Langsung                              | Langsung                              | Iteratif                                 |
| Proses utama         | Eliminasi maju dan substitusi mundur  | Eliminasi hingga RREF                 | Perhitungan berulang                     |
| Nilai awal           | Tidak perlu                           | Tidak perlu                           | Perlu                                    |
| Kriteria konvergensi | Tidak menggunakan iterasi konvergensi | Tidak menggunakan iterasi konvergensi | Diperlukan                               |
| Kompleksitas dasar   | O(n³)                                 | O(n³)                                 | Bergantung jumlah iterasi                |
| Penggunaan           | Sistem persamaan linear umum          | Penyelesaian dan manipulasi matriks   | Sistem besar dengan struktur yang sesuai |

### **8.1 Perbedaan Metode Langsung dan Iteratif**

**Metode langsung**

Metode langsung berusaha memperoleh solusi melalui sejumlah operasi matematis yang terstruktur.

Contoh:

- Eliminasi Gauss.
- Gauss-Jordan.

**Metode iteratif**

Metode iteratif menggunakan nilai awal dan melakukan perhitungan berulang untuk mendekati solusi.

Contoh:

- Gauss-Seidel.
- Jacobi.

## **9. Mengukur Ketelitian Hasil dengan Residual**

Dalam penyelesaian sistem persamaan linear, kita dapat mengukur seberapa baik solusi numerik memenuhi persamaan awal menggunakan residual.

Bentuk matematis:

\\[ r=b-Ax \\]

Keterangan:

- \\(A\\) = matriks koefisien.
- \\(x\\) = vektor solusi.
- \\(b\\) = vektor konstanta.
- \\(r\\) = vektor residual.

Jika nilai residual mendekati nol, berarti solusi numerik semakin memenuhi sistem persamaan awal.

Contoh implementasi Python:

```
def hitung_residual(A, b, x):    n = len(b)    residual = []    for i in range(n):        hasil = sum(            A[i][j] * x[j]            for j in range(n)        )        residual.append(b[i] - hasil)    return residualA = [    [2, 1, 1],    [1, 2, 1],    [1, 1, 2]]b = [7, 8, 9]x = [1, 2, 3]residual = hitung_residual(A, b, x)print("Residual:", residual)print("Residual maksimum:", max(abs(r) for r in residual))
```

Output:

```
Residual: [0, 0, 0]
Residual maksimum: 0
```

Pada contoh ini, solusi memenuhi seluruh persamaan secara eksak.

Untuk perhitungan floating-point, residual mungkin tidak selalu nol persis. Karena itu, kita dapat menggunakan norma residual, misalnya:

\\[ \\|r\\|\_\infty=\max_i|r_i| \\]

Nilai ini menunjukkan residual terbesar dari seluruh persamaan.

# **BAGIAN VI — STUDI KASUS TEKNIK ELEKTRO**

## **10. Studi Kasus: Analisis Rangkaian Listrik Menggunakan Hukum Kirchhoff**

[节点电压法的详细讲解（节点分析法）](https://images.openai.com/static-rsc-4/btAGDykGgVWe93Z0fOVJhEC-9LZ9lwUokoYp1cYL7L2LvVAbl2MNgHHUZtbSACogf00XmDQnU_jgmK_h-voFLFAMWo7wBFXq6752T2OrcAm0eEn76YqQX5byX0FeypjzU-TiEA5bCWd0uqMiuXcmHxnj71ycP55EkQ5Ad84N59Y?purpose=inline)

[panz.com.cn](https://www.panz.com.cn/changshi/wGgEyglb17.html?utm_source=chatgpt.com)

### **10.1 Deskripsi Permasalahan**

Sebuah rangkaian listrik DC memiliki dua node utama, yaitu Node 1 dan Node 2. Rangkaian terdiri atas:

- Sumber tegangan DC sebesar 12 V.
- Resistor 2 Ω yang menghubungkan sumber tegangan ke Node 1.
- Resistor 4 Ω yang menghubungkan Node 1 ke ground.
- Resistor 6 Ω yang menghubungkan Node 1 dan Node 2.
- Resistor 3 Ω yang menghubungkan Node 2 ke ground.
- Sumber arus 2 A yang menginjeksikan arus ke Node 2.

Kita ingin menentukan tegangan pada Node 1 dan Node 2 menggunakan analisis nodal berdasarkan Hukum Arus Kirchhoff (KCL).

### **10.2 Membentuk Persamaan Matematis**

Hukum Arus Kirchhoff menyatakan bahwa jumlah arus yang masuk ke suatu node sama dengan jumlah arus yang keluar dari node tersebut.

**Persamaan pada Node 1:**

\\[ \frac{V_1-12}{2}+\frac{V_1}{4} +\frac{V_1-V_2}{6}=0 \\]

Kalikan dengan 12:

\\[ 6(V_1-12)+3V_1+2(V_1-V_2)=0 \\]

Sederhanakan:

\\[ 11V_1-2V_2=72 \\]

**Persamaan pada Node 2:**

\\[ \frac{V_2-V_1}{6}+\frac{V_2}{3}=2 \\]

Kalikan dengan 6:

\\[ V_2-V_1+2V_2=12 \\]

Sederhanakan:

\\[ -V_1+3V_2=12 \\]

### **10.3 Representasi Matriks**

Kedua persamaan dapat ditulis sebagai:

\\[ \begin{bmatrix} 11&-2\\\ -1&3 \end{bmatrix} \begin{bmatrix} V_1\\\ V_2 \end{bmatrix} = \begin{bmatrix} 72\\\ 12 \end{bmatrix} \\]

Sehingga:

\\[ A= \begin{bmatrix} 11&-2\\\ -1&3 \end{bmatrix} \\]

\\[ B= \begin{bmatrix} 72\\\12 \end{bmatrix} \\]

Solusi yang dicari adalah tegangan \\(V_1\\) dan \\(V_2\\).

### **10.4 Penyelesaian Manual**

Dari persamaan kedua:

\\[ -V_1+3V_2=12 \\]

\\[ V_1=3V_2-12 \\]

Substitusikan ke persamaan pertama:

\\[ 11(3V_2-12)-2V_2=72 \\]

\\[ 33V_2-132-2V_2=72 \\]

\\[ 31V_2=204 \\]

\\[ V_2=\frac{204}{31} \\]

\\[ V_2\approx6.580645\ V \\]

Kemudian:

\\[ V_1=3(6.580645)-12 \\]

\\[ V_1\approx7.741935\ V \\]

**Hasil penyelesaian rangkaian**

# **7,7419 V**

Tegangan Node 1

# **6,5806 V**

Tegangan Node 2

### **10.5 Implementasi Menggunakan Eliminasi Gauss**

```
def gauss_elimination(A, b):    n = len(b)    M = [        A[i][:] + [b[i]]        for i in range(n)    ]    # Eliminasi maju    for i in range(n):        max_row = max(            range(i, n),            key=lambda r: abs(M[r][i])        )        M[i], M[max_row] = M[max_row], M[i]        if abs(M[i][i]) < 1e-12:            raise ValueError("Matriks singular")        for j in range(i + 1, n):            faktor = M[j][i] / M[i][i]            for k in range(i, n + 1):                M[j][k] -= faktor * M[i][k]    # Substitusi mundur    x = [0.0] * n    for i in range(n - 1, -1, -1):        jumlah = sum(            M[i][j] * x[j]
```

Output:

```
=== ANALISIS RANGKAIAN LISTRIK ===
Tegangan Node 1: 7.741935483870968 Volt
Tegangan Node 2: 6.580645161290323 Volt
```

### **10.6 Verifikasi Hasil Perhitungan**

Kita dapat memeriksa apakah hasil perhitungan memenuhi persamaan awal.

Persamaan pertama:

\\[ 11(7.741935)-2(6.580645)\approx72 \\]

Persamaan kedua:

\\[ -7.741935+3(6.580645)\approx12 \\]

Kedua persamaan terpenuhi dengan selisih numerik yang sangat kecil.

### **10.7 Analisis Arus Rangkaian**

Setelah tegangan node diperoleh, arus pada setiap resistor juga dapat dihitung menggunakan Hukum Ohm.

Arus dari sumber menuju Node 1:

\\[ I_1=\frac{12-V_1}{2} \\]

Arus dari Node 1 menuju ground:

\\[ I_2=\frac{V_1}{4} \\]

Arus dari Node 1 menuju Node 2:

\\[ I_3=\frac{V_1-V_2}{6} \\]

Arus dari Node 2 menuju ground:

\\[ I_4=\frac{V_2}{3} \\]

Implementasi:

```
V1 = hasil[0]V2 = hasil[1]I1 = (12 - V1) / 2I2 = V1 / 4I3 = (V1 - V2) / 6I4 = V2 / 3print("=== HASIL ANALISIS ARUS ===")print("Arus sumber:", I1, "A")print("Arus resistor 4 Ohm:", I2, "A")print("Arus resistor 6 Ohm:", I3, "A")print("Arus resistor 3 Ohm:", I4, "A")
```

Hasil pendekatan:

| Parameter         | Nilai    |
| ----------------- | -------- |
| Arus dari sumber  | 2,1290 A |
| Arus resistor 4 Ω | 1,9355 A |
| Arus resistor 6 Ω | 0,1935 A |
| Arus resistor 3 Ω | 2,1935 A |

Perhatikan bahwa pada Node 1:

\\[ I_1=I_2+I_3 \\]

Dan pada Node 2:

\\[ I_3+2=I_4 \\]

Dengan demikian, hasil numerik juga memenuhi Hukum Arus Kirchhoff.

**Catatan:** Model ini mengasumsikan rangkaian DC resistif dalam kondisi tunak, dengan sumber arus 2 A menginjeksikan arus ke Node 2.

# **BAGIAN VII — EKSPERIMEN KOMPUTASI NUMERIK**

## **11. Membandingkan Ketiga Metode pada Sistem yang Sama**

Untuk memahami karakteristik metode langsung dan iteratif, kita dapat menggunakan sistem persamaan yang sama.

\\[ 10x+y+z=12 \\]

\\[ 2x+10y+z=13 \\]

\\[ 2x+2y+10z=14 \\]

Sistem ini memiliki matriks koefisien yang dominan diagonal secara ketat sehingga sesuai untuk demonstrasi Gauss-Seidel.

### **11.1 Menghitung Solusi dengan Metode Langsung**

```
A = [    [10, 1, 1],    [2, 10, 1],    [2, 2, 10]]b = [12, 13, 14]hasil_gauss = gauss_elimination(A, b)hasil_jordan = gauss_jordan(A, b)print("Eliminasi Gauss:", hasil_gauss)print("Gauss-Jordan:", hasil_jordan)
```

Kedua metode akan memberikan solusi yang sama, dengan kemungkinan selisih sangat kecil akibat representasi floating-point.

### **11.2 Menghitung Solusi dengan Gauss-Seidel**

Gunakan implementasi Gauss-Seidel sebelumnya dengan nilai awal:

\\[ x_0=y_0=z_0=0 \\]

Toleransi:

\\[ \varepsilon=0.0001 \\]

Amati bagaimana nilai variabel berubah pada setiap iterasi hingga memenuhi kriteria penghentian.

### **11.3 Mengamati Residual**

Untuk membandingkan kualitas hasil, gunakan:

\\[ r=b-Ax \\]

Hitung residual setiap metode dan bandingkan nilai:

\\[ \\|r\\|\_\infty \\]

Nilai residual yang kecil menunjukkan bahwa solusi semakin memenuhi sistem persamaan awal.

**Hal yang perlu diamati mahasiswa:**

- Apakah ketiga metode memberikan hasil yang mendekati sama?
- Berapa iterasi yang dibutuhkan Gauss-Seidel?
- Bagaimana perubahan nilai solusi pada setiap iterasi?
- Apakah residual sudah cukup kecil?
- Apa perbedaan proses metode langsung dan iteratif?

## **12. Penggunaan NumPy untuk Verifikasi**

Dalam pengembangan aplikasi numerik, Python memiliki library NumPy yang menyediakan berbagai operasi matriks dan aljabar linear.

Kita dapat menggunakan `numpy.linalg.solve()` untuk memverifikasi hasil perhitungan manual.

```
import numpy as npA = np.array([    [11, -2],    [-1, 3]], dtype=float)b = np.array([72, 12], dtype=float)hasil = np.linalg.solve(A, b)print("Hasil menggunakan NumPy:")print("V1 =", hasil[0])print("V2 =", hasil[1])
```

Output:

```
Hasil menggunakan NumPy:
V1 = 7.741935483870968
V2 = 6.580645161290323
```

NumPy dapat digunakan untuk memverifikasi hasil implementasi algoritma yang dibuat sendiri.

Namun, pada tahap pembelajaran ini, mahasiswa tetap harus memahami dan mampu mengimplementasikan metode Eliminasi Gauss, Gauss-Jordan, serta Gauss-Seidel secara manual menggunakan Python.

## **13. Kesalahan Umum dalam Penyelesaian Sistem Persamaan Linear**

| Kesalahan                    | Penyebab                              | Solusi                               |
| ---------------------------- | ------------------------------------- | ------------------------------------ |
| Hasil perhitungan salah      | Koefisien matriks tidak sesuai        | Periksa kembali persamaan            |
| Pembagian dengan nol         | Pivot bernilai nol                    | Gunakan pivoting                     |
| Gauss-Seidel tidak konvergen | Karakteristik matriks tidak mendukung | Periksa kondisi konvergensi          |
| Iterasi terlalu banyak       | Toleransi terlalu ketat               | Sesuaikan toleransi                  |
| Residual besar               | Solusi belum memenuhi sistem          | Periksa algoritma dan hasil          |
| Matriks singular             | Persamaan tidak memiliki solusi unik  | Analisis rank dan konsistensi sistem |
| Hasil sedikit berbeda        | Pembulatan floating-point             | Gunakan presisi yang memadai         |

### **13.1 Kasus Matriks Singular**

Matriks singular merupakan matriks yang determinannya bernilai nol.

Contoh:

\\[ A= \begin{bmatrix} 1&2\\\ 2&4 \end{bmatrix} \\]

Baris kedua merupakan dua kali baris pertama. Kedua persamaan tidak independen.

Untuk sistem:

\\[ x+2y=5 \\]

\\[ 2x+4y=10 \\]

terdapat tak terhingga banyak solusi.

Sementara itu, jika ruas kanan persamaan kedua diubah menjadi 12:

\\[ x+2y=5 \\]

\\[ 2x+4y=12 \\]

maka sistem tidak memiliki solusi karena kedua persamaan saling bertentangan.

Ini menunjukkan bahwa tidak semua sistem persamaan linear memiliki solusi tunggal.

## **14. Ringkasan Materi**

Pada pertemuan ini, mahasiswa telah mempelajari:

1. Sistem persamaan linear merupakan kumpulan persamaan dengan variabel berpangkat satu.
2. Sistem persamaan linear dapat direpresentasikan dalam bentuk matriks \\(AX=B\\).
3. Matriks augmented digunakan untuk mempermudah operasi baris elementer.
4. Eliminasi Gauss mengubah matriks menjadi bentuk segitiga atas dan menggunakan substitusi mundur.
5. Gauss-Jordan mengubah matriks hingga mencapai bentuk RREF.
6. Gauss-Seidel menyelesaikan sistem persamaan melalui proses iterasi.
7. Konvergensi merupakan aspek penting dalam metode iteratif.
8. Residual digunakan untuk mengevaluasi seberapa baik solusi memenuhi persamaan awal.
9. Pivoting membantu meningkatkan kestabilan proses eliminasi.
10. Metode sistem persamaan linear dapat digunakan untuk analisis rangkaian listrik berdasarkan Hukum Kirchhoff.

**Inti pembelajaran:** Metode numerik memungkinkan penyelesaian sistem persamaan linear secara sistematis. Pemilihan metode harus mempertimbangkan ukuran sistem, karakteristik matriks, efisiensi perhitungan, serta ketelitian hasil.

## **15. Referensi Pembelajaran**

1. Chapra, S. C., & Canale, R. P. (2021). *Numerical Methods for Engineers*, 8th Edition. McGraw-Hill.
2. Burden, R. L., Faires, J. D., & Burden, A. M. (2016). *Numerical Analysis*, 10th Edition. Cengage Learning.
3. Sauer, T. (2018). *Numerical Analysis*, 3rd Edition. Pearson.
4. Python Software Foundation. [Python Data Structures](https://docs.python.org/3/tutorial/datastructures.html).
5. NumPy Documentation. [NumPy Linear Algebra](https://numpy.org/doc/stable/reference/routines.linalg.html).
