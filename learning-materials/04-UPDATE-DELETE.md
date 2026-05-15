# 📝 Update & Delete Documents

Modul ini adalah materi tambahan yang membahas bagaimana cara memperbarui (*Update*) dan menghapus (*Delete*) dokumen yang sudah ada di dalam *collection* MongoDB.

## 1. Update (Memperbarui Data)

Untuk memperbarui data, MongoDB mengharuskan kita menggunakan **Update Operators** (seperti `$set`, `$inc`, dll) agar secara eksplisit memberi tahu *database* apa yang ingin diubah.

### Perintah `updateOne`
Digunakan untuk memperbarui **satu** dokumen pertama yang cocok dengan kriteria filter.
* **Sintaks Dasar:** `db.[koleksi].updateOne({ filter_pencarian }, { $operator: { field_yang_diubah: nilai_baru } })`
* **Operator `$set`:** Mengubah nilai dari sebuah *field* atau menambahkan *field* baru jika belum ada.
  * *Contoh:* `db.users.updateOne({ name: "Kalendra Wijaya" }, { $set: { age: 23, status: "Active" } })`
* **Operator `$inc` (Increment):** Menambah atau mengurangi nilai angka pada sebuah *field* tanpa perlu tahu nilai lamanya.
  * *Contoh:* `db.users.updateOne({ name: "Kalendra Wijaya" }, { $inc: { age: 1 } })` *(Menambah umur sebanyak 1)*.

### Perintah `updateMany`
Digunakan untuk memperbarui **semua** dokumen yang cocok dengan kriteria filter sekaligus.
* **Sintaks Dasar:** `db.[koleksi].updateMany({ filter_pencarian }, { $operator: { ... } })`
* **Contoh:** `db.users.updateMany({ age: { $lt: 20 } }, { $set: { category: "Teenager" } })` *(Mengubah kategori semua user yang umurnya di bawah 20 tahun)*.

---

## 2. Delete (Menghapus Data)

Menghapus data di MongoDB cukup sederhana dan hanya memerlukan argumen filter (kriteria pencarian) untuk menentukan dokumen mana yang akan dibuang. **Peringatan:** Lakukan operasi ini dengan hati-hati!

### Perintah `deleteOne`
Menghapus **satu** dokumen pertama yang cocok dengan kriteria filter. Sangat disarankan untuk menggunakan `_id` sebagai filter agar tidak salah hapus.
* **Sintaks Dasar:** `db.[koleksi].deleteOne({ filter_pencarian })`
* **Contoh:** `db.users.deleteOne({ _id: ObjectId("69ff4c935689cb0ee87da14a") })`

### Perintah `deleteMany`
Menghapus **semua** dokumen yang cocok dengan kriteria filter.
* **Sintaks Dasar:** `db.[koleksi].deleteMany({ filter_pencarian })`
* **Contoh:** `db.users.deleteMany({ age: { $gt: 50 } })` *(Menghapus semua user yang umurnya di atas 50 tahun)*.
* **Menghapus Semua Data Koleksi:** Jika Anda mengosongkan objek filter `{}`, perintah ini akan menghapus *semua* dokumen di dalam koleksi tersebut (koleksinya tetap ada, tapi isinya kosong).
  * *Contoh:* `db.users.deleteMany({})`

---
[⬅️ Kembali ke README.md](../README.md) | [Lanjut ke Querying Arrays ➡️](./05-QUERYING-ARRAYS.md)