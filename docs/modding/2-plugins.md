# Plugin dan mod JVM

Mindustry mendukung memuat file `jar` dengan kodebita Java di desktop & Android. Fungsi itu mirip seperti mod JS, dan harus menyediakan kelas utama dan instantiasi jika mod itu dibuat

Secara teori, semua bahasa JVM seharusnya tendukung.

Mod JAR/JVM menggunakan file meta `mod.hjson` yang sama itu mod biasa lakukan, tetapi dengan satu tambahan: *kelas utama yang sepenuhnya dikualifikasi* dsapat dispesifikasi dengan `main: "mypackage.MyMod"`. Kelas ini seharusnya memanjang ke `mindustry.mod.Mod`.

Jika sebuah kelas utama tidak diberikan, itu secara defauilt ke `modnameinlowercase.ModName + "Mod".`

`mod.hjson` yang simpel untuk mod Java terlihat seperti ini:

```hjson
name: "Nothing"
author: "Yourself"
main: "nothing.NothingMod"
description: "..."
version: "99.99"
```

Lihat [repositori contoh mod Java](https://github.com/Anuken/ExampleJavaMod), [repositori contoh mod Kotlin](https://github.com/Anuken/ExampleKotlinMod) atau [templat mod Java](https://github.com/Sonnicon/mindustry-modtemplate) untuk informasi tambahan.

## Plugin
Plugin adalah mod Java yang bertujuan untuk dijalanke hanya di server. Biasanya, mereka menambahkan *perintah baru* atau *mode permainan baru*.
Semua kelas utama plugin seharusnya memanjang ke `mindustry.mod.Plugin`. Itu membuat mereka secara implicit *hidden* - Klien tidak membutuhkan untuk mendownload plugin untuk menghubung ke server. Mereka itu hanya server-side.

Nama file meta plugin mereka `plugin.[h]json`. Struktur file itu indentik seperti mod Java lainnya - lihat diatas untuk detail.

Kamu bisa melihat contoh plugin [disini](https://github.com/Anuken/ExamplePlugin). Untuk contoh lebih praktis itu dapat digunakan kedalam server asli. lihat [repo ini](https://github.com/Anuken/AuthorizePlugin).

## Mengimpor

Gak seperti mod JS atau JSON, mod jar harus disusun. itu bermaksud mereka itu tidak diimport secara langsung dari Github - malahan *Rilis Github* digunakan.

Kapan sebuah user untuk install sebuah mod JAR, Mindustry hanya ngecek yang terbaru (dan *hanya* yang terbaru) untuk artefak `.jar`. Kapan artefak pertama ditemuka, itu diunduh ke klien. Catatan pra-rilis tidak dianggap.

Saya merekomendasikan gunakan Github Action (atau CI yang lain) untuk membangun dan mengunggah artefak jar ke rilis baru secara otomatis.

## Kapabilitas dan Keamanan

Sebagai mod jar telah memuat secara langsung ke URLClassLoader dengan tanpa sandboxing, mereka tidak memiliki beberapa kekurangan keamanan. Itu berarti:

- Semua API Java bisa diakses.
- Refleksi dapat digunakan untuk akses properti yang pribadi/tersembunyi
- Mod dapat akses penuh ke komputer milik klien, membuka pintu untuk berpotensi aksi kejahatan.
- Mod dapat mengubah file game atau menulis ulang kodebita inti

Jadi, kamu seharusnya *jangan pernah mengimpor mod jar dari sumbet tidak dipercaya.* Sekarang, kamu akan berpikir: Kenapa mod jar tidak disandbox? Itu bukan ancaman keamanan yang masif?

Jawabannya: *Ya*, tentu. Tetapi, tidak ada alternatif yang bagus. sampai jika saya mengimplementasi `SecurityManager` untuk membatasi kapabilitas mod, itu sia-sia - Java itu sebenarnya tidak aman, dan beberapa alasan-implementasi sandbox yang "aman" (*jika satupun ada*) harus membutuhkan mematikan refleksi dalam mod, itu yang tidak dapat diterima.

Sebagai poin dari perbandingan, Forge (*sebuah memuat mod java yang populer untuk Minecraft*) tidak ada mod sandbox pula.
