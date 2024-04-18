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
string[] nevsor = new string[12];
```
*Minden egyes gyerek nevéhez tartozik egy szám (index), ezzel tudjuk őket azonosítani. <br> Jelen esetben az osztály 12 fős (string[**12**]. <br> Mivel a tömb indexelése 0-val kezdődik, ezért a kódunkban át kell alakítani a felsorolást, ha ki szeretnénk iratni a névsort.*
```csharp
//Tömb:

nevsor[0] = "Antal Pista";
nevsor[1] = "Dénes Albert";
nevsor[2] = "Nagy Lajos";
nevsor[n+1] = "....";

for(int i=0;i<nevsor.length;i++){
 Console.WriteLine("{0}. {1}", i+1 , nevsor[i])
}
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
string[,] palya = new string[3,3]{
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
- ### Sort(tomb)
  > Ez a függvény, a tömb elemeit növekvő sorrendbe rendezi.
  ```csharp
  int[] tomb = { 3, 1, 4, 2 };
  Array.Sort(tomb);
  ```
  **Eredmény:**
  > [1,2,3,4]

>[!NOTE]
> Ha string-et (karakter sorozatot) szeretnénk sort() függvénnyel sorba rendezni, akkor az, az ABC-nek megfelelően helyezi sorba.

- ### Reverse(tomb)
  > Ez a függvény, megfordítja a tömb elemeinek sorrendjét.
    ```csharp
  int[] tomb = { 1, 2, 3, 4 };
  Array.Reverse(numbers);
  ```
  **Eredmény:**
  > [4,3,2,1]
- ### IndexOf(tomb, int)
  > Ez a függvény, egy adott értéket keres a tömbben, és az érték *(első előfordulásának)* indexét adja vissza.
     ```csharp
      int[] tomb = { 1, 2, 3, 4 };
      int index = Array.IndexOf(numbers, 3);
     ```
    **Eredmény:**
    > Index: 2
> [!IMPORTANT]
> Ha az értéket nem találja, akkor -1-et ad vissza.
- ### Clear(tomb)
  > Ez a függvény, a tömb összes elemét egy alapértelmezett értékre állítja.
    ```csharp
    int[] tomb = { 1, 2, 3, 4 };
    Array.Clear(tomb, 0, numbers.Length);
    ```
  **Eredmény:**
  > [0,0,0,0]
- ### Resize(tomb, int)
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

### Deklarálás
```csharp
List<int> egeszSzam = new List<int>();

List<string> karakterLanc = new List<string>(2);

string[] tomb = { "elem" };
List<string> tombbolLista = new List<string>(tomb);
```

## Lista feltöltése
> Többféle módon tölthetjük fel a listánkat elemekkel:
### Add(elem) 
Ezzel a függvénnyel egyesével tudjuk , hozzáadni az elemeket a listánkhoz.
```csharp
List<string> lista = new List<string>();
lista.Add("Ez egy elem lesz");
lista.Add("Ez egy másik elem");
```
> Eredmény
```{"Ez egy elem lesz", "Ez egy másik elem"}```
### AddRange(elemek-csoportja)
> Az `AddRange()` függvény egy adott elem csoportot (/vagy tömb elemeit) ad hozzá a listánkhoz
```csharp
int[] tomb = {1,2,3,4};
List<int> lista = new List<int>();
lista.AddRange(tomb);
```
> Eredmény
```{1,2,3,4}```

*vagy*
```csharp
int[] tomb = {1,2,3,4};
List<int> lista = new List<int>();
tomb.ForEach(elem => lista.Add(elem));
```
> Eredmény
```{1,2,3,4}```

>[!IMPORTANT]
> Ha tömbből szeretnénk listába áthelyezni az elemeket, akkor azonos adattípusú kell legyen a két tároló. (list<int> , int[])

### Insert(id, elem)
> Az `Insert()` függvénnyel egy listába , index alapján tudunk beszúrni elemet
```csharp
int[] tomb = {1,2,3,4};
List<int> lista = new List<int>();
tomb.ForEach(elem => lista.Add(elem));
/*
lista:{
1, id: 0
2, id: 1
3, id: 2
4  id: 3
}
*/
lista.Insert(1, 4)
```
> Eredmény
```{1,4,3,4}```

[//]: <> (TODO: lista folytatása , dictionary-vel)
