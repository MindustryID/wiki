# Server

Server adalah bagian besar dari Mindustry karena mereka menawarkan kemampuan untuk bermain game dengan orang lain. Ada dua jenis server utama; server khusus dan server LAN lokal.

## Server Khusus

Server khusus adalah versi game mandiri tanpa kepala yang hanya berfokus pada penyediaan sarana bagi orang-orang untuk bermain Multiplayer. Mereka biasanya dijalankan di komputer sebagai program terpisah daripada dalam game, dan dioperasikan dari terminal. Ini biasanya lebih kuat daripada server LAN lokal karena mereka memiliki lebih banyak sumber daya yang tersedia bagi mereka untuk mendukung lebih dari dua atau tiga pemain, dan dapat dijalankan 24/7. Mereka juga lebih fleksibel dan kuat karena mereka memiliki banyak perintah untuk memberikan administrator kendali lebih atasnya, dan mereka dapat dengan mudah dimodifikasi agar sesuai dengan kebutuhan administrator.

Anda dapat terhubung ke salah satunya menggunakan tombol "Gabung Game" di bawah menu "Mainkan". Tidak seperti server LAN lokal, Anda harus memasukkan alamat IP dan port host. Juga tidak seperti server LAN lokal, setelah Anda menambahkan server, itu akan secara otomatis muncul di daftar server Anda ketika Anda membukanya, dan permainan akan secara otomatis memeriksa status server.

Untuk membuat server khusus, mesin Linux atau Windows khusus ** sangat ** direkomendasikan.

1. Jika Anda belum melakukannya, instal setidaknya JRE dan JDK 8.
2. Unduh rilis server yang diinginkan dari [itch.io](https://anuke.itch.io/mindustry), atau kompilasi sendiri.
3. Buka terminal atau sesi TTY lalu ubah `cd` ke direktori tempat JAR ditempatkan.
4. Jalankan `java -jar server.jar` menggunakan Command Prompt (di Windows) atau terminal favorit Anda (di Linux dan Mac). Perintah tersebut dijelaskan dalam perintah `help`.
5. Mulai hosting peta dengan `host <mapname> [mode]` setelah Anda mengkonfigurasi server.
6. Jika Anda menggunakan Windows untuk menjalankan server Anda, gunakan mesin pencari favorit Anda untuk mencari cara menambahkan aturan ke Windows Firewall Anda, karena sebagian besar waktu memblokir port tersebut. Pastikan untuk mengizinkan ** port 6567 TCP dan UDP **.

Kecuali Anda telah mengaktifkan penerusan port, server khusus Anda hanya dapat dihubungkan oleh klien dalam jaringan lokal Anda. Jika Anda ingin membuat server Anda tersedia secara global, baca di bawah.

### Apa itu IP dan bagaimana cara mengetahui apa milik saya?

Dalam istilah yang disederhanakan, alamat IP adalah angka yang mengidentifikasi komputer Anda di internet. Anda dapat terhubung ke server Mindustry seseorang jika Anda mengetahui alamat IP mereka. Ada dua jenis; alamat ** publik ** dan ** lokal **.

- Untuk ** IP lokal **, ketika misalnya Anda ingin bermain dengan teman di jaringan yang sama seperti milik Anda, setiap perangkat memiliki caranya sendiri untuk menampilkannya. Anda dapat Google cara melakukannya untuk perangkat Anda, mis. "temukan ip lokal di Mac".
- Untuk ** IP publik **, cukup Google "what is my ip".

### Menjalankan Server Khusus di Rumah

Seringkali, inilah yang harus Anda ingat; ** jangan pernah membagikan IP publik Anda dengan publik jika Anda menghosting dari rumah, kecuali Anda mengetahui implikasinya! ** IP publik Anda terikat dengan rumah tangga Anda, dan jika jatuh ke tangan yang salah, dan kapan diletakkan di tangan yang salah, dapat membuka jaringan Anda terhadap kerentanan dan bahaya. ** Berhati-hatilah, lakukan riset, dan gunakan VPN atau host web jika memungkinkan. **

Juga direkomendasikan dan Anda menggunakan nama domain atau layanan DNS untuk menutupi IP Anda untuk server publik untuk kemudahan penggunaan, atau bahkan lebih baik, menggunakan layanan cloud, mis. Amazon AWS atau server / VM khusus dari penyedia hosting seperti Linode atau DigitalOcean, yang jauh lebih aman. ** Lakukan riset **, dan tentukan opsi mana yang paling sesuai dengan kebutuhan Anda.

1. Temukan merek / model router Anda. Ini biasanya terdapat pada stiker di bagian bawah atau belakang router.
2. Gunakan mesin pencari favorit Anda untuk mencari "port forward ASUS RT-ACRH17" dan gunakan panduan untuk mengikuti ** port 6567 TCP dan UDP **. Petunjuk ini berbeda untuk setiap router, jadi pastikan untuk membaca panduan Anda secara menyeluruh!
3. Anda dapat menggunakan layanan seperti [You Get Signal](https://www.yougetsignal.com/tools/open-ports/) untuk memeriksa apakah Anda telah melakukan portforwarding dengan benar.

## Server LAN & Uap Lokal

Server LAN atau Steam lokal adalah server yang dibangun di dalam game, dan dapat dimulai menggunakan tombol "Host Multiplayer Game" di menu dalam game. Ini dimaksudkan agar sederhana dan lugas, untuk sesi antara beberapa pemain di bawah jaringan LAN (alias di jaringan WiFi rumah tangga Anda). Ini tidak benar-benar dimaksudkan untuk beberapa pemain, karena dibutuhkan lebih banyak sumber daya dari perangkat Anda untuk dapat menggunakannya dengan cara itu; untuk itu Anda memerlukan server khusus yang disebutkan di atas. Itu hanya bisa berjalan saat permainan terbuka, dan segera dihentikan saat ditutup.

Anda dapat terhubung ke salah satunya menggunakan tombol "Gabung Game" di bawah menu "Mainkan". Tidak seperti server khusus, perangkat Anda akan secara otomatis menemukan perangkat host dan biasanya akan muncul di daftar server tanpa Anda harus memasukkan alamat IP host di.

## Perintah Server Khusus

$serverCommands

## Opsi Konfigurasi Server Khusus

$serverConfigs
