# 🍃 Pembelajaran MongoDB

Repositori ini berisi dokumentasi dan catatan pembelajaran mengenai MongoDB. Materi di dalamnya disusun secara terstruktur mulai dari konsep pembuatan koleksi, manipulasi data dasar (CRUD), hingga penggunaan operator query yang kompleks. Dokumentasi ini disusun sebagai referensi cepat untuk mendukung pengembangan arsitektur database pada ekosistem MERN Stack.

## 📂 Daftar Isi (Navigasi Pembelajaran)

Silakan klik tautan pada masing-masing modul di bawah ini untuk melihat detail materi:

1. **[Konsep Dasar & Creation](./learning-materials/01-CREATION.md)**
   * Membahas perbedaan mendasar antara *Implicit Creation* (Pembuatan Otomatis) dan *Explicit Creation* (Pembuatan Manual).
   * Pengaturan *Capped Collection* untuk membatasi ukuran atau jumlah maksimal data.

2. **[Create & Read Documents](./learning-materials/02-CREATE-READ.md)**
   * Menambahkan dokumen menggunakan perintah `insertOne` dan `insertMany`.
   * Mengambil dan membaca data menggunakan `find()` dan `findOne()`.
   * Penggunaan *Projection* untuk memilih *field* spesifik yang ingin ditampilkan.

3. **[Operator Query Kompleks](./learning-materials/03-COMPLEX-OPERATORS.md)**
   * Penggunaan operator komparasi seperti `$gt`, `$lt`, `$gte`, dan `$lte`.
   * Penggunaan operator logika `$or` dan struktur logika `AND` (baik secara implisit maupun eksplisit).
   * Pencocokan daftar nilai spesifik menggunakan operator `$in` dan `$nin`.

4. **[Update & Delete Documents](./learning-materials/04-UPDATE-DELETE.md)**
   * *Materi Tambahan:* Tata cara memperbarui struktur dan nilai dokumen yang sudah ada.
   * *Materi Tambahan:* Langkah-langkah aman dalam menghapus dokumen dari dalam koleksi.

5. **[Querying Arrays](./learning-materials/05-QUERYING-ARRAYS.md)**
   * *Materi Tambahan:* Melakukan pencarian tingkat lanjut secara spesifik pada data yang memiliki struktur *array*.

---
*Catatan: Repositori ini akan terus diperbarui secara berkala seiring dengan berjalannya proses pembelajaran dan implementasi teknis.*