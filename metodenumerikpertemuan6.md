# **MODUL 6**

## **Metode Numerik untuk Penyelesaian Sistem Persamaan Linear**

Pertemuan 6 · Program Studi Teknik Elektro

## **1. Deskripsi Pembelajaran**

Sistem persamaan linear merupakan sekumpulan persamaan yang melibatkan beberapa variabel dengan hubungan linear. Permasalahan ini banyak ditemukan dalam bidang Teknik Elektro, terutama pada analisis rangkaian listrik, analisis jaringan, sistem tenaga, pemodelan sistem kendali, dan berbagai persoalan rekayasa lainnya.

Dalam analisis rangkaian listrik, misalnya, hukum Kirchhoff dapat digunakan untuk membentuk sejumlah persamaan yang menggambarkan hubungan antara tegangan dan arus pada suatu rangkaian. Ketika jumlah persamaan dan variabel semakin besar, penyelesaian secara manual menjadi kurang praktis.

Metode numerik menyediakan beberapa pendekatan untuk menyelesaikan sistem persamaan tersebut. Secara umum, metode penyelesaian sistem persamaan linear dibagi menjadi dua kelompok, yaitu metode langsung (*direct methods*) dan metode iteratif (*iterative methods*).

Metode langsung memperoleh solusi melalui serangkaian operasi aljabar hingga sistem persamaan mencapai bentuk yang dapat diselesaikan. Sementara itu, metode iteratif menghasilkan solusi secara bertahap melalui proses pengulangan berdasarkan nilai pendekatan sebelumnya.

## **2. Capaian Pembelajaran**

Setelah mengikuti pembelajaran ini, mahasiswa diharapkan mampu:

1. Menjelaskan konsep sistem persamaan linear dan representasi matriks.
2. Memahami karakteristik matriks dalam penyelesaian sistem persamaan linear.
3. Menjelaskan prinsip metode Eliminasi Gauss dan Gauss-Jordan.
4. Menjelaskan prinsip metode iteratif Jacobi dan Gauss-Seidel.
5. Melakukan perhitungan manual menggunakan masing-masing metode.
6. Mengimplementasikan metode penyelesaian sistem persamaan linear menggunakan Python.
7. Menganalisis konvergensi, stabilitas, dan ketelitian solusi.
8. Menerapkan metode numerik pada permasalahan analisis rangkaian listrik.

## **3. Konsep Dasar Sistem Persamaan Linear**

### **3.1 Pengertian sistem persamaan linear**

Sistem persamaan linear merupakan kumpulan persamaan yang memiliki beberapa variabel dengan pangkat tertinggi satu.

Contoh:

\\[ 2x+3y=8 \\]

\\[ x-y=1 \\]

Sistem tersebut memiliki dua persamaan dan dua variabel, yaitu \\(x\\) dan \\(y\\).

Tujuan penyelesaian sistem persamaan linear adalah menentukan nilai setiap variabel yang memenuhi seluruh persamaan secara bersamaan.

### **3.2 Representasi matriks**

Sistem persamaan linear dapat direpresentasikan dalam bentuk matriks:

\\[ AX=B \\]

Keterangan:

- \\(A\\) = matriks koefisien.
- \\(X\\) = vektor variabel.
- \\(B\\) = vektor konstanta.

Sebagai contoh:

\\[ \begin{aligned} 2x+3y&=8\\\ x-y&=1 \end{aligned} \\]

Dapat dituliskan menjadi:

\\[ \begin{bmatrix} 2&3\\\ 1&-1 \end{bmatrix} \begin{bmatrix} x\\\y \end{bmatrix} = \begin{bmatrix} 8\\\1 \end{bmatrix} \\]

Bentuk matriks ini menjadi dasar penerapan berbagai metode numerik.

### **3.3 Jenis penyelesaian sistem persamaan linear**

Berdasarkan karakteristiknya, sistem persamaan linear dapat memiliki:

1. **Solusi tunggal:** terdapat tepat satu kombinasi nilai variabel yang memenuhi seluruh persamaan.
2. **Tidak memiliki solusi:** persamaan saling bertentangan sehingga tidak ada kombinasi variabel yang memenuhi semuanya.
3. **Memiliki tak hingga banyak solusi:** terdapat beberapa variabel yang saling bergantung sehingga solusi tidak tunggal.

