# Plan
---
## Introduction

## Chapitres

### Contexte

### Problématique
Compte tenu de mes deux expériences durant cette formation, où j'ai pu travailler d'un côté sur du développement bare-metal et de l'autre sur OS embarqué, j'aimerais donner mon retour d'expérience et confronter ces deux approches notamment sur des points de programmation rencontrés

### État de l'art
todo

### Spécification/conception
#### Co-assist
Co-assist développe un bracelet d'alerte de chute. Ma mission était de travailler sur la partie "embarqué". Les objectifs principaux étaient d'améliorer la précision de la détection de chute et de la géolocalisation, d'intégrer un écran et d'afficher l'heure ainsi que des pictogrammes, et d'optimiser l'ergonomie de l'interface

#### Systerel
S2OPC est une implémentation de OPC Unified Architecture, un protocole de communication industriel. S2OPC est déjà déployé sur Linux et sur Windows. Le sujet du stage est de porter S2OPC sur Zephyr, un système d'exploitation embarqué et temps réel. Il s'agira, à partir des dépendances connues de la pile S2OPC à Windows, d'identifier les équivalences sur Zephyr ou de proposer des solutions de contournement

### Réalisation
#### Co-assist
Cette partie est pour l'instant plutôt désordonnée car je ne trouve pas de "fil conducteur". Comme je n'étais pas le seul à travailler sur le projet, ces réalisations constituent des briques qui n'ont pas de lien évident entre elles. Elles s'intègrent au projet plus ou moins indépendamment les unes des autres. Pour l'instant, j'ai regroupé les tâches en développement de pilotes de périphériques et en développement de modules applicatifs car les approches et les résultats de sortie attendus étaient différents

1. Développement de pilotes de périphériques <br />
Développement qui comprend la configuration du périphérique et la mise en place de ses échanges avec le système. Des configurations de registre ou des protocoles de communication bas niveau (I2C, SPI) ont été utilisé

  1. Capteur altimètre

  2. Carte SD

  3. Écran monochrome (debug)

2. Développement de modules applicatifs <br />
Développement de fonctionnalités pour répondre à des besoins spécifiques et qui repose souvent sur des API propriétaires ou internes

  1. Module "inactivité" (traitement de données accéléromètriques)

  2. Système d'acquisition de données

  3. Menu d'administration sur la montre (IHM)

  4. Compression d'images monochromes (algorithme de codage par plages)

#### Systerel
L'idée est de dégager de mon travail un "workflow" qui pourrait être réutilisé comme ligne directrice dans l'éventualité d'un autre portage

1. Installation <br />
Il s'agit ici de présenter le modèle de génération de S2OPC et de Zephyr ainsi que les outils nécessaires à installer sur le poste de travail

  1. S2OPC sur la machine (dockers, test avec serveur de démo)

  2. Zephyr: environnement (outils, SDK, etc.) et test sur la carte de développement

2. Portage de S2OPC sur Zephyr <br />
Il s'agit ici de distinguer les différentes étapes du portage, ainsi que les supports dont je me suis servi, et d'expliquer, pour chaque étape, les méthodes utilisées, le choix des solutions et les écueils rencontrées

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
Différences entre le développement bare-metal et sur OS embarqué <br />
Dans ce chapitre, basé sur mes expériences et mes recherches, je traiterai des différences de développement bare-metal et sur OS embarqué. J'aborderai en particulier des points que j'ai rencontré

* Gestion de la mémoire

  1. Registre, flash

  2. Allocation dynamique

* Multitâche

  1. Interruption, ordonnancement

  2. Thread, sémaphore

* Standardisation

  1. Bibliothèque ou framework propriétaire

  2. Posix

## Conclusion

## Bibliographie
