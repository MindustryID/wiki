# Markup

Penyaji teks menggunakan bahasa markup sederhana untuk mewarnai teks.

- `[name]` menyetel warna berdasarkan nama, ada beberapa [warna bawaan] (# warna bawaan);
- `[#rrggbb]` / `[#rrggbbaa]` menyetel warna menurut nilai hex, dengan setiap nilai menjadi apa saja dari `00` hingga` ff`:
    - `rr` adalah nilai merah,
    - `gg` adalah nilai hijau,
    - `bb` adalah nilai biru,
    - `aa` adalah nilai alpha;
- `[]` menyetel warna kembali ke warna sebelumnya;
- `[[` mengesampingkan tanda kurung kiri, jadi Anda bisa menulis `[[merah]` untuk menulis dan itu akan dirender sebagai `[merah]`.

Catatan:

- kesalahan / warna yang tidak diketahui akan diabaikan secara diam-diam.

Contoh:

    [red]red
    [#ff0000]full-red
    [#ff000066]half-red
    [#ff000033]half-half-red
    [#00ff00]green
    []half-half-red



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
