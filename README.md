# Tárolók
<img src="tombok.jpg"/>

## Tömb
> A tömb olyan adatszerkezet, amely több azonos típusú változót tárolhat. Egy tömb deklarálásához meg kell adnunk ,hogy milyen típusú elemeket fogunk benne tárolni. Ha bármilyen típusú elemeket szeretnénk tárolni benne, akkor a tömböt `object`-ként kell deklarálni.
```csharp
típus[] elnevezés;
```
- példa `típus`-ok:
  - ```csharp
    int[] egeszSzam = new int[x];
    ```
  - ```csharp
    string[] karakterLanc = new string[x];
    ```
  - ```csharp
    bool[] logikai = new bool[x];
    ```
  - ...
- Tömbök egydimenziósak és többdimenziósak is lehetnek. Ezeket a deklarálások során kell megadni.
>[!IMPORTANT]
>Az indexelés 0-val kezdődik. Ez azt jelenti, hogy a tömb első eleme a 0. indexen lesz, nem pedig az 1-ön.
  
### Egydimenziós tömb:
> Az egydimenziós tömb olyan adatszerkezet ,amelynek elemei egymás után kerülnek tárolásra a memóriában. Ezt úgy lehet elképzelni, mint egy listát (Array), ahol minden elemnek van egy **egyedi** indexe, amely **nullával** kezdődik.
Deklarálás:
```csharp
int[] 1DTomb = new int[14];
```
**Példa: Osztálynévsor**
```csharp
int[] nevsor = new string[12];
```
*Minden egyes gyerek nevéhez tartozik egy szám, ezzel tudjuk őket megkülönböztetni. <br> Jelen esetben az osztály 12 fős (string[**12**]. <br> Mivel a tömb 0. indexe az osztályfőnök neve lesz, ezért a gyerekek 1.-től lesznek megszámozva*
```
Tömb:

nevsor[0] = "Nagy Pista tanárúr";
nevsor[1] = "Kis Albert";
nevsor[2] = "Nagy Lajos";
nevsor[n+1] = "....";
```

### Többdimenziós/mátrix tömb:
> A többdimenziós tömbök, egynél több dimenzióval rendelkező tömbök. Egy kétdimenziós tömb például egy sorokkal és oszlopokkal rendelkező táblázatként jeleníthető meg.
> Úgy is mondhatjuk, hogy ez a "tömbök tömbje"
Deklarálás:
```csharp
int[,] tobbDimenzios = new int[sor][oszlop];
```

**Példa: Tic-Tac-Toe**
```csharp
int[,] palya = new string[3,3]{
  { "", "", "" },
  { "", "", "" },
  { "", "", "" }
};
```
*Tic-Tac-Toe játéktere 3 oszlopból és 3 sorból áll.
Minden olyan kombinációt meg kell vizsgálnunk, amivel a játékos nyerhet.
Ezt úgy valósítjuk meg, hogy a tömb adott indexein lévő elemeket összevetjük a velük (függölegesen/vízszintesen/átlósan) szomszédos elemekkel.*
```
"Koordináták" szerint:
   |  0 | 1 | 2
0  |{ 0,  1,  2 } -> palya[0, 0], palya[0, 1], palya[0, 2]);
1  |{ 0,  1,  2 } -> palya[1, 0], palya[1, 1], palya[1, 2]);
2  |{ 0,  1,  2 } -> palya[2, 0], palya[2, 1], palya[2, 2]);

A kód szerint:
   |   0  | 1  | 2
0  |{ "O", "O", "O" }
1  |{ "O", "X", "X" }
2  |{ "X", "O", "X" }
```
*A fenti ábrán az "O" játékos nyert, ugyanis az első sorban 3 "O"-t tett le egymás mellé, ezt az alábbi módon tudjuk leellenőrizni:*
```csharp
if (palya[0, 0] == "O" && (palya[0, 0] == palya[0, 1]) && (palya[0, 1] == palya[0, 2]))
  {
  //Console.WriteLine("O nyert");
  }
```

### Tömbök feltöltése:
> A tömb random számokkal való feltöltése `for` ciklussal:
```csharp
Random rnd = new Random();

for (int i=0; i<tomb.Length; i++){
  tomb[i] = rnd.Next(); 
}
```
> A tömb a felhasználó megadott adatokkal feltöltése `for` ciklussal:
```csharp
for (int i=0; i<tomb.Length; i++){                
  Console.WriteLine("Adja meg a/az {0}. elemet: ", i);
  tomb[i] = Console.ReadLine();
}
```
### Tömb elemeinek kiiratása:
> Tömb elemeinek kiiratása `foreach`-al:
```csharp
foreach(var elem in tömb)
{
 Console.WriteLine(elem.ToString());
}
```
> Tömb elemeinek kiiratása `for` ciklussal:
```csharp
for (int i=0; i<tomb.Length; i++){                
  Console.WriteLine(tomb[i].ToString());          
}
```

## Tömbön használt függvények
- ### Sort()
  > Ez a függvény, a tömb elemeit növekvő sorrendbe rendezi.
  ```csharp
  int[] tomb = { 3, 1, 4, 2 };
  Array.Sort(tomb);
  ```
  **Eredmény:**
  > [1,2,3,4]
- ### Reverse()
  > Ez a függvény, megfordítja a tömb elemeinek sorrendjét.
    ```csharp
  int[] tomb = { 1, 2, 3, 4 };
  Array.Reverse(numbers);
  ```
  **Eredmény:**
  > [4,3,2,1]
- ### IndexOf()
  > Ez a függvény, egy adott értéket keres a tömbben, és az érték *(első előfordulásának)* indexét adja vissza.
     ```csharp
      int[] tomb = { 1, 2, 3, 4 };
      int index = Array.IndexOf(numbers, 3);
     ```
    **Eredmény:**
    > Index: 2
> [!IMPORTANT]
> Ha az értéket nem találja, akkor -1-et ad vissza.
- ### Clear()
  > Ez a függvény, a tömb összes elemét egy alapértelmezett értékre állítja.
    ```csharp
    int[] tomb = { 1, 2, 3, 4 };
    Array.Clear(tomb, 0, numbers.Length);
    ```
  **Eredmény:**
  > [0,0,0,0]
- ### Resize()
  > Ez a függvény megváltoztatja a tömb méretét, akár elemek hozzáadásával, akár eltávolításával. 
    ```csharp
    int[] tomb = { 1, 2, 3, 4 };
    Array.Resize(ref tomb, 6);
    ```
  **Eredmény:**
  > [1,2,3,4,0,0]

## Lista

*A List<> osztály egy erősen tipusos objektumlistát reprezentál.A lista, funkciót biztosít objektumok listájának létrehozásához, elemek hozzáadásához a listához, valamint a listában lévő elemek kereséséhez, rendezéséhez és frissítéséhez.*

>A C# lista egy általános osztály, és a  eléréséhez ezt a névteret kell importálnia a projektjébe.
```csharp
using System.Collections.Generic
```