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
1. Installation
  1. S2OPC sur la machine (dockers, test avec serveur de démo)
  2. Zephyr: environnement (outils, SDK, etc.) et test sur la carte de développement
2. Portage de S2OPC sur Zephyr
  1. Établissement des travaux à réaliser / Identification des dépendances
    * Document des dépendances connues sur d'autres plateformes
    * Documentation Zephyr
    * Importation et compilation du code source de S2OPC sur Zephyr
  2. Outils de validation?
    * Tests unitaires: dépendances entre les modules et les tests, tests qui font appel à plusieurs modules
    * Intégration continue?
  3. Portage module par module: array, thread, etc.
  4. Compilation croisée de S2OPC et lien comme bibliothèque statique

### Contribution
Différences entre le développement bare-metal et sur OS embarqué
1. Gestion de la mémoire
  1. Registre, flash
  2. Allocation dynamique
2. Multitâche
  1. Interruption, ordonnancement
  2. Thread, sémaphore
3. Standardisation
  1. Bibliothèque ou framework propriétaire
  2. Posix

## Conclusion

## Bibliographie
