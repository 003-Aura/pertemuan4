# LAPORAN PRAKTIKUM 04
# IMPLEMENTASI BACKEND DAN DATABASE MYSQL

## 1. Tujuan Praktikum

Praktikum ini bertujuan untuk memahami proses implementasi backend yang terhubung dengan database MySQL. Melalui praktikum ini, mahasiswa mempelajari cara mempersiapkan project backend, melakukan instalasi package, menjalankan database, serta menggunakan Prisma ORM untuk mengelola data.

Selain itu, praktikum ini bertujuan agar mahasiswa memahami proses kerja backend dalam menerima permintaan pengguna, melakukan validasi, memproses data, menyimpan data ke database, dan memberikan respons melalui API.

## 2. Persiapan Praktikum

Sebelum memulai praktikum, beberapa perangkat lunak yang digunakan adalah:

| No. | Perangkat | Kegunaan |
|---|---|---|
| 1 | Visual Studio Code | Membuka dan mengelola source code. |
| 2 | Node.js | Menjalankan aplikasi backend. |
| 3 | npm | Mengelola dan memasang package. |
| 4 | Docker Desktop | Menjalankan database menggunakan Docker Compose. |
| 5 | MySQL | Menyimpan data aplikasi. |
| 6 | Prisma ORM | Menghubungkan backend dengan database. |
| 7 | PowerShell | Menjalankan perintah melalui terminal. |

## 3. Langkah-Langkah Pengerjaan

### 3.1 Membuka Project Backend

Project backend yang telah diunduh dari lampiran praktikum diekstrak ke dalam komputer. Selanjutnya, folder project dibuka menggunakan Visual Studio Code.

Folder yang digunakan adalah `praktikum-backend`. Terminal dibuka pada folder utama project yang berisi file `package.json` agar perintah praktikum dapat dijalankan pada direktori yang benar.

### 3.2 Instalasi Package

Instalasi package dilakukan menggunakan perintah berikut:

```bash
npm install
```

Perintah tersebut digunakan untuk mengunduh dan memasang seluruh package yang dibutuhkan oleh aplikasi berdasarkan konfigurasi pada file `package.json`.

Hasil instalasi menunjukkan bahwa sebanyak 128 package berhasil ditambahkan dan 129 package telah diaudit. Terdapat pula beberapa peringatan keamanan dan install script Prisma yang perlu diperiksa lebih lanjut.

**Bukti instalasi package:**

![Hasil Instalasi Package](bukti/01-install-package..png)

### 3.3 Menjalankan Database MySQL

Database MySQL digunakan sebagai tempat penyimpanan data aplikasi. Pada praktikum ini, database dijalankan menggunakan Docker Compose sesuai petunjuk pada README paket backend.

Perintah yang digunakan disesuaikan dengan konfigurasi Docker Compose yang tersedia pada project.

```bash
[TULISKAN PERINTAH SESUAI README]
```

Setelah perintah dijalankan, dilakukan pemeriksaan untuk memastikan container database berhasil berjalan.

**Bukti database MySQL berjalan:**

![Database MySQL Berjalan](bukti/02-database-mysql.png)

### 3.4 Menjalankan Prisma Generate

Prisma ORM digunakan untuk membantu backend berkomunikasi dengan database. Proses generate dilakukan untuk menghasilkan Prisma Client berdasarkan struktur database yang telah didefinisikan.

Perintah yang digunakan:

```bash
[TULISKAN PERINTAH SESUAI README]
```

Apabila proses berhasil, Prisma Client dapat digunakan oleh aplikasi backend untuk melakukan operasi terhadap database.

**Bukti Prisma Generate:**

![Prisma Generate Berhasil](bukti/03-prisma-generate.png)

### 3.5 Menjalankan Migrasi Database

Migrasi database dilakukan untuk menerapkan struktur tabel yang telah didefinisikan pada file schema Prisma ke dalam database MySQL.

Proses ini bertujuan agar tabel dan relasi yang dibutuhkan oleh aplikasi tersedia di dalam database.

Perintah yang digunakan:

```bash
[TULISKAN PERINTAH SESUAI README]
```

**Bukti migrasi database:**

