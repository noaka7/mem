# Plan
---
## Introduction

## Chapitres

### Contexte
Dans ce chapitre, afin de recontextualiser le cadre de mes missions, je donnerai des informations sur les entreprises d'accueil, leur situation, le produit ou le service sur lequel j'ai travaillé et l'organisation des équipes dont j'ai fait partie

#### Co-assist
Co-assist s'inscrit parmi les entreprises de la silver économie, à savoir le marché des seniors. En particulier, elle tente de mettre la technologie au service des personnes âgées avec son produit phare: un bracelet d'alerte. C'est pour l'instant un marché de niche sans acteur majeur. L'entreprise essaie de se distinguer de ses concurrents en proposant à la fois davantage de fonctionnalités et un coût moindre. Pour cela, elle repose sur une maîtrise en interne de toutes les étapes du produit, de la conception à la distribution. Aujourd'hui, Co-assist est divisé en deux sites avec un pôle technique au Havre et un pôle commercial à Paris

#### Systerel
Systerel est une société de prestation de services spécialisée dans l’ingénierie des systèmes et logiciels critiques. Elle développe entre autres ses propres produits dont celui sur lequel porte mon stage: S2OPC, une implémentation de protocole de communication industriel issu de la fondation OPC. Systerel est basée à Aix-en-Provence et possède aussi des sites à Malakoff et à Toulouse. L'entreprise compte en tout une centaine de salariés dont une vingtaine à Malakoff où j'effectue mon stage

### Problématique
Compte tenu de mes deux expériences durant cette formation, où j'ai pu travailler d'un côté sur du développement bare-metal et de l'autre sur OS embarqué, j'aimerais donner mon retour d'expérience et confronter ces deux approches notamment sur des points de programmation rencontrés

### État de l'art
Pour l'état de l'art, je présenterai les bases des projets depuis lesquelles je suis parti ainsi que les ressources sur lesquelles je me suis reposé lors de mon travail, comment elles m'ont servi, à savoir:

#### Co-assist
Ayant rejoint le projet lors du passage entre la version 1 et 2, je donnerai une perspective de ce qui existait déjà en terme de code et de fonctionnalités et j'expliquerai, éventuellement, comment j'ai pu m'en servir

Ressources:

* [Documentation du microcontrôleur](https://www.silabs.com/support/resources.p-microcontrollers_32-bit-mcus_leopard-gecko)
* [Documentation de l'altimètre](https://www.infineon.com/dgdl/Infineon-DPS310-DS-v01_00-EN.pdf?fileId=5546d462576f34750157750826c42242)
* [Documentation pour la carte SD](https://www.sdcard.org/downloads/pls/index.html)
* [Documentation de l'API du pilote pour l'écran](https://siliconlabs.github.io/Gecko_SDK_Doc/efm32g/html/group__glib.html)

#### Systerel
Le projet de portage de S2OPC sur Zephyr a commencé avec mon stage. Néanmoins, le travail de déploiement multi-plateforme sur Linux et sur Windows a été un point de départ. D'autre part, un portage sur un autre OS embarqué (FreeRTOS) se faisait en parallèle de mon stage

Ressources:

* [Dépôt de S2OPC](https://gitlab.com/systerel/S2OPC)
* [Référence de la carte de développement](https://www.nxp.com/support/developer-resources/evaluation-and-development-boards/i.mx-evaluation-and-development-boards/mimxrt1064-evk-i.mx-rt1064-evaluation-kit:MIMXRT1064-EVK)
* [Site de Zephyr](https://www.zephyrproject.org/)

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
Dans ce chapitre, je tenterai de comparer, dans la mesure de mon expérience personnelle, le développement bare-metal et sur OS embarqué. J'essaierai d'illustrer mes propos par des exemples avec des points rencontrés. Pour l'instant, je pense pouvoir parler des points suivants:

Les points 1) concernent la programmation bare-metal et 2) la programmation sur OS (embarqué)

* Gestion de la mémoire

	1. Registre, flash: nécessaire de connaître le matériel (spécification)

	2. Allocation dynamique: appel **système**

* Multitâche <br />
Pour ce point, je pense comparer comment s'organise le multitâche sur bare-metal et sur OS. 1) et 2) sont les outils que j'ai pu utilisé dans ce cadre

	1. Interruption, ordonnancement

	2. Thread, sémaphore

* Standardisation <br />
Ici, je pensais parler la standardisation du code, surtout présente sur OS embarqué, et son incidence sur la programmation

	1. Bibliothèque ou framework propriétaire

	2. Posix

À la fin, il s'agit de s'être fait une idée sur quelques tenants et aboutissants entre le développement bare-metal et sur OS embarqué

## Conclusion

## Bibliographie
