# Machine à pince – Projet P2I 3

Conception complète, sous **Solid Edge**, d'une machine à pince de fête foraine (« claw machine ») : structure, axes motorisés X / Y / Z, pince à électro-aimant, capteurs de fin de course, électronique de commande et interface joueur.

![Vue d'ensemble de la machine](images/vue_ensemble.png)

## Le projet

L'objectif était de concevoir une machine fonctionnelle et fabricable dans laquelle le joueur pilote une pince au joystick pour attraper un lot dans le plateau de jeu, puis le déposer dans la trappe de sortie.

La machine se décompose en plusieurs sous-ensembles :

| Sous-ensemble | Dossier | Description |
|---|---|---|
| **Bâti** | `FINAL/bati` | Cadre en profilés aluminium 20×20 (540×500), plateau de jeu en MDF, protections en plexiglas, tiroir de récupération, pieds |
| **Axe X** | `FINAL/Axe_x` | Chariot entraîné par moteur pas-à-pas NEMA 17 et courroie GT2, guidé sur rail par des galets |
| **Glissière** | `FINAL/glissière` | Galets sur roulements (625) roulant dans les rainures du profilé 20×40 |
| **Support pince / axe Z** | `FINAL/support pince` | Tôles pliées supportant le treuil (moteur Z + poulie à rainure) qui monte et descend la pince |
| **Pince** | `FINAL/Pince` | Pince à 3 griffes actionnée par électro-aimant via un système bielle-griffe |
| **Canne télescopique** | `FINAL/canne à pêche` | Tube télescopique guidant la pince verticalement et l'empêchant de tourner |
| **Capteurs** | `FINAL/Capteur` | Micro-switchs Grove de fin de course pour la prise d'origine des axes X, Y et Z |
| **Électronique** | `FINAL/bati/platine_compo` | Arduino Mega 2560 + shield Grove, drivers micro-pas, convertisseur LM2596, module relais (électro-aimant), alimentation |
| **Interface joueur** | `FINAL/bati/interface utilisateur finale` | Boîtier à créneaux avec joystick KY-023, bouton Grove et écran LCD 4 lignes I²C |

L'assemblage général est `Pince_finale/assemblage final.asm`.

## La pince

![Détail de la pince](images/pince.png)

La pince est le cœur du projet :

- **Actionnement par électro-aimant** (bloc rouge) : en tirant l'axe central, il entraîne les **bielles** qui referment les **3 griffes** autour du lot ; au relâchement, la pince s'ouvre.
- Ouverture des griffes d'environ **49 mm**, adaptée à la taille des lots.
- Pièces en **tôlerie pliée** (pièces vertes : pièce haute, pièce basse) pour rester légères et faciles à fabriquer.
- Axes Ø8 mm et entretoises pour les liaisons pivot.
- Une **butée** déclenche le capteur Z pour détecter la position haute.

## Ce que j'ai réalisé

- Modélisation 3D des pièces et des sous-ensembles sous Solid Edge (pièces volumiques `.par`, tôlerie `.psm`, assemblages `.asm`).
- Conception du mécanisme de la pince (cinématique bielle / griffe, choix de l'électro-aimant).
- Conception des axes motorisés : supports moteurs, poulies, liens de courroie, galets de guidage.
- Intégration des capteurs de fin de course et de leurs supports.
- Intégration de l'électronique (carte de commande, drivers, alimentation) et de l'interface utilisateur dans le bâti.
- Mise en plan / préparation des pièces pour la fabrication (tôlerie, découpe MDF et plexiglas).

## Technologies et composants

- **CAO** : Solid Edge
- **Structure** : profilés aluminium 20×20 / 20×40, MDF, PMMA (plexiglas), tôle pliée
- **Motorisation** : 3 moteurs pas-à-pas NEMA 17, courroies et poulies GT2
- **Commande** : Arduino Mega 2560, shield Grove, drivers micro-pas, relais
- **Interface** : joystick KY-023, bouton Grove, écran LCD I²C 4 lignes

## Ouvrir les fichiers

Les fichiers sont au format natif **Solid Edge**. Ouvrir `Pince_finale/assemblage final.asm` en conservant l'arborescence des dossiers pour que les liens entre pièces et assemblages restent valides.

```
Pince_finale/
├── assemblage final.asm      ← assemblage général
└── FINAL/
    ├── Axe_x/
    ├── bati/
    ├── canne à pêche/
    ├── Capteur/
    ├── glissière/
    ├── Pince/
    └── support pince/
```
