# Utiliser une image de base Python
FROM python:3.9-slim

# Définir l'auteur
LABEL maintainer="JosueNGWALA"

# Définir le répertoire de travail dans le conteneur
WORKDIR /app

# Installer netcat-openbsd pour vérifier la disponibilité de MySQL
RUN apt-get update && apt-get install -y netcat-openbsd && rm -rf /var/lib/apt/lists/*

# Copier le fichier requirements.txt et installer les dépendances
COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

# Copier le code de l'application dans le conteneur
COPY . .

# Ajouter le script wait-for-it.sh pour attendre la disponibilité de MySQL
COPY wait-for-it.sh /wait-for-it.sh

# Rendre le script exécutable
RUN chmod +x /wait-for-it.sh

# Définir la variable d'environnement pour indiquer à Flask le fichier principal de l'application
ENV FLASK_APP=application.py
ENV FLASK_RUN_HOST=0.0.0.0

# Exposer le port 5000 pour Flask
EXPOSE 5000

# Commande pour démarrer l'application en attendant que MySQL soit prêt
CMD ["/wait-for-it.sh", "mysql:3306", "--", "sh", "-c", "flask run"]