Untuk sistem persegi, keberadaan solusi tunggal berkaitan dengan determinan matriks koefisien yang tidak sama dengan nol.

\\[ \det(A)\neq0 \\]

Jika determinan tidak nol, matriks bersifat nonsingular dan sistem memiliki solusi tunggal.

## **4. Metode Eliminasi Gauss**

### **4.1 Prinsip dasar**

Metode Eliminasi Gauss merupakan metode langsung yang digunakan untuk mengubah sistem persamaan linear menjadi bentuk segitiga atas (*upper triangular matrix*).

Proses dilakukan melalui operasi baris elementer, kemudian dilanjutkan dengan substitusi mundur (*back substitution*) untuk memperoleh nilai setiap variabel.

Tiga operasi baris elementer yang digunakan adalah:

1. Menukar dua baris.
2. Mengalikan suatu baris dengan konstanta bukan nol.
3. Menambahkan kelipatan suatu baris ke baris lainnya.

### **4.2 Tahapan Eliminasi Gauss**

1. Bentuk matriks augmented dari sistem persamaan.
2. Tentukan elemen pivot.
3. Lakukan eliminasi terhadap elemen di bawah pivot.
4. Ulangi proses hingga matriks menjadi segitiga atas.
5. Gunakan substitusi mundur untuk menentukan nilai variabel.

### **4.3 Contoh perhitungan manual**

Diketahui sistem persamaan:

\\[ \begin{aligned} 2x+y+z&=7\\\ 4x-6y&=-2\\\ -2x+7y+2z&=9 \end{aligned} \\]

Matriks augmented:

\\[ \left[ \begin{array}{ccc|c} 2&1&1&7\\\ 4&-6&0&-2\\\ -2&7&2&9 \end{array} \right] \\]

**Langkah 1: Eliminasi kolom pertama**

Operasi:

\\[ R_2\rightarrow R_2-2R_1 \\]

\\[ R_3\rightarrow R_3+R_1 \\]

Hasil:

\\[ \left[ \begin{array}{ccc|c} 2&1&1&7\\\ 0&-8&-2&-16\\\ 0&8&3&16 \end{array} \right] \\]

**Langkah 2: Eliminasi kolom kedua**

Operasi:

\\[ R_3\rightarrow R_3+R_2 \\]

Hasil:

\\[ \left[ \begin{array}{ccc|c} 2&1&1&7\\\ 0&-8&-2&-16\\\ 0&0&1&0 \end{array} \right] \\]

Matriks sudah berbentuk segitiga atas.

**Langkah 3: Substitusi mundur**

Dari baris ketiga:

\\[ z=0 \\]

Dari baris kedua:

\\[ -8y-2z=-16 \\]

\\[ -8y=-16 \\]

\\[ y=2 \\]

Dari baris pertama:

\\[ 2x+y+z=7 \\]

\\[ 2x+2=7 \\]

\\[ x=2.5 \\]

Dengan demikian, solusi sistem persamaan adalah:

\\[ \boxed{x=2.5,\quad y=2,\quad z=0} \\]

### **4.4 Implementasi Python**

```
import numpy as npdef gaussian_elimination(A, b):    A = np.array(A, dtype=float)    b = np.array(b, dtype=float)    n = len(b)    # Membentuk matriks augmented    M = np.column_stack((A, b))    # Eliminasi maju dengan partial pivoting    for i in range(n):        pivot_row = i + np.argmax(            np.abs(M[i:, i])        )        if abs(M[pivot_row, i]) < 1e-12:            raise ValueError("Matriks singular.")        M[[i, pivot_row]] = M[[pivot_row, i]]        for j in range(i + 1, n):            factor = M[j, i] / M[i, i]            M[j, i:] -= factor * M[i, i:]    # Substitusi mundur    x = np.zeros(n)    for i in range(n - 1, -1, -1):        x[i] = (            M[i, -1]            - np.dot(M[i, i+1:n], x[i+1:n])        ) / M[i, i]    return xA = [    [2, 1, 1],    [4, -6, 0],    [-2, 7, 2]]b = [7, -2, 9]hasil = gaussian_elimination(A, b)print("Solusi sistem:")print(hasil)
```

