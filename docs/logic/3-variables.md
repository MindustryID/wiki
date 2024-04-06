# Variabel dan Konstan

Variabel dan konstan pada dasarnya "kontainer" dari value(isi). Setiap satu memiliki nama dan value. Mindustry memiliki variabel yang mana bisa diatur oleh user dan kode mereka, dan konstan yang mana bisa diubah hanya oleh prosesor dan tidak dapat diubah oleh user

*Untuk mencari tahu data yang mungkin atau tipe parameter dari variabel dan konstan, lihat Glosarium*

## Variabel

### Membuat dan Mengubah Variabel

Variabel yang mereka nama menunjukan; sebuah value yang dapat diubah.

Contohnya, dalam kode: `set myVariable 3`, intruksi `set` akan membuat sebuah variabel yang bernama `myVariable`, dan memberikan suatu value untuk `3`.

Kemudian itu, ini dapat diubah value itu ke `9`: `set myVariable 9`.

Beritahu bagaimana kita menggunakan inrtuksi yang sama untuk antara membuat dan mengubah variabel. ini karena **jika sebuah variabel yang itu berubah tidak sebenarnya ada, sebuah intruksi akan membuat itu dulu**
Jika kamu tahu Python, kamu akan mungkin telah sadar bagaimana itu bekerja dalam tujuan yang sama.
If you know Python, you'll probably have realized that it works in the same way.


Contoh yang lain dengan menggunakan `sensor`: `sensor playerX playerUnit @x` (atau Sensor playerX = @x dalam playerUnit untuk editor visual)

Menganggap itu posisi player adalah `141, 20`, sebuah variabel dengan nama `playerX` akan dibuat terlebih dahulu, lalu mengisi sebuah value dari `141`.

Meskipun, kita memiliki variabel dalam contoh yang disebut `playerUnit`. Variabel itu adalah **parameter**. Sebuah parameter sebuah masukan value kedalam intruksi. Dalam kasus ini, kita mungkin dapat `playerUnit` dari intruksi `radar`. jika parameter tidak ditunjukan tau salah, intruksi tidak bakal dijalankan.

### Tipe Data dan Pengubahan Implisit


Value dalam variabel, tentu saja, ada tipe yang berbeda itu adalah spesifik ke sumber yang berbeda
dan tujuannya, seperti `Unit` untuk Units, `number` untuk angka yang manapun, dll. Kamu bisa cari sebuah daftar dari semua itu di Glosarium.

Mindustry Logic juga memiliki hal ini dengan variabel disebut **Pengubahan Implisit**. Itu bermaksud itu, jika dibutuhkan, itu akan mengubah sebuah value milik variabel dari satu tipe ke lain.

Jika sebuah intruksi dimasukan sebuah `number`, tetapi itu membutuhkan `Object`, itu akan diubah menjadi `null`. 
Jika sebuah intruksi membutuhkan sebuah `number`, tetapi itu dimasukan `Object`, itu akan diubah menjadi 1 jika objek bukan `null`, lain kali 0. 
If an instruction needs a `number`, but is given an `Object`, it will be converted to 1 if the object isn't `null`, sebaliknya 0.

Contoh:

* `53` -> `null`
* `null` -> 0,
* `Object` yang mana itu Silicon Crucible -> 1

Intruksi `print` adalah hanya intruksi yang membutuhkan `String`sebagai input, jadi peraturan itu telah sudah dinyatakan dalam bagian dari panduan itu sendiri.

### Penamaan Variabel

Penamaan Variabel disesuaikan sebuah keahlian penting yang dimiliki jika pemograman pada dasarnya. itu membantu dalam membuat kode lebih mudah dibaca dan dimengerti. Demikian, itu dapat membuai it lebih mudah untuk seseorang untuk belajar darinya atay memperbaiki kodemu.

Nama Variabel dapat berisi karakter yang mana bisa diketik. Walaupun, mereka tidak bisa sepenuhnya angka, sejak itu akan seharusnya gunakan angka yang sebenarnya.

Penamaan konvensi yang biasa antara mayoritas dari kode mlog adalah camelCase, sebuah contoh yang mana itu sendiri. contoh variabel yang menggunakan camelCase adalah: `playerX`, `coreFound`, `vertexAngle`. 

**Kapan penamaan variabel, seharunya mereka adalah deskriptif tapi pendek** Mereka harus menjelaskan value yang mereka pegang atau tujuan mereka. Pada waktu yang sama, mereka seharusnya tidak sebagai kalimat yang selesai atau pindah semua lembar, atau jadi lebih pendek itu yang bikin membingungkan, kamu bisa gunakan singkatan, akronim, atau istilah pendek untuk membuat itu lebih singkat.

