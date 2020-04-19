## Programozás alapjai

### Bevezető

Első ránézésre a programozás igen bonyolultnak tűnhet. Aztán még pár évig az is
fog maradni, amíg az ember meg nem ismerkedik három-négy különböző fajtával, és rá
nem jön: az összes pont ugyanazt csinálja, csak egy kicsit másképp néznek ki.
Persze szigorúan tekintve ez sem igaz, de mint minden, ami már elég bonyolult ahhoz,
hogy karriert lehessen belőle építeni, itt sem érdemes elmerülni a részletekben
mindjárt az elején. Éppen ebből kifolyólag elhallgatásra fog kerülni minden olyan
részlet, ami nem feltétlenül fontos az adott témakör megértéséhez. Ezt a hozzáállást
javasolnám az olvasóknak is. *Elégséges mindig csak annyira megérteni a dolgok mikéntjét,
amennyire az adott probléma megoldásához szükséges.* Egy feladat megoldását is a feladat
szintjén kell megtenni. Egyébiránt hamar rá fogunk jönni: minden lehet elég komplikált,
hogy aztán végül azt se tudjuk, merre tegyük meg az első lépést...

### Hozzáállás

Kiből lesz egy jó programozó? Abból, aki minél korábban rájön, valójában
milyen keveset is tud, és erre folyamatos fejlődési lehetőségként tekint. Lássuk be,
mindnyájan emberek vagyunk. Ebből kifolyólag nem tudunk
mindig mindenre odafigyelni, valamikor fáradtabbak vagyunk, mint máskor és néha nem
is akarunk foglalkozni vele, bármi is legyen a feladat. Ezért nem kell mindent tökéletesen
csinálni, és nem kell különösebben foglalkozni vele, hogyan lehetett volna valamit jobban
megoldani. Ahogy telnek majd a hetek és visszatekintünk a korábbi munkáinkra, szinte
mindig szörnyülettel fog elfogni minket a gondolat: "Te jó ég, hogy tudtam ilyen butaságot
leírni!". Ez a szép az egészben. Bármennyit is tanulunk meg, mindig fogjuk tudni
jobban és jobban csinálni, pont ezért nem szabad leragadni a mostban, hanem menni kell előre.

### Alapok

Ebben megismerkedünk az alap fogalmakkal, amik szükségesek ahhoz, hogy egy programról
el tudjunk kezdeni beszélni.

Magasból tekintve programozni pont olyan, mint LEGO<sup>TM</sup>-zni. Egyszerű építőelemeink
vannak, amelyeket megfelelő sorrendben összerakva lényegében mindent meg tudunk csinálni.
A feladatunk megtanulni, milyen építőelemeink vannak, és azokkal hogyan tudjuk a gép számára
megfogalmazni, mit is szeretnénk.

Az alap építőelemeink:
- változó
- operátor
- elágazás
- ciklus
- függvény

Ezek mind kifejezések, amiket bonyolultabb kifejezésekbe rendezünk, amelyeket a számítógép szépen
sorban végrehajt. A kifejezéseknek számos csoportja van, de lényegében minden sor utasítás
amit leírtunk a gép számára, valamilyen kifejezés lesz.

##### Változó (Variable)
```Processing
int x;
```
Egy _x_ nevű változó, aminek a típusa _int_, azaz _integer_, vagyis egy egész szám.
Kezdeti értéke a *Processing*-ben nem ismert. Más nyelvekben lehet nulla, vagy valamilyen
egyéb érték.

Egy változót létre tudunk hozni, ki tudunk értékelni, és a rajta értelmezett műveletekkel
tudunk módosítani. Célja egy érték tárolása.
```Processing
int x; //x értékét nem tudjuk
x = 3; //x értéke 3
x = x + 2; //x értéke már 5
x = 0; //x már nulla
```

Számtalan változótípus van, amelyeket sok-sok csoportba tudunk rendezni és amelyekbe
jelenleg nincs szükségünk belemenni.

##### Operátor (Operator)
Operátornak hívunk minden olyan kifejezést, amit egy adott változótípuson el lehet végezni.
```Processing
x = 3; //egyenlővé tétel operátor
x = x + 2; //összeadás és egyenlővé tétel operátor
```

