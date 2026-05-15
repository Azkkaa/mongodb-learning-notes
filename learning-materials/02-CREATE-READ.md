# 💾 Create & Read Documents

Modul ini membahas cara memasukkan data (*Create*) dan mengambil data (*Read*) dari koleksi MongoDB.

## 1. Create (Menambahkan Data)

### Perintah `insertOne`
Digunakan untuk menambahkan **satu** dokumen ke dalam koleksi.
* **Sintaks:** `db.[nama_koleksi].insertOne({ objek_data })`.
* **Contoh:** `db.users.insertOne({ name: "Kalendra Wijaya", age: 22 })`.

### Fitur Otomatis Saat Insert:
* **Auto-Generate ID:** Anda tidak perlu mendefinisikan field `_id` secara manual; MongoDB akan otomatis membuatkan `ObjectId` yang unik untuk setiap dokumen baru.
* **Koleksi Dinamis:** Koleksi tidak perlu dibuat secara manual terlebih dahulu. Jika Anda melakukan *insert* ke koleksi yang belum ada, MongoDB akan otomatis membuatnya beserta dokumen pertamanya.

### Perintah `insertMany`
Digunakan untuk memasukkan **lebih dari satu** dokumen sekaligus secara massal.
* **Syarat:** Argumen harus berupa *Array of Objects* `[{...}, {...}]`.
* **Sintaks:** `db.[nama_koleksi].insertMany([{ data_1 }, { data_2 }])`.

---

## 2. Read (Membaca Data)

### Perintah Dasar `find`
Digunakan untuk menampilkan dokumen di dalam koleksi. Secara bawaan, MongoDB Shell akan menampilkan 20 dokumen pertama.
* **Sintaks:** `db.[collection_name].find()`.
* **Navigasi:** Ketik `it` (*iterate*) untuk melihat 20 dokumen berikutnya jika ada.



### Menggunakan Filter (Kriteria Pencarian)
Anda dapat menambahkan objek sebagai argumen pertama untuk mencari data yang spesifik.
* **Contoh:** `db.users.find({ age: 22 })` (Mencari semua pengguna dengan usia 22).

### Menggunakan Projection (Memilih Field)
Digunakan untuk menentukan field apa saja yang ingin ditampilkan dalam hasil pencarian.
* **Aturan:** Gunakan angka `1` untuk menampilkan field. Field `_id` akan selalu muncul kecuali diatur sebaliknya (`0`).
* **Contoh:** `db.users.find({name: "Andi Saputra"}, {age: 1})` (Hanya menampilkan field `age` untuk Andi).
* **Projection Tanpa Filter:** Gunakan objek kosong `{}` pada argumen pertama jika ingin mengambil semua data tapi hanya menampilkan field tertentu.

### Perintah `findOne`
Berbeda dengan `find`, perintah ini hanya mengembalikan **satu** dokumen pertama yang cocok dengan kriteria. Sangat berguna untuk mencari data spesifik berdasarkan `_id`.

---
[⬅️ Kembali ke README.md](../README.md) | [Lanjut ke Operator Query Kompleks ➡️](./03-COMPLEX-OPERATORS.md)