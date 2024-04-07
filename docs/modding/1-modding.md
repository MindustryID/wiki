
# Intruksi Modding

Mod Mindustry adalah lebih simpel direktori dari aset. mereka ada banyak cara untuk menggunakan API modding, tergantung dalam tepatnya apa yang kamu inginkan untuk dilakukan, dan seberapa jauh kamu menginginkan itu melakuan itu 

Kamu harus hanya resprite konten yang udah ada di game, kamu bisa bikin konten game dengan JSON API yang dipermudah (yang mana itu fokus utama dalam dokumentasi), kamu dapat menambahkan suara kustom (atau menggunakan lagi yang udah ada). itu mungkin untuk menambahkan peta kedalam mode kampanye, dan nambahan skrip untuk memogran kebiasaan special dalam modmu, seperti efek kustom.

Membagikan modmu itu mudah seperti memberi seseorang direktori projekmu; mod juga cross-platform ke beberapa platform yang mendukung itu. Kamu ingin menggunakan [GitHub](#github) (*atau layanan yang serupa, seperti; gitbucket sama gitlab*) untuk melayankan kode sumbermu.
Untuk membuat mod semua yang kamu diperlukan adalah sebuah komputer dengan penyunting teks.


## Struktur Direktori

Direktori projekmu seharusnya terlihat seperti ini:

    project
    ├── mod.hjson
    ├── content
    │   ├── items
    │   ├── blocks
    │   ├── liquids
    │   └── units
    ├── maps
    ├── bundles
    ├── sounds
    ├── schematics
    ├── scripts
    ├── sprites-override
    └── sprites

-   `mod.hjson` (required) file metadata untuk modmu,
-   `content/*` direktori untuk [Konten](#konten),
-   `maps/` direktori untuk peta dalam-game,
-   `bundles/` direktori untuk [Bundle](#bundles),
-   `sounds/` direktori untuk [Suara](#suara) files,
-   `schematics/` direktori untuk [Skematik](#skematik) files,
-   `scripts/` direktori untuk [Skrip](#skrip),
-   `sprites-override/` [Sprites](#sprites) Direktori untuk menimpa konten dalam-game,
-   `sprites/` [Sprites](#sprites) Direktori untuk kontenmu,

Setiap platform memiliki direktori data user aplikasi, dan itu dimana modmu seharusnya diletakan:

-   Linux: `~/.local/share/Mindustry/mods/`
-   Steam: `steam/steamapps/common/Mindustry/mods/`
-   Windows: `%appdata%/Mindustry/mods/`
-   MacOS: `~/Library/Application Support/Mindustry/mods/`

*Catatan nama filemu seharusnya tidak kapital dan tanda penghubung dipisahkan:*

-   benar: `my-custom-block.json`
-   salah: `My Custom Block.json`


## Hjson

Mindustry gunakan [Hjson](https://hjson.org/), yang mana untuk seseorang siapa tahu json, itu sesimpel sebuah superset dari bahasa yang diserialisasi sangat populer diketahui sebagai [Json](https://en.wikipedia.org/wiki/JSON). &#x2013; Itu berarti itu beberapa json yang valid akan bekerja, tetapi kamu memiliki hal ekstra yang berguna:

    # single line comment
    
    // single line comment
    
    /* multiline
    comment */
    
    key1: single line string
    
    key2:
    '''
    multiline
    string
    '''
    
    key3: [ value 1
            value 2
            value 3 ]
    
    key4: { key1: string
            key2: 0 }

Jika kamu gak tau beberapa kata itu. &#x2013; Sebuah bahasa serialisasi, adalah sesimpel sebuah bahasa yang mengodekan informasi untuk sebuah program, dan *encode* berarti untuk menerjemahkan suatu informasi dari satu bentuk ke bentuk lain, dan dalam kasus ini, untuk menerjemahkan teks kedalam struktur data Java.



## `mod.hjson`

Pada akar dari direktori projekmu, kamu harus memiliki satu `mod.json` yang mana menjelaskan metadata dasar untuk projekmu. File ini dapat juga (secara opsional) dinamakan `mod.hjson` untuk berpotensi membantu kamu penyunting teks memilih penebalan sintaks yang baik.

    name: "mod-name"
    displayName: "This isn't a mod."
    author: Yourself
    description: "Bbfashbjhcbabfhsbafbhajbf"
    version: "1.0"
    minGameVersion: "$latestRelease"
    dependencies: [ ]
    hidden: false

-   `name` akan digunakan untuk referensi pada modmu, jadi berhati-hati dalam penamaan;
-   `displayName` adalah yang akan digunakan sebagai nama yang ditampilkan untuk UI, yang mana kamu bisa gunakan menambahkan *formating* untuk menyebutan nama;
-   `description` pada mod akan disajikan di manajer mod dalam game, jadi tetap itu pendek dan ke intinya;
-   `dependencies` adalah opsional, jika kamu ingin tahu lebih lanjut, pergi ke bagian[dependensi](#dependensi);
-   `minGameVersion` adalah minimum versi build pada game, Ini **Diperlukan** kepada angka yang lebih besar daripada 105.
-   `hidden` adalah apakah atau tidak mod ini essensial untuk multiplayer, false secara default. Texture packs, Plugin JS, dll. Seharusnya gunakan ini sebagai tidak terjadinya konflik dengan server dan klien secara respektif. sebagai aturan prakis, jika modmu membuat konten itu seharusnya tiak jadi tersembunyi


## Konten

Pada akar dari direktori projekmu kamu bisa memiliki satu direktori `content/`, ini dimana semua data Json/Hjson berada. Didalam `content/` kamu memiliki subdirektori untuk macam-macam konten, mereka adalah yang satu-satunya umum saat ini:

-   `content/items/` untuk [items](#item), seperti `copper` dan `surge-alloy`;
-   `content/blocks/` dan [blocks](#block), seperti turrets and floors;
-   `content/liquids/` dan [liquids](#liquid), seperti `water` and `slag`;
-   `content/units/` untuk [units](#unittype) udara atau darat, seperti `eclipse` dan `dagger`;

Note that each one of these subdirectories needs a specific content type. The filenames of these files is important, because the stem name of your path *(filename without the extension)* is used to reference it.

Furthermore the files within these `content/<content-type>/*` directories may be arbitrarly nested into other sub-directories of any name, to help you organize them further, for example:

-   `content/items/metals/iron.hjson`, which would respectively create an item named `iron`.

The content of these files will tend to look something like this:

    type: TypeOfThing
    name: Name Of Thing
    description: Description of thing.
    # ... more fields here ...

|field|type|notes|
|---|---|---|
|type|String|Content type of this object.|
|name|String|Displayed name of content.|
|description|String|Displayed description of content.|

Other fields included will be the fields of the type itself.

A side note, `name` and `description` are not required to be in the json structure. You can define them for any language with (Bundles)[#bundles]. However, if they are not present in either then the name will be <type>.<modname>-<stemname>.name and an empty description respectively.



## Types

Types have numerous fields, but the important one is `type`; this is a special field used by the content parser, that changes which type your object is. *A `Router` type can't be a `Turret` type*, as they're just completely different.

Types *extend* each other, so if `MissileBulletType` extends `BasicBulletType`, you'll have access to all the fields of `BasicBulletType` inside of `MissileBulletType` like `damage`, `lifetime` and `speed`. Fields are case sensitive: `hitSize =/= hitsize`.

What you can expect a field to do is up to the specific type, some types do absolutely nothing with their fields, and work mostly as a base types will extend from. One such type is `Block`.

In this unit example, the type of the unit is `flying`. The type of the `bullet` is `BulletType`, so you can use `MissileBulletType`, because `MissileBulletType` extends `BulletType`.

One could also use `mech`, `legs`, `naval` or `payload` as the unit type here.

```hjson
type: flying
weapons: [
  {
    bullet: {
      type: MissileBulletType
      damage: 9000
    }
  }
]
```

As of build `125.1`, types can also be the *fully-qualified class name* of a Java class. 

For example, to specify a block as a `MendProjector`, you may write
`type: mindustry.world.blocks.defense.MendProjector` instead of `type: MendProjector`.

While not particularly useful for vanilla types, this can be used to load block types *from other Java mods* as dependencies.

## Tech Tree

Much like `type` there exist another magical field known as `research` which can go at the root of any block object to put it in the techtree.

    research: duo

This would put your block after `duo` in the techtree, and to put it after your own mods block you would write your `<block-name>`, a mod name prefix is only required if you're using the content from another mod.

Research costs:

|type|cost|notes|
|---|---|---|
|blocks|`requirements ^ 1.1 * 20 * researchCostMultiplier`|`researchCostMultiplier` is a stat that can be set on blocks|
|units|`requirements ^ 1.1 * 50`|---|

The cost is then rounded down to the nearest 10, 100, 1k, 10k, or 100k depending on how expensive the cost is.

`requirements` is the cost of the block or unit. Units use their build cost/upgrade cost for the calculations.

If you want to set custom research requirements use this object in place of just a name:

    research: {
      parent: duo
      requirements: [
        copper/100
      ]
    }

This can be used to override block or unit costs, or make resources need to be researched instead of just having to produce it.

## Sprites

All you need to make sprites, is an image editor that supports transparency *(aka: not paint).* Block sprites should be `32 * size`, so a `2x2` block would require a `64x64` image. Images must be PNG files with a 32-bit RGBA pixel format.
**Any other pixel format, such as 16-bit RGBA, may cause Mindustry to crash with a "Pixmap decode error".** You can use the command-line tool `file` to print information about your sprites:

    file sprites/**.png

If any of them are not 32-bit RGBA formatted, fix them.

Sprites can simply be dropped in the `sprites/` subdirectory. The content parser will look through it recursively.
Images are packed into an "atlas" for efficient for rendering. The first directory in `sprites/`, e.g. `sprites/blocks`, determines the page in this atlas that sprites are put in. Putting a block's sprite in the `units` page is likely to cause lots of lag; thus, you should try to organize things similarly to how the [vanilla game does](https://github.com/Anuken/Mindustry/tree/master/core/assets-raw/sprites).

Content is going to look for sprites relative to it's own name. `content/blocks/my-hail.json` has the name `my-hail` and similarly `sprites/my-hail.png` has the name `my-hail`, so it'll be used by this content.

Content may look for multiple sprites. `my-hail` could be a turret, and it could look for the suffix `<name>-heat` and what this means is it'll look for `my-hail-heat`.

You can find all the vanilla sprites here:

-   <https://github.com/Anuken/Mindustry/tree/master/core/assets-raw/sprites>

Another thing to know about sprites is that some of them are modified by the game. Turrets specifically have a black border added to them, so you must account for that while making your sprites, leaving transparent space around turrets for example: [Ripple](https://raw.githubusercontent.com/Anuken/Mindustry/master/core/assets-raw/sprites/blocks/turrets/ripple.png)

To override ingame content sprites, you can simply put them in `sprites-override/`.
This removes the `<modname>-` prefix to their id, which allows them to override sprites from vanilla and even other mods.
You can also use this to create sprites with nice short names like `cat` for easy use with scripts, just beware of name collisions with other mods.



## Sound

Custom sounds can be added through the modding system by dropping them in the `sounds/` subdirectory. It doesn't matter where you put them after that. Two formats are supported: `ogg` and `mp3`. Note that `mp3` files cannot loop seamlessly, so try to use `ogg` whenever possible.

Just like any other assets, you reference them by the stem of your filenames, so `pewpew.ogg` and `pewpew.mp3` can be referenced with `pewpew` from a field of type `Sound`.

Here's a list of built-in sounds:

$sounds

## Dependencies

You can add dependencies to your mod by simple adding other mods name in your `mod.json`:

    dependencies: [
      other-mod-name
      not-a-mod
    ]

The name of dependencies are lower-cased and spaces are replaced with `-` hyphens, for example `Other MOD NamE` becomes `other-mod-name`.

To reference the other mods assets, you must prefix the asset with the other mods name:

-   `other-mod-name-not-copper` would reference `not-copper` in `other-mod-name`
-   `other-mod-name-angry-dagger` would reference `angry-dagger` in `other-mod-name`
-   `not-a-mod-angry-dagger` would reference `angry-dagger` in `not-a-mod`



## Bundles

An optional addition to your mod is called bundles. The main use of bundles are give translations of your content, but there's no reason you couldn't use them in English. These are plaintext files which go in the `bundles/` subdirectory, and they should be named something like `bundle_ru.properties` (for Russian).

The contents of this file is very simple:

    block.example-mod-silver-wall.name = Серебряная Стена
    block.example-mod-silver-wall.description = Стена из серебра.

If you've read the first few sections of this guide, you'll spot it right away:

-   `<content type>.<mod name>-<content name>.name`
-   `<content type>.<mod name>-<content name>.description`

With your own custom bundle lines for use in scripts you can use whatever key you like:

-    `message.egg = Eat your eggs`
-    `randomline = Random Line`

Notes:

-   mod/content names are lowercased and hyphen separated.

List of content types:

$contentTypes

List of bundle suffixes relative to languages:

$bundles


## GitHub

Once you have a mod of some kind, you'll want to actually share it, and you may even want to work with other people on it, and to do that you can use [GitHub](https://github.com/). If you don't know what Git (or GitHub) is at all, then you should look into [GitHub Desktop](https://desktop.github.com/), otherwise simply use your favorite command line tool or text editor plugin. 

All you need understand is how to open repositories on GitHub, stage and commit changes in your local repository, and push changes to the GitHub repository. Once your project is on GitHub, there are three ways to share it:

-   with the endpoint, for example `Anuken/ExampleMod`, which could then be typed in the ingame GitHub interface, and that would download it;
-   with the zip file, for example `https://github.com/Anuken/ExampleMod/archive/master.zip`, which would download the repository as a zip file, and put in mod directory (unzipping is not required);
-   add the topic/tag `mindustry-mod` on your repository, which should add it to the topic search and the [Mod scraper](https://github.com/Anuken/MindustryMods).



## FAQ

-   `time` in game is calculated through `ticks`;
-   `ticks` *sometimes called `frames`,* are assumed to be 1/60th of a second;
-   `tilesize` is 8 units internally;
-   to calculate range out of `lifetime` and `speed` you can do `lifetime * speed = range`;
-   *Abstract* what is `abstract`? All you need to know about abstract types is that they cannot be instantiated/initialized by themselves. If you do so, you'll  get an *"initialization exception"* of some kind;
-   what is a `NullPointerException`? This is an error message that indicates a field is null and shouldn't be null, meaning one of the required fields may be missing;
-   *bleeding-edge* what is `bleeding-edge`? This is the developer version of Mindustry, specifically it's refering to the Github master branch. Changes on bleeding-edge usually make it into Mindustry in the next release.


