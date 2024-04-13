# Tárolók
<img src="tombok.jpg"/>

## Tömb
> A tömb olyan adatszerkezet, amely több azonos típusú változót tárolhat. Egy tömb deklarálásához meg kell adnunk, hogy milyen típusú elemeket fogunk benne tárolni. Ha bármilyen típusú elemeket szeretnénk tárolni benne, akkor a tömböt `object`-ként kell deklarálni.
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
- Az indexelés 0-val kezdődik. Ez azt jelenti, hogy a tömb első eleme a 0. indexen lesz, nem pedig az 1-ön.
  
### Egydimenziós tömb deklarálása:
> Az egydimenziós tömb olyan lineáris adatszerkezet, amelynek elemei egymás után kerülnek tárolásra a memóriában. Ezeket a tömböket úgy lehet elképzelni, mint egy elemeket tartalmazó listát, ahol minden elemnek van egy egyedi indexe, amely nullával kezdődik.
```csharp
int[] 1DTomb = new int[14];
```

### Kétdimenziós deklarálása:
> A többdimenziós tömbök egynél több dimenzióval rendelkező tömbök. Egy kétdimenziós tömb például egy sorokkal és oszlopokkal rendelkező táblázatként jeleníthető meg.
```csharp
int[,] 2DTomb = new int[4,2];
```
### Többdimenziós/matrix tömb deklarálás:
```csharp
int[,] tobbDimenzios = new int[,]{
  { 1, 2, 3 },
  { 4, 5, 6 },
  { 7, 8, 9 }
};
```

### Feltöltés:
> A tömb random számokkal való feltöltése for ciklussal:
```csharp
Random rnd = new Random();

for (int i=0; i<tomb.Length; i++){
  tomb[i] = rnd.Next(); 
}
```
> A tömb a felhasználó megadott adatokkal feltöltése for ciklussal:
```csharp
for (int i=0; i<tomb.Length; i++){                
  Console.WriteLine("Adja meg a/az {0}. elemet: ", i);
  tomb[i] = Console.ReadLine();
}
```
### Kiiratás
> Tömb elemeinek kiiratása foreach-al:
```csharp
foreach(var elem in tömb)
{
 Console.WriteLine(elem.ToString());
}
```
> Tömb elemeinek kiiratása for ciklussal:
```csharp
for (int i=0; i<tomb.Length; i++){                
  Console.WriteLine(tomb[i].ToString());          
}
```

## Tömbön használt függvények
- ### Sort()
  > Ez a függvény egy tömb elemeit növekvő sorrendbe rendezi.
  ```csharp
  int[] tomb = { 3, 1, 4, 2 };
  Array.Sort(tomb);
  ```
  **Eredmény:**
  > [1,2,3,4]
- ### Reverse()
  > Ez a függvény megfordítja a tömb elemeinek sorrendjét.
    ```csharp
  int[] tomb = { 1, 2, 3, 4 };
  Array.Reverse(numbers);
  ```
  **Eredmény:**
  > [4,3,2,1]
- ### IndexOf()
  > Ez a függvény egy adott értéket keres a tömbben, és az érték (első előfordulásának) indexét adja vissza.
     ```csharp
      int[] tomb = { 1, 2, 3, 4 };
      int index = Array.IndexOf(numbers, 3);
     ```
    **Eredmény:**
    > Index: 2
> [!IMPORTANT]
> Ha az értéket nem találja, akkor -1-et ad vissza.
- ### Clear()
  > Ez a függvény a tömb összes elemét egy alapértelmezett értékre állítja.
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
