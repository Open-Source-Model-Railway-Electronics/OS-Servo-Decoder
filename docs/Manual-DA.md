> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; 🇩🇰 DA &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# OS-Servo-Decoders Manual

## 📘 Introduktion
OS-Servo-Decoder er en enkel og robust DCC-tilbehørsdekoder designet til at drive op til 8 servomotorer. Den understøtter moderne modeljernbaner med fleksible konfigurationsmuligheder, eksterne relæmoduler til polaritetsskift (valgfrit) og direkte styring ved hjælp af både indgangsafbrydere, DCC-tilbehørskommandoer og lokomotivfunktioner (F1–F8).

---

## 📚 Indholdsfortegnelse

- [OS-Servo-Decoders Manual](#os-servo-decoders-manual)
  - [📘 Introduktion](#-introduktion)
  - [📚 Indholdsfortegnelse](#-indholdsfortegnelse)
  - [🔧 Egenskaber](#-egenskaber)
  - [🔌 Tilslutning af dekoderen](#-tilslutning-af-dekoderen)
  - [💪 Styring af servo-udgange](#-styring-af-servo-udgange)
  - [🛠️ DCC-konfigurationstilstand](#️-dcc-konfigurationstilstand)
  - [🛠️ Knapkonfigurationstilstand](#️-knapkonfigurationstilstand)
  - [🌟 Lagring af servo-positioner](#-lagring-af-servo-positioner)
  - [🚗 Lokomotivfunktionstilstande](#-lokomotivfunktionstilstande)
  - [⚖️ Adresseforskydning](#️-adresseforskydning)
  - [⏰ Auto-toggle-tilstand](#-auto-toggle-tilstand)
  - [📊 Oversigt](#-oversigt)

---

## 🔧 Egenskaber
- Styrer op til 8 servoer  
- Bruger tilsluttbare skrueterminaler til nem kabeltrækning  
- Eksterne relæmoduler  
- Understøtter fuldt ud:  
  - Standard sporskiftebevægelse  
  - Polaritetsskift (hvor understøttet)  
  - Justerbare servo-endpositioner (via knapper)  
- Selvstændig konfiguration: ingen PC, CV'er eller programmere påkrævet  
- Valgfri DCC-lokomotivfunktionsstyring (F1–F18)  
- Understøtter Roco 4-adresse-forskydning  

---

## 🔌 Tilslutning af dekoderen

![OS-Servo-Decoder-8 med forskellige relæudvidelseskonfigurationer](board_w_extensions.png)

*OS-Servo-Decoder-8 vist med forskellige relæudvidelsesmoduler tilsluttet (øverst til venstre: selvholdende relæer; øverst til højre: general-purpose relæer; nederst: kombinationer med servoer tilsluttet).*

OS-Servo-Decoder-8 bruger det samme kabeltrækningslayout som OS-Solenoid-Decoder:

- **Øvre header (POW / DCC):** Forbind enten DCC-skinnesænkning eller en DC-strømforsyning (maks. 19 V)
- ⚠️ **Vigtigt:** Brug ikke AC-spænding — dette vil beskadige dekoderen
- **Servo-headere (højre side):** Forbind hver servomotor til 3-pin-stikket
  - Standard pinout: **GND — +5 V — Signal**
- **Relæstik (venstre side):** A, COM, B — til OS-relæudvidelsesmoduler

---

## 💪 Styring af servo-udgange

Hver servo-udgang styres af en DCC-tilbehørsadresse. Når dekoderen modtager en DCC-kommando for en tildelt adresse, bevæger den servoens jævnt til den lagrede position for den kommandotilstand (LIGE eller KURVET).

- Afsendelse af **LIGE**-kommandoen bevæger servoens til dens lagrede lige endposition.
- Afsendelse af **KURVET**-kommandoen bevæger servoens til dens lagrede kurvede endposition.
- Hvis relæudvidelsesmoduler er monteret, skifter relækontakterne synkront med servoens til hjertestykke-polarisering.

Servo-endpositioner lagres ved hjælp af lokomotivfunktionsknapper — se [Lagring af servo-positioner](#-lagring-af-servo-positioner) nedenfor.

---

## 🛠️ DCC-konfigurationstilstand

Dekoderen understøtter en konfigurationstilstand, der fungerer udelukkende fra din DCC-styreenhed — ingen computer, ingen CV-programmer påkrævet.

For at gå ind i konfigurationstilstand, vælg lokomotivadresse **9999** på din styreenhed og sæt **F0, F1 og F2 alle til FRA**. Dekoderen vil gå ind i konfigurationstilstand og acceptere funktionstastskommandoer.

Når du er i konfigurationstilstand, bruges funktionstasterne (F1–F8) til at indstille muligheder som beskrevet i afsnittene nedenfor. Tryk på **F0 = FRA** for at afslutte og vende tilbage til normal drift.

---

## 🛠️ Knapkonfigurationstilstand

Kortet har to fysiske knapper: **CONFIGURE** og **TOGGLE**.

- **CONFIGURE** — går direkte ind i konfigurationstilstand uden behov for en styreenhed. Dekoderen reagerer med LED-tilbagemelding, der angiver den aktive indstilling.
- **TOGGLE** — skifter manuelt den aktuelt valgte servo-udgang mellem dens to lagrede positioner. Nyttigt til test af bevægelse og justering af endpositioner.

---

## 🌟 Lagring af servo-positioner
Mens du er i Kørselstilstand, brug disse funktioner til at programmere:

- **F1 = TIL ➔** Gem aktuel position som *KURVET*  
- **F2 = TIL ➔** Gem aktuel position som *LIGE*  
- **F3 = TIL ➔** Inverter frog-relæet *(kun 6-relæ-model)*  
- **F0 = FRA ➔** Afslut kørselstilstand  

---

## 🚗 Lokomotivfunktionstilstande
I konfigurationstilstand kan du vælge at styre dekoderen ved hjælp af lokomotivfunktionsknapper i stedet for tilbehørskommandoer.

- **F4 = TIL ➔** Deaktiver lokomotivsstyring *(standard)*  
- **F5 = TIL ➔** Aktiver lokomotivsfunktionstilstand *(F1–F8)* — bruger 1 adresse  
- **F6 = TIL ➔** Aktiver 4-funktionstilstand *(F1–F4)* — bruger 2 adresser  

Dette muliggør ultrahurtig skift ved brug af styrenheder som Roco Lokmaus eller Multimaus.

---

## ⚖️ Adresseforskydning
For at kompensere for Rocos forskydning på 4, brug:

- **F7 = TIL ➔** Aktiver 4-adresse-forskydning  

---

## ⏰ Auto-toggle-tilstand
Aktiver automatisk toggling af en valgt motor:

- **F8 = TIL ➔** Motor skifter hvert 5. sekund  
  - Hastighed styres af styreenheden  
  - Styrenheds-retning er ligegyldig  
  - Styreenhed 0 = langsom, Maks = hurtig  

I denne tilstand er motoren ikke længere slavebundet til styrenheds-funktionstaster.

---

## 📊 Oversigt
- Brug knapperne til direkte opsætning og servo-justering  
- Brug DCC-lokomotivadresse **9999** med **F0, F1, F2 FRA** for at gå ind i konfigurationstilstand  
- Brug **F1/F2** til at lagre servo-positioner  
- Brug **F4–F8** til at aktivere lokomotivfunktionsstyring, adresseforskydning eller toggle-tilstande  

Alle OS-Servo-dekodere deler denne grænseflade og logik.  
Ingen computer påkrævet. Ingen CV'er. Bare kabelforbind den, adressér den og kør.
