# BigData-WordCount-PySpark
Implementasi WordCount menggunakan PySpark untuk tugas mata kuliah Big Data.
# Implementasi WordCount Menggunakan PySpark

Repository ini berisi implementasi WordCount menggunakan Apache Spark melalui PySpark untuk memenuhi tugas individu mata kuliah Big Data.

## Identitas

- Nama: Muhamad Firdaus
- NIM: 312410367
- Program Studi: Teknik Informatika
- Mata Kuliah: Big Data

## Deskripsi

Program ini digunakan untuk menghitung frekuensi kemunculan kata pada dataset teks menggunakan PySpark.

Dataset yang digunakan berupa file `bigdata.txt` sebanyak 6.000 baris.

Tahapan pemrosesan meliputi:

1. Membaca dataset menggunakan PySpark RDD
2. Melakukan preprocessing teks
3. Memecah kalimat menjadi kata menggunakan `flatMap()`
4. Membentuk pasangan `(kata, 1)` menggunakan `map()`
5. Menghitung frekuensi kata menggunakan `reduceByKey()`
6. Mengurutkan hasil WordCount
7. Menampilkan 10 kata dengan frekuensi tertinggi
8. Menguji pengaruh jumlah partition terhadap waktu pemrosesan
9. Menganalisis Spark Job, Stage, Task, dan Shuffle

## Hasil Pengujian

Hasil pemrosesan dataset:

- Jumlah baris: 6.000
- Total kata: 61.680
- Jumlah kata unik: 143
- Partition awal: 2

### Pengujian Jumlah Partition

| Jumlah Partition | Kata Unik | Waktu Proses |
|---:|---:|---:|
| 1 | 143 | 0.2952 detik |
| 2 | 143 | 0.4041 detik |
| 4 | 143 | 0.4804 detik |
| 8 | 143 | 1.0537 detik |

Pada pengujian ini, penggunaan 1 partition menghasilkan waktu pemrosesan paling cepat.

## Spark Job, Stage, dan Task

Hasil pengujian menunjukkan:

- Job ID: 23
- Jumlah Stage: 2
- Stage 42: 2 Task
- Stage 43: 2 Task
- Task gagal: 0

Operasi `reduceByKey()` menyebabkan proses shuffle untuk mengelompokkan kata yang memiliki key yang sama.

## File Repository

- `PySpark_MuhamadFirdaus.ipynb`  
  Berisi kode lengkap implementasi WordCount menggunakan PySpark beserta hasil pengujian.

- `bigdata.txt`  
  Dataset teks sebanyak 6.000 baris yang digunakan dalam proses WordCount.

## Kesimpulan

PySpark berhasil digunakan untuk melakukan WordCount terhadap dataset teks. Hasil pengujian menunjukkan bahwa jumlah partition dapat memengaruhi waktu pemrosesan dan penambahan partition tidak selalu membuat proses menjadi lebih cepat, terutama pada dataset yang relatif kecil.
