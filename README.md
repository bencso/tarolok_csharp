# Tömbök és Listák

## Tartalomjegyzék
1. [Tömb](#tömb)
   - [Egydimenziós tömb](#egydimenziós-tömb)
   - [Többdimenziós/mátrix tömb](#többdimenziósmátrix-tömb)
   - [Tömbök feltöltése](#tömbök-feltöltése)
   - [Tömb elemeinek kiiratása](#tömb-elemeinek-kiiratása)
   - [Tömbön használt függvények](#tömbön-használt-függvények)
2. [Lista](#lista)
   - [Lista feltöltése](#lista-feltöltése)
   - [Listán használt függvények](#listán-használt-függvények)
3. [Tömbök és Listák Összefoglalása](#tömbök-és-listák-összefoglalása)
4. [Példa Projektek és Gyakorlatok](#példa-projektek-és-gyakorlatok)

## Tömb
> A tömb olyan adatszerkezet, amely több azonos típusú változót tárolhat. A tömb deklarálásához meg kell adni, hogy milyen típusú elemeket fogunk benne tárolni.

### Deklarálás
```csharp
típus[] elnevezés;
```
### Példák a típusokra:
```csharp
int[] egeszSzam = new int[10]; // 10 elemű egész számok tömbje
string[] karakterLanc = new string[10]; // 10 elemű karakterláncok tömbje
bool[] logikai = new bool[10]; // 10 elemű logikai értékek tömbje
```
## Egydimenziós tömb
> Az egydimenziós tömb egy olyan adatszerkezet, amelynek elemei egymás után, egy vonalban kerülnek tárolásra a memóriában. Az egydimenziós tömböt úgy is elképzelhetjük, mint egy listát, ahol minden elemnek van egy egyedi indexe, amely nullával kezdődik. Az indexek lehetővé teszik, hogy könnyen hozzáférjünk a tömb elemeihez, és módosíthassuk azokat.

### Deklarálás
```csharp
int[] egydimenziosTomb = new int[14]; // 14 elemű egész számok tömbje
```

### Példa: Osztálynévsor
> Képzeljük el egy osztályt, amelyben 12 diák neve található. A diákok nevét egy tömbként tároljuk le.
```csharp
string[] nevsor = new string[12];
```
### Nevek feltöltése
> Mivel a tömbök indexelése 0-val kezdődik, a diákok neveit a következő módon adhatjuk meg:
```csharp
nevsor[0] = "Bak Tass";
nevsor[1] = "Ceruza Elemér";
nevsor[2] = "Cserepes Virág";
// ....
nevsor[11] = "Lekv Áron";
```
### Nevek kiíratása
> A tömb elemeit a `for` ciklus segítségével kiírhatjuk a konzolra:
```csharp
for(int i = 0; i < nevsor.Length; i++) Console.WriteLine("{0}. {1}", i + 1, nevsor[i]);
```
> [!NOTE]  
> Mivel a tömb indexelése 0-val kezdődik, ezért a fenti módon `i+1` tudjuk, a diákok sorszámozását 1-től kezdeni.

## Többdimenziós/mátrix tömb
> A többdimenziós tömbök egynél több dimenzióval rendelkező tömbök. Egy kétdimenziós tömb például egy sorokkal és oszlopokkal rendelkező táblázatként jeleníthető meg. Úgy is mondhatjuk, hogy ez a "tömbök tömbje".

### Deklarálás
```csharp
int[,] tobbDimenzios = new int[sor, oszlop]; // pl. 3 sor 3 oszlop
```

### Példa: TicTacToe
> A Tic-Tac-Toe játéktere egy kétdimenziós tömb segítségével könnyen megvalósítható:
```csharp
string[,] palya = new string[3,3] {
    { "", "", "" },
    { "", "", "" },
    { "", "", "" }
};
```
A játék során ellenőriznünk kell, hogy a játékos nyert-e, ehhez a tömb adott indexein lévő elemeket kell összevetnünk. Példa:

## Tömbök feltöltése
> A tömböket különböző módokon tölthetjük fel, például véletlenszerű számokkal vagy felhasználói bemenettel.

### Random számokkal való feltöltés:
```csharp
Random rnd = new Random();
for (int i = 0; i < tomb.Length; i++) tomb[i] = rnd.Next(); // véletlenszámok generálása
```

### Felhasználó által megadott adatokkal való feltöltés:
```csharp
for (int i = 0; i < tomb.Length; i++) {
    Console.WriteLine("Adja meg a(z) {0}. elemet: ", i);
    tomb[i] = Console.ReadLine();
}
```

## Tömb elemeinek kiiratása
### `foreach` ciklussal
```csharp
foreach(var elem in tomb) Console.WriteLine(elem.ToString());
```
### `for` ciklussal
```csharp
for (int i = 0; i < tomb.Length; i++) Console.WriteLine(tomb[i].ToString());
```

## Tömbön használt függvények
|    Függvény neve   |                  Függvény leírása                 |                                 LINQ                                 |
|:------------------:|:-------------------------------------------------:|:--------------------------------------------------------------------:|
|     Sort(tomb)     |     Növekvő sorrendbe rendezi a tömb elemeit.     | `int [] tomb = {3,1,4,2}; Array.Sort(tomb);` |
|    Reverse(tomb)   |      Megfordítja a tömb elemeinek sorrendjét.     |           `int[] tomb = {1,2,3,4}; Array.Reverse(tomb);`          |
| IndexOf(tomb, int) |      Visszaadja az első előfordulás indexét.      |            `Array.IndexOf(tomb, 3); // Eredmény: 2`          |
|     Clear(tomb)    | Az összes elemet alapértelmezett értékre állítja. |            `Array.Clear(tomb, 0, tomb.Length); // [0,0,0,0]`           |
|  Resize(tomb, int) |           Megváltoztatja a tömb méretét.          |             ` Array.Resize(ref tomb, 6); // [1,2,3,4,0,0]`             |
