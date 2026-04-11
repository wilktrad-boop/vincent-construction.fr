---
title: "Schéma électrique guirlande LED 3 fils : branchement et explication"
slug: "schema-electrique-guirlande-led-3-fils"
date: 2025-11-18
description: "Comment brancher une guirlande LED à 3 fils ? Explication du rôle de chaque fil, schéma de câblage avec ou sans télécommande, et dépannage des erreurs courantes."
categories: ["Maison"]
tags: ["guirlande LED", "électricité", "câblage", "3 fils", "décoration", "branchement"]
summary: "Une guirlande LED à 3 fils dépasse le simple + et −. Le troisième fil sert à la commande (PWM, télécommande, variateur). Voici comment identifier chaque fil et les brancher correctement."
ShowToc: true
TocOpen: true
cover:
  image: "/images/guirlande-led-3-fils.webp"
  alt: "Schéma branchement guirlande LED 3 fils"
---

## Pourquoi une guirlande LED peut avoir 3 fils ?

Une guirlande LED basique n'a besoin que de 2 fils : un positif (+) et un négatif (−). Si votre guirlande a **3 fils**, c'est pour l'une de ces raisons :

1. **Guirlande à effets lumineux** : le 3ème fil est un fil de données ou de commande pour piloter les LEDs indépendamment (clignotement, dégradé, chenillard)
2. **Guirlande avec fil de masse séparé** : certaines guirlandes alimentées en 230V ont une phase, un neutre, et un fil de terre
3. **Guirlande RGB ou RGBW** : en 12V ou 24V, les 3 fils correspondent aux 3 canaux de couleur (R, G, B) avec un fil commun (+) séparé ou inclus
4. **Guirlande avec contrôleur intégré** : 2 fils alimentation + 1 fil signal de télécommande IR

## Identifier le rôle des 3 fils

### Par la couleur (convention courante)

| Couleur | Fonction probable |
|---------|-------------------|
| Rouge | + (positif, Vcc) |
| Noir | − (négatif, GND) |
| Blanc ou jaune | Signal / données |
| Vert/Jaune | Terre (PE) en 230V |

**Attention** : il n'existe pas de norme universelle pour les guirlandes de décoration. Mesurez toujours avec un multimètre avant de brancher.

### Par mesure au multimètre

Avec le multimètre en mode tension DC (si alimentation basse tension) :
1. Branchez l'alimentation sans connecter la guirlande
2. Mesurez entre chaque paire de fils
3. La paire qui donne la tension d'alimentation (ex : 12V) = + et −
4. Le 3ème fil est le signal

En mode continuité (diode) entre les 3 fils éteints :
- Le fil commun (GND) sera en continuité avec les cathodes des LEDs

## Schéma de branchement selon le type

### Type 1 : Guirlande LED 12V avec fil de données (WS2812B, addressable)

Ces guirlandes "intelligentes" utilisent un protocole numérique sur le 3ème fil.

```
Alimentation 12V (ou 5V selon modèle) :
+Vcc ─── Fil rouge (VCC)
GND  ─── Fil noir  (GND)
Signal depuis contrôleur ─── Fil blanc (DIN)
```

Le fil de données doit être connecté à un contrôleur (Arduino, NodeMCU, module dédié) pour fonctionner. Sans signal sur DIN, la guirlande reste éteinte ou affiche une couleur fixe selon le modèle.

### Type 2 : Guirlande 230V (phase + neutre + terre)

```
Tableau électrique :
Phase (noir/rouge) ─── Fil phase guirlande
Neutre (bleu) ────── Fil neutre guirlande
Terre (vert/jaune) ── Fil terre guirlande
```

Ne jamais raccorder une guirlande 230V sans relier la terre si elle est présente sur le câble.

### Type 3 : Guirlande RGB 12V (cathode commune)

Sur une guirlande RGB à 4 fils (3 couleurs + 1 commun) ou 3 fils (anode commune, 3 cathodes) :

**Anode commune (+ commun) :**
```
+12V ─── Fil commun (+)
Contrôleur R ─── Fil Rouge
Contrôleur G ─── Fil Vert
Contrôleur B ─── Fil Bleu
```

**Cathode commune (− commun) :**
```
Contrôleur R ─── Fil Rouge
Contrôleur G ─── Fil Vert
Contrôleur B ─── Fil Bleu
GND ─── Fil commun (−)
```

Les deux configurations existent. Le contrôleur RGB doit être compatible avec l'une ou l'autre.

## Branchement sans contrôleur (allumage fixe)

Si vous souhaitez allumer une guirlande LED 3 fils sans contrôleur en couleur fixe :
- Pour une guirlande à données : branchez seulement VCC et GND. Selon le modèle, les LEDs s'allument en blanc ou restent éteintes. Un signal fixe sur DIN (HIGH ou LOW) peut forcer une couleur.
- Pour une guirlande RGB : court-circuitez les 3 fils de couleur ensemble pour un blanc approximatif, ou n'alimentez qu'un fil couleur pour une couleur unie.

## Dépannage

| Symptôme | Cause probable | Solution |
|----------|---------------|----------|
| Guirlande ne s'allume pas | Fils inversés | Vérifier + et − |
| Moitié de la guirlande allumée | Coupure dans le fil de données | Vérifier continuité fil signal |
| Couleurs incorrectes | Fils R/G/B inversés | Permuter les fils de couleur |
| Scintillement | Alimentation insuffisante | Vérifier ampérage du bloc |
| LEDs brûlées au branchement | Tension trop élevée | Vérifier tension : 5V, 12V ou 24V ? |

## Sécurité

- N'intervenez jamais sur une guirlande 230V branchée au secteur
- Pour les guirlandes basse tension (5V, 12V, 24V), le risque électrique est faible mais la surchauffe d'une alimentation sous-dimensionnée peut être dangereuse
- Utilisez des alimentations à découpage certifiées (marquage CE)

{{< amazon >}}
- [Contrôleur LED RGB WiFi 12V](https://www.amazon.fr/s?k=controleur+led+rgb+wifi+12v&tag=wtr097-21)
- [Alimentation 12V 5A pour guirlande LED](https://www.amazon.fr/s?k=alimentation+12v+5a+guirlande+led&tag=wtr097-21)
- [Multimètre numérique débutant](https://www.amazon.fr/s?k=multimetre+numerique+debutant&tag=wtr097-21)
{{< /amazon >}}
