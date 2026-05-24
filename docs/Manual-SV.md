> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; 🇸🇪 SV &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# OS-Servo-Decoders Manual

## 📘 Introduktion
OS-Servo-Decoder är en enkel och robust DCC-tillbehörsdecoder utformad för att driva upp till 8 servomotorer. Den stöder moderna modellbanor med flexibla konfigurationsalternativ, externa relämoduler för polaritetsväxling (valfritt) och direktstyrning med både ingångsknappar, DCC-tillbehörskommandon och lokfunktioner (F1–F8).

---

## 📚 Innehållsförteckning

- [OS-Servo-Decoders Manual](#os-servo-decoders-manual)
  - [📘 Introduktion](#-introduktion)
  - [📚 Innehållsförteckning](#-innehållsförteckning)
  - [🔧 Funktioner](#-funktioner)
  - [🔌 Ansluta decodern](#-ansluta-decodern)
  - [💪 Styra servoutgångarna](#-styra-servoutgångarna)
  - [🛠️ DCC-konfigurationsläge](#️-dcc-konfigurationsläge)
  - [🛠️ Knapprationsläge](#️-knappkonfigurationsläge)
  - [🌟 Lagra servopositioner](#-lagra-servopositioner)
  - [🚗 Lokfunktionslägen](#-lokfunktionslägen)
  - [⚖️ Adressoffset](#️-adressoffset)
  - [⏰ Auto-växlingsläge](#-auto-växlingsläge)
  - [📊 Sammanfattning](#-sammanfattning)

---

## 🔧 Funktioner
- Styr upp till 8 servon  
- Använder inkopplingsbara skruvplintrar för enkel kabelanslutning  
- Externa relämoduler  
- Fullt stöd för:  
  - Standard växelrörelse  
  - Polaritetsväxling (där det stöds)  
  - Justerbara servoändpositioner (via knappar)  
- Fristående konfiguration: ingen PC, inga CV:er eller programmerare krävs  
- Valfri DCC lokfunktionsstyrning (F1–F18)  
- Stöder Roco 4-adressoffset  

---

## 🔌 Ansluta decodern

![OS-Servo-Decoder-8 med olika reläutvidgningskonfigurationer](board_w_extensions.png)

*OS-Servo-Decoder-8 visad med olika reläutvidgningsmoduler inkopplade (övre vänster: låsande reläer; övre höger: generella reläer; nedre: kombinationer med servon anslutna).*

OS-Servo-Decoder-8 använder samma kopplingsschema som OS-Solenoid-Decoder:

- **Övre kontaktsockel (POW / DCC):** Anslut antingen DCC-spårspänning eller en DC-strömförsörjning (max 19 V)
- ⚠️ **Viktigt:** Använd inte AC-spänning — det skadar decodern
- **Servokontaktsocklarna (höger sida):** Anslut varje servomotor till 3-stiftskontakten
  - Standard stiftkonfiguration: **GND — +5 V — Signal**
- **Reläkontakter (vänster sida):** A, COM, B — för OS reläutvidgningsmoduler

---

## 💪 Styra servoutgångarna

Varje servoutgång styrs av en DCC-tillbehörsadress. När decodern tar emot ett DCC-kommando för en tilldelad adress rör den servonet smidigt till den lagrade positionen för det kommandotillståndet (RAK eller KRÖKT).

- Att skicka kommandot **RAK** rör servonet till sin lagrade raka ändposition.
- Att skicka kommandot **KRÖKT** rör servonet till sin lagrade krökta ändposition.
- Om reläutvidgningsmoduler är monterade växlar reläkontakterna synkroniserat med servonet för hjärtpunktspolarisering.

Servoändpositioner lagras med lokfunktionsknappar — se [Lagra servopositioner](#-lagra-servopositioner) nedan.

---

## 🛠️ DCC-konfigurationsläge

Decodern stöder ett konfigurationsläge som fungerar helt från din DCC-reglage — ingen dator, ingen CV-programmerare krävs.

För att aktivera konfigurationsläge, välj lokadress **9999** på ditt reglage och ställ **F0, F1 och F2 alla på OFF**. Decodern aktiverar konfigurationsläget och accepterar funktionsknappkommandon.

När du är i konfigurationsläge, använd funktionstangenterna (F1–F8) för att ställa in alternativ enligt beskrivningen i avsnitten nedan. Tryck på **F0 = OFF** för att avsluta och återgå till normal drift.

---

## 🛠️ Knappkonfigurationsläge

Kortet har två fysiska knappar: **CONFIGURE** och **TOGGLE**.

- **CONFIGURE** — aktiverar konfigurationsläge direkt, utan behov av ett reglage. Decodern svarar med LED-återkoppling som indikerar den aktiva inställningen.
- **TOGGLE** — växlar manuellt den aktuellt valda servoutgången mellan dess två lagrade positioner. Användbart för att testa rörelsen och justera ändpositioner.

---

## 🌟 Lagra servopositioner
I körläget, använd dessa funktioner för att programmera:

- **F1 = ON ➔** Spara aktuell position som *KRÖKT*  
- **F2 = ON ➔** Spara aktuell position som *RAK*  
- **F3 = ON ➔** Invertera hjärtpunktrelä *(endast 6-relämodell)*  
- **F0 = OFF ➔** Avsluta körläget  

---

## 🚗 Lokfunktionslägen
I konfigurationsläget kan du välja att styra decodern med lokfunktionstangenter istället för tillbehörskommandon.

- **F4 = ON ➔** Inaktivera lokstyrning *(standard)*  
- **F5 = ON ➔** Aktivera lokfunktionsläge *(F1–F8)* — använder 1 adress  
- **F6 = ON ➔** Aktivera 4-funktionsläge *(F1–F4)* — använder 2 adresser  

Det möjliggör ultrasnabb växling med reglage som Roco Lokmaus eller Multimaus.

---

## ⚖️ Adressoffset
För att kompensera för Rocos offset på 4, använd:

- **F7 = ON ➔** Aktivera 4-adressoffset  

---

## ⏰ Auto-växlingsläge
Aktivera automatisk växling av en vald motor:

- **F8 = ON ➔** Motorn växlar var 5:e sekund  
  - Hastigheten styrs av reglaget  
  - Reglagets riktning spelar ingen roll  
  - Reglage 0 = långsamt, Max = snabbt  

I detta läge är motorn inte längre slavad till reglagets funktionstangenter.

---

## 📊 Sammanfattning
- Använd knapparna för direkt inställning och servoreglering  
- Använd DCC-lokadress **9999** med **F0, F1, F2 OFF** för att aktivera konfigurationsläge  
- Använd **F1/F2** för att lagra servopositioner  
- Använd **F4–F8** för att aktivera lokfunktionsstyrning, adressoffset eller växlingslägen  

Alla OS-Servo-Decoders delar detta gränssnitt och denna logik.  
Ingen dator behövs. Inga CV:er. Bara koppla det, adressera det och kör.
