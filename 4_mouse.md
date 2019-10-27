## Egér kezelés

A billentyűzeten kívül az egér az egyik legfontosabb beviteli eszközünk. Nélküle számtalan feladat jóval körülményesebb lenne mint amennyire az muszáj volna. Például nem is volna grafikus felületünk az egér nélkül. Ugyanis ha nincs mivel rákattintanunk egy ikonra akkor nincs jelentősége az ikonoknak. Nem volna asztalunk ahonnét meg tudnánk
nyitni a böngészőt, el tudnánk indítani egy videót. Mindent be kéne gépelnünk, ami felettébb fárasztó lenne.

### Globális változók (Global variables)

A Processing számos információt tesz igen kényelmesen elérhetővé az alábbi globális változók segítségével:
- **mouseX** - Az egér aktuális X koordinátája a vásznon.
- **mouseY** - Az egér aktuális Y koordinátája a vásznon.
- **pmouseX** - Az egér előző X koordinátája a vásznon.
- **pmouseY** - Az egér előző Y koordinátája a vásznon.
- **winMouseX** - Az egér aktuális X koordinátája a képernyőn.
- **winMouseY** - Az egér aktuális Y koordinátája a képernyőn.
- **pwinMouseX** - Az egér előző X koordinátája a képernyőn.
- **pwinMouseY** - Az egér előző Y koordinátája a képernyőn.
- **movedX** - Az egér X irányú elmozdulása az előző kirajzolás óta.
- **movedY** - Az egér Y irányú elmozdulása az előző kirajzolás óta.
- **mouseButton** - Melyik egér billentyű van lenyomva.
- **mouseIsPressed** - Az egér valamelyik billentyűje le van nyomva.

#### mouseX, mouseY, pmouseX, pmouseY
Mouse nevű változók az aktuális, míg a p-vel prefixelt pmouse (previous mouse) változók az előző egér pozíciót adják.
```JavaScript
function setup() {
  createCanvas(400, 400);
  stroke(255, 0, 0);
}

function draw() {
  background(220);
  line(mouseX, mouseY, pmouseX, pmouseY);
}
```

Minden egyes kirajzoláskor látni fogunk egy vonalat aminek az egyik pontja az egér
aktuális pozíciója lesz, míg a másik az előző kirajzolás idejekor felvett egér pozíció.
Pew, pew, kicsit Star Wars&trade;-os lézerharc érzésem van tőle.

#### winMouseX, winMouseY, pwinMouseX, pwinMouseY

Ezekkel nem a vásznunkon lévő egér pozíciót láthatjuk. Hanem az egész képernyő szempontjából értendő egér koordinátákat. A kettő közti különbséget az alábbi programocska szemlélteti.
```JavaScript
function setup() {
  let canvas = createCanvas(400, 400);
  canvas.position(100, 100);
}

function draw() {
  background(220);
  print("mouseX: " + mouseX + " mouseY: " + mouseY);
  print("winMouseX: " + winMouseX + " winMouseY: " + winMouseY);
}
```
Lássuk mi is történik. Először is létrehoztunk egy változót **canvas** néven.
Ennek értékül adtuk a szokásos módon létrehozott vásznunkat. Így magát a vásznat is
arrébb tudtuk tolni 100-al az X és Y tengely mentén. Ha kipróbáljuk a fenti programot
megfigyelhetjük, hogy **mouseX**, **mouseY** negatív értékeket is felt tud venni egészen -100-ig. Pont ennyivel toltuk el a vásznunkat is.
Nyilvánvalóan ha a vásznunkat nem bolygatjuk akkor mouse és winMouse ugyan azokat az értékeket fogja mutatni.

#### movedX, movedY
Ez a két változó jelenleg nem elérhető, de működésük ekvivalens kell legyen azzal mintha
kivonnánk egymásból a megfelelő **mouse** és **pmouse** párt.
```JavaScript
function setup() {
   createCanvas(400, 400);
}

function draw() {
  background(220);
  print("mouseX-pmouseX: " + (mouseX-pmouseX) + " mouseY-pmouseY: " + (mouseY-pmouseY));
  print("movedX: " + movedX + " movedY: " + movedY);
}
```

#### mouseIsPressed, mouseButton
Magukban nem különösebben hasznosak, hanem majd a későbbi eventeknél lesz nagyobb szerepük.
```JavaScript
function setup() {
   createCanvas(400, 400);
}

function draw() {
  background(220);
  if (mouseIsPressed){
    if (mouseButton === LEFT){
      print("BAL");
    }
    if (mouseButton === CENTER){
      print("KÖZÉP");
    }
    if (mouseButton === RIGHT){
      print("JOBB");
    }
  }
}
```
Lényegében segítenek az egér állapotának a megismerésében. A **mouseIsPressed** igaz
ha valamelyik egér gomb le lett nyomva. Ha igaz, akkor a **mouseButton**-ból ki tudjuk
olvasni melyik gomb lett lenyomva.

