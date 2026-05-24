> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; 🇫🇷 FR &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# Manuel des décodeurs OS-Servo

## 📘 Introduction
Le OS-Servo-Decoder est un décodeur DCC accessoire simple et robuste conçu pour piloter jusqu'à 8 servomoteurs. Il prend en charge les réseaux ferroviaires miniatures modernes avec des options de configuration flexibles, des modules relais externes pour la commutation de polarité (optionnels) et une commande directe via des interrupteurs d'entrée, des commandes DCC accessoire et des fonctions de locomotive (F1–F8).

---

## 📚 Table des matières

- [Manuel des décodeurs OS-Servo](#manuel-des-décodeurs-os-servo)
  - [📘 Introduction](#-introduction)
  - [📚 Table des matières](#-table-des-matières)
  - [🔧 Caractéristiques](#-caractéristiques)
  - [🔌 Connexion du décodeur](#-connexion-du-décodeur)
  - [💪 Commande des sorties servo](#-commande-des-sorties-servo)
  - [🛠️ Mode de configuration DCC](#️-mode-de-configuration-dcc)
  - [🛠️ Mode de configuration par bouton](#️-mode-de-configuration-par-bouton)
  - [🌟 Mémorisation des positions servo](#-mémorisation-des-positions-servo)
  - [🚗 Modes de fonctions de locomotive](#-modes-de-fonctions-de-locomotive)
  - [⚖️ Décalage d'adresse](#️-décalage-dadresse)
  - [⏰ Mode basculement automatique](#-mode-basculement-automatique)
  - [📊 Récapitulatif](#-récapitulatif)

---

## 🔧 Caractéristiques
- Commande jusqu'à 8 servos  
- Utilise des borniers à vis enfichables pour un câblage facile  
- Modules relais externes  
- Prend entièrement en charge :  
  - Le mouvement standard de l'aiguille  
  - La commutation de polarité (lorsque prise en charge)  
  - Les positions finales de servo réglables (via boutons)  
- Configuration autonome : aucun PC, CV ou programmateur requis  
- Commande optionnelle par fonctions de locomotive DCC (F1–F18)  
- Prend en charge le décalage d'adresse Roco de 4

---

## 🔌 Connexion du décodeur

![OS-Servo-Decoder-8 avec différentes configurations d'extension relais](board_w_extensions.png)

*Le OS-Servo-Decoder-8 présenté avec divers modules d'extension relais branchés (en haut à gauche : relais bistables ; en haut à droite : relais à usage général ; en bas : combinaisons avec servos connectés).*

Le OS-Servo-Decoder-8 utilise la même disposition de câblage que le OS-Solenoid-Decoder :

- **En-tête supérieur (POW / DCC) :** Connectez soit la tension de voie DCC, soit une alimentation DC (max. 19 V)
- ⚠️ **Important :** N'utilisez pas de tension AC — cela endommagerait le décodeur
- **En-têtes servo (côté droit) :** Connectez chaque servomoteur au connecteur 3 broches
  - Brochage standard : **GND — +5 V — Signal**
- **Connecteurs relais (côté gauche) :** A, COM, B — pour les modules d'extension de relais OS

---

## 💪 Commande des sorties servo

Chaque sortie servo est commandée par une adresse DCC accessoire. Lorsque le décodeur reçoit une commande DCC pour une adresse assignée, il déplace le servo en douceur vers la position mémorisée pour cet état de commande (DROITE ou COURBE).

- L'envoi de la commande **DROITE** déplace le servo vers sa position finale droite mémorisée.
- L'envoi de la commande **COURBE** déplace le servo vers sa position finale courbe mémorisée.
- Si des modules d'extension relais sont installés, les contacts relais commutent en synchronisation avec le servo pour la polarisation du cœur.

Les positions finales du servo sont mémorisées à l'aide des touches de fonction de locomotive — voir [Mémorisation des positions servo](#-mémorisation-des-positions-servo) ci-dessous.

---

## 🛠️ Mode de configuration DCC

Le décodeur prend en charge un mode de configuration fonctionnant entièrement depuis votre manette DCC — aucun ordinateur, aucun programmateur CV requis.

Pour entrer en mode de configuration, sélectionnez l'adresse de locomotive **9999** sur votre manette et réglez **F0, F1 et F2 tous sur OFF**. Le décodeur entrera en mode configuration et acceptera les commandes de touches de fonction.

Une fois en mode configuration, utilisez les touches de fonction (F1–F8) pour régler les options décrites dans les sections ci-dessous. Appuyez sur **F0 = OFF** pour quitter et revenir au fonctionnement normal.

---

## 🛠️ Mode de configuration par bouton

La carte comporte deux boutons physiques : **CONFIGURE** et **TOGGLE**.

- **CONFIGURE** — entre directement en mode configuration, sans nécessiter de manette. Le décodeur répond avec un retour LED indiquant le réglage actif.
- **TOGGLE** — bascule manuellement la sortie servo actuellement sélectionnée entre ses deux positions mémorisées. Utile pour tester le mouvement et ajuster les positions finales.

---

## 🌟 Mémorisation des positions servo
En mode de fonctionnement normal, utilisez ces fonctions pour programmer :

- **F1 = ON ➔** Sauvegarder la position actuelle comme *COURBE*  
- **F2 = ON ➔** Sauvegarder la position actuelle comme *DROITE*  
- **F3 = ON ➔** Inverser le relais de cœur *(modèle 6 relais uniquement)*  
- **F0 = OFF ➔** Quitter le mode de fonctionnement  

---

## 🚗 Modes de fonctions de locomotive
En mode configuration, vous pouvez choisir de commander le décodeur en utilisant les touches de fonction de locomotive plutôt que les commandes accessoire.

- **F4 = ON ➔** Désactiver la commande locomotive *(par défaut)*  
- **F5 = ON ➔** Activer le mode fonction locomotive *(F1–F8)* — utilise 1 adresse  
- **F6 = ON ➔** Activer le mode 4 fonctions *(F1–F4)* — utilise 2 adresses  

Cela permet une commutation ultra-rapide avec des manettes comme la Roco Lokmaus ou la Multimaus.

---

## ⚖️ Décalage d'adresse
Pour compenser le décalage de 4 de Roco, utilisez :

- **F7 = ON ➔** Activer le décalage d'adresse de 4  

---

## ⏰ Mode basculement automatique
Activer le basculement automatique d'un moteur sélectionné :

- **F8 = ON ➔** Le moteur bascule toutes les 5 secondes  
  - La vitesse est contrôlée par la manette  
  - Le sens de la manette n'a pas d'importance  
  - Manette à 0 = lent, Maximum = rapide  

Dans ce mode, le moteur n'est plus asservi aux touches de fonction de la manette.

---

## 📊 Récapitulatif
- Utilisez les boutons pour la configuration directe et le réglage des servos  
- Utilisez l'adresse de locomotive DCC **9999** avec **F0, F1, F2 sur OFF** pour entrer en mode configuration  
- Utilisez **F1/F2** pour mémoriser les positions des servos  
- Utilisez **F4–F8** pour activer la commande par fonctions de locomotive, le décalage d'adresse ou les modes de basculement  

Tous les OS-Servo-Decoders partagent cette interface et cette logique.  
Aucun ordinateur nécessaire. Aucun CV. Câblez simplement, adressez et faites rouler.
