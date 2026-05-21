# analisis-kebiasaan-belajar-mahasiswa-program-studi-statistika-universitas-mataram-terhadap-persiapan-ujian-semester-tugas-2 
## Latar Belakang
Kebiasaan belajar mahasiswa merupakan salah satu faktor penting yang memengaruhi kesiapan dalam menghadapi ujian semester. Pola belajar yang teratur, manajemen waktu yang baik, serta konsistensi dalam memahami materi dapat membantu meningkatkan pemahaman akademik dan hasil belajar mahasiswa.
Namun, pada kenyataannya masih banyak mahasiswa yang memiliki kebiasaan belajar yang berbeda-beda, seperti belajar hanya menjelang ujian, kurangnya jadwal belajar yang teratur, maupun rendahnya intensitas latihan soal. Perbedaan kebiasaan belajar tersebut dapat memengaruhi tingkat kesiapan mahasiswa dalam menghadapi ujian semester.
Mahasiswa Program Studi Statistika universitas mataram sebagai populasi penelitian memiliki karakteristik akademik yang erat kaitannya dengan kemampuan analisis dan pengolahan data. Oleh karena itu, penelitian ini dilakukan untuk mengetahui kebiasaan belajar mahasiswa dalam mempersiapkan ujian semester melalui penyebaran kuesioner.
Analisis dilakukan menggunakan bahasa pemrograman R dengan metode uji validitas dan uji reliabilitas untuk memastikan bahwa instrumen penelitian yang digunakan mampu mengukur variabel secara tepat dan konsisten.

## Tujuan
Penelitian ini bertujuan untuk menganalisis kebiasaan belajar mahasiswa program studi statistika universitas mataram dalam mempersiapkan ujian semester melalui data kuesioner. Selain itu, penelitian ini dilakukan untuk mengetahui apakah instrumen penelitian yang digunakan telah memenuhi syarat validitas dan reliabilitas. Proses analisis dilakukan menggunakan bahasa pemrograman R dengan metode uji validitas korelasi item-total serta uji reliabilitas menggunakan Cronbach Alpha agar hasil pengukuran yang diperoleh dapat dipercaya dan konsisten.

## Metode
Penelitian ini menggunakan metode kuantitatif dengan teknik pengumpulan data melalui penyebaran kuesioner kepada mahasiswa Program Studi Statistika universitas mataram sebagai populasi penelitian. Data yang diperoleh kemudian dianalisis menggunakan bahasa pemrograman R.
Tahapan analisis meliputi penentuan jumlah sampel menggunakan rumus Slovin, uji validitas menggunakan korelasi item-total, serta uji reliabilitas menggunakan metode Cronbach Alpha. Pengolahan data dilakukan dengan bantuan package `readxl` untuk membaca data dan `psych` untuk analisis statistik.

## Tahapan Analisis Data
### 1. Menentukan Jumlah Sampel dengan Rumus Slovin
Rumus Slovin digunakan untuk menentukan jumlah sampel penelitian berdasarkan jumlah populasi dan tingkat kesalahan tertentu.
N <- 154
e <- 0.15
n <- ceiling(N / (1 + N * e^2))
cat("Jumlah sampel berdasarkan rumus Slovin =", n)

### 2. Import Data
Data kuesioner yang telah disimpan dalam file Excel diimpor ke dalam R menggunakan package `readxl`.
library(readxl)
library(psych) 

data <- read_excel("~/data teksam survei.xlsx")

### 3. Uji Validitas
Uji validitas dilakukan untuk mengetahui apakah item pertanyaan pada kuesioner mampu mengukur variabel yang diteliti.
item <- data[, c("p1","p2","p3","p4","p5","p6","p7","p8","p9","p10")]

corr.test(item)
total <- rowSums(item)
cor(item, total)

Kriteria:
* r hitung > 0.30 → Valid
* r hitung < 0.30 → Tidak Valid

### 4. Uji Reliabilitas

Uji reliabilitas dilakukan menggunakan metode Cronbach Alpha untuk mengetahui konsistensi instrumen penelitian.
alpha(item)$total
alpha(item)$total$raw_alpha

Kriteria:
* Alpha > 0.70 → Reliabel

## Hasil dan Pembahasan
### Hasil Uji Validitas
Berdasarkan hasil analisis menggunakan korelasi item-total, seluruh item pertanyaan memperoleh nilai korelasi di atas 0.30 sehingga seluruh item pada kuesioner dinyatakan valid.

| Item | r hitung | Keterangan |
| ---- | -------- | ---------- |
| P1   | 0.594    | Valid      |
| P2   | 0.711    | Valid      |
| P3   | 0.818    | Valid      |
| P4   | 0.400    | Valid      |
| P5   | 0.701    | Valid      |
| P6   | 0.891    | Valid      |
| P7   | 0.772    | Valid      |
| P8   | 0.748    | Valid      |
| P9   | 0.783    | Valid      |
| P10  | 0.752    | Valid      |

Hasil tersebut menunjukkan bahwa seluruh item pertanyaan mampu mengukur variabel kebiasaan belajar mahasiswa program studi statistika universitas mataram terhadap persiapan ujian semester dengan baik.

### Hasil Uji Reliabilitas
Hasil uji reliabilitas menggunakan metode Cronbach Alpha memperoleh nilai sebesar: 0.920

| Metode | Nilai Cronbach Alpha | Keterangan |
|---------|----------------------|-------------|
| Cronbach Alpha | 0.920 | Sangat Reliabel |

Berdasarkan hasil uji reliabilitas menggunakan metode Cronbach Alpha diperoleh nilai sebesar 0.920. Nilai tersebut lebih besar dari 0.70 sehingga instrumen penelitian dinyatakan reliabel dengan tingkat reliabilitas sangat tinggi.

## Kesimpulan
Berdasarkan hasil analisis data kuesioner mengenai kebiasaan belajar mahasiswa program studi statistika universitas mataram terhadap persiapan ujian semester, diperoleh bahwa seluruh item pertanyaan dinyatakan valid berdasarkan uji validitas korelasi item-total.
Selain itu, hasil uji reliabilitas menggunakan Cronbach Alpha memperoleh nilai sebesar 0.920 yang menunjukkan bahwa instrumen penelitian memiliki tingkat reliabilitas sangat tinggi.
Dengan demikian, kuesioner yang digunakan dalam penelitian ini dapat dipercaya untuk mengukur kebiasaan belajar mahasiswa program studi statistika universitas mataram terhadap persiapan ujian semester.

## Tools dan Library
* R
* readxl
* psych
