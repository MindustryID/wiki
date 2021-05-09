# Tipe

$allTypes


## BuildVisibility

Bendera yang digunakan oleh game untuk mengubah beberapa hal kasus khusus. Ini mungkin salah satu dari string berikut:

-   `hidden`
-   `shown` (default)
-   `debugOnly`
-   `sandboxOnly`
-   `campaignOnly`
-   `lightingOnly`



## BlockGroup

Grup untuk blok untuk dibangun di atas satu sama lain:

-   `none`
-   `walls`
-   `turrets`
-   `transportation`
-   `power`
-   `liquids`
-   `drills`


## ItemStack

Sebuah `ItemStack` bisa berupa string atau objek. Ini digunakan untuk mendeskripsikan jenis dan jumlah item ke sebuah mesin.

Sebagai `string`:

    copper/5

Sebagai `objek`:

    item: copper
    amount: 5

|bidang|tipe|catatan|
|---|---|---|
|item|string|Nama dari [Item] (#item).|
|amount|int|Jumlah item tersebut.|



## LiquidStack

Sebuah `LiquidStack` bisa berupa string atau objek. Ini digunakan untuk mendeskripsikan jenis dan jumlah item ke sebuah mesin.

Sebagai `string`:

    water/5

Sebagai `objek`:

    liquid: water
    amount: 5

|bidang|tipe|catatan|
|---|---|---|
|liquid|string|Nama dari [Liquid] (#liduid).|
|amount|int|Jumlah item tersebut.|


## Kategori

Kategori untuk menu bangunan:

-    `turret` Menara ofensif;
-    `production` Blok yang menghasilkan sumber daya mentah, seperti bor;
-    `distribution` Blok yang memindahkan item;
-    `liquid` Blok yang memindahkan cairan;
-    `power` Blok yang menghasilkan atau mengangkut daya;
-    `defence` Tembok dan struktur pertahanan lainnya;
-    `crafting` Blok yang membuat sesuatu;
-    `units` Blok yang membuat unit;
-    `logic` Blok yang terkait dengan operasi logika;
-    `effect` Hal untuk penyimpanan atau efek pasif.


## Color

Warna adalah string heksadesimal, `<rr> <gg> <bb>` misalnya:

- `ff0000` berwarna merah,
- `00ff00` berwarna hijau,
- `0000ff` berwarna biru,
- `ffff00` berwarna kuning,
- `00ffff` adalah cyan,
- dll.



## CacheLayer

Bendera yang digunakan oleh untuk perenderan cache:

- lapisan normal `normal`;
- lapisan dinding `wall`;
- Lapisan air `water`, menambahkan peneduh air ubin, dan memberikan pantulan gelombang;
- Lapisan tar `tar`, menambahkan shader tar, membuatnya lebih gelap dan memberinya beberapa pantulan gelembung;

## TargetPriority

Urutan yang lebih tinggi berarti prioritas yang lebih tinggi. Pemblokiran dengan prioritas lebih tinggi akan selalu ditargetkan daripada yang berprioritas lebih rendah, berapa pun jaraknya.

1.  `base`
2.  `turret`

