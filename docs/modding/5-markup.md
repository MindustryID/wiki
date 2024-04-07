# Markup

Penyaji teks digunakan bahasa markup simpel dalam perwarnaan teks.

## Warna
-   `[name]` ubah warna dari nama, mereka ada beberapa [warna bawaan](#warna-bawaan);
-   `[#rrggbb]` / `[#rrggbbaa]` ubah warna dengan nilai heks, dengan setiap semua nilai dari `00` ke `ff`:
    -   `rr` adalan nilai merah,
    -   `gg` adalan nilai hijau,
    -   `bb` adalan nilai biru,
    -   `aa` adalan nilai alfa(transparansi);
-   `[]` ubah warna dengan warna sebelumnya;
-   `[[` lolos dari branket kiri, jadi kamu bisa menulis `[[red]` untuk menulis itu akan menyajikan sebagai `[red]`.

Catatan:

-   warna error/tidak diketahui akan diabaikan secara diam-diam

Contoh:

    [red]merah
    [#ff0000]merah-penuh
    [#ff000066]setengah-merah
    [#ff000033]setengah-setengah-merah
    [#00ff00]hijau
    []setengah-setengah-merah



### Warna Bawaan

    [clear]clear
    [black]black
    [white]white
    [lightgray]lightgray
    [gray]gray
    [darkgray]darkgray
    [blue]blue
    [navy]navy
    [royal]royal
    [slate]slate
    [sky]sky
    [cyan]cyan
    [teal]teal
    [green]green
    [acid]acid
    [lime]lime
    [forest]forest
    [olive]olive
    [yellow]yellow
    [gold]gold
    [goldenrod]goldenrod
    [orange]orange
    [brown]brown
    [tan]tan
    [brick]brick
    [red]red
    [scarlet]scarlet
    [coral]coral
    [salmon]salmon
    [pink]pink
    [magenta]magenta
    [purple]purple
    [violet]violet
    [maroon]maroon

## Ikon

Ikon (lebih tepatnya emoji) adalah penyaji suatu gambar kecil pada teks, biasanya menggunakan **unicode** untuk menggunakan ikon in-game (karena mereka menggunakan font ikon untuk aset game)

ini adalah icon dari aset game `icon.ttf` dengan **Character Map**:
![alt text](/wiki/images/modding/markup/image.png)
*Catatan: kamu harus ke [sini](https://github.com/Anuken/Mindustry/tree/master/core/assets/fonts) lalu Unduh dan Pasang `icon.ttf` ke komputermu*

*Untuk Icon Item, Cairan, Blok sama Unit, menggunakan cara yang berbeda.*
