
# AgyKurier Zombi Futár API Felhasználói Kézikönyv

Ez a dokumentáció segíti a felhasználókat az AgyKurier Zombi Futár szolgáltatás API-jának kezelésében, amely lehetővé teszi csomagok küldését zombik segítségével.

## Alap URL

Minden kérés az alábbi alap URL-re kell, hogy irányuljon:

```
http://team-4.retreat.alerant.hu/api
```

## Végpontok

### 1. Új rendelés létrehozása

**Használat:** Új csomagrendelés indítására szolgál, meghatározva a feladót, a címzettet, a csomag tartalmát és a kívánt szállítási időt.

**Metódus:** `POST`

**Útvonal:** `/orders`

### 2. Rendelés státuszának lekérdezése

**Használat:** Egy adott rendelés részleteit és aktuális állapotát lehet lekérdezni.

**Metódus:** `GET`

**Útvonal:** `/orders/{orderId}`

### 3. Rendelés státuszának frissítése

**Használat:** Rendelések állapotának frissítésére szolgál. Lehetséges státuszok: Felvéve, Úton, Kézbesítve, Megrágva, Elveszett.

**Metódus:** `PATCH`

**Útvonal:** `/orders/{orderId}/status`

### 4. Zombi hozzárendelése rendeléshez

**Használat:** Egy adott rendeléshez zombit rendelhetünk hozzá, aki kézbesíti a csomagot.

**Metódus:** `POST`

**Útvonal:** `/orders/{orderId}/assign-zombie`

### 5. Megrágási kockázat lekérdezése

**Használat:** Megtekinthető, hogy egy adott csomag kézbesítése során mekkora a megrágás kockázata.

**Metódus:** `GET`

**Útvonal:** `/orders/{orderId}/risk`

## Példák a gyakori használati esetekre

### Rendelés feladása

Egy új rendelés létrehozásakor a felhasználó megadja a feladó és a címzett adatait, valamint a szállítandó csomag tartalmát és a kézbesítés időpontját. Az API visszaadja a rendelés azonosítóját és a rendelés alapvető adatait.

### Státusz ellenőrzése

A felhasználó bármikor lekérdezheti a csomagja státuszát, így nyomon követheti, hogy a csomag éppen milyen fázisban van a kézbesítési folyamat során.

### Rendelés módosítása

Ha a rendelés kézbesítési állapota megváltozik (például kézbesítés során megrágás történik), azt a státuszfrissítési végponttal jelezheti az API-n keresztül.

### Zombi hozzárendelés

A rendelés indítása után szükség van egy zombi futár kiválasztására, amelyet a zombi hozzárendelési végponton keresztül tehet meg.

### Kockázatelemzés

A kockázatelemzési végpont segítségével ellenőrizhető, hogy mennyire biztonságos a csomag kézbesítése, és milyen kockázatokkal kell számolni a megrágás szempontjából.