Egy integer típusú változón számos operátort tudunk végrehajtani. Fentebb láttuk az összeadás
és az egyenlővé tétel operátorait és a matematikából ismert alap operátorok is rendelkezésre
állnak. Kivonás _(-)_, szorzás _(\*)_, osztás _(/)_, stb. A pontos lista mindig az adott típustól fog függeni.
Egy operátornak 1 vagy több paramétere van, és kiértékelésének lesz egy adott következménye vagy éppen
következményei.

A _+_ operátor két paraméterű. Van egy bal oldali (left hand side) és egy jobb oldali (right hand side)
paramétere. A kiértékelésének eredménye a két oldal összege lesz. Pl.: _3+2 => 5_

Az _=_ operátor úgyszintén két paraméterű. Annyi megkötése van, hogy a bal oldalán egy olyan változó
kell álljon, ami fel tudja venni értékként a jobb oldalon szereplő értéket. Pl.: _int x = 2_

Aztán van a kisebb _>_ operátor, ami megint csak két paraméterű. Viszont ez csak egy igaz hamis
értékkel tud visszatérni. A bal oldalon szereplő érték nagyobb, mint a jobb oldalon lévő? Akkor igaz, ha
nem akkor hamis. Pl.: _3 > 5 => hamis (false)_

##### Elágazás (Conditional)
Egy elágazás egy olyan kifejezés amivel "ha ez teljesül, akkor történjék ez" feltételeket
tudunk megfogalmazni.

```Processing
int x;
x = 3;
if (x > 5) {
  // x értéke több mint 5, csináljunk valamit
}
else {
  // x értéke kisebb vagy egyenlő 5-el, csináljunk valami mást
}
```
Lényegében azt fogalmaztuk meg: "Ha x nagyobb mint öt, akkor csináljunk valamit,
egyébként csináljunk valami mást."
Kicsit részletekbe menően: ha a > operátor x-en és 5-ön kiértékelve igazat add, akkor
csináljunk valamit, egyébként (else) csináljunk valami mást.

##### Ciklus (Loop)
Egy olyan iterációs kifejezés, ahol egy adott kifejezés sorozatot adott kifejezés teljesüléséig
szeretnénk újra és újra végrehajtani.
Két fő fajta ciklus van:
- for
- while

A _for ciklust_ tipikusan olyan helyzetekben alkalmazzuk, amikor egy adott művelethalmazt
megadott darab alkalommal szeretnénk végrehajtani.
Három elemből áll: kezdő kifejezés, megállási feltétel, iterációs kifejezés
```Processing
for(int y = 0; y < 100; ++y) {
  // valamit tevékenykedünk
}
```
Azaz _y_ induljon nulláról, fussunk, amíg _y_ értéke kisebb, mint száz, minden végrehajtás
végén növeljük az értékét eggyel. Tehát 0-ról indulva egészen 99-ig egyesével nő majd
_y_ értéke, miközben valamit tevékenykedünk.

A _while ciklus_ egy speciális _for ciklus_, ahol a _for ciklus_ három eleméből csak a középső
(a megállási feltétel) szerepel. Ezt kényelmi okokból használjuk, de legegyszerűbb az előző
példán szemléltetni. Először is írjuk át a _for ciklust_ egy pontosan ugyanazt jelentő, de más
alakra:
```Processing
int y = 0;
for(;y < 100;){
  // valamit tevékenykedünk
  ++y;
}
```
Ez while ciklussal kifejezve:
```Processing
int y = 0;
while(y < 100){
  // valamit tevékenykedünk
  ++y;
}
```

Mind a kettőnek megvan a helye és idővel tudni fogjuk melyik és hol lesz a megfelelő választás.

##### Függvény (Function)

Függvénynek nevezzük egy kifejezéssorozat nevesített halmazát. Egy függvénynek lehet 0 vagy több
bemeneti paramétere, illetve pontosan 1 visszatérési értéke.
```Processing
int add(int x, int y){
  return x + y;
}
```
A fenti egy összeadás függvény, amely paraméterként vár két int típusú értéket, ezeket x és y
változó értékeibe másolja, majd meghívva rajtuk az összeadás operátort visszatér (return)
az eredménnyel.

Függvényeket tudunk mi is csinálni, illetve a későbbiekben sok beépített függvényt
fogunk használni. Mint például a print, println, text, stroke etc...

### Hogyan tovább
Ez az összes fogalom, amit egy hosszú ideig ismerni érdemes.
Amíg ezek a fogalmak ülepszenek, megismerkedhetünk a Processing nyelv általunk
alkalmazott formájával: a *p5.js*-el.
