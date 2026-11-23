# Grist en local

## Démarrage

Avec Docker et Docker Compose installés, cloner le dépôt puis ouvrir un terminal dans le dossier `grist_training`.

1. Copier `.env.example` vers `.env` (`cp .env.example .env` sous Linux ou `Copy-Item .env.example .env` sous PowerShell).
2. Renseigner son adresse e-mail et un secret de session aléatoire dans `.env`. Si OpenSSL est installé, `openssl rand -hex 32` génère un secret adapté.
3. Lancer `docker compose up -d`. Compose télécharge l’image officielle `gristlabs/grist` au premier lancement.
4. Ouvrir [Grist](http://localhost:8484) sur le PC et suivre l’assistant de mise en route.

## Vérifier la persistance

Créer un document test, lancer `docker compose down` puis `docker compose up -d` et vérifier que le document est toujours présent.

Le volume Docker `grist-data` conserve les données au chemin `/persist` dans le conteneur. L’option `docker compose down -v` supprime ce volume et ses données.

## Déploiement sur un serveur

Cette configuration publie Grist sur l’adresse de boucle locale du PC. Pour un accès distant, prévoir HTTPS et une méthode de connexion adaptée avant de rendre l’instance accessible. Pour retrouver les documents et la configuration locale, sauvegarder et transférer les données du volume en plus des fichiers du dépôt.

[Documentation officielle de Grist auto-hébergé](https://support.getgrist.com/self-managed/)
