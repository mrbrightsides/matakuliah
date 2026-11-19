## **Modul 4 — Konsep Dasar Metode Numerik dan Analisis Galat**

Pertemuan 4 · Program Studi Teknik Elektro

### **1. Deskripsi pembelajaran**

Metode Numerik merupakan cabang ilmu matematika terapan yang mempelajari teknik penyelesaian masalah matematis menggunakan pendekatan numerik. Metode ini digunakan ketika solusi analitik sulit diperoleh, membutuhkan proses perhitungan yang kompleks, atau ketika data yang tersedia hanya berupa nilai diskrit hasil pengukuran.

Dalam bidang Teknik Elektro, metode numerik banyak digunakan untuk menyelesaikan persoalan analisis rangkaian listrik, pemrosesan sinyal, sistem kendali, analisis elektromagnetik, serta pemodelan karakteristik komponen elektronika.

Berbeda dengan penyelesaian analitik yang menghasilkan solusi eksak dalam bentuk matematis, metode numerik menghasilkan solusi pendekatan yang memiliki tingkat ketelitian tertentu. Oleh karena itu, pemahaman terhadap galat, ketelitian, stabilitas, dan konvergensi menjadi bagian penting dalam penerapan metode numerik.

### **2. Capaian pembelajaran**

Setelah mengikuti pembelajaran ini, mahasiswa diharapkan mampu:

1. Menjelaskan konsep dan ruang lingkup metode numerik.
2. Mengidentifikasi perbedaan penyelesaian analitik dan numerik.
3. Memahami sumber-sumber galat dalam perhitungan numerik.
4. Menghitung galat absolut, relatif, dan persentase galat.
5. Memahami konsep presisi, akurasi, konvergensi, dan stabilitas.
6. Mengimplementasikan perhitungan dasar analisis galat menggunakan Python.
7. Menganalisis ketelitian hasil perhitungan numerik pada kasus sederhana Teknik Elektro.

### **3. Konsep dasar metode numerik**

**3.1 Penyelesaian analitik dan numerik**

Penyelesaian analitik merupakan pendekatan matematis untuk memperoleh solusi eksak berdasarkan manipulasi persamaan.

Contoh:

\\[ 2x+4=10 \\]

Maka:

\\[ 2x=6 \\]

\\[ x=3 \\]

Sementara itu, penyelesaian numerik menggunakan prosedur perhitungan tertentu untuk memperoleh nilai pendekatan.

Misalnya, suatu persamaan memiliki solusi:

\\[ x=\sqrt{2} \\]

Nilai eksaknya tidak dapat dinyatakan sebagai bilangan desimal berhingga. Dalam perhitungan numerik, nilai tersebut dapat didekati menjadi:

\\[ x\approx1.4142 \\]

Perbedaan utama keduanya dapat dilihat berikut ini:

| Aspek      | Analitik                                          | Numerik                                                    |
| ---------- | ------------------------------------------------- | ---------------------------------------------------------- |
| Hasil      | Solusi eksak                                      | Solusi pendekatan                                          |
| Proses     | Manipulasi matematis                              | Algoritma perhitungan                                      |
| Ketelitian | Bergantung bentuk solusi                          | Dipengaruhi metode dan parameter                           |
| Penggunaan | Persamaan yang dapat diselesaikan secara analitik | Persoalan kompleks atau sulit diselesaikan secara analitik |

**3.2 Tahapan umum penyelesaian numerik**

Secara umum, proses penyelesaian persoalan menggunakan metode numerik meliputi:

1. Mengidentifikasi permasalahan matematis.
2. Menentukan model atau persamaan matematis.
3. Memilih metode numerik yang sesuai.
4. Menentukan parameter perhitungan.
5. Melakukan proses perhitungan atau iterasi.
6. Mengevaluasi hasil berdasarkan galat dan kriteria ketelitian.
7. Menginterpretasikan hasil sesuai konteks permasalahan.

### **4. Konsep galat dalam metode numerik**

Galat merupakan selisih antara nilai sebenarnya atau nilai acuan dengan nilai pendekatan yang diperoleh dari perhitungan numerik.

Misalkan:

- \\(x_t\\) = nilai sebenarnya atau nilai acuan.
- \\(x_a\\) = nilai pendekatan.

**4.1 Galat absolut**

Galat absolut menunjukkan besarnya perbedaan antara nilai acuan dan nilai pendekatan.

\\[ E_a=|x_t-x_a| \\]

Contoh:

