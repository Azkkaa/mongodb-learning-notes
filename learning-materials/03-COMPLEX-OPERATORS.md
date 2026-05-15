# 🔍 Operator Query Kompleks

Modul ini membahas cara menggunakan *Query Operators* bawaan MongoDB untuk mencari dokumen tidak hanya berdasarkan kecocokan nilai eksak (*exact match*), tetapi juga menggunakan logika kondisi lanjutan. Dalam MongoDB, semua operator khusus ini selalu diawali dengan simbol dolar (`$`).

## 1. Operator Komparasi (Perbandingan Nilai)

Operator komparasi digunakan untuk membandingkan nilai numerik atau tanggal di dalam *field*.

* **`$gt` (Greater Than):** Mencari nilai yang lebih besar dari kriteria.
  * *Contoh:* `db.users.find({ age: { $gt: 25 } })`.
* **`$lt` (Less Than):** Mencari nilai yang lebih kecil dari kriteria.
  * *Contoh:* `db.users.find({ age: { $lt: 25 } })`.
* **`$gte` (Greater Than or Equal):** Mencari nilai yang lebih besar dari atau sama dengan kriteria.
* **`$lte` (Less Than or Equal):** Mencari nilai yang lebih kecil dari atau sama dengan kriteria.

## 2. Operator Logika

### Logika AND
Digunakan ketika seluruh kriteria pencarian **wajib** terpenuhi.
* **Implisit (Otomatis):** Jika Anda menulis beberapa *field* secara berurutan dalam satu objek filter, MongoDB secara otomatis memperlakukannya sebagai logika "AND". Ini adalah cara yang paling sering digunakan.
  * *Contoh:* `db.users.find({ age: 30, author: "Eko Prasetyo" })` (Mencari user yang umurnya 30 DAN penulisnya Eko Prasetyo).
* **Eksplisit (Operator `$and`):** Menggunakan format *array* objek. Biasanya hanya digunakan secara spesifik untuk *query* bersarang (*nested*) yang sangat kompleks, misalnya menggabungkan beberapa `$or`.
  * *Sintaks:* `db.users.find({ $and: [{ kriteria_1 }, { kriteria_2 }] })`.

### Logika OR (Operator `$or`)
Digunakan ketika Anda ingin mencari data yang memenuhi **salah satu** dari sekian banyak kondisi. Formatnya juga menggunakan *array*.
* **Sintaks Dasar:** `db.[koleksi].find({ $or: [{ kriteria_1 }, { kriteria_2 }] })`.
* **Contoh *Field* Sama:** `db.users.find({ $or: [{ age: 25 }, { age: 30 }] })`.
* **Contoh Operator Gabungan:** `db.users.find({ $or: [{ age: { $lt: 23 } }, { age: { $gt: 28} }] })`.

## 3. Operator `$in` dan `$nin`

Operator ini sangat berguna sebagai jalan pintas (*shortcut*) yang lebih bersih dibandingkan menggunakan operator `$or` secara berulang-ulang pada *field* yang sama.

* **`$in` (In):** Memerintahkan MongoDB untuk mencari dokumen yang nilai *field*-nya ada di dalam daftar *array* yang kita berikan.
  * *Sintaks:* `db.[koleksi].find({ field: { $in: [nilai_1, nilai_2, nilai_3] } })`.
  * *Contoh:* `db.users.find({ age: { $in: [25, 22, 28] } })`.
* **`$nin` (Not In):** Kebalikan mutlak dari `$in`. Mencari dokumen yang nilai *field*-nya **TIDAK ADA** di dalam daftar *array* tersebut.
  * *Sintaks:* `db.[koleksi].find({ field: { $nin: [nilai_1, nilai_2] } })`.

---
[⬅️ Kembali ke README.md](../README.md) | [Lanjut ke Update & Delete Documents ➡️](./04-UPDATE-DELETE.md)