Hasil:

```
[2.5 2.  0. ]
```

Metode Eliminasi Gauss cocok digunakan untuk sistem persamaan linear dengan solusi tunggal. Dalam implementasi komputasi, teknik *partial pivoting* dapat meningkatkan keandalan proses eliminasi, terutama ketika elemen pivot sangat kecil.

## **5. Metode Gauss-Jordan**

### **5.1 Prinsip dasar**

Metode Gauss-Jordan merupakan pengembangan dari Eliminasi Gauss.

Jika Eliminasi Gauss mengubah matriks menjadi bentuk segitiga atas, Gauss-Jordan melanjutkan eliminasi hingga matriks koefisien menjadi matriks identitas.

Bentuk akhir yang diharapkan adalah:

\\[ \left[ \begin{array}{ccc|c} 1&0&0&x\\\ 0&1&0&y\\\ 0&0&1&z \end{array} \right] \\]

Dengan demikian, nilai variabel dapat langsung diperoleh tanpa proses substitusi mundur.

### **5.2 Tahapan Gauss-Jordan**

1. Bentuk matriks augmented.
2. Tentukan elemen pivot.
3. Tukar baris apabila diperlukan.
4. Normalisasi baris pivot sehingga elemen pivot bernilai satu.
5. Eliminasi seluruh elemen lain dalam kolom pivot.
6. Ulangi hingga matriks koefisien menjadi matriks identitas.

### **5.3 Contoh perhitungan manual**

Gunakan sistem persamaan yang sama:

\\[ \begin{aligned} 2x+y+z&=7\\\ 4x-6y&=-2\\\ -2x+7y+2z&=9 \end{aligned} \\]

Matriks augmented:

\\[ \left[ \begin{array}{ccc|c} 2&1&1&7\\\ 4&-6&0&-2\\\ -2&7&2&9 \end{array} \right] \\]

Setelah dilakukan eliminasi dan normalisasi baris secara bertahap, diperoleh:

\\[ \left[ \begin{array}{ccc|c} 1&0&0&2.5\\\ 0&1&0&2\\\ 0&0&1&0 \end{array} \right] \\]

Sehingga:

\\[ \boxed{x=2.5,\quad y=2,\quad z=0} \\]

### **5.4 Implementasi Python**

```
import numpy as npdef gauss_jordan(A, b):    A = np.array(A, dtype=float)    b = np.array(b, dtype=float)    n = len(b)    M = np.column_stack((A, b))    for i in range(n):        # Partial pivoting        pivot_row = i + np.argmax(            np.abs(M[i:, i])        )        if abs(M[pivot_row, i]) < 1e-12:            raise ValueError("Matriks singular.")        M[[i, pivot_row]] = M[[pivot_row, i]]        # Normalisasi baris pivot        M[i] = M[i] / M[i, i]        # Eliminasi semua baris lain        for j in range(n):            if j != i:                factor = M[j, i]                M[j] = M[j] - factor * M[i]    return M[:, -1]A = [    [2, 1, 1],    [4, -6, 0],    [-2, 7, 2]]b = [7, -2, 9]hasil = gauss_jordan(A, b)print("Solusi sistem:")print(hasil)
```

Metode Gauss-Jordan memiliki keunggulan karena menghasilkan solusi secara langsung setelah proses reduksi matriks. Namun, proses eliminasi yang dilakukan lebih banyak dibandingkan Eliminasi Gauss karena seluruh elemen selain pivot harus dieliminasi.

## **6. Metode Iteratif Jacobi**

### **6.1 Prinsip dasar**

Metode Jacobi merupakan metode iteratif yang digunakan untuk menyelesaikan sistem persamaan linear melalui pendekatan berulang.

Setiap variabel dihitung menggunakan nilai variabel dari iterasi sebelumnya.

Untuk sistem tiga variabel:

\\[ a\_{11}x+a\_{12}y+a\_{13}z=b_1 \\]