![Migrasi Database Berhasil](bukti/04-migrasi-database.png)

### 3.6 Memasukkan Data Awal Menggunakan Seed

Seed merupakan proses memasukkan data awal atau data contoh ke dalam database. Data tersebut digunakan untuk membantu proses pengujian aplikasi.

Data awal dapat berupa akun pengguna, jadwal kegiatan, dan contoh pendaftaran peserta sesuai data yang tersedia pada project.

Perintah yang digunakan:

```bash
[TULISKAN PERINTAH SESUAI README]
```

Setelah proses selesai, dilakukan pemeriksaan untuk memastikan data awal berhasil dimasukkan ke database.

**Bukti proses seed:**

![Seed Database Berhasil](bukti/05-seed-database.png)

### 3.7 Menjalankan Backend

Setelah database dan konfigurasi Prisma siap, aplikasi backend dijalankan menggunakan perintah:

```bash
npm run dev
```

Perintah tersebut digunakan untuk menjalankan server backend dalam mode pengembangan.

Backend berjalan menggunakan port 3000 agar API dapat menerima permintaan dari aplikasi atau pengguna.

**Bukti backend aktif:**

![Backend Aktif](bukti/06-backend-aktif.png)

### 3.8 Melakukan Health Check

Health check dilakukan untuk memastikan bahwa server backend dapat diakses dan memberikan respons dengan baik.

Pemeriksaan dilakukan menggunakan perintah:

```bash
curl -i http://localhost:3000/api/v1/health
```

Hasil yang diharapkan adalah status HTTP 200 dengan respons:

```json
{
  "status": "ok"
}
```

Hasil tersebut menunjukkan bahwa API berjalan dengan baik dan dapat memberikan respons sesuai yang diharapkan.

**Bukti health check:**

![Hasil Health Check](bukti/07-health-check.png)

## 4. Penjelasan Source Code

### 4.1 schema.prisma

File `schema.prisma` digunakan untuk mendefinisikan struktur database yang akan digunakan oleh aplikasi.

Di dalam file tersebut terdapat konfigurasi datasource MySQL dan model yang menggambarkan tabel beserta hubungan antar tabel.

### 4.2 seed.js

File `seed.js` digunakan untuk menjalankan proses pengisian data awal ke database. File ini memanggil fungsi seed yang telah disediakan dan menampilkan informasi setelah proses selesai.

### 4.3 seed-data.js

File `seed-data.js` berisi proses utama untuk memasukkan data contoh ke database. Proses tersebut meliputi pembacaan data fixture, pembuatan hash password, penyimpanan akun pengguna, penyimpanan jadwal, serta pemeriksaan kapasitas pendaftaran.

### 4.4 fixtures.json

File `fixtures.json` digunakan untuk menyimpan data contoh yang akan dimasukkan ke database, seperti data pengguna, jadwal kegiatan, dan contoh pendaftaran peserta.

### 4.5 db.js

File `db.js` digunakan untuk mengatur koneksi Prisma Client dengan database sehingga aplikasi backend dapat melakukan operasi pengelolaan data.

### 4.6 server.js

File `server.js` digunakan untuk menjalankan server backend, menghubungkan aplikasi dengan database, dan mengatur port yang digunakan oleh API.

## 5. Perubahan Kode

Pada bagian ini dijelaskan perubahan kode yang dilakukan selama praktikum. Penjelasan mencakup lokasi file yang diubah, bagian kode yang mengalami perubahan, alasan perubahan, dan hasil setelah perubahan diterapkan.

| Keterangan | Penjelasan |
|---|---|
| Lokasi file | [Isi sesuai file yang diubah] |
| Bagian kode | [Isi bagian kode yang diubah] |
| Alasan perubahan | [Jelaskan alasan perubahan] |
| Hasil perubahan | [Jelaskan hasil setelah perubahan] |

Apabila tidak melakukan perubahan kode, jelaskan bahwa source code masih menggunakan kode yang disediakan pada lampiran praktikum.

## 6. Hasil Pengujian

Pengujian dilakukan untuk mengetahui apakah aplikasi backend dapat menjalankan fungsi sesuai kebutuhan. Pengujian terdiri dari skenario berhasil dan skenario gagal.

