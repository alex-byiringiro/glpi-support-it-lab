

# `IT Support & Helpdesk Lab (GLPI)`

**Simulation d’un environnement de support informatique**, inspiré des pratiques utilisées en entreprise, déployé sur un laboratoire virtualisé et documenté étape par étape.

Ce projet a pour objectif de démontrer des compétences en **support IT, gestion des incidents et administration d’un outil de helpdesk**.  
Il met en pratique l’utilisation de **GLPI pour la gestion des tickets, des utilisateurs et des actifs IT**, tout en suivant une approche **structurée et professionnelle de la gestion du support informatique**.

##  Objectif du projet

Ce projet a pour objectif de démontrer la mise en place complète d’un **outil ITSM avec GLPI** dans un contexte professionnel.
Il couvre :

* [l’installation de GLPI sur Debian](01-installation/installation-glpi-debian11.md)
* [la configuration initiale](02-configuration/configuration-glpi-initiale.md)
* [la gestion des utilisateurs et des profils](02-configuration/gestion-utilisateurs-profils.md)
* [la gestion des tickets (incident / demande)](03-gestion-des-tickets/creation-ticket.md)
* [le cycle de vie d’un ticket](03-gestion-des-tickets/cycle-de-vie-ticket.md)
* [un workflow de support N1 / N2](03-gestion-des-tickets/workflow-support-n1-n2.md)
* des cas pratiques détaillés


## Architecture technique

* **OS serveur** : Debian 11
* **Serveur web** : Apache
* **Base de données** : MariaDB
* **Application ITSM** : GLPI (version 10.0.6)
* **Navigateur client** : Web


##  Structure du projet

```arduino
glpi-support-it-lab/
│
├── 01-installation/
│   └── installation-glpi-debian11.md
│
├── 02-configuration/
│   └── configuration-glpi-initiale.md
│
├── 03-gestion-glpi/
│   ├── gestion-utilisateurs-profils.md
│   ├── creation-ticket.md
│   ├── cycle-de-vie-ticket.md
│   └── workflow-support-n1-n2.md
│
├── 04-cas-pratiques/
│   ├── ticket-perte-internet.md
│   └── ticket-poste-non-demarre.md
|
├── 05-screenshots/
│   ├── 01-dashboard-glpi.png
|   ├── 02-profils-utilisateurs
|   ├── 03-utilisateurs
|   ├── 04-creation-ticket
|   ├── 05-ticket-en-cours
|   └── 06-ticket-resolu
└── README.md
```


##  Contenu détaillé

### 1️. Installation de GLPI

* Installation sur Debian 11
* Configuration Apache / PHP / MariaDB
* Sécurisation minimale  



### 2️. Configuration initiale

* Première connexion
* Paramètres généraux
* Activation des fonctionnalités principales  

![Dashboard GLPI](05-screenshots/01-dashboard-glpi.png)


### 3. Gestion des utilisateurs et profils

* Création des utilisateurs
* Profils (Self-service, Support N1, Support N2, Administrateur)
* Droits et permissions  


### 4️. Gestion des tickets

* Création d’un ticket (incident / demande)
* Catégorisation
* Priorité et urgence  

![Création d’un ticket](05-screenshots/04-creation-ticket.png)


### 5️. Cycle de vie d’un ticket
* Nouveau → En cours → Résolu → Clos
* Rôles des acteurs
* Bonnes pratiques ITIL


### 6️. Workflow Support N1 / N2

* Qualification N1
* Diagnostic
* Escalade vers N2
* Résolution et clôture


### 7️. Cas pratiques

####  Cas pratique 1 – Perte de connexion Internet

* [Incident réseau simple](04-cas-pratiques/ticket-perte-internet.md)
* Résolution au niveau N1


####  Cas pratique 2 – Poste utilisateur qui ne démarre pas

* [Incident matériel](04-cas-pratiques/ticket-poste-non-demarre.md)
* Escalade N1 → N2


##  Compétences démontrées

* ITSM / ITIL (gestion des incidents)
* GLPI (outil de ticketing)
* Support utilisateur N1 / N2
* Diagnostic technique
* Documentation professionnelle
* Méthodologie et structuration


##  Évolutions possibles

* Ajout de l’inventaire automatique (GLPI Agent)
* Lien avec un annuaire (LDAP / Active Directory)
* Ajout des SLA
* Tableaux de bord et statistiques
* Supervision et alertes


## 🎓 Objectif pédagogique & recrutement

Ce projet met en avant :

- La mise en place d’un **outil professionnel de gestion du support IT**
- La capacité à **structurer un système de gestion des tickets et des incidents**
- L’utilisation de **GLPI pour la gestion des utilisateurs, des actifs et du support**
- Une approche **organisée du support informatique et de la documentation**

👉 Projet conçu pour illustrer des compétences en **support IT, gestion des incidents et administration d’outils de helpdesk**, et servir de **support lors d’entretiens techniques ou de présentations professionnelles**.


## 👤 Auteur

**Alex** – Technicien Systèmes et Réseaux | Support IT & Infrastructure 


Ce projet s’inscrit dans mon **Home Lab personnel**, où je conçois et teste des infrastructures IT afin d’approfondir mes compétences en supportr IT, en administration systèmes, réseaux et sécurité.

🔗 LinkedIn : https://linkedin.com/in/alex-byiringiro   
💻 GitHub : https://github.com/alex-byiringiro


