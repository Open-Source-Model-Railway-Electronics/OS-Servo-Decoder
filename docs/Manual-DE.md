> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; 🇩🇪 DE &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# OS-Servo-Decoder Handbuch

## 📘 Einführung
Der OS-Servo-Decoder ist ein einfacher und robuster DCC-Zubehördecoder für die Steuerung von bis zu 8 Servomotoren. Er unterstützt moderne Modellbahnen mit flexiblen Konfigurationsmöglichkeiten, externen Relaismodulen für Polaritätsumschaltung (optional) und direkter Steuerung über Eingangsschalter, DCC-Zubehörbefehle und Lokfunktionen (F1–F8).

---

## 📚 Inhaltsverzeichnis

- [OS-Servo-Decoder Handbuch](#os-servo-decoder-handbuch)
  - [📘 Einführung](#-einführung)
  - [📚 Inhaltsverzeichnis](#-inhaltsverzeichnis)
  - [🔧 Merkmale](#-merkmale)
  - [🔌 Anschließen des Decoders](#-anschließen-des-decoders)
  - [💪 Steuerung der Servoausgänge](#-steuerung-der-servoausgänge)
  - [🛠️ DCC-Konfigurationsmodus](#️-dcc-konfigurationsmodus)
  - [🛠️ Tasten-Konfigurationsmodus](#️-tasten-konfigurationsmodus)
  - [🌟 Speichern von Servopositionen](#-speichern-von-servopositionen)
  - [🚗 Lokfunktionsmodi](#-lokfunktionsmodi)
  - [⚖️ Adress-Offset](#️-adress-offset)
  - [⏰ Automatischer Umschaltmodus](#-automatischer-umschaltmodus)
  - [📊 Zusammenfassung](#-zusammenfassung)

---

## 🔧 Merkmale
- Steuert bis zu 8 Servos  
- Verwendet steckbare Schraubklemmen für einfache Verdrahtung  
- Externe Relaismodule  
- Vollständige Unterstützung für:  
  - Standardmäßige Weichenbewegung  
  - Polaritätsumschaltung (wo unterstützt)  
  - Einstellbare Servo-Endpositionen (über Tasten)  
- Eigenständige Konfiguration: kein PC, keine CVs oder Programmierer erforderlich  
- Optionale DCC-Lokfunktionssteuerung (F1–F18)  
- Unterstützt Roco 4-Adress-Offset  

---

## 🔌 Anschließen des Decoders

![OS-Servo-Decoder-8 mit verschiedenen Relaiserweiterungs-Konfigurationen](board_w_extensions.png)

*Der OS-Servo-Decoder-8 mit verschiedenen eingesteckten Relaiserweiterungsmodulen (oben links: bistabile Relais; oben rechts: Universalrelais; unten: Kombinationen mit angeschlossenen Servos).*

Der OS-Servo-Decoder-8 verwendet dasselbe Verdrahtungsschema wie der OS-Solenoid-Decoder:

- **Obere Stiftleiste (POW / DCC):** Entweder DCC-Gleisspannung oder eine DC-Stromversorgung anschließen (max. 19 V)
- ⚠️ **Wichtig:** Keine Wechselspannung verwenden — dies beschädigt den Decoder
- **Servo-Stiftleisten (rechte Seite):** Jeden Servomotor an den 3-poligen Stecker anschließen
  - Standardbelegung: **GND — +5 V — Signal**
- **Relais-Stecker (linke Seite):** A, COM, B — für OS-Relaiserweiterungsmodule

---

## 💪 Steuerung der Servoausgänge

Jeder Servoausgang wird durch eine DCC-Zubehöradresse gesteuert. Wenn der Decoder einen DCC-Befehl für eine zugewiesene Adresse empfängt, bewegt er den Servo gleichmäßig zur gespeicherten Position für diesen Befehlszustand (GERADE oder GEBOGEN).

- Das Senden des **GERADE**-Befehls bewegt den Servo zu seiner gespeicherten geraden Endposition.
- Das Senden des **GEBOGEN**-Befehls bewegt den Servo zu seiner gespeicherten gebogenen Endposition.
- Wenn Relaiserweiterungsmodule eingebaut sind, schalten die Relaiskontakte synchron mit dem Servo für die Herzstück-Polarisierung.

Servo-Endpositionen werden mit Lokfunktionstasten gespeichert — siehe [Speichern von Servopositionen](#-speichern-von-servopositionen) unten.

---

## 🛠️ DCC-Konfigurationsmodus

Der Decoder unterstützt einen Konfigurationsmodus, der vollständig über dein DCC-Fahrgerät funktioniert — kein Computer, kein CV-Programmierer erforderlich.

Um den Konfigurationsmodus aufzurufen, Lokadresse **9999** am Fahrgerät wählen und **F0, F1 und F2 alle auf AUS** stellen. Der Decoder wechselt in den Konfigurationsmodus und akzeptiert Funktionstastenbefehle.

Im Konfigurationsmodus die Funktionstasten (F1–F8) verwenden, um Optionen wie in den folgenden Abschnitten beschrieben einzustellen. **F0 = AUS** drücken, um zu beenden und zum Normalbetrieb zurückzukehren.

---

## 🛠️ Tasten-Konfigurationsmodus

Die Platine hat zwei physische Tasten: **CONFIGURE** und **TOGGLE**.

- **CONFIGURE** — wechselt direkt in den Konfigurationsmodus, ohne ein Fahrgerät zu benötigen. Der Decoder antwortet mit LED-Feedback, das die aktive Einstellung anzeigt.
- **TOGGLE** — schaltet den aktuell ausgewählten Servoausgang manuell zwischen seinen beiden gespeicherten Positionen um. Nützlich zum Testen der Bewegung und zum Anpassen der Endpositionen.

---

## 🌟 Speichern von Servopositionen
Im Fahrmodus diese Funktionen zum Programmieren verwenden:

- **F1 = EIN ➔** Aktuelle Position als *GEBOGEN* speichern  
- **F2 = EIN ➔** Aktuelle Position als *GERADE* speichern  
- **F3 = EIN ➔** Frog-Relais invertieren *(nur 6-Relais-Modell)*  
- **F0 = AUS ➔** Fahrmodus beenden  

---

## 🚗 Lokfunktionsmodi
Im Konfigurationsmodus kann gewählt werden, den Decoder über Lokfunktionstasten anstelle von Zubehörbefehlen zu steuern.

- **F4 = EIN ➔** Lok-Steuerung deaktivieren *(Standard)*  
- **F5 = EIN ➔** Lokfunktionsmodus aktivieren *(F1–F8)* — verwendet 1 Adresse  
- **F6 = EIN ➔** 4-Funktions-Modus aktivieren *(F1–F4)* — verwendet 2 Adressen  

Dies ermöglicht ultraschnelles Schalten mit Fahrgeräten wie Roco Lokmaus oder Multimaus.

---

## ⚖️ Adress-Offset
Um Rocos Offset von 4 zu kompensieren, verwenden:

- **F7 = EIN ➔** 4-Adress-Offset aktivieren  

---

## ⏰ Automatischer Umschaltmodus
Automatisches Umschalten eines ausgewählten Motors aktivieren:

- **F8 = EIN ➔** Motor schaltet alle 5 Sekunden um  
  - Geschwindigkeit wird durch das Fahrgerät gesteuert  
  - Fahrtrichtung des Fahrgeräts spielt keine Rolle  
  - Fahrgerät 0 = langsam, Maximum = schnell  

In diesem Modus ist der Motor nicht mehr an die Funktionstaten des Fahrgeräts gebunden.

---

## 📊 Zusammenfassung
- Tasten für direkte Einrichtung und Servo-Anpassung verwenden  
- DCC-Lokadresse **9999** mit **F0, F1, F2 AUS** verwenden, um den Konfigurationsmodus aufzurufen  
- **F1/F2** zum Speichern von Servopositionen verwenden  
- **F4–F8** zum Aktivieren von Lokfunktionssteuerung, Adress-Offset oder Umschaltmodi verwenden  

Alle OS-Servo-Decoder teilen diese Schnittstelle und Logik.  
Kein Computer erforderlich. Keine CVs. Einfach verkabeln, adressieren und fahren.