Setiap orang memiliki gaya dan preferensi mereka sendiri, tetapi mencoba untuk belajar dari contoh yang baik dalam memogram di mlog atau bahasa lain, walaupun pada waktu yang sama tetap menutup ke gaya umum.

## Variabel dan Konstan prosesor

Konstan juga memiliki value, tapi tidak bisa diubah. setiap prosesor memiliki konstan dan variabel bawaan:

### prosesor

#### @this `constant` `Building`

Sebuah Objek `Building` itu merepresentasikan prosesor itu sendiri. kamu bisa gunakan itu dengan `sensor` untuk mencari beberapa properti tentang prosesor.

#### @thisx `constant` `number`

Koordinat x dari prosesor.

#### @thisy `constant` `number`

Koordinat y dari prosesor.

#### @ipt `constant` `number`

Angka dari eksekusi intruksi per tick (60 tick/detik).

* Micro Processor -> 2
* Logic Processor -> 8
* Hyper Processor -> 25 

#### @counter `variable` `number`

Sebuah variabel itu merepresentasikan baris selanjutnya akan dibaca code darinya, setara pada `%IP` di x86. itu bisa diubah seperti variabel yang lain sebagai jalan lain untuk mekakukan loncatan.

Contoh (lanjutan) dari pengaturan `@counter` untuk meloncat ke sebuah fungsi, lalu loncat lagi ke pemanggil:

```
op add retAddr @counter 1 # Save where we will continue after the function returns by adding 1 to the counter
set @counter myFunc       # Jump to the line representing myFunc
...
set @counter retAddr      # Return to the line set earlier after the function is called
```
### Tautan

#### @links `constant` `number`

Sebuah konstan itu sama dengan angka dari bangunan yang ditaut ke prosesor. itu bisa diubah dengan prosesor yang blok ditaut atau dilepas.

Kamu bisa menggunakan bersama dengan `getlink` untuk memutar semua bangunan yang ditaut, jadi seperti:

```
set linkIter 0                  # Create iterator variable
getlink block linkIter          # Get Building Object of the "linkIter"th linked building.
# Do what you want with the building here
jump 1 lessThan linkIter @links # Loop
```

#### <buidingName><n> `constant` `Building`

Ini adalah sebenarnya beberapa konstan, satu dari setiap bangunan ditautkan ke prosesor. Mereka adalah dihapus atau ditambah kapan itu sebuah bangunan itu dilepaskan atau ditautkan ke prosesor. 

`buildingName` merepresentasikan **nama internal** suatu bangunan, yang mana kamu bisa cari di sisa dari Wiki.

`n` dimulai pada satu dan menambah jika suatu bangunan dari tipe itu yang ditautkan. itu semacam seperti bangunan dari tipe ke-`n`

Ini bisa jadi agak susah untuk dimengerti, jadi ini beberapa contoh:

* Scatter pertama yang ditautkan: `scatter1`
* Ripple ketiga yang ditautkan: `ripple3`
* Bor Laser kedua ditautkan: `drill2`
* Penekan Spora kesebelas ditautkan: `press11`

Kamu juga bisa lihat "nama konstan" setiap bangunan yang ditautkan diatas mereka jika prosesor yang dipilih.

<img src="/wiki/images/misc/logic-variables-constants-links-linkedBuilding.png">

### Lainnya

#### @unit `constant` `Unit`

Sebuah konstan yang merepresentasikan unit yang terikat saat ini. itu hanya diubah jika prosesor melepaskan sebuah unit atau mengikat yang lain. itu bisa diakses dengan intruksi unit seperti `ucontrol`, `ulocate`, dan `uradar`. Sejak itu sebuah Objek Unit, kamu juga bisa gunakan itu dengan `sensor`.

Ini memberikan sebuah bagian inti dari kendali unit di mlog; **hanya satu unit bisa diikat pada waktunya.** Namun, kamu bisa mereferensikan ini dalam variabel, seperti `set unitReference @unit`. Itu variabel, walau, bisa tidak dapat digunakan untuk kendali unit yang direferensikan. itu hanya bisa digunakan untuk cek betentangan unit lain atau mendapatkan informasi tentang itu. Oleh karena itu, kamu bisa berpikir itu sebagai "indentitas unit".

#### @time `constant` `number`

Merepresentasikan sebagai catatan waktu UNIX saat ini *in milliseconds*.

#### @tick `constant` `float`

Merepresentasikan jumlah tick (60 tick/detik) sejak peta berlangsung.

#### @mapw `constant` `number`

Lebar peta, dalam petak.

#### @maph `constant` `number`

Tinggi peta, dalam petak.
