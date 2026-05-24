> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; 🇵🇱 PL &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# Instrukcja dekoderów OS-Servo

## 📘 Wprowadzenie
OS-Servo-Decoder to prosty i niezawodny dekoder akcesoriów DCC zaprojektowany do sterowania nawet 8 serwomechanizmami. Obsługuje nowoczesne makiety kolejowe z elastycznymi opcjami konfiguracji, zewnętrznymi modułami przekaźnikowymi do przełączania biegunowości (opcjonalnie) oraz bezpośrednim sterowaniem za pomocą przełączników wejściowych, poleceń akcesoriów DCC i funkcji lokomotywy (F1–F8).

---

## 📚 Spis treści

- [Instrukcja dekoderów OS-Servo](#instrukcja-dekoderów-os-servo)
  - [📘 Wprowadzenie](#-wprowadzenie)
  - [📚 Spis treści](#-spis-treści)
  - [🔧 Właściwości](#-właściwości)
  - [🔌 Podłączenie dekodera](#-podłączenie-dekodera)
  - [💪 Sterowanie wyjściami serw](#-sterowanie-wyjściami-serw)
  - [🛠️ Tryb konfiguracji DCC](#️-tryb-konfiguracji-dcc)
  - [🛠️ Tryb konfiguracji przyciskami](#️-tryb-konfiguracji-przyciskami)
  - [🌟 Zapisywanie pozycji serw](#-zapisywanie-pozycji-serw)
  - [🚗 Tryby funkcji lokomotywy](#-tryby-funkcji-lokomotywy)
  - [⚖️ Przesunięcie adresu](#️-przesunięcie-adresu)
  - [⏰ Tryb automatycznego przełączania](#-tryb-automatycznego-przełączania)
  - [📊 Podsumowanie](#-podsumowanie)

---

## 🔧 Właściwości
- Steruje nawet 8 serwomechanizmami  
- Używa wtykowych zacisków śrubowych do łatwego okablowania  
- Zewnętrzne moduły przekaźnikowe  
- W pełni obsługuje:  
  - Standardowy ruch zwrotnicy  
  - Przełączanie biegunowości (gdzie jest obsługiwane)  
  - Regulowane pozycje końcowe serw (za pomocą przycisków)  
- Autonomiczna konfiguracja: nie wymaga PC, CV ani programatorów  
- Opcjonalne sterowanie funkcjami lokomotywy DCC (F1–F18)  
- Obsługuje przesunięcie 4-adresowe Roco  

---

## 🔌 Podłączenie dekodera

![OS-Servo-Decoder-8 z różnymi konfiguracjami rozszerzenia przekaźnikowego](board_w_extensions.png)

*OS-Servo-Decoder-8 pokazany z różnymi modułami rozszerzenia przekaźnikowego (lewy górny: przekaźniki zatrzaskowe; prawy górny: przekaźniki ogólnego przeznaczenia; dolny: kombinacje z podłączonymi serwomechanizmami).*

OS-Servo-Decoder-8 używa tego samego schematu okablowania co OS-Solenoid-Decoder:

- **Górny nagłówek (POW / DCC):** Podłącz napięcie torowe DCC lub zasilacz DC (maks. 19 V)
- ⚠️ **Ważne:** Nie używaj napięcia AC — uszkodzi to dekoder
- **Nagłówki serw (prawa strona):** Podłącz każdy serwomechanizm do 3-pinowego złącza
  - Standardowy układ pinów: **GND — +5 V — Sygnał**
- **Złącza przekaźnikowe (lewa strona):** A, COM, B — dla modułów rozszerzenia przekaźnikowego OS

---

## 💪 Sterowanie wyjściami serw

Każde wyjście serwa jest sterowane adresem akcesoriów DCC. Gdy dekoder odbiera polecenie DCC dla przypisanego adresu, płynnie przesuwa serwo do zapisanej pozycji dla danego stanu polecenia (PROSTO lub KRZYWO).

- Polecenie **PROSTO** przesuwa serwo do zapisanej prostej pozycji końcowej.
- Polecenie **KRZYWO** przesuwa serwo do zapisanej krzywej pozycji końcowej.
- Jeśli zamontowane są moduły rozszerzenia przekaźnikowego, styki przekaźnikowe przełączają się synchronicznie z serwomechanizmem w celu polaryzacji sercówki.

Pozycje końcowe serw są zapisywane za pomocą klawiszy funkcji lokomotywy — patrz [Zapisywanie pozycji serw](#-zapisywanie-pozycji-serw) poniżej.

---

## 🛠️ Tryb konfiguracji DCC

Dekoder obsługuje tryb konfiguracji działający całkowicie z regulatora DCC — nie wymaga komputera ani programatora CV.

Aby wejść w tryb konfiguracji, wybierz adres lokomotywy **9999** na regulatorze i ustaw **F0, F1 i F2 na WYŁ**. Dekoder wejdzie w tryb konfiguracji i będzie przyjmował polecenia klawiszy funkcji.

Po wejściu w tryb konfiguracji użyj klawiszy funkcji (F1–F8) do ustawiania opcji opisanych w poniższych sekcjach. Naciśnij **F0 = WYŁ**, aby wyjść i wrócić do normalnej pracy.

---

## 🛠️ Tryb konfiguracji przyciskami

Płytka ma dwa fizyczne przyciski: **CONFIGURE** i **TOGGLE**.

- **CONFIGURE** — wchodzi bezpośrednio w tryb konfiguracji bez potrzeby używania regulatora. Dekoder odpowiada sygnalizacją LED wskazującą aktywne ustawienie.
- **TOGGLE** — ręcznie przełącza aktualnie wybrane wyjście serwa między dwiema zapisanymi pozycjami. Przydatne do testowania ruchu i dostosowywania pozycji końcowych.

---

## 🌟 Zapisywanie pozycji serw
W trybie pracy użyj tych funkcji do programowania:

- **F1 = WŁ ➔** Zapisz bieżącą pozycję jako *KRZYWO*  
- **F2 = WŁ ➔** Zapisz bieżącą pozycję jako *PROSTO*  
- **F3 = WŁ ➔** Odwróć przekaźnik sercówki *(tylko model z 6 przekaźnikami)*  
- **F0 = WYŁ ➔** Wyjdź z trybu pracy  

---

## 🚗 Tryby funkcji lokomotywy
W trybie konfiguracji możesz wybrać sterowanie dekoderem za pomocą klawiszy funkcji lokomotywy zamiast poleceń akcesoriów.

- **F4 = WŁ ➔** Wyłącz sterowanie lokomotywą *(domyślnie)*  
- **F5 = WŁ ➔** Włącz tryb funkcji lokomotywy *(F1–F8)* — używa 1 adresu  
- **F6 = WŁ ➔** Włącz tryb 4-funkcyjny *(F1–F4)* — używa 2 adresów  

Umożliwia to bardzo szybkie przełączanie za pomocą regulatorów takich jak Roco Lokmaus lub Multimaus.

---

## ⚖️ Przesunięcie adresu
Aby skompensować przesunięcie o 4 w Roco, użyj:

- **F7 = WŁ ➔** Włącz przesunięcie o 4 adresy  

---

## ⏰ Tryb automatycznego przełączania
Włącz automatyczne przełączanie wybranego silnika:

- **F8 = WŁ ➔** Silnik przełącza się co 5 sekund  
  - Prędkość jest kontrolowana przez regulator  
  - Kierunek regulatora nie ma znaczenia  
  - Regulator 0 = wolno, Max = szybko  

W tym trybie silnik nie jest już zależny od klawiszy funkcji regulatora.

---

## 📊 Podsumowanie
- Użyj przycisków do bezpośredniej konfiguracji i regulacji serw  
- Użyj adresu lokomotywy DCC **9999** z **F0, F1, F2 WYŁ**, aby wejść w tryb konfiguracji  
- Użyj **F1/F2** do zapisywania pozycji serw  
- Użyj **F4–F8**, aby włączyć sterowanie funkcjami lokomotywy, przesunięcie adresu lub tryby przełączania  

Wszystkie OS-Servo-Decodery mają wspólny interfejs i logikę.  
Nie potrzeba komputera. Żadnych CV. Wystarczy podłączyć, zaadresować i uruchomić.
