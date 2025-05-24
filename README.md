# Minecraft-Project-server
Projet serveur minecraft explications


## 1. Présentation du projet

Ce projet est un serveur Minecraft moddé basé sur Fabric 1.20.1, intégrant le mod **Cobblemon** pour offrir une expérience immersive proche de Pokémon, directement dans Minecraft.  

Il vise à créer un univers riche et RP (roleplay) où les joueurs peuvent capturer, entraîner des Pokémon, combattre en arène, rejoindre des factions, participer à des événements PvP/PvE et découvrir une nouvelle dimension secrète.  

L’objectif est d’avoir un serveur compétitif mais aussi narratif avec un lore profond, des quêtes cachées, et un système de progression motivant les joueurs à coopérer et rivaliser.

---

## 2. Fonctionnalités principales

- **Système de factions** : Les joueurs peuvent créer ou rejoindre des factions. Chaque faction gagne des points selon les actions de ses membres (capturer des Pokémon, victoires, participation aux événements).  
- **Classement des factions** : Un tableau de classement dynamique est affiché en spawn, mettant en valeur les meilleures factions en temps réel.  
- **Arènes multi-dimensionnelles** : Des arènes sont placées dans différentes dimensions Minecraft (Overworld, Nether, End) avec une ambiance en ruines, permettant d’invoquer des champions grâce à des tickets spéciaux.  
- **Lootbox** : Un système de lootbox interactif permet aux joueurs de tenter leur chance pour obtenir des objets rares, avec effets visuels de spin.  
- **Événements PvP/PvE** : Des événements réguliers téléportent les joueurs dans des zones dédiées pour combattre des adversaires (joueurs ou NPC) et gagner des points bonus.  
- **Lore évolutif** : Des livres disséminés dans les arènes racontent une histoire ancienne. En les combinant, les joueurs peuvent accéder à une nouvelle dimension contenant des arènes majestueuses et des récompenses exclusives.  
- **API & Base de données** : Un backend Java Spring Boot analyse les fichiers JSON du serveur, stocke les données dans MySQL et offre un tableau de bord web pour afficher les statistiques des joueurs et factions.

---

## 3. Technologies utilisées

- **Minecraft Java Edition 1.20.1** avec **Fabric** comme mod loader  
- **Cobblemon mod** : ajoute les Pokémon dans Minecraft  
- **KubeJS** : scripts personnalisés pour gestion des événements, lootbox, et affichage en jeu  
- **Java Spring Boot** : API backend pour la collecte et le traitement des données serveur  
- **MySQL** : base de données relationnelle pour stocker statistiques et classements  
- **Apache Mina SSHD** : accès et automatisations du serveur via SSH  
- **VS Code** : environnement de développement  

---

## 4. Architecture du serveur

Le serveur est organisé en plusieurs couches :  

- **Mod Fabric + Cobblemon + KubeJS** : gestion en temps réel des interactions en jeu, données stockées dans des fichiers JSON et fichiers de configuration (`faction.dat`, `player_profile.dat`, etc.)  
- **API Java Spring Boot** : lit les données JSON exportées, les nettoie, les normalise et les injecte dans une base MySQL  
- **Base MySQL** : stockage durable et rapide des données joueurs, factions, classements  
- **Interface web (dashboard)** : consultation des statistiques via navigateur, affichage des meilleurs joueurs, factions et progression globale  

---

## 5. Structure des données importantes

- **Dossiers principaux** :  
  - `world/cobblemonplayerdata/` : données spécifiques à chaque joueur concernant leurs Pokémon et captures  
  - `world/data/academy/player_profile.dat` : correspondance UUID - pseudonyme des joueurs  
  - `factions/faction.dat` : contient les données des factions (nom, membres, puissance, relations)  

- **Champs clés** :  
  - UUID (identifiant unique joueur)  
  - Nombre de Pokémon capturés (Pokédex)  
  - Points de faction (calculés selon actions en jeu)  
  - Relations entre factions (alliances, guerres)  
  - Historique d’événements PvP/PvE  

---

## 6. Systèmes personnalisés détaillés

### 6.1 Système de factions et points

Chaque action réalisée par un joueur (capturer un Pokémon, gagner un combat, participer à un event) génère des points pour sa faction. Ces points s’agrègent pour un classement global. Un tableau en spawn affiche les factions les mieux classées.  

### 6.2 Événements PvP/PvE

Hebdomadairement, les joueurs sont téléportés dans une zone spéciale pendant 30 minutes. Ils combattent entre eux ou contre des NPC pour gagner des points supplémentaires, renforçant leur faction et leurs récompenses.  

### 6.3 Lootbox interactif

Le système de lootbox permet un « spin » visuel et sonore via KubeJS. Les joueurs peuvent gagner des objets rares ou ne rien obtenir. Ce système motive la participation et la progression.  

### 6.4 Arènes et progression

Les arènes sont en ruines et dispersées dans les dimensions Overworld, Nether, et End. Chaque arène propose un défi spécifique et permet, via des tickets d’invocation, d’affronter des champions légendaires.  

### 6.5 Lore et nouvelle dimension

Des livres contenant des fragments d’histoire sont cachés dans les arènes. En les rassemblant, les joueurs découvrent l’existence d’une nouvelle dimension secrète, riche en arènes majestueuses et en récompenses rares.  

---

## 7. API & Base de données

L’API Java Spring Boot récupère les fichiers JSON et les données sauvegardées sur le serveur, puis les insère dans une base MySQL. Cette API permet :  

- Affichage des statistiques des joueurs (captures, victoires)  
- Classement des factions en temps réel  
- Gestion des événements et points  
- Dashboard accessible depuis un navigateur web  

---
