> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; 🇳🇴 NO &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# OS-Servo-Decoders Manual

## 📘 Innledning
OS-Servo-Decoder er en enkel og robust DCC-tilbehørsdekoder utviklet for å drive opptil 8 servomotorer. Den støtter moderne modelljernbaner med fleksible konfigurasjonsalternativer, eksterne relé-moduler for polaritetskobling (valgfritt) og direkte styring ved hjelp av både inngangsbrytere, DCC-tilbehørskommandoer og lokomotivfunksjoner (F1–F8).

---

## 📚 Innholdsfortegnelse

- [OS-Servo-Decoders Manual](#os-servo-decoders-manual)
  - [📘 Innledning](#-innledning)
  - [📚 Innholdsfortegnelse](#-innholdsfortegnelse)
  - [🔧 Egenskaper](#-egenskaper)
  - [🔌 Tilkobling av dekoderen](#-tilkobling-av-dekoderen)
  - [💪 Styring av servoutgangene](#-styring-av-servoutgangene)
  - [🛠️ DCC-konfigurasjonsmodus](#️-dcc-konfigurasjonsmodus)
  - [🛠️ Knapp-konfigurasjonsmodus](#️-knapp-konfigurasjonsmodus)
  - [🌟 Lagre servoposisjoner](#-lagre-servoposisjoner)
  - [🚗 Lokomotivfunksjonsmodus](#-lokomotivfunksjonsmodus)
  - [⚖️ Adresseforskyvning](#️-adresseforskyvning)
  - [⏰ Auto-veksel-modus](#-auto-veksel-modus)
  - [📊 Sammendrag](#-sammendrag)

---

## 🔧 Egenskaper
- Styrer opptil 8 servoer  
- Bruker uttrekkbare skrueterminaler for enkel kabling  
- Eksterne relé-moduler  
- Støtter fullt ut:  
  - Standard sporskiftebevegelse  
  - Polaritetskobling (der støttet)  
  - Justerbare servo-endeposisjoner (via knapper)  
- Frittstående konfigurasjon: ingen PC, CV-er eller programmerere nødvendig  
- Valgfri DCC-lokomotivfunksjonsstyring (F1–F18)  
- Støtter Roco 4-adresseforskyvning  

---

## 🔌 Tilkobling av dekoderen

![OS-Servo-Decoder-8 med ulike relé-utvidelseskonfigurasjoner](board_w_extensions.png)

*OS-Servo-Decoder-8 vist med ulike relé-utvidelsesmoduler plugget inn (øverst til venstre: selvholdende reléer; øverst til høyre: generelle reléer; nederst: kombinasjoner med servoer tilkoblet).*

OS-Servo-Decoder-8 bruker samme kablingslayout som OS-Solenoid-Decoder:

- **Toppoverskrift (POW / DCC):** Koble enten DCC sporsspenning eller en DC-strømforsyning (maks 19 V)
- ⚠️ **Viktig:** Ikke bruk AC-spenning — dette vil skade dekoderen
- **Servo-overskrifter (høyre side):** Koble hver servomotor til 3-pins koblingen
  - Standard pinout: **GND — +5 V — Signal**
- **Relé-koblinger (venstre side):** A, COM, B — for OS relé-utvidelsesmoduler

---

## 💪 Styring av servoutgangene

Hver servoutgang styres av en DCC-tilbehørsadresse. Når dekoderen mottar en DCC-kommando for en tildelt adresse, beveger den servoen jevnt til den lagrede posisjonen for den kommandotilstanden (RETT eller KURVET).

- Sending av **RETT**-kommandoen beveger servoen til den lagrede rette endeposisjonen.
- Sending av **KURVET**-kommandoen beveger servoen til den lagrede kurvede endeposisjonen.
- Hvis relé-utvidelsesmoduler er montert, kobles reléekontaktene synkront med servoen for frog-polarisering.

Servo-endeposisjoner lagres ved hjelp av lokomotivfunksjonstaster — se [Lagre servoposisjoner](#-lagre-servoposisjoner) nedenfor.

---

## 🛠️ DCC-konfigurasjonsmodus

Dekoderen støtter en konfigurasjonsmodus som fungerer helt fra DCC-reguleringen din — ingen datamaskin, ingen CV-programmerer nødvendig.

For å gå inn i konfigurasjonsmodus, velg lokoadresse **9999** på regulatoren din og sett **F0, F1 og F2 alle til AV**. Dekoderen vil gå inn i konfig-modus og akseptere funksjonstastkommandoer.

Når du er i konfig-modus, bruk funksjonstastene (F1–F8) til å angi alternativer som beskrevet i avsnittene nedenfor. Trykk **F0 = AV** for å avslutte og gå tilbake til normal drift.

---

## 🛠️ Knapp-konfigurasjonsmodus

Kortet har to fysiske knapper: **CONFIGURE** og **TOGGLE**.

- **CONFIGURE** — går direkte inn i konfigurasjonsmodus, uten behov for en regulator. Dekoderen responderer med LED-tilbakemelding som indikerer den aktive innstillingen.
- **TOGGLE** — veksler manuelt den valgte servoutgangen mellom de to lagrede posisjonene. Nyttig for å teste bevegelse og justere endeposisjoner.

---

## 🌟 Lagre servoposisjoner
Mens i Kjøremodus, bruk disse funksjonene for å programmere:

- **F1 = PÅ ➔** Lagre gjeldende posisjon som *KURVET*  
- **F2 = PÅ ➔** Lagre gjeldende posisjon som *RETT*  
- **F3 = PÅ ➔** Inverter frog-relé *(kun 6-relé-modell)*  
- **F0 = AV ➔** Avslutt kjøremodus  

---

## 🚗 Lokomotivfunksjonsmodus
I konfig-modus kan du velge å styre dekoderen ved hjelp av lokomotivfunksjonstaster i stedet for tilbehørskommandoer.

- **F4 = PÅ ➔** Deaktiver loko-styring *(standard)*  
- **F5 = PÅ ➔** Aktiver lokomotivfunksjonsmodus *(F1–F8)* — bruker 1 adresse  
- **F6 = PÅ ➔** Aktiver 4-funksjonsmodus *(F1–F4)* — bruker 2 adresser  

Dette gir ultrarask kobling ved hjelp av regulatorer som Roco Lokmaus eller Multimaus.

---

## ⚖️ Adresseforskyvning
For å kompensere for Roco sin forskyvning på 4, bruk:

- **F7 = PÅ ➔** Aktiver 4-adresseforskyvning  

---

## ⏰ Auto-veksel-modus
Aktiver automatisk veksling av valgt motor:

- **F8 = PÅ ➔** Motor veksler hvert 5. sekund  
  - Hastigheten styres av regulatoren  
  - Regulatorretningen spiller ingen rolle  
  - Regulator 0 = sakte, Maks = raskt  

I denne modusen er motoren ikke lenger styrt av regulatorens funksjonstaster.

---

## 📊 Sammendrag
- Bruk knappene for direkte oppsett og servijustering  
- Bruk DCC lokoadresse **9999** med **F0, F1, F2 AV** for å gå inn i konfig-modus  
- Bruk **F1/F2** til å lagre servoposisjoner  
- Bruk **F4–F8** for å aktivere lokomotivfunksjonsstyring, adresseforskyvning eller vekselmodus  

Alle OS-Servo-Decoders deler dette grensesnittet og denne logikken.  
Ingen datamaskin nødvendig. Ingen CV-er. Bare koble til, angi adresse og kjør.
