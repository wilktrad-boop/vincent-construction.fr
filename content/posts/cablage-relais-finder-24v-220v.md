---
title: "Câblage relais Finder 24V 220V : schéma et branchement"
slug: "cablage-relais-finder-24v-220v"
date: 2025-11-17
description: "Comment câbler un relais Finder bobine 24V pour piloter un circuit 220V : schéma de branchement, numéros de broches, et exemples d'application pratique."
categories: ["Maison"]
tags: ["relais", "Finder", "électricité", "câblage", "automatisme", "24V", "220V"]
summary: "Un relais Finder 24V permet de piloter un circuit 220V depuis une commande basse tension. Voici comment l'identifier, le câbler correctement et éviter les erreurs classiques."
ShowToc: true
TocOpen: true
cover:
  image: "/images/relais-finder-24v.webp"
  alt: "Câblage relais Finder 24V 220V schéma"
---

## Qu'est-ce qu'un relais Finder et à quoi sert-il ?

Un relais électromécanique Finder est un composant d'automatisme qui permet de **piloter un circuit de puissance (220V) à partir d'un signal de commande basse tension (24V DC ou AC)**. C'est le principe de l'interrupteur commandé à distance.

**Applications courantes :**
- Piloter un contacteur de volet roulant depuis un automate ou Arduino
- Couper une alimentation 220V sur signal d'un détecteur (présence, température)
- Séparer galvaniquement une commande basse tension d'un circuit 230V

Finder est une marque italienne reconnue en automatisme industriel et résidentiel. Leurs relais sont très répandus dans les coffrets électriques et domotique.

## Identifier votre relais Finder

La référence est marquée sur le corps du relais. Exemples courants :

| Référence | Bobine | Contact | Intensité max |
|-----------|--------|---------|--------------|
| 40.31 | 24V AC/DC | 1RT (1 inverseur) | 10 A |
| 40.52 | 24V AC/DC | 2RT (2 inverseurs) | 8 A |
| 44.52 | 24V AC/DC | 2RT avec LED | 8 A |
| 41.31 | 24V AC | 1RT | 10 A |

Le suffixe indique la tension bobine : **.024** = 24V DC, **.024.0060** = 24V AC.

## Schéma de branchement

### Relais Finder 40.31 (le plus courant — 1 contact inverseur, bobine 24V)

Ce relais 8 broches se monte sur socle (référence 95.05 ou 95.85). Les numéros de broches sont gravés sur le corps et indiqués sur le schéma du couvercle.

**Bobine (commande 24V) :**
- **Broche A1** : + 24V DC (ou phase 24V AC)
- **Broche A2** : 0V DC (ou neutre 24V AC)

**Contact inverseur (circuit 220V) :**
- **Broche 11** : Commun (COM) — à relier à la phase 220V
- **Broche 14** : Normalement Ouvert (NO) — circuit fermé quand relais activé
- **Broche 12** : Normalement Fermé (NF) — circuit fermé quand relais au repos

### Câblage type : piloter une charge 220V depuis un signal 24V

```
Alimentation 24V DC :
(+) ─────────────── A1 [RELAIS]
(-)  ─────────────── A2 [RELAIS]

Circuit 220V :
Phase 230V ─────── 11 (COM)
              └── 14 (NO) ──── Charge 220V ──── Neutre 230V
```

Quand le 24V est appliqué sur A1/A2, la bobine s'excite, le contact bascule de NF vers NO, et la charge 220V est alimentée.

### Câblage avec interrupteur de commande basse tension

```
+24V ── [Interrupteur 24V] ── A1
                               A2 ── GND (0V)

Phase 230V ── 11 ── 14 ── Charge ── Neutre
```

## Socle Finder 95.05 : identification des broches

Le socle 95.05 (pour relais 8 broches) porte les mêmes numéros que le relais. La face du socle (côté câblage, montage rail DIN) est miroir : vérifiez toujours sur la sérigraphie du socle, pas sur la mémoire.

**Astuce** : la diagonale entre A1 et A2 sur le socle 95.05 est la plus grande distance entre deux bornes. C'est un repère visuel utile.

## Relais Finder avec LED indicateur

Les modèles 44.xx et 46.xx intègrent une LED qui s'allume quand la bobine est excitée. Très pratique pour le diagnostic : si la LED est allumée mais la charge ne s'active pas, c'est le contact qui est défaillant (pas la commande).

## Précautions et erreurs fréquentes

### Ne pas dépasser le courant nominal

Le 40.31 supporte 10A sous 250V AC. Pour des charges supérieures (moteur, convecteur > 2 kW), utilisez le relais pour piloter un contacteur de puissance, pas directement la charge.

### Bobine DC : respecter la polarité

Pour une bobine 24V DC, A1 doit recevoir le + et A2 le −. L'inversion empêche l'activation (ou, sur certains modèles avec diode de protection, peut endommager le circuit de commande).

### Protection contre les surtensions

Ajouter une diode de roue libre (1N4007) en antiparallèle sur la bobine d'un relais 24V DC pour protéger l'électronique de commande contre les pics de tension lors de la désexcitation.

### Marquage sur le socle

Toujours utiliser le socle prévu pour le relais. Un 8 broches ne rentre pas dans un socle 11 broches et inversement.

{{< amazon >}}
- [Relais Finder 40.31 bobine 24V 10A](https://www.amazon.fr/s?k=relais+finder+40.31+24v&tag=wtr097-21)
- [Socle relais Finder 95.05 rail DIN](https://www.amazon.fr/s?k=socle+finder+95.05&tag=wtr097-21)
- [Multimètre numérique pour électricité](https://www.amazon.fr/s?k=multimetre+numerique+electricite&tag=wtr097-21)
{{< /amazon >}}