Diketahui nilai sebenarnya suatu besaran tegangan adalah 12 V. Hasil perhitungan numerik menghasilkan 11,8 V.

\\[ E_a=|12-11.8| \\]

\\[ E_a=0.2\text{ V} \\]

Jadi, galat absolut sebesar 0,2 V.

**4.2 Galat relatif**

Galat relatif menunjukkan perbandingan galat absolut terhadap nilai sebenarnya.

\\[ E_r=\frac{|x_t-x_a|}{|x_t|} \\]

Menggunakan contoh sebelumnya:

\\[ E_r=\frac{0.2}{12} \\]

\\[ E_r=0.01667 \\]

**4.3 Persentase galat**

Persentase galat merupakan galat relatif yang dinyatakan dalam bentuk persen.

\\[ E_p=E_r\times100\\% \\]

\\[ E_p=0.01667\times100\\% \\]

\\[ E_p=1.667\\% \\]

Dengan demikian, hasil pengukuran atau perhitungan memiliki persentase galat sekitar 1,667%.

### **5. Sumber-sumber galat**

Dalam metode numerik, terdapat beberapa sumber galat yang perlu diperhatikan.

**5.1 Round-off error**

Galat pembulatan terjadi karena komputer memiliki keterbatasan dalam merepresentasikan bilangan dengan jumlah digit tertentu.

Contohnya, nilai:

\\[ \pi=3.14159265358979... \\]

Dapat direpresentasikan secara terbatas menjadi:

\\[ \pi\approx3.1416 \\]

Pemotongan representasi tersebut menyebabkan perbedaan antara nilai sebenarnya dan nilai yang digunakan dalam komputasi.

**5.2 Truncation error**

Galat pemotongan terjadi ketika suatu proses matematis yang seharusnya memiliki jumlah suku tak terhingga dihentikan pada jumlah suku tertentu.

Contoh pendekatan deret Taylor:

\\[ e^x=1+x+\frac{x^2}{2!}+\frac{x^3}{3!}+\cdots \\]

Jika hanya digunakan tiga suku pertama:

\\[ e^x\approx1+x+\frac{x^2}{2} \\]

Maka terdapat galat akibat suku-suku berikutnya yang diabaikan.

**5.3 Measurement error**

Galat pengukuran muncul akibat keterbatasan alat ukur, kondisi lingkungan, gangguan sinyal, maupun karakteristik sensor.

Dalam Teknik Elektro, contoh sederhana adalah pembacaan tegangan menggunakan sensor yang memiliki toleransi dan resolusi tertentu.

**5.4 Propagation of error**

Galat dapat merambat dari satu proses perhitungan ke proses berikutnya. Jika suatu hasil perhitungan digunakan sebagai input bagi perhitungan lain, galat awal dapat memengaruhi hasil akhir.

Hal ini penting dalam pemodelan rangkaian dan sistem pengukuran yang melibatkan beberapa variabel.

### **6. Konsep akurasi dan presisi**

Akurasi menggambarkan kedekatan hasil perhitungan terhadap nilai sebenarnya atau nilai acuan.

Presisi menggambarkan tingkat konsistensi hasil ketika pengukuran atau perhitungan dilakukan berulang kali.

Contoh:

| Percobaan | Hasil pengukuran |
| --------- | ---------------- |
| 1         | 9,81             |
| 2         | 9,82             |
| 3         | 9,81             |
| 4         | 9,82             |

Jika nilai acuannya 10,00, hasil tersebut cukup konsisten atau presisi, tetapi belum sepenuhnya akurat.

Dengan demikian, presisi dan akurasi merupakan dua konsep yang berbeda.

### **7. Konsep konvergensi dan stabilitas**

**7.1 Konvergensi**

Konvergensi merupakan kondisi ketika hasil suatu proses numerik semakin mendekati nilai solusi yang diharapkan.

Misalnya, suatu proses iterasi menghasilkan nilai:

| Iterasi | Hasil  |
| ------- | ------ |
| 1       | 1,5000 |
| 2       | 1,4200 |
| 3       | 1,4150 |
| 4       | 1,4143 |
| 5       | 1,4142 |

Nilai tersebut semakin mendekati:

\\[ \sqrt{2}\approx1.4142 \\]

**7.2 Stabilitas**

Stabilitas berkaitan dengan kemampuan suatu metode numerik dalam mengendalikan pengaruh galat selama proses perhitungan.

