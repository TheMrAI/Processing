## Processing

A **Processing** egy nagyon kényelmesen és könnyen használható nyelv, amivel minimális
tapasztalattal, szakértelemmel is lehet valami kézzelfoghatót létrehozni. Ez a legtöbb
programozási nyelvről a legkevésbé sem mondható el. Sokukhoz heteket kell csak az
elmélettel foglalkozni mielőtt megpróbálkozhatunk valami hasznos létrehozásában.
A **Processinggel** ez nincs így, és a kezdéshez csupán csak az [Alapok](1_alapok.md) fejezetben leírtakra lesz szükségünk.

A források nyelve mind angol, mert a programozás, illetve a tudomány nyelve általánosságban
az angol. Ezért a későbbiekben érdemes az angol nyelvre fókuszálnunk, és amikor csak
tehetjük, törekedjünk minden kódot angolul írni. Ennek nem kell feltétlenül helyesnek
lennie. Ez nem igazán fontos most. A későbbiekben viszont, ha a sors ebbe az irányba tereli majd a pályánk, nagyon jól fog jönni, ha az angollal már jóban vagyunk.

Ebben a fejezetben megnézzük mi is maga a **Processing**, és mi milyen megjelenési formáját
fogjuk használni.

### Processing a nyelv
Amikor magáról a **Processing** nyelvről beszélünk, akkor az alábbit értjük: [Processing](https://processing.org/).
Minden mai nagyobb operációs rendszerhez rendelkezésre áll a fejlesztő környezetük a [Download](https://processing.org/download/)
fül alatt. Számos oktatóanyag is elérhető a weboldalon, és lényegében minden egyéb is, amit a nyelvről tudni érdemes. A legfontosabb forrás mind közül a **Referencia** lesz: [Reference](https://processing.org/reference/). Minden változótípus, operátor vagy beépített függvény megtalálható itt. Ezen felül minden funkcionalitás rendelkezik egy pontos leírással és példákkal is. A referencia lesz egy idő után minden, amire szükségünk lesz.

Ez egy kifejlett programozási nyelv, amivel lényegében mindent meg tudunk
csinálni, amit szeretnénk. Ennek hátránya a komplexitás lesz. Komplexitás a nyelvvel,
a környezettel, és a megosztással. Mi ezzel a komplexitással nem feltétlenül
szeretnénk foglalkozni, ezért inkább a [p5.js](https://p5js.org/)-el fogunk dolgozni.
Ez is *Processing*, csak egy kicsit kevésbé komplikált.

### p5.js
[p5.js](https://p5js.org/) a [Processing](https://processing.org/)-re épített
környezet, ami többek között olyan színvonalú támogatással rendelkezik, mint az eredeti
nyelv, de van egy kényelmesen használható online szerkesztő felülete, a [p5 Web Editor](https://editor.p5js.org/). Ehhez is megtalálható minden, amire szükségünk van
a [Reference](https://p5js.org/reference/) fül alatt. Bármit is szeretnénk megtudni,
ez legyen az első állomásunk.

A továbbiakban [p5 Web Editor](https://editor.p5js.org/) fogunk foglalkozni. Nyissuk is meg a felületet, ahol ez a példaprogram fog várni minket:
```JavaScript
function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(220);
}
```
Na puff. Mi ez a _function_? Egy függvény, de az előző fejezetben máshogy nézett ki egy
függvény. Volt visszatérési típusa, nem volt kiírva elé a "function". Mi ez?
Ez is ugyanaz a **Processing** belül, mint amit az előzőekben láttunk, és minden igaz az előző
fejezetből is. Csak már egy másik nyelven, a _Javascript_-en keresztül fogjuk használni.
Kicsit egyszerűbb vele dolgozni, viszont a hátérben pont ugyanazok a folyamatok
játszódnak le, amiket előzőleg is láttunk. Nézzük meg gyorsan, mi micsoda.

#### Processing és p5.js konverzió
Az alap építőelemeink ugyanazok, és ugyanazt csinálják:
- változó
- operátor
- elágazás
- ciklus
- függvény

##### Változó
Az eredeti:
```Processing
int x = 4;
float y = 2.3;
String country = "Hungary";
```
Az új:
```JavaScript
let x = 4;
let y = 2.3;
let country = "Hungary";
```

Már nem kell megadnunk egy változó típusát. Elég csak annyit írnunk **let** és
mi legyen a változó neve és kész. A típusát csupán az fogja meghatározni, milyen
értéket adunk neki! Így az előző példában:
```Processing
int x = 4;
x = 2.3; //<= hiba
x = "Hungary"; //<= hiba
```
**x**-nek nem adhatunk mást értékként, csak egész számot. Viszont a _JavaScript_-es verzióban:
```JavaScript
let x = 4; // x int típusú
x = 2.3; // x már float típusú
x = "Hungary"; // x már String
```
Ez a szabadság a típusokkal egyszerre áldás és átok. Ugyanúgy van mindennek típusa,
csak az rugalmasabb, és nem ellenőrzött. Érdemes ezt szem elött tartanunk, amikor
furcsa hibákba ütközünk, amiknek látszólag nincs értelme. Könnyen előfordulhat, hogy egy
olyan változótípuson próbáltunk egy műveletet végrehajtani, amin az nem értelmezhető.

##### Operátor és Elágazás
Jó hírem van! Itt nincs különbség.

##### Ciklus
A ciklusok is csak minimálisan különböznek:
```Processing
for(int y = 0; y < 100; ++y) {
  // valamit tevékenykedünk
}
```
Inkább:
```JavaScript
for(let y = 0; y < 100; ++y) {
  // valamit tevékenykedünk
}
```
A _while ciklus_ változatlan.

##### Függvény
Az eredetiben:
```Processing
int add(int x, int y){
  return x + y;
}
```
Az új felületen:
```JavaScript
function add(x, y){
  return x + y;
}
```
Lényegében eltűnt az összes változótípus. Míg a sima **Processingben** meg kellett
mondjuk, mik a bemeneti paraméterek és annak típusai, és mi a visszatérési érték és
annak típusa, itt már csak a műveletekkel kell csak foglalkoznunk. Illetve ki kell írjuk
a **function** kulcsszót.

### Összefoglaló
Tehát nincs valójában sok különbség. A változók és a függvények térnek el elsősorban.
Viszont sose keverjük össze a két nyelvet! Ugyan a **p5.js** is **Processingre** alapul a
hátérben, mivel más nyelv, ezért nem minden érhető el, illetve nem ugyanúgy, mint az eredetiben.
Mindig a megfelelő referenciát kutassuk:
 - [Processing Reference](https://processing.org/reference/)
 - [p5.js Reference](https://p5js.org/reference/)

 ### Hogyan tovább
 Most, hogy tudjuk mi a **Processing** és mi a **p5.js**, és mik a különbségek köztük, csináljunk
 is végre valamit.

 [Példaprogram és a szerkesztő](3_editor.md)
