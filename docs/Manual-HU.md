> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; 🇭🇺 HU &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# OS-Servo-Dekóderek Kézikönyve

## 📘 Bevezetés
Az OS-Servo-Decoder egy egyszerű és megbízható DCC kiegészítő dekóder, amelyet legfeljebb 8 szervómotor meghajtására terveztek. Rugalmas konfigurációs lehetőségekkel, opcionális külső relés modulokkal a polaritásváltáshoz, valamint közvetlen vezérléssel támogatja a modern modellvasutakat — bemeneti kapcsolókon, DCC kiegészítő parancsokon és mozdony funkciógombokon (F1–F8) keresztül egyaránt.

---

## 📚 Tartalomjegyzék

- [OS-Servo-Dekóderek Kézikönyve](#os-servo-dekóderek-kézikönyve)
  - [📘 Bevezetés](#-bevezetés)
  - [📚 Tartalomjegyzék](#-tartalomjegyzék)
  - [🔧 Jellemzők](#-jellemzők)
  - [🔌 A Dekóder Csatlakoztatása](#-a-dekóder-csatlakoztatása)
  - [💪 A Szervó Kimenetek Vezérlése](#-a-szervó-kimenetek-vezérlése)
  - [🛠️ DCC Konfigurációs Mód](#️-dcc-konfigurációs-mód)
  - [🛠️ Gombos Konfigurációs Mód](#️-gombos-konfigurációs-mód)
  - [🌟 Szervópozíciók Tárolása](#-szervópozíciók-tárolása)
  - [🚗 Mozdony Funkció Módok](#-mozdony-funkció-módok)
  - [⚖️ Cím Eltolás](#️-cím-eltolás)
  - [⏰ Automatikus Váltakozó Mód](#-automatikus-váltakozó-mód)
  - [📊 Összefoglalás](#-összefoglalás)

---

## 🔧 Jellemzők
- Legfeljebb 8 szervót vezérel  
- Dugaszolható csavartalpas csatlakozókat használ az egyszerű bekötéshez  
- Külső relés modulok  
- Teljes mértékben támogatja:  
  - Szabványos kitérő mozgást  
  - Polaritásváltást (ahol támogatott)  
  - Állítható szervó végállásokat (gombokon keresztül)  
- Önálló konfiguráció: nincs szükség PC-re, CV-re vagy programozóra  
- Opcionális DCC mozdony funkció vezérlés (F1–F18)  
- Támogatja a Roco 4-es cím eltolást  

---

## 🔌 A Dekóder Csatlakoztatása

![OS-Servo-Decoder-8 különböző relébővítő konfigurációkkal](board_w_extensions.png)

*Az OS-Servo-Decoder-8 különböző bedugott relébővítő modulokkal (bal felső: reteszelő relék; jobb felső: általános célú relék; alul: kombinációk csatlakoztatott szervókkal).*

Az OS-Servo-Decoder-8 ugyanolyan bekötési elrendezést használ, mint az OS-Solenoid-Decoder:

- **Felső csatlakozófej (POW / DCC):** DCC sínfeszültséget vagy DC tápellátást csatlakoztass (max. 19 V)
- ⚠️ **Fontos:** Ne használj AC feszültséget — ez megrongálja a dekódert
- **Szervó csatlakozófejek (jobb oldal):** Csatlakoztass minden szervómotort a 3 tűs csatlakozóhoz
  - Szabványos lábkiosztás: **GND — +5 V — Jel**
- **Relés csatlakozók (bal oldal):** A, COM, B — OS relébővítő modulokhoz

---

## 💪 A Szervó Kimenetek Vezérlése

Minden szervó kimenet egy DCC kiegészítő cím által vezérelt. Amikor a dekóder DCC parancsot kap egy hozzárendelt címre, a szervót simán a tárolt pozícióba mozgatja az adott parancsállapothoz (EGYENES vagy ÍVELT).

- Az **EGYENES** parancs küldése a szervót a tárolt egyenes végállásba mozgatja.
- Az **ÍVELT** parancs küldése a szervót a tárolt ívelt végállásba mozgatja.
- Ha relébővítő modulok vannak felszerelve, a relékontaktusok szinkronban kapcsolnak a szervóval a szárpolarizáláshoz.

A szervó végállások tárolása mozdony funkciógombokon keresztül történik — lásd [Szervópozíciók Tárolása](#-szervópozíciók-tárolása) alább.

---

## 🛠️ DCC Konfigurációs Mód

A dekóder egy olyan konfigurációs módot támogat, amely teljes egészében a DCC szabályozódból működtethető — nincs szükség számítógépre vagy CV programozóra.

A konfigurációs módba lépéshez válaszd ki a **9999** mozdony címet a szabályozódon, és állítsd az **F0, F1 és F2 billentyűket mind KI** állásra. A dekóder belép a konfigurációs módba, és elfogadja a funkciógombok parancsait.

A konfigurációs módban a funkciógombok (F1–F8) segítségével állíts be opciókat az alábbi szakaszokban leírtak szerint. Nyomj **F0 = KI** gombot a kilépéshez és a normál működéshez való visszatéréshez.

---

## 🛠️ Gombos Konfigurációs Mód

A lapon két fizikai gomb található: **KONFIGURÁLÁS** és **VÁLTÁS**.

- **KONFIGURÁLÁS** — közvetlenül belép a konfigurációs módba, szabályozó nélkül. A dekóder LED visszajelzéssel jelzi az aktív beállítást.
- **VÁLTÁS** — manuálisan váltja a jelenleg kiválasztott szervó kimenetet a két tárolt pozíció között. Hasznos a mozgás teszteléséhez és a végállások beállításához.

---

## 🌟 Szervópozíciók Tárolása
Futási módban ezekkel a funkciókkal lehet programozni:

- **F1 = BE ➔** Aktuális pozíció mentése *ÍVELT*-ként  
- **F2 = BE ➔** Aktuális pozíció mentése *EGYENES*-ként  
- **F3 = BE ➔** Szárrelé invertálása *(csak 6 reléses modellen)*  
- **F0 = KI ➔** Kilépés a Futási módból  

---

## 🚗 Mozdony Funkció Módok
Konfigurációs módban a dekóder vezérléséhez kiegészítő parancsok helyett mozdony funkciógombokat is választhatsz.

- **F4 = BE ➔** Mozdony vezérlés letiltása *(alapértelmezett)*  
- **F5 = BE ➔** Mozdony funkcióvezérlés engedélyezése *(F1–F8)* — 1 címet használ  
- **F6 = BE ➔** 4 funkciós mód engedélyezése *(F1–F4)* — 2 címet használ  

Ez ultragyors kapcsolást tesz lehetővé olyan szabályozókkal, mint a Roco Lokmaus vagy Multimaus.

---

## ⚖️ Cím Eltolás
A Roco 4-es eltolásának kompenzálásához használd:

- **F7 = BE ➔** 4-es cím eltolás engedélyezése  

---

## ⏰ Automatikus Váltakozó Mód
Kiválasztott motor automatikus váltakozásának engedélyezése:

- **F8 = BE ➔** A motor minden 5 másodpercben vált  
  - A sebességet a szabályozó vezérli  
  - A szabályozó iránya nem számít  
  - 0-ás sebesség = lassú, Maximum = gyors  

Ebben a módban a motor már nem a szabályozó funkciógombjaihoz van kötve.

---

## 📊 Összefoglalás
- Használd a gombokat a közvetlen beállításhoz és a szervó beállításhoz  
- Használd a DCC mozdony **9999** címet **F0, F1, F2 KI** állással a konfigurációs módba való belépéshez  
- Használd az **F1/F2** gombokat a szervópozíciók tárolásához  
- Használd az **F4–F8** gombokat a mozdony funkcióvezérlés, cím eltolás vagy váltakozó módok engedélyezéséhez  

Minden OS-Servo-Dekóder ezt a felületet és logikát osztja.  
Nincs szükség számítógépre. Nincs CV. Csak bekötni, megszámozni és indítani.