Metode yang tidak stabil dapat menyebabkan galat semakin membesar sehingga hasil perhitungan menjadi tidak dapat diandalkan.

Stabilitas menjadi sangat penting pada simulasi sistem dinamis, pemrosesan sinyal, dan penyelesaian persamaan diferensial.

### **8. Implementasi analisis galat menggunakan Python**

Berikut contoh implementasi sederhana untuk menghitung galat absolut, relatif, dan persentase galat.

```
# Analisis Galat Numeriknilai_sebenarnya = 12.0nilai_pendekatan = 11.8# Menghitung galat absolutgalat_absolut = abs(    nilai_sebenarnya - nilai_pendekatan)# Menghitung galat relatifgalat_relatif = (    galat_absolut / abs(nilai_sebenarnya))# Menghitung persentase galatpersentase_galat = galat_relatif * 100print("Nilai Sebenarnya :", nilai_sebenarnya)print("Nilai Pendekatan :", nilai_pendekatan)print("Galat Absolut    :", galat_absolut)print("Galat Relatif    :", galat_relatif)print("Persentase Galat :", persentase_galat, "%")
```

Hasil keluaran:

```
Nilai Sebenarnya : 12.0
Nilai Pendekatan : 11.8
Galat Absolut    : 0.2
Galat Relatif    : 0.0166667
Persentase Galat : 1.66667 %
```

### **9. Studi kasus Teknik Elektro: Analisis galat pembacaan sensor tegangan**

Sebuah sensor tegangan digunakan untuk mengukur tegangan pada suatu rangkaian elektronik. Berdasarkan alat ukur referensi, tegangan sebenarnya adalah 24 V. Sensor menghasilkan pembacaan sebesar 23,65 V.

Tentukan:

1. Galat absolut.
2. Galat relatif.
3. Persentase galat.
4. Interpretasi hasil pengukuran.

**Penyelesaian:**

Diketahui:

\\[ V_t=24\text{ V} \\]

\\[ V_a=23.65\text{ V} \\]

Galat absolut:

\\[ E_a=|24-23.65|=0.35\text{ V} \\]

Galat relatif:

\\[ E_r=\frac{0.35}{24}=0.014583 \\]

Persentase galat:

\\[ E_p=0.014583\times100\\% \\]

\\[ E_p=1.4583\\% \\]

**Interpretasi:**

Sensor memiliki persentase galat sekitar 1,46% terhadap alat ukur referensi. Hasil ini menunjukkan adanya selisih pembacaan yang perlu dipertimbangkan ketika sensor digunakan dalam sistem monitoring atau pengendalian tegangan.

Perlu diperhatikan bahwa nilai alat ukur referensi juga memiliki ketidakpastian. Karena itu, dalam eksperimen sebenarnya, nilai 24 V diperlakukan sebagai nilai acuan, bukan selalu nilai absolut yang bebas galat.

### **10. Rangkuman**

Pada pertemuan ini, mahasiswa telah mempelajari:

- Konsep dasar dan ruang lingkup metode numerik.
- Perbedaan pendekatan analitik dan numerik.
- Tahapan umum penyelesaian persoalan numerik.
- Pengertian galat absolut, relatif, dan persentase galat.
- Sumber galat berupa round-off, truncation, dan measurement error.
- Perbedaan akurasi dan presisi.
- Konsep konvergensi dan stabilitas.
- Implementasi analisis galat menggunakan Python.
- Penerapan analisis galat pada pengukuran tegangan sensor.

### **11. Referensi pembelajaran**

1. Chapra, S. C., & Canale, R. P. *Numerical Methods for Engineers*. McGraw-Hill.
2. Burden, R. L., Faires, J. D., & Burden, A. M. *Numerical Analysis*. Cengage Learning.
3. Sauer, T. *Numerical Analysis*. Pearson.
4. Kiusalaas, J. *Numerical Methods in Engineering with Python 3*. Cambridge University Press.
Bro, **Modul 4 selesai sebagai fondasi konseptual**. Kita sengaja belum masuk ke algoritma penyelesaian persamaan secara mendalam karena itu akan menjadi fokus pertemuan 5.

Berikutnya kita masuk ke **Modul 5: Metode Numerik untuk Penyelesaian Persamaan Nonlinear**. Kali ini kita bisa memperluas pembahasan dengan metode Secant juga, sehingga mahasiswa dapat membandingkan empat pendekatan berdasarkan prinsip, algoritma, kecepatan konvergensi, dan karakteristik masing-masing.