\\[ a\_{21}x+a\_{22}y+a\_{23}z=b_2 \\]

\\[ a\_{31}x+a\_{32}y+a\_{33}z=b_3 \\]

Persamaan dapat disusun ulang menjadi:

\\[ x^{(k+1)}= \frac{b_1-a\_{12}y^{(k)}-a\_{13}z^{(k)}} {a\_{11}} \\]

\\[ y^{(k+1)}= \frac{b_2-a\_{21}x^{(k)}-a\_{23}z^{(k)}} {a\_{22}} \\]

\\[ z^{(k+1)}= \frac{b_3-a\_{31}x^{(k)}-a\_{32}y^{(k)}} {a\_{33}} \\]

Keterangan:

- \\(k\\) = nomor iterasi.
- \\(k+1\\) = iterasi berikutnya.
- \\(x^{(k)}\\), \\(y^{(k)}\\), dan \\(z^{(k)}\\) = nilai pendekatan sebelumnya.

Karakteristik utama Jacobi adalah seluruh variabel pada iterasi baru dihitung menggunakan nilai dari iterasi sebelumnya.

### **6.2 Algoritma Jacobi**

1. Tentukan matriks koefisien dan vektor konstanta.
2. Susun persamaan untuk setiap variabel.
3. Tentukan nilai awal semua variabel.
4. Hitung seluruh variabel menggunakan nilai iterasi sebelumnya.
5. Hitung perubahan nilai atau residual.
6. Ulangi sampai toleransi terpenuhi.

### **6.3 Contoh perhitungan manual**

Diketahui sistem:

\\[ \begin{aligned} 10x-y+2z&=6\\\ -x+11y-z&=22\\\ 2x-y+10z&=-10 \end{aligned} \\]

Susun ulang:

\\[ x=\frac{6+y-2z}{10} \\]

\\[ y=\frac{22+x+z}{11} \\]

\\[ z=\frac{-10-2x+y}{10} \\]

Gunakan tebakan awal:

\\[ x^{(0)}=0,\quad y^{(0)}=0,\quad z^{(0)}=0 \\]

**Iterasi pertama**

\\[ x^{(1)}=\frac{6+0-2(0)}{10}=0.6 \\]

\\[ y^{(1)}=\frac{22+0+0}{11}=2 \\]

\\[ z^{(1)}=\frac{-10-2(0)+0}{10}=-1 \\]

Hasil iterasi pertama:

\\[ (x^{(1)},y^{(1)},z^{(1)}) =(0.6,2,-1) \\]

**Iterasi kedua**

Gunakan seluruh nilai dari iterasi pertama:

\\[ x^{(2)}=\frac{6+2-2(-1)}{10}=1 \\]

\\[ y^{(2)}=\frac{22+0.6-1}{11} =1.963636 \\]

\\[ z^{(2)}=\frac{-10-2(0.6)+2}{10} =-0.92 \\]

Proses dilanjutkan hingga nilai variabel semakin mendekati solusi.

### **6.4 Implementasi Python**

```
import numpy as np    n = len(b)    x = np.zeros(n)    if np.any(np.abs(np.diag(A)) < 1e-12):        raise ValueError("Elemen diagonal tidak boleh nol.")    print("Iterasi | Nilai variabel")    for k in range(1, max_iter + 1):        x_new = np.zeros(n)        for i in range(n):            sigma = np.dot(A[i], x) - A[i, i] * x[i]            x_new[i] = (                b[i] - sigma            ) / A[i, i]        error = np.linalg.norm(x_new - x, ord=np.inf)        print(k, x_new)        if error < tol:            return x_new        x = x_new    return xA = [    [10, -1, 2],    [-1, 11, -1],    [2, -1, 10]]b = [6, 22, -10]hasil = jacobi(A, b)print("\nSolusi pendekatan:")print(hasil)
```

Metode Jacobi memiliki keunggulan berupa proses perhitungan yang relatif sederhana dan setiap variabel dapat dihitung secara independen pada suatu iterasi.

Namun, metode ini dapat memerlukan banyak iterasi dan tidak selalu konvergen untuk setiap sistem persamaan linear.

