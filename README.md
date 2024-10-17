# Distribution Data-Quality

Ce projet contient le fichier `docker-compose.yml` ainsi que tous les fichiers `.env` nécessaires au lancement de l'application Data-Quality.

## Prérequis

### Docker
Assurez-vous que Docker est installé et fonctionne sur votre système. L'installation par défaut nécessite les éléments suivants :
- [Docker](https://docs.docker.com/engine/install/)
- [Docker Compose](https://docs.docker.com/compose/install/)

### Clone
Clonez ce dépôt pour récupérer le fichier `docker-compose.yml` ainsi que tous les fichiers nécessaires au fonctionnement de Data-Quality.

### Modifier les fichiers
Modifiez les fichiers `.env` des différents services. Attention : certaines informations, comme l'utilisateur pour la base de données (BDD), sont déjà renseignées, mais il est fortement recommandé de les personnaliser.

Renseignez la clé publique de votre serveur SFTP dans le fichier `known_hosts`

### Dossier specific

Ce dossier contient les différents éléments spécifiques à chaque installation.
- default_banner.png
- default_logo.png
- config.js
- spec.css

default_banner.png et default_logo.png sont le logo et la bannière, vous pouvez les modifier en remplacant les images par les votre en gardant le même nom de fichier.

config.js contient l'url du back à modifier.

spec.css permet de surcharger le css de l'application.

### Token AWS
Assurez-vous de disposer d'un token de connexion pour récupérer les images Docker depuis l'ECR d'AWS.

## Lancement de data-quality
Pour démarrer Data-Quality, exécutez la commande suivante :

`docker compose -p dataquality up`

## Composition du docker-compose.yml
La stack docker est composée de cinq services :
* `dataquality-postgres`
* `dataquality-back`
* `dataquality-front`
* `dataquality-avro`
* `dataquality-integrator`

### dataquality-postgres
Ce service utilise l'image Docker Postgres avec une persistance des données via le volume `dataquality-postgres`.
### dataquality-back
Ce service utilise l'image Docker du back de Data-Quality à récupérer sur l'ECR AWS ainsi que le fichier `.env.back`
### dataquality-front
Ce service utilise l'image Docker du front de Data-Quality à récupérer sur l'ECR AWS.
### dataquality-avro
Ce service utilise l'image Docker du convertisseur Avro à récupérer sur l'ECR AWS ainsi que le fichier `.env.avro`
### dataquality-integrator
Ce service utilise l'image Docker du l'intégrateur Data-Quality à récupérer sur l'ECR AWS ainsi que le fichier `.env.integrator`