### 6.1 Pengujian Berhasil

Pengujian berhasil dilakukan dengan memberikan input yang sesuai dengan ketentuan sistem. Sistem diharapkan dapat memproses permintaan dan memberikan respons sesuai dengan hasil yang diharapkan.

**Bukti pengujian berhasil:**

![Pengujian Berhasil](bukti/08-pengujian-berhasil.png)

### 6.2 Pengujian Gagal

Pengujian gagal dilakukan dengan memberikan input yang tidak sesuai atau kondisi yang menyebabkan permintaan tidak dapat diproses. Pengujian ini bertujuan mengetahui bagaimana sistem menangani kesalahan dan memberikan respons kepada pengguna.

**Bukti pengujian gagal:**

![Pengujian Gagal](bukti/09-pengujian-gagal.png)

### 6.3 Ringkasan Hasil Pengujian

| No. | Skenario Pengujian | Hasil yang Diharapkan | Hasil Aktual |
|---|---|---|---|
| 1 | Instalasi package | Package berhasil dipasang | [Isi hasil] |
| 2 | Menjalankan database | Database aktif | [Isi hasil] |
| 3 | Prisma Generate | Prisma Client berhasil dibuat | [Isi hasil] |
| 4 | Migrasi database | Struktur tabel berhasil diterapkan | [Isi hasil] |
| 5 | Seed database | Data awal berhasil dimasukkan | [Isi hasil] |
| 6 | Menjalankan backend | Backend aktif pada port 3000 | [Isi hasil] |
| 7 | Health check | API memberikan respons HTTP 200 | [Isi hasil] |
| 8 | Pengujian berhasil | Permintaan diproses sesuai ketentuan | [Isi hasil] |
| 9 | Pengujian gagal | Sistem menangani kesalahan dengan baik | [Isi hasil] |

## 7. Jawaban Pertanyaan Praktikum

### 7.1 Dari mana input fitur berasal dan di file mana input tersebut diperiksa?

Input fitur berasal dari pengguna melalui permintaan yang dikirimkan ke API. Permintaan tersebut diterima oleh backend melalui endpoint yang telah disediakan. Selanjutnya, input diperiksa melalui proses validasi pada bagian route, controller, atau fungsi validasi sesuai struktur source code sebelum diproses lebih lanjut.

### 7.2 Fungsi apa yang mengubah data atau state, dan kapan respons ditampilkan kepada pengguna?

Perubahan data dilakukan oleh fungsi yang menjalankan proses penyimpanan, pembaruan, atau penghapusan data melalui Prisma Client. Setelah proses pengolahan data selesai, backend mengirimkan respons melalui API sehingga pengguna dapat mengetahui apakah permintaannya berhasil atau gagal.

### 7.3 Apa yang terjadi jika permintaan gagal sebelum dan sesudah penyimpanan data?

Jika permintaan gagal sebelum proses penyimpanan dilakukan, data belum masuk ke database. Namun, apabila kegagalan terjadi setelah penyimpanan berhasil, terdapat kemungkinan data sudah tersimpan meskipun pengguna menerima respons gagal.

Oleh karena itu, diperlukan penanganan kesalahan dan penggunaan transaksi database untuk menjaga konsistensi data apabila terdapat beberapa proses penyimpanan yang saling berkaitan.

## 8. Kesimpulan

Berdasarkan praktikum yang telah dilakukan, dapat disimpulkan bahwa backend memiliki peran penting dalam mengatur proses pengolahan data pada aplikasi. Backend menerima permintaan pengguna, melakukan validasi, memproses data, menyimpan data ke database, dan memberikan respons melalui API.

Dalam praktikum ini, Node.js digunakan untuk menjalankan backend, MySQL digunakan sebagai tempat penyimpanan data, sedangkan Prisma ORM membantu proses komunikasi antara backend dan database.

Melalui praktikum ini, mahasiswa memperoleh pemahaman mengenai instalasi package, menjalankan database, melakukan generate Prisma Client, migrasi database, memasukkan data awal menggunakan seed, menjalankan server backend, serta melakukan pengujian API.