Az egerünk lehet több gombos is, de a p5.js csak ezt a fenti három gombot támogatja.

#### Globális változók csapdája
Mint mondtam ezek globális változók amiket számunkra előre feltölt mindig értékekkel
a p5.js és mivel minden változót tetszőlegesen meg tudunk változtatni, igen könnyen meg tudjuk változtatni az egyes változók értelmét.

```JavaScript
function setup() {
   createCanvas(400, 400);
}

function draw() {
  background(220);
  let mouseX = 30;
  line(mouseX, mouseY, pmouseX, pmouseY);
}
```
Ennél még érdekesebb ha mondjuk azt mondjuk:
```JavaScript
let mouseX = "Krumpli";
```
Ezt érdemes észben tartani ha valami nem úgy akar viselkedni ahogy az a referenciában le van írva. Könnyen lehet véletlenül átdefiniáltuk a változót.

### Események (Events)

Eddig még nem volt szó az eseményekről. Lényegében egy *event* nem más mint egy olyan
függvény amit egy adott helyzet hatására egy külső kód meghív. Ilyen a draw függvény is. Mi leírjük bele mit szeretnénk csinálni amikor a rajzolás esemény zajlik és az fog történni. A p5.js számos dolgot csinál a háttérben amiről nekünk nem kell tudnunk. Csak azt szeretnénk tudni mikor van épp a rajzolás ideje és mit is szeretnénk azzal kezdeni.

Ezzel analóg módon viselkedik minden egér esemény:
- **mouseMoved** - Az egér elmozdult.
- **mouseDragged** - Az egér elmozdult miközben le volt nyomva valamelyik gombja.
- **mousePressed** - Az egér valamelyik gombja lenyomásra került.
- **mouseReleased** - Az egér valamelyik korábban lenyomott gombja felengedésre került.
- **mouseClicked** - Az egér valamelyik gombja le lett nyomva és utána fel is lett engedve.
- **doubledClicked** - Az egér valamelyik gombja kétszer lett kattintva.
- **mouseWheel** - Az egér görgője helyzetet változtatott.

Nem minden esemény működik minden böngészővel. Nekem például se Firefox se Google Chrome alatt nem működött a **doubleClicked** esemény.

Hogyan használjunk hát egy eseményt? Egyszerűen csak írjunk egy függvényt aminek
a tetszőleges esemény a neve és olyan paramétereket vesz át mint ahogy az a referenciában le van írva. Például **mouseMoved** paraméter nélkül:
```JavaScript
function mouseMoved(){
  print("mouseMoved");
}
```
és **mouseMoved** paraméterrel:
```JavaScript
function mouseMoved(){
  print(event);
}
```

Semmi egyéb dolgunk nincs, ugyanis a p5.js számít ezekre a függvényekre, így csak le kell írnunk minek kéne történnie.

Mivel elég helyzet függőek maguk az események ezért nem demonstráljuk mit csinál az összes. Emelet kevés gyakorlati különbség van a **mousePressed**, **mouseReleased** és a **mouseClicked** között.

Nézzünk egy kisebb példát ahol használjuk a **mousePressed** és a **mouseWheel** eseményeket.

```JavaScript
function setup() {
  createCanvas(400, 400);
  fill(0);
}

let keepDrawing = false;
let diameter = 10;

function draw() {
  if(!keepDrawing){
    background(220);
  }
  circle(mouseX, mouseY, diameter);
}

function mousePressed(){
  keepDrawing = !keepDrawing;
}

function mouseWheel(event){
  diameter += event.delta;
}
```

A görgőt görgetve változik a kör átmérője. Míg klikkeléskor be vagy épp kikapcsoljuk a
képernyő "törlését". Így olyan hatást érünk el mintha rajzolnánk.
Ahogy látjuk a **mouseWheel** esemény átvesz egy paramétert amiből ki tudjuk olvasni
hogyan változott a *delta* értéke, amivel módosítjuk a kör átmérőjét. Ha esetleg nincs leírva milyen információt kaphatunk egy esemény adott paraméterétől azt érdemes lehet kiírni és akkor láthatjuk mit is érünk el. Például a görgő paramétere kiírva
```
WheelEvent {isTrusted: true, delta: 3, constructor: Object}
isTrusted: true
delta: 3
<constructor>: "WheelEvent"
```
Innen láthatjuk van egy delta nevű változónk ami görgetéskor változtatja az aktuális értékét.

[Példaprogram és a szerkesztő](3_editor.md)