## **7. Metode Gauss-Seidel**

### **7.1 Prinsip dasar**

Metode Gauss-Seidel merupakan metode iteratif yang memiliki prinsip serupa dengan Jacobi, tetapi menggunakan nilai terbaru yang sudah diperoleh dalam iterasi yang sedang berlangsung.

Perbedaan utama kedua metode terletak pada penggunaan nilai variabel.

Pada Jacobi, seluruh variabel baru dihitung menggunakan nilai iterasi sebelumnya.

Pada Gauss-Seidel, nilai variabel yang sudah diperbarui langsung digunakan untuk menghitung variabel berikutnya.

Rumus umum untuk tiga variabel:

\\[ x^{(k+1)}= \frac{b_1-a\_{12}y^{(k)}-a\_{13}z^{(k)}} {a\_{11}} \\]

\\[ y^{(k+1)}= \frac{b_2-a\_{21}x^{(k+1)}-a\_{23}z^{(k)}} {a\_{22}} \\]

\\[ z^{(k+1)}= \frac{b_3-a\_{31}x^{(k+1)}-a\_{32}y^{(k+1)}} {a\_{33}} \\]

### **7.2 Algoritma Gauss-Seidel**

1. Tentukan sistem persamaan linear.
2. Tentukan nilai awal variabel.
3. Hitung variabel pertama.
4. Gunakan hasil terbaru untuk menghitung variabel berikutnya.
5. Hitung perubahan nilai atau residual.
6. Ulangi sampai toleransi terpenuhi.

### **7.3 Contoh perhitungan manual**

Gunakan sistem yang sama dengan metode Jacobi:

\\[ \begin{aligned} 10x-y+2z&=6\\\ -x+11y-z&=22\\\ 2x-y+10z&=-10 \end{aligned} \\]

Dengan bentuk persamaan:

\\[ x=\frac{6+y-2z}{10} \\]

\\[ y=\frac{22+x+z}{11} \\]

\\[ z=\frac{-10-2x+y}{10} \\]

Nilai awal:

\\[ x^{(0)}=0,\quad y^{(0)}=0,\quad z^{(0)}=0 \\]

**Iterasi pertama**

Hitung \\(x\\):

\\[ x^{(1)}=\frac{6+0-2(0)}{10}=0.6 \\]

Hitung \\(y\\) menggunakan nilai \\(x\\) terbaru:

\\[ y^{(1)}=\frac{22+0.6+0}{11} =2.054545 \\]

Hitung \\(z\\) menggunakan nilai \\(x\\) dan \\(y\\) terbaru:

\\[ z^{(1)}= \frac{-10-2(0.6)+2.054545}{10} \\]

\\[ z^{(1)}=-0.914545 \\]

Hasil iterasi pertama:

\\[ (x^{(1)},y^{(1)},z^{(1)}) = (0.6,2.054545,-0.914545) \\]

**Iterasi kedua**

\\[ x^{(2)}= \frac{6+2.054545-2(-0.914545)}{10} \\]

\\[ x^{(2)}=0.988364 \\]

\\[ y^{(2)}= \frac{22+0.988364-0.914545}{11} \\]

\\[ y^{(2)}\approx2.006711 \\]

\\[ z^{(2)}= \frac{-10-2(0.988364)+2.006711}{10} \\]

\\[ z^{(2)}\approx-0.997002 \\]

Proses dilanjutkan sampai solusi mendekati nilai:

\\[ \boxed{x=1,\quad y=2,\quad z=-1} \\]

### **7.4 Implementasi Python**

```
import numpy as npdef gauss_seidel(A, b, tol=1e-6, max_iter=100):    A = np.array(A, dtype=float)    b = np.array(b, dtype=float)    n = len(b)    x = np.zeros(n)    if np.any(np.abs(np.diag(A)) < 1e-12):        raise ValueError("Elemen diagonal tidak boleh nol.")    print("Iterasi | Nilai variabel")    for k in range(1, max_iter + 1):        x_old = x.copy()        for i in range(n):            sigma = (                np.dot(A[i], x) -                A[i, i] * x[i]            )            x[i] = (                b[i] - sigma            ) / A[i, i]        error = np.linalg.norm(x - x_old, ord=np.inf)        print(k, x)        if error < tol:            return x    return xA = [    [10, -1, 2],    [-1, 11, -1],    [2, -1, 10]]b = [6, 22, -10]hasil = gauss_seidel(A, b)print("\nSolusi pendekatan:")print(hasil)
```

