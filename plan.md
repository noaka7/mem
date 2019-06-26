# Plan
---
## Introduction

## Chapitres

### Contexte

### Problématique

### État de l'art

### Spécification/conception
#### Systerel
S2OPC est une implémentation de OPC Unified Architecture, un protocole de communication industriel. S2OPC est déjà déployé sur Linux et sur Windows. Le sujet du stage est de porter S2OPC sur Zephyr, un système d'exploitation embarqué et temps réel. Il s'agira, à partir des dépendances connues de la pile S2OPC à Windows, d'identifier les équivalences sur Zephyr ou de proposer des solutions de contournement

### Réalisation
#### Systerel
1. Installation de S2OPC sur la machine (test avec serveur de démo)
2. Installation de Zephyr: environnement (outils, SDK, etc.) et test sur la carte de développement
3. Portage de S2OPC sur Zephyr
  1. Importation du code source de S2OPC vers Zephyr
  2. Compilation croisée de S2OPC et lien comme bibliothèque statique
  3. Correction des dépendances de S2OPC, module par module: array, threads, etc.

Tests unitaires avec des assertions simples (assert.h)

### Contribution

## Conclusion

## Bibliographie
