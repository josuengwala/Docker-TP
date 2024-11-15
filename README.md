## Todo Application Stack

## Description

Cette stack Docker déploie une application Todo complète avec un frontend en React, un backend en Flask, une base de données MySQL, une interface de gestion de base de données (PHPMyAdmin), et un reverse proxy (Nginx).

## Pré-requis
Docker et Docker Compose doivent être installés.

## Structure du Projet
Le projet est organisé en plusieurs dossiers :

- frontend : contient l'application React.
- backend : contient l'application Flask.
- preview : contient des captures d'écran de l'application en fonctionnement.

## Installation
1. Cloner le Repository
Clonez le repository et placez-vous dans le dossier du projet :

- git clone https://github.com/Remy349/todo-app-flask-reactjs
- cd todo-app-flask-reactjs

2. Configurer les Dockerfiles
Les Dockerfiles sont déjà créés dans les dossiers respectifs :

- Frontend (React) : Un Dockerfile est configuré pour construire et servir l'application avec Nginx.
- Backend (Flask) : Le Dockerfile installe les dépendances et configure le serveur Flask pour répondre aux requêtes.

3. Configurer les Services avec Docker Compose
Le fichier docker-compose.yml configure les services suivants :

- MySQL : Base de données avec un volume persistant pour conserver les données.
- PHPMyAdmin : Interface de gestion de la base de données, accessible sur le port 8080.
- Frontend et Backend : Les services React et Flask sont configurés pour se connecter à MySQL.
- Nginx : Reverse proxy pour gérer les accès HTTP aux services.

4. Variables d’Environnement
Les informations de connexion de MySQL (nom de la base, utilisateur, mot de passe) sont définies dans .env (Backend\.env)

## Utilisation
1. Démarrer les Services
Exécutez la commande suivante pour démarrer tous les services :

docker-compose up -d

2. Accéder aux Services
- Accéder à la stack via : http://localhost/
- PHPMyAdmin : http://localhost:8081 (utilisateur : user, mot de passe : password)