Metode Gauss-Seidel sering mencapai konvergensi lebih cepat daripada Jacobi pada sistem tertentu karena langsung menggunakan nilai terbaru. Namun, hal tersebut tidak berlaku untuk seluruh sistem persamaan linear.

## **8. Perbandingan Metode Langsung dan Iteratif**

Metode langsung dan iteratif memiliki karakteristik yang berbeda. Pemilihannya bergantung pada ukuran sistem, struktur matriks, kebutuhan ketelitian, serta sumber daya komputasi.

| Aspek             | Gauss                                | Gauss-Jordan                 | Jacobi                                            | Gauss-Seidel                                      |
| ----------------- | ------------------------------------ | ---------------------------- | ------------------------------------------------- | ------------------------------------------------- |
| Kategori          | Langsung                             | Langsung                     | Iteratif                                          | Iteratif                                          |
| Prinsip           | Eliminasi maju dan substitusi mundur | Reduksi ke matriks identitas | Iterasi serentak                                  | Iterasi berurutan                                 |
| Nilai awal        | Tidak perlu                          | Tidak perlu                  | Perlu                                             | Perlu                                             |
| Konvergensi       | Tidak berbasis iterasi               | Tidak berbasis iterasi       | Bergantung matriks                                | Bergantung matriks                                |
| Kebutuhan turunan | Tidak                                | Tidak                        | Tidak                                             | Tidak                                             |
| Penggunaan        | Sistem ukuran kecil-menengah         | Sistem dan reduksi matriks   | Sistem tertentu, termasuk sistem besar dan jarang | Sistem tertentu, termasuk sistem besar dan jarang |

### **8.1 Kondisi konvergensi metode iteratif**

Salah satu kondisi yang cukup untuk menjamin konvergensi metode Jacobi dan Gauss-Seidel adalah matriks koefisien yang dominan secara diagonal ketat (*strictly diagonally dominant*).

Suatu matriks dikatakan dominan secara diagonal ketat apabila:

\\[ |a\_{ii}|> \sum\_{j\neq i}|a\_{ij}| \\]

untuk setiap baris \\(i\\).

Contoh matriks:

\\[ A= \begin{bmatrix} 10&-1&2\\\ -1&11&-1\\\ 2&-1&10 \end{bmatrix} \\]

Baris pertama:

\\[ 10>|-1|+|2|=3 \\]

Baris kedua:

\\[ 11>|-1|+|-1|=2 \\]

Baris ketiga:

\\[ 10>|2|+|-1|=3 \\]

Dengan demikian, matriks tersebut dominan secara diagonal ketat sehingga memenuhi salah satu syarat cukup konvergensi bagi kedua metode iteratif tersebut.

Perlu diingat, dominasi diagonal ketat merupakan syarat cukup, bukan syarat wajib. Ada matriks yang tidak memenuhi kondisi tersebut tetapi metode iteratifnya tetap konvergen.

## **9. Evaluasi Hasil Menggunakan Residual**

Dalam penyelesaian sistem persamaan linear, nilai variabel yang diperoleh perlu diuji kembali untuk mengetahui seberapa baik solusi tersebut memenuhi persamaan awal.

Residual didefinisikan sebagai:

\\[ r=b-Ax \\]

Keterangan:

- \\(A\\) = matriks koefisien.
- \\(b\\) = vektor konstanta.
- \\(x\\) = vektor solusi pendekatan.
- \\(r\\) = vektor residual.

Salah satu ukuran yang dapat digunakan adalah norma infinity:

\\[ \\|r\\|\_{\infty} = \max_i |r_i| \\]

Semakin kecil nilai residual, semakin baik solusi pendekatan dalam memenuhi sistem persamaan.

Contoh implementasi Python:

```
import numpy as npA = np.array([    [10, -1, 2],    [-1, 11, -1],    [2, -1, 10]], dtype=float)b = np.array([6, 22, -10], dtype=float)# Solusi dari metode Gauss-Seidelx = np.array([1, 2, -1], dtype=float)# Menghitung residualr = b - A @ xprint("Solusi:", x)print("Residual:", r)print("Norma residual:", np.linalg.norm(r, ord=np.inf))
```

Hasil:

```
Solusi: [ 1.  2. -1.]
Residual: [0. 0. 0.]
Norma residual: 0.0
```

Residual nol menunjukkan bahwa solusi tersebut memenuhi sistem persamaan secara tepat dalam perhitungan contoh ini.

Untuk hasil komputasi floating-point, residual biasanya tidak selalu tepat nol meskipun solusinya sangat akurat.

## **10. Studi Kasus Teknik Elektro: Analisis Rangkaian DC Menggunakan Metode Tegangan Simpul**

### **10.1 Deskripsi kasus**

Sebuah rangkaian listrik DC memiliki dua node utama, yaitu Node 1 dan Node 2. Rangkaian terdiri dari sumber tegangan, resistor, dan sumber arus.

Diketahui:

- Sumber tegangan 12 V terhubung ke Node 1 melalui resistor 2 Ω.
- Node 1 terhubung ke ground melalui resistor 4 Ω.
- Node 1 dan Node 2 dihubungkan melalui resistor 6 Ω.
- Node 2 terhubung ke ground melalui resistor 3 Ω.
- Terdapat sumber arus 2 A yang menginjeksikan arus ke Node 2.

Tujuan analisis adalah menentukan tegangan pada Node 1 dan Node 2 menggunakan metode numerik.

### **10.2 Membentuk persamaan berdasarkan KCL**

