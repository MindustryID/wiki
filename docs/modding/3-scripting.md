# Scripting
Mindustry menggunakan Javascript untuk *mod scripting*. Skrip gunakan ekstensi `js` dan diletakan kedalam subdirektori `scripts/`.

Eksekusi dimulai dengan file bernama `main.js`. file skrip yang lain dapat diimpor dengan file utama dengan `require("script_name")`. 

setup secara tipikal terliat seperti ini:

*scripts/main.js*:
```js

require("blocks");
require("items");

```

*scripts/blocks.js*:
```js
const myBlock = extend(Conveyor, "terrible-conveyor", {
  // various overrides...
  size: 3,
  health: 200
  //...
});
```

*scripts/items.js*:
```js

const terribleium = Item("terribleium");
terribleium.color = Color.valueOf("ff0000");
//...

```

# Contoh

## Mendengarkan suatu Event(Acara)

<img src="/wiki/images/misc/modding-pathetic.gif">

```js

// Mendengarkan acara tentang unit telah hancur
Events.on(UnitDestroyEvent, event => {
  // Menampilakn toast diatas layar yang bertulisan "Pathetic."
  if(event.unit.isPlayer()){
    Vars.ui.hudfrag.showToast("Pathetic.");
  }
})

```

Cara yang gampang untuk mencari event yang kau dapat didengar untuk itu dengan lihat file sumber: [Mindustry/blob/master/core/src/mindustry/game/EventType.java](https://github.com/Anuken/Mindustry/blob/master/core/src/mindustry/game/EventType.java)

## Menampilkan kotak Dialog

```js
const myDialog = new BaseDialog("Dialog Title");
// Add "go back" button
myDialog.addCloseButton();
// Add text to the main content
myDialog.cont.add("Goodbye.");
// Show dialog
myDialog.show();
```

## Memainkan suatu musik kustom

Memainkan audio kuston itu mudah, menyediakan kamu untuk menyimpan klip suaramu sebagai file `.mp3` atau `.ogg` dalam direktori `/sounds` mu.

Untuk contoh, kita telah menyimpan `example.mp3` di `/sounds/example.mp3`.
For this example, we have stored `example.mp3` at `/sounds/example.mp3`.

### Gunakan sebuah pustaka untuk memuat suara

*scripts/alib.js*:
```js
exports.loadSound = (() => {
    const cache = {};
    return (path) => {
        const c = cache[path];
        if (c === undefined) {
            return cache[path] = loadSound(path);
        }
        return c;
    }
})();

```

*scripts/main.js*:

```js
const lib = require("alib");

Events.on(WaveEvent, event => {
    // loads example.mp3
    const mySound = lib.loadSound("example");
    // engine will spawn this sound at this location (X,Y)
    mySound.at(1, 1);
})
```

//TODO test these out and add more examples