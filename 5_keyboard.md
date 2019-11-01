## Programozás alapjai

A billentyűzet is elengedhetetlen része a számítógépeknek. Az idők kezdetén
amikor még csak zsenik és az ufók értettek a számítástechnikához, na akkor is,
billentyűzetet használtak! Lássuk mit tudunk a p5.js segítségével elérni.

### Globális változók (Global variables)

Az egér kezeléshez hasonlóan a billentyűzethez is elérhetőek előre definiált globális
változók.
 - **keyIsPressed** - Egy tetszőleges billentyű le van e nyomva vagy sem.
 - **key** - A legutolsó alkalommal lenyomott billentyű.
 - **keyCode** - A legutolsó alkalommal lenyomott billentyű kódja.

Próbáljuk ki az alábbi programocskát. Nyomkodjuk a billentyűket és figyeljük mit
látunk a kimeneten.
- Mit látunk ha egy sima karaktert nyomunk le? Pl.: a
- Mit látunk ha egy nagy betűt gépelünk be? Pl.: F
- Mi lesz ha a nyíl billentyűket vagy épp a space-t nyomjuk le?

Hasonlóan meg tudjuk egy kicsit talán még szemléletesebben tekinteni a *key* és *keyCode*
különbségeket az alábbi oldalon: [Keycode](http://keycode.info/).

```JavaScript
function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(220);
  if(keyIsPressed){
    print("key: " + key + " keyCode: " + keyCode);
  }
}
```

A *key*-ben mindig megjelenik az aktuális billentyű a megszokott szöveges formában
Pl.: a, b, Shift, ArrowUp.

A *keyCode* pedig egy szám kódot ír ki minden billentyűre, például a fenti billentyűkhöz:
65, 66, 16, 38.

Érdekes módon ha lenyomjuk a Shift-et és közben írunk valamit akkor látjuk, igen ahogy megszoktuk
nagy betűt látunk a *key*-ben, de a *keyCode* ugyan az maradt! Miért van ez?

#### Billentyűzet és a kiosztásai

Talán először futottunk bele a hardware és a szoftver közötti különbségekbe és ezt jól
szimbolizálja a fenti példa. Lényegében a billentyűzet nem más mint gombok egy halmaza amiket
több fajta méretben tudunk elérni mint pl.: 105, 104, 86, 61 vagy 44 gombbal. Ezeknek a gomboknak
van egy fizikai helye magán a billentyűzeten, amit le tudunk kódolni valamilyen számmá. Így
amikor fizikailag lenyomunk egy billentyűt a gép abból valójában nem lát mást csak ezt a kódot. Ez a pontos
kód rengeteg mindentől függ, de számunkra csak az a lényeges, hogy ezek a kódok a hardware-től
függenek.
A *key* viszont egy kicsit több ennél. A *key* már egy a gép általi értelmezése ennek a *keyCode*-nak.
Ezt az értelmezést befolyásolja  mondjuk hogy lenyomtuk e a Shift-et. A beállított nyelv is befolyásolja mi lesz
a pontos értelmezése. Sőt még azt is megváltoztatja mi lesz a *keyCode*! Ez pedig azért lesz, mert
az operációs rendszerünk (Windows, Mac, Linux) tudja milyen fizikai kiosztással szokott rendelkezni
például egy magyar és egy angol billentyűzet.

Magyar:

![Magyar](hun-keyboard.png)

Angol:

![Angol](en-us-keyboard.png)

Nézzük egy az alábbi példán hogy alakulnak a *key* és *keyCode*-ok a nyelvi beállítástól
függően:

Magyar (HU) |-| Angol (ENG) |-  
 ------------ | ------ | ---------- | -------
 *key* | *keyCode* | *key* | *keyCode*
 q|81|q|81
 a|65|a|65
 í|220|\\|220
 ,|188|,|188
 -|173|/|191
 ö|192|0|48

A fenti példában pontosan ugyan azokat a fizikai billentyűket nyomtam le mind a két
nyelvi beállításnál. Valahol ott volna ugyan az a fizikai gomb mint a két nyelvnél
valahol nem. Ettől függően vagy ugyanaz a *keyCode* vagy nem.

Ezzel a hétköznapokban nem kell foglalkoznunk. Ezt a gép mind elvfedi eldőlünk.
Viszont érdemes észben tartanunk ha valamilyen problémába ütközünk ami nem tűnik
lehetségesnek.

### Események (Events)
 - **keyPressed()**
 - **keyReleased()**
 - **keyTyped()**
 - **keyIsDown()**