Berdasarkan Hukum Kirchhoff Arus (*Kirchhoff's Current Law*), jumlah arus yang masuk dan keluar pada setiap node harus seimbang.

Untuk Node 1:

\\[ \frac{V_1-12}{2} + \frac{V_1}{4} + \frac{V_1-V_2}{6} =0 \\]

Kalikan seluruh persamaan dengan 12:

\\[ 6(V_1-12)+3V_1+2(V_1-V_2)=0 \\]

Sederhanakan:

\\[ 11V_1-2V_2=72 \\]

Untuk Node 2:

\\[ \frac{V_2-V_1}{6} + \frac{V_2}{3} -2=0 \\]

Kalikan seluruh persamaan dengan 6:

\\[ V_2-V_1+2V_2-12=0 \\]

Sederhanakan:

\\[ -V_1+3V_2=12 \\]

### **10.3 Representasi matriks**

Kedua persamaan tersebut dapat dituliskan menjadi:

\\[ \begin{bmatrix} 11&-2\\\ -1&3 \end{bmatrix} \begin{bmatrix} V_1\\\V_2 \end{bmatrix} = \begin{bmatrix} 72\\\12 \end{bmatrix} \\]

### **10.4 Penyelesaian menggunakan Eliminasi Gauss**

Matriks augmented:

\\[ \left[ \begin{array}{cc|c} 11&-2&72\\\ -1&3&12 \end{array} \right] \\]

Dengan eliminasi baris diperoleh:

\\[ \left[ \begin{array}{cc|c} 11&-2&72\\\ 0&\frac{31}{11}&\frac{204}{11} \end{array} \right] \\]

Dari baris kedua:

\\[ \frac{31}{11}V_2=\frac{204}{11} \\]

\\[ V_2=\frac{204}{31} \\]

\\[ V_2\approx6.580645\text{ V} \\]

Substitusi ke persamaan pertama:

\\[ 11V_1-2(6.580645)=72 \\]

\\[ V_1\approx7.741935\text{ V} \\]

Dengan demikian:

\\[ \boxed{V_1\approx7.741935\text{ V}} \\]

\\[ \boxed{V_2\approx6.580645\text{ V}} \\]

### **10.5 Implementasi Python**

```
import numpy as np# Matriks koefisienA = np.array([    [11, -2],    [-1, 3]], dtype=float)# Vektor konstantab = np.array([72, 12], dtype=float)# Menggunakan metode Eliminasi Gausssolusi = gaussian_elimination(A, b)V1, V2 = solusiprint("Tegangan Node 1:", V1, "Volt")print("Tegangan Node 2:", V2, "Volt")# Verifikasi menggunakan residualresidual = b - A @ solusiprint("Residual:", residual)print(    "Norma residual:",    np.linalg.norm(residual, ord=np.inf))
```

### **10.6 Interpretasi hasil**

Hasil perhitungan menunjukkan bahwa tegangan Node 1 lebih tinggi dibandingkan Node 2.

Perbedaan tegangan ini menyebabkan arus mengalir melalui resistor yang menghubungkan kedua node.

Sebagai pemeriksaan tambahan, arus pada masing-masing cabang dapat dihitung menggunakan Hukum Ohm:

Arus dari sumber menuju Node 1:

\\[ I_1=\frac{12-V_1}{2} \\]

\\[ I_1\approx2.129032\text{ A} \\]

Arus dari Node 1 menuju ground:

\\[ I_2=\frac{V_1}{4} \\]

\\[ I_2\approx1.935484\text{ A} \\]

Arus dari Node 1 menuju Node 2:

\\[ I_3=\frac{V_1-V_2}{6} \\]

\\[ I_3\approx0.193548\text{ A} \\]

Arus dari Node 2 menuju ground:

\\[ I_4=\frac{V_2}{3} \\]

\\[ I_4\approx2.193548\text{ A} \\]

Pemeriksaan KCL:

Pada Node 1:

\\[ I_1=I_2+I_3 \\]

Pada Node 2:

\\[ I_3+2=I_4 \\]

Kedua persamaan terpenuhi, sehingga hasil analisis konsisten dengan Hukum Kirchhoff Arus.

## **11. Kesalahan Umum dalam Penyelesaian Sistem Persamaan Linear**

Beberapa kesalahan yang sering terjadi dalam penerapan metode numerik antara lain:

1. Salah membentuk matriks koefisien dan vektor konstanta.
2. Melakukan operasi baris elementer secara tidak tepat.
3. Tidak memperhatikan elemen pivot yang bernilai nol atau sangat kecil.
4. Mengabaikan kebutuhan pivoting dalam metode langsung.
5. Salah menggunakan nilai iterasi sebelumnya pada metode Jacobi.
6. Tidak menggunakan nilai terbaru pada metode Gauss-Seidel.
7. Menganggap semua metode iteratif selalu konvergen.
8. Menggunakan toleransi tanpa mengevaluasi residual.
9. Tidak memeriksa kembali hasil terhadap persamaan awal.
10. Menggunakan metode iteratif pada sistem yang tidak memenuhi kondisi konvergensi tanpa melakukan analisis lebih lanjut.

## **12. Rangkuman**

Pada pertemuan ini, mahasiswa telah mempelajari:

- Konsep dasar sistem persamaan linear.
- Representasi sistem persamaan dalam bentuk matriks.
- Karakteristik solusi sistem persamaan linear.
- Metode Eliminasi Gauss.
- Metode Gauss-Jordan.
- Metode iteratif Jacobi.
- Metode iteratif Gauss-Seidel.
- Perbedaan metode langsung dan iteratif.
- Kondisi cukup konvergensi metode iteratif.
- Evaluasi hasil menggunakan residual.
- Penerapan sistem persamaan linear pada analisis rangkaian DC menggunakan metode tegangan simpul.

## **13. Referensi Pembelajaran**

1. Chapra, S. C., & Canale, R. P. *Numerical Methods for Engineers*. McGraw-Hill.
2. Burden, R. L., Faires, J. D., & Burden, A. M. *Numerical Analysis*. Cengage Learning.
3. Sauer, T. *Numerical Analysis*. Pearson.
4. Kiusalaas, J. *Numerical Methods in Engineering with Python 3*. Cambridge University Press.
5. Alexander, C. K., & Sadiku, M. N. O. *Fundamentals of Electric Circuits*. McGraw-Hill.
