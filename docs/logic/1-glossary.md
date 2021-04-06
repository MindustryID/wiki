# Glosarium

Glosarium ini memberikan penjelasan yang lebih rinci tentang banyak istilah yang digunakan dalam manual ini.

## Jenis Data

Ada dua tipe data utama di Mindustry; angka dan Objek.

### nomor

Angka desimal. Bisa negatif atau positif, dan dapat mewakili nilai benar (apa pun yang tidak sama dengan 0) atau salah (0). Null juga direpresentasikan sebagai 0.

Beberapa instruksi hanya dapat menerima bilangan bulat, jadi itu ditunjukkan sesuai dengan manual ini.

Secara internal, angka disimpan sebagai nilai floating point 64-bit (`double`), dan dioperasikan sebagai integer bertanda 64-bit (` long`) saat bitshifting terlibat.

### String

Objek yang mewakili teks yang diapit tanda kutip, mis. `"halo mindustry"`

### Bangunan

Objek yang merepresentasikan Bangunan fisik di dunia.

**Ini berbeda dari Block**; Blok hanyalah sejenis Bangunan, tetapi Bangunan adalah Blok berwujud - seperti dalam, ia memiliki kesehatan, berinteraksi dengan kekuatan dan barang, dll.

Intinya, **Bangunan adalah Blok yang secara fisik ada di dunia.**

Misalnya, instruksi `getlink` akan mengembalikan Objek * Membangun *, di mana Anda bisa mendapatkan informasi tentang menggunakan`sensor`.

### Satuan

Objek yang mewakili Unit di dunia, termasuk pemain.

Misalnya, instruksi `ubind` akan menyetel variabel prosesor` @unit` ke Objek Unit yang mewakili unit terikat.

## Jenis Parameter

Ini seperti tipe data, tetapi hanya berfungsi sebagai parameter untuk instruksi, dan tidak dikembalikan oleh instruksi apa pun.

### BuildingType `content`

Suatu jenis Bangunan. Dimulai dengan `@`.

Di dalam kode permainan, ini lebih baik disebut sebagai "Blokir". Namun, agar panduan ini mudah dibaca, kami akan menyebutnya Tipe Bangunan. *Lihat [###Building] untuk penjelasan tentang Building vs. Block.*

Tidak seperti Item dan Cairan, Anda tidak dapat menggunakan ini di `sensor`. Namun, Anda dapat menggunakan `@ type` dalam` sensor`, dan membandingkannya dengan `jump`.

Contoh: `@scatter`

### UnitType `content`

Jenis Unit. Dimulai dengan `@`.

Contoh: `@toxopid`

*Daftar lengkap ditampilkan di bawah tombol pensil di blok instruksi "Unit Bind".*

<img src="/wiki/images/misc/logic-glossary-unitType-unitBind.png">

### Masuk akal

Properti Item, Cairan, atau Bangunan atau Unit yang dapat "dideteksi" oleh `sensor`. Dimulai dengan `@`.

Contoh: `@scrap`,` @slag`, `@totalAmmo`

*Daftar lengkap ditampilkan di bawah tombol pensil di blok instruksi "Sensor".*

<img src="/wiki/images/misc/logic-glossary-senseable-sensor.png">

### Target

Sifat untuk memfilter unit atau memblokir target. Terutama digunakan dalam `radar`,` uradar`, dan `ulocate`. `radar` dan` uradar` memiliki Target yang sama, tetapi `ulocate` berbeda, karena mencari Gedung.

*Daftar lengkap ditampilkan dengan menekan parameter setelah "target" di `radar` dan` uradar`, atau "find" dan "type" di `uradar`.*

<img src="/wiki/images/misc/logic-glossary-target-radar.png">

### Op

Operasi matematika. * Ini berbeda dari instruksi `op`.*

*Daftar lengkap ditampilkan di bawah tombol "+" di blok instruksi "Operasi".*

<img src="/wiki/images/misc/logic-glossary-op-operation.png">

Untuk yang lebih kompleks, Anda dapat menggunakan Google "<operation name\> matematika Java".

### Komp

Sebuah perbandingan. Terutama digunakan dalam instruksi `jump` saat membandingkan dua nilai. `always` akan kembali menjadi true apa pun yang terjadi, jadi itu akan selalu menyebabkan lompatan.

*Daftar lengkap ditampilkan di bawah tombol perbandingan di blok instruksi "Lompat".*

<img src="/wiki/images/misc/logic-glossary-comp-jump.png">
