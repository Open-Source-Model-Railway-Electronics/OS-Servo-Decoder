> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; 🇳🇱 NL &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# OS-Servo-Decoders Handleiding

## 📘 Inleiding
De OS-Servo-Decoder is een eenvoudige en robuuste DCC-accessoire­decoder ontworpen voor het aansturen van maximaal 8 servo­motoren. Hij ondersteunt moderne modelbanen met flexibele configuratie­opties, externe relais­modules voor polariteits­schakeling (optioneel) en directe besturing via invoer­schakelaars, DCC-accessoire­commando's en locomotief­functies (F1–F8).

---

## 📚 Inhoudsopgave

- [OS-Servo-Decoders Handleiding](#os-servo-decoders-handleiding)
  - [📘 Inleiding](#-inleiding)
  - [📚 Inhoudsopgave](#-inhoudsopgave)
  - [🔧 Kenmerken](#-kenmerken)
  - [🔌 De decoder aansluiten](#-de-decoder-aansluiten)
  - [💪 De servo­uitgangen bedienen](#-de-servo­uitgangen-bedienen)
  - [🛠️ DCC-configuratie­modus](#️-dcc-configuratiemodus)
  - [🛠️ Knop­configuratie­modus](#️-knopconfiguratiemodus)
  - [🌟 Servo­posities opslaan](#-servopo­sities-opslaan)
  - [🚗 Locomotief­functie­modi](#-locomotieffunctiemodi)
  - [⚖️ Adres­offset](#️-adresoffset)
  - [⏰ Auto-wissel­modus](#-auto-wisselmodus)
  - [📊 Samenvatting](#-samenvatting)

---

## 🔧 Kenmerken
- Bestuurt tot 8 servo's  
- Gebruikt insteekbare schroef­klemmen voor eenvoudige bedrading  
- Externe relais­modules  
- Volledig ondersteunt:  
  - Standaard wissel­beweging  
  - Polariteits­schakeling (waar ondersteund)  
  - Instelbare servo­eindstanden (via knoppen)  
- Zelfstandige configuratie: geen pc, CV's of programmeurs vereist  
- Optionele DCC-locomotief­functiebe­sturing (F1–F18)  
- Ondersteunt Roco 4-adres­offset  

---

## 🔌 De decoder aansluiten

![OS-Servo-Decoder-8 met verschillende relais­uitbreidings­configuraties](board_w_extensions.png)

*De OS-Servo-Decoder-8 getoond met diverse relais­uitbreidings­modules aangesloten (linksboven: zelfhoudende relais; rechtsboven: algemeen­gebruik­relais; onder: combinaties met aangesloten servo's).*

De OS-Servo-Decoder-8 gebruikt dezelfde bedradingsindeling als de OS-Solenoid-Decoder:

- **Bovenste header (POW / DCC):** Sluit DCC-baan­spanning of een DC-voeding aan (max. 19 V)
- ⚠️ **Belangrijk:** Gebruik geen AC-spanning — dit beschadigt de decoder
- **Servo-headers (rechterzijde):** Sluit elke servo­motor aan op de 3-polige aansluiting
  - Standaard pin­indeling: **GND — +5 V — Signaal**
- **Relais­aansluitingen (linkerzijde):** A, COM, B — voor OS-relais­uitbreidings­modules

---

## 💪 De servo­uitgangen bedienen

Elke servo­uitgang wordt bestuurd door een DCC-accessoire­adres. Wanneer de decoder een DCC-commando ontvangt voor een toegewezen adres, beweegt de servo soepel naar de opgeslagen positie voor die commando­staat (RECHT of GEBOGEN).

- Het **RECHT**-commando beweegt de servo naar de opgeslagen rechte eindstand.
- Het **GEBOGEN**-commando beweegt de servo naar de opgeslagen gebogen eindstand.
- Als relais­uitbreidings­modules zijn geplaatst, schakelen de relais­contacten gelijktijdig met de servo voor hartpunt­polarisering.

Servo­eindstanden worden opgeslagen met locomotief­functie­toetsen — zie [Servo­posities opslaan](#-servopo­sities-opslaan) hieronder.

---

## 🛠️ DCC-configuratie­modus

De decoder ondersteunt een configuratie­modus die volledig werkt via uw DCC-handregelaar — geen computer, geen CV-programmeur vereist.

Om de configuratie­modus te activeren, selecteert u locomotief­adres **9999** op uw handregelaar en zet u **F0, F1 en F2 alle op UIT**. De decoder gaat de configuratie­modus in en accepteert functie­toets­commando's.

Eenmaal in de configuratie­modus, gebruikt u de functie­toetsen (F1–F8) om opties in te stellen zoals beschreven in de onderstaande secties. Druk op **F0 = UIT** om af te sluiten en terug te keren naar normale werking.

---

## 🛠️ Knop­configuratie­modus

De kaart heeft twee fysieke knoppen: **CONFIGURE** en **TOGGLE**.

- **CONFIGURE** — activeert de configuratie­modus direct, zonder een handregelaar. De decoder reageert met LED-feedback die de actieve instelling aangeeft.
- **TOGGLE** — schakelt de momenteel geselecteerde servo­uitgang handmatig tussen de twee opgeslagen standen. Handig voor het testen van beweging en het aanpassen van eindstanden.

---

## 🌟 Servo­posities opslaan
Gebruik in de rijmodus deze functies om te programmeren:

- **F1 = AAN ➔** Sla huidige positie op als *GEBOGEN*  
- **F2 = AAN ➔** Sla huidige positie op als *RECHT*  
- **F3 = AAN ➔** Keer hartpunt­relais om *(alleen 6-relais model)*  
- **F0 = UIT ➔** Verlaat rijmodus  

---

## 🚗 Locomotief­functie­modi
In de configuratie­modus kunt u kiezen om de decoder te bedienen via locomotief­functie­toetsen in plaats van accessoire­commando's.

- **F4 = AAN ➔** Locomotief­besturing uitschakelen *(standaard)*  
- **F5 = AAN ➔** Locomotief­functiemodus inschakelen *(F1–F8)* — gebruikt 1 adres  
- **F6 = AAN ➔** 4-functiemodus inschakelen *(F1–F4)* — gebruikt 2 adressen  

Dit maakt ultra­snel schakelen mogelijk via handregelaars zoals de Roco Lokmaus of Multimaus.

---

## ⚖️ Adres­offset
Om te compenseren voor de offset van 4 bij Roco, gebruik:

- **F7 = AAN ➔** 4-adres­offset inschakelen  

---

## ⏰ Auto-wissel­modus
Schakel automatisch wisselen van een geselecteerde motor in:

- **F8 = AAN ➔** Motor wisselt elke 5 seconden  
  - Snelheid wordt bepaald door de rijregelaar  
  - Rijrichting doet er niet toe  
  - Rijregelaar 0 = langzaam, Max = snel  

In deze modus is de motor niet langer gekoppeld aan de functie­toetsen van de rijregelaar.

---

## 📊 Samenvatting
- Gebruik de knoppen voor directe instelling en servo­aanpassing  
- Gebruik DCC-locomotief­adres **9999** met **F0, F1, F2 UIT** om de configuratie­modus te activeren  
- Gebruik **F1/F2** om servo­posities op te slaan  
- Gebruik **F4–F8** om locomotief­functiebe­sturing, adres­offset of wissel­modi in te schakelen  

Alle OS-Servo-Decoders delen deze interface en logica.  
Geen computer nodig. Geen CV's. Gewoon bedraden, adresseren en rijden.
