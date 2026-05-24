> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; 🇮🇹 IT &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# Manuale OS-Servo-Decoder-8

## 📘 Introduzione
L'OS-Servo-Decoder è un decoder DCC per accessori semplice e robusto progettato per pilotare fino a 8 servomotori. Supporta i moderni plastici ferroviari digitali con opzioni di configurazione flessibili, moduli relè esterni per la commutazione della polarità (opzionali) e controllo diretto tramite interruttori di ingresso, comandi DCC per accessori e funzioni locomotiva (F1–F8).

---

## 📚 Indice

- [Manuale OS-Servo-Decoder-8](#manuale-os-servo-decoder-8)
  - [📘 Introduzione](#-introduzione)
  - [📚 Indice](#-indice)
  - [🔧 Caratteristiche](#-caratteristiche)
  - [🔌 Collegamento del Decoder](#-collegamento-del-decoder)
  - [💪 Controllo delle Uscite Servo](#-controllo-delle-uscite-servo)
  - [🛠️ Modalità di Configurazione DCC](#️-modalità-di-configurazione-dcc)
  - [🛠️ Modalità di Configurazione tramite Pulsante](#️-modalità-di-configurazione-tramite-pulsante)
  - [🌟 Memorizzazione delle Posizioni Servo](#-memorizzazione-delle-posizioni-servo)
  - [🚗 Modalità Funzioni Locomotiva](#-modalità-funzioni-locomotiva)
  - [⚖️ Offset Indirizzo](#️-offset-indirizzo)
  - [⏰ Modalità Commutazione Automatica](#-modalità-commutazione-automatica)
  - [📊 Riepilogo](#-riepilogo)

---

## 🔧 Caratteristiche
- Controlla fino a 8 servo  
- Utilizza morsetti a vite innestabili per un cablaggio semplice  
- Moduli relè esterni  
- Supporto completo per:  
  - Movimento standard degli scambi  
  - Commutazione della polarità (dove supportato)  
  - Posizioni finali del servo regolabili (tramite pulsanti)  
- Configurazione autonoma: non richiede PC, CV o programmatori  
- Controllo opzionale tramite funzioni locomotiva DCC (F1–F18)  
- Supporto offset a 4 indirizzi Roco  

---

## 🔌 Collegamento del Decoder

![OS-Servo-Decoder-8 con diverse configurazioni di estensione relè](board_w_extensions.png)

*L'OS-Servo-Decoder-8 mostrato con vari moduli relè di estensione inseriti (in alto a sinistra: relè a mantenimento; in alto a destra: relè a uso generale; in basso: combinazioni con servo collegati).*

L'OS-Servo-Decoder-8 utilizza lo stesso schema di cablaggio dell'OS-Solenoid-Decoder:

- **Connettore superiore (POW / DCC):** collegare la tensione del binario DCC oppure un'alimentazione DC (max 19 V)
- ⚠️ **Importante:** non utilizzare tensione AC — danneggerà il decoder
- **Connettori servo (lato destro):** collegare ciascun servomotore al connettore a 3 pin
  - Pinout standard: **GND — +5 V — Segnale**
- **Connettori relè (lato sinistro):** A, COM, B — per i moduli di estensione OS-relays

---

## 💪 Controllo delle Uscite Servo

Ogni uscita servo è controllata da un indirizzo DCC per accessori. Quando il decoder riceve un comando DCC per un indirizzo assegnato, sposta il servo in modo fluido verso la posizione memorizzata per quello stato di comando (DRITTO o CURVO).

- L'invio del comando **DRITTO** sposta il servo alla posizione finale dritta memorizzata.
- L'invio del comando **CURVO** sposta il servo alla posizione finale curva memorizzata.
- Se sono montati moduli relè di estensione, i contatti del relè commutano in sincronia con il servo per la polarizzazione del frog.

Le posizioni finali del servo vengono memorizzate utilizzando i tasti funzione della locomotiva — vedere [Memorizzazione delle Posizioni Servo](#-memorizzazione-delle-posizioni-servo) di seguito.

---

## 🛠️ Modalità di Configurazione DCC

Il decoder supporta una modalità di configurazione che funziona interamente dal proprio regolatore DCC — senza computer, senza programmatore CV.

Per accedere alla modalità di configurazione, selezionare l'indirizzo locomotiva **9999** sul proprio regolatore e impostare **F0, F1 e F2 tutti su OFF**. Il decoder entrerà in modalità configurazione e accetterà i comandi dei tasti funzione.

Una volta in modalità configurazione, utilizzare i tasti funzione (F1–F8) per impostare le opzioni come descritto nelle sezioni seguenti. Premere **F0 = OFF** per uscire e tornare al funzionamento normale.

---

## 🛠️ Modalità di Configurazione tramite Pulsante

La scheda dispone di due pulsanti fisici: **CONFIGURE** e **TOGGLE**.

- **CONFIGURE** — accede direttamente alla modalità di configurazione, senza necessità di un regolatore. Il decoder risponde con segnalazione LED che indica l'impostazione attiva.
- **TOGGLE** — commuta manualmente l'uscita servo selezionata tra le due posizioni memorizzate. Utile per testare il movimento e regolare le posizioni finali.

---

## 🌟 Memorizzazione delle Posizioni Servo
In modalità di esecuzione, utilizzare queste funzioni per programmare:

- **F1 = ON ➔** Salva la posizione attuale come *CURVO*  
- **F2 = ON ➔** Salva la posizione attuale come *DRITTO*  
- **F3 = ON ➔** Inverti il relè frog *(solo modello a 6 relè)*  
- **F0 = OFF ➔** Esci dalla modalità di esecuzione  

---

## 🚗 Modalità Funzioni Locomotiva
In modalità configurazione, è possibile scegliere di controllare il decoder tramite i tasti funzione locomotiva anziché i comandi per accessori.

- **F4 = ON ➔** Disabilita il controllo locomotiva *(predefinito)*  
- **F5 = ON ➔** Abilita la modalità funzione locomotiva *(F1–F8)* — utilizza 1 indirizzo  
- **F6 = ON ➔** Abilita la modalità a 4 funzioni *(F1–F4)* — utilizza 2 indirizzi  

Ciò consente una commutazione ultrarapida con regolatori come Roco Lokmaus o Multimaus.

---

## ⚖️ Offset Indirizzo
Per compensare l'offset di 4 di Roco, utilizzare:

- **F7 = ON ➔** Abilita l'offset a 4 indirizzi  

---

## ⏰ Modalità Commutazione Automatica
Abilitare la commutazione automatica di un motore selezionato:

- **F8 = ON ➔** Il motore commuta ogni 5 secondi  
  - La velocità è controllata dal regolatore  
  - La direzione del regolatore non ha importanza  
  - Regolatore a 0 = lento, Massimo = veloce  

In questa modalità, il motore non è più subordinato ai tasti funzione del regolatore.

---

## 📊 Riepilogo
- Utilizzare i pulsanti per la configurazione diretta e la regolazione del servo  
- Utilizzare l'indirizzo locomotiva DCC **9999** con **F0, F1, F2 OFF** per accedere alla modalità configurazione  
- Utilizzare **F1/F2** per memorizzare le posizioni del servo  
- Utilizzare **F4–F8** per abilitare il controllo tramite funzioni locomotiva, l'offset dell'indirizzo o le modalità di commutazione  

Tutti gli OS-Servo-Decoder condividono questa interfaccia e logica.  
Nessun computer necessario. Nessun CV. Basta cablarlo, impostare l'indirizzo e farlo funzionare.
