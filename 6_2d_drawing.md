## 2D Rajzolás

A Processing egyik fő erőssége a kényelmes rajzolás. Míg szinte minden más programozási
nyelvben meg kéne küzdenünk a rajzoló környezet felállításával, itt nem kell ilyennel
bajlódnunk. Nem kell belemennünk a **shader**-ek világába és nem kell átbújnunk mindenfajta
**API**-okat amik meghatároznák hogyan lehet az adott könyvtárral programozni.

**API** - Application programming interface, egy kódbázis használati felülete. Például
a p5.js API-ja minden amit a [Reference](https://p5js.org/reference/)-ben leírva találunk.
Ez a felület amit nekünk programozók számára elérhetővé tettek p5.js tervezői.

**Shader** -  Shadernek hívunk egy olyan funkciót ami meghatározott körülmények között
leírja, milyen "színűnek" kell lennie egy adott pixelnek. Egy **shader** nemcsak a dolgok
színét határozhatja meg, de legegyszerűbb így elképzelni őket.

### createCanvas

[Ez](https://p5js.org/reference/#/p5/createCanvas) lesz a függvény amit mindig pontosan egyszer
meg kell hívnunk a programunk elején, ha bármit is ki szeretnénk rajzolni a képernyőre.

```JavaScript
createCanvas(width, height, [renderer])
```

*Szögletes zárójelek függvény paramétereknél* - Opcionális paramétereket szokás
megadni szögletes zárójelek között. Ezeknek ilyen esetekben általában van egy alapértelmezett
értéke.

- **width** - A vásznunk szélessége pixelekben.
- **height** - A vásznunk magassága pixelekben.
- **renderer** - P2D vagy WEBGL. P2D az alapértelmezett és minden két dimenziós rajzolást
tesz elérhetővé. Minden 3D-s alakzathoz a WEBGL renderelő engine-t kell használjuk.

### Beállítások

### Ívek (Curves)

### Alakzatok (Shapes)

### Vertexek
