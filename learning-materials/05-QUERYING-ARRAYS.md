# 📦 Querying Arrays

Modul ini adalah materi tambahan yang berfokus pada cara melakukan *query* atau pencarian dokumen berdasarkan *field* yang menyimpan data dengan tipe *Array* (daftar nilai).

## 1. Pencarian Elemen Dasar

Jika sebuah *field* berisi *array*, Anda bisa mencari dokumen hanya dengan menyebutkan salah satu elemen di dalam *array* tersebut.
* **Konsep:** MongoDB akan otomatis mencari dokumen di mana *array* tersebut mengandung nilai yang dicari.
* **Contoh Kasus:** Anda memiliki *collection* `products` dengan *field* `tags` (misal: `["electronics", "smart-home", "iot"]`).
* **Kueri:** `db.products.find({ tags: "iot" })` *(Akan mengembalikan semua produk yang memiliki tag "iot" di dalam array-nya)*.

## 2. Pencocokan Array Presisi (Exact Match)

Anda bisa mencari dokumen yang *array*-nya persis sama persis dengan yang Anda minta, **termasuk urutannya**.
* **Kueri:** `db.products.find({ tags: ["apple", "red"] })`
* **Catatan Penting:** Ini hanya akan cocok jika *array* di database persis `["apple", "red"]`. Jika di database urutannya `["red", "apple"]` atau ada elemen tambahan seperti `["apple", "red", "sweet"]`, dokumen tersebut **tidak akan** terpanggil.

## 3. Operator Spesifik Array

MongoDB menyediakan operator khusus untuk memanipulasi dan memfilter *array* dengan lebih dinamis.

### Operator `$all`
Digunakan jika Anda ingin mencari dokumen yang *array*-nya memiliki **semua** elemen yang diminta, **tanpa mempedulikan urutannya**.
* **Sintaks Dasar:** `db.[koleksi].find({ field_array: { $all: [nilai1, nilai2] } })`
* **Contoh:** `db.products.find({ tags: { $all: ["smart-home", "esp32"] } })` *(Dokumen akan terpanggil selama ada "smart-home" dan "esp32" di dalam array, tidak peduli apa urutannya atau apakah ada tag lain)*.

### Operator `$size`
Digunakan untuk mencari dokumen berdasarkan **jumlah elemen** yang ada di dalam sebuah *array*.
* **Sintaks Dasar:** `db.[koleksi].find({ field_array: { $size: jumlah_angka } })`
* **Contoh:** `db.products.find({ tags: { $size: 3 } })` *(Mengembalikan dokumen yang tepat memiliki 3 elemen di dalam field `tags`)*.

### Operator `$elemMatch`
Sangat berguna ketika Anda berhadapan dengan **Array of Objects** (misalnya data log sensor harian). Operator ini memastikan setidaknya ada *satu* objek di dalam *array* yang memenuhi *semua* kriteria pencarian yang Anda tentukan.
* **Contoh Kasus:** Anda punya *array* `sensor_readings` yang berisi daftar objek `{ temperature: 30, humidity: 80 }`.
* **Kueri:**
    ```javascript
    db.ruangsense_logs.find({ 
        sensor_readings: { 
        $elemMatch: { temperature: { $gt: 28 }, humidity: { $lt: 85 } } 
        } 
    })
    ```
    *(Akan mencari dokumen di mana setidaknya ada SATU pembacaan sensor dalam array yang suhunya di atas 28 DAN kelembapannya di bawah 85)*.

---
[⬅️ Kembali ke Update & Delete Documents](./04-UPDATE-DELETE.md) | [🏠 Kembali ke README.md](../README.md)