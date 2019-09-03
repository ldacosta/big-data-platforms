# Plateformes Big Data

Ce document explore les avantages et inconvénients d'utiliser diverses plateformes en science de données. 


Si suit une description sommaire des sections du document:
* Exploration des plateformes, pour chaque plateforme suivante : KNIME, H2O.ai, Domino, Databricks, décrire les avantages / inconvénients.


## Objectifs
1. Comprendre l'offre est la direction du marché dans le domaine de sciences des données.
1. Évaluer si les plateformes de sciences de données peuvent nous aider à accélérer le développement des modèles.


## Processus de création d'un modèle d'apprentissage machine
(ou _Processus d'analyse en sciences de données_)

Cette section décrit le processus permettant, à partir des données d'entraînement 
fournies par le client, de livrer un algorithme de prédiction / classification. 

[//]: # (Une courte description décrit ensuite comment ce processus est implémenté via les notebooks en python)

Le processus de création d'un modèle d'apprentissage machine commence par la compréhension de la problématique du client, 
et fini avec un algorithme qui permet soit de prédire ou de catégoriser un éventement par rapport aux événements historiques. 

[//]: # (Un simple exemple serait d’entraîner un algorithme à prédire la probabilité qu'un bâtiment passe au feu. L'algorithme est entraîné en utilisant les données historiques des feux de bâtiments.)
Le processus au complet peut être visualisé dans l'image suivante. Nous allons décrire chaque partie en détail ici-bas.

![Image](images/full.jpg)

### Nomenclature
Les acteurs dans ce schéma sont:
* **Client**: Personne qui '_commande_' le modèle
* **Consommateur**: personne qui utilise les prédictions / classification du modèle en production.
* **Data Scientist**: Personne responsable de la livraison du modèle au client. 
Ils font les rencontres avec le client, choisissent les données, entraînent le modèle et communiquent le résultat.
* **Data Engineer**: Personne responsable de certains aspects spécifiques du processus d'apprentissage machine
(eg, la mise en production et le _monitoring_ du modèle).
* **Annotateur**: Personne responsable d'annoter les données nécessaires pour entraîner le modèle d'apprentissage machine.

### Section Exploration
La section "Exploration" sert à définir les besoins réalistes est de créer un modèle permettant de faire de répondre à ces besoins.

Voci une description des tâches dans cette section; certaines sont explicites et ne nécessitent pas d'une description 
particulière:

* "Analyse de besoins avec le client"
* "Définition du besoin en termes de problème d'apprentissage machine"
* "Analyse exploratoire des données" (NB: boucle d'itération). 
* "Définir découpage train/test"
* "Revue de littérature" (NB: important de communiquer le résultat de la revue au client)
* La tâche "Préparation des données" sert à créer un set des données de base pouvant servir à entraîner le modèle. 
(NB: Le processus est itératif pour chaque une des sources des données). 
* "entraînement des modèles" 
* "(cas d'utilisation) [Apprentissage Actif](https://en.wikipedia.org/wiki/Active_learning_(machine_learning)". 
Cette technique est utilisée pour itérativement demander des données à chaque cycle d'entraînement (voir ). 
Ceci permet de réduire significativement le nombre d'échantillons nécessitant une annotation manuelle, 
en limitant jusqu'à un certain seuil la qualité du modèle entraîné. 
* "Présentation des résultats" 
    * souvent des visualisations. 
    * le client peut apporter des corrections sur certaines données.
    * le meilleur modèle peut être mis en production si la performance est satisfaisante. 

### Section Production Service
Sert à encapsuler le modèle dans un service en production et de le rendre disponible aux clients.

Voci une description des tâches dans cette section; certaines sont explicites et ne nécessitent pas d'une description 
particulière:

* "Service déployé qui encapsule le modèle entraîne" sert à encapsuler le meilleur modèle entraîné précédemment
 dans un service. 
    * Le client pourrait appeler le service via un API pour obtenir des prédictions / classification etc . 

### Section Production re-entraînement du modèle
Sert à créer un pipeline permettant de re-entraîner le modèle automatiquement et de le redéployer en production.

* La tâche "Monitoring de performances" surveille les performances du modèle sur les données de production 
via des KPI / indicateurs spécifiques. 
    * peut lancer le ré-entraînement. 
* "Annotation des données". 
* "ETL des données pour actualiser le jeu d'entraînement" cherche les données des diverses sources.
* "Re-entraînement du modèle".
* "Encapsulation du modèle dans un service". 
* "Déploiement du service".

## Critères d'analyse des divers cadriciels (_frameworks_)

Chaque cadriciel serait analysé selon les critères suivants:
1. **Besoin minimal d'infrastructure**: minimum d'infrastructure dont un client besoin pour commencer à utiliser 
la solution. 
1. **Impact sur le "_Processus de création du modèle d'apprentissage machine_"**: 
efficacité à réaliser diverses tâches du processus d'apprentissage machine.
1. **Courbe d'apprentissage pour chaque intervenant (DataScientist, DataEngineer)**
1. **Mise à l'échelle pour des volumes larges de données**: 
effort nécessaire (logiciels, infrastructure) afin de pouvoir travailler avec des set de données larges (1G+ ,10M+ de rangées).  
1. **Scalabilité organisationnelle et DevOps**: facilité de créer et déployer une large quantité de modèles 
par un large éventail de personnes. 

