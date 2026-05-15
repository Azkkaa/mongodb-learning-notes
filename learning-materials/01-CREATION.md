# 🛠️ Konsep Dasar & Creation

Dalam MongoDB, pembuatan *database* dan *collection* dapat dilakukan dengan dua cara utama: secara otomatis (*implicit*) atau secara manual (*explicit*) jika membutuhkan konfigurasi khusus.

## 1. Implicit Creation (Otomatis)

*Implicit Creation* adalah proses di mana MongoDB secara otomatis membuatkan *collection* saat Anda memasukkan data untuk pertama kalinya.

### Cara Kerja:
* **Memilih Database:** Gunakan perintah `use mydatabase` untuk memilih *database* yang ingin digunakan. Jika *database* tersebut belum ada, MongoDB akan menyimpannya dan baru benar-benar membuatnya setelah ada data yang dimasukkan ke dalam *collection*.
* **Memasukkan Data:** Perintah `db.users.insertOne({name: "azka", age: 21})` akan otomatis menciptakan *collection* bernama `users` (setara dengan *table* di MySQL) dan menyimpan data tersebut sebagai *document* (setara dengan *row* di MySQL).
* **Auto-Generate ID:** MongoDB akan otomatis membuatkan *unique id* (`_id`) untuk setiap data meskipun Anda tidak menyertakannya secara manual.
* **Status Acknowledged:** Jika Anda melihat pesan `acknowledged: true`, itu berarti MongoDB telah berhasil memproses operasi pembuatan data sesuai standar.

## 2. Explicit Creation (Manual)

Cara ini digunakan jika pengembang perlu melakukan konfigurasi khusus pada *collection*, seperti mengatur aturan alur data masuk dan keluar.

### Capped Collection
*Capped Collection* adalah jenis *collection* yang batas ukuran atau jumlah datanya sudah dikunci sejak awal.

* **Analogi:** Cara kerjanya persis seperti rekaman CCTV atau *dashcam* mobil. Jika kapasitas maksimal (misalnya 10.000 data) sudah penuh, data ke-10.001 tidak akan ditolak, melainkan MongoDB akan otomatis menghapus data tertua untuk memberi ruang bagi data baru.
* **Contoh Sintaks:**
  ```javascript
  db.createCollection("sensor_log", {capped: true, size: 5242880, max: 10000})
  ```
  *(Perintah di atas membuat collection khusus untuk log sensor dengan batas ukuran dan jumlah data tertentu)*.


---
[⬅️ Kembali ke README.md](../README.md) | [Lanjut ke Create & Read Documents ➡️](./02-CREATE-READ.md)