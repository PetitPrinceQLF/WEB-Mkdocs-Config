# Installation de Docker sur Debian

## Étape 1 : Suppression de la précédente version de Docker
Pour supprimer toute version précédente de Docker :
```bash
sudo apt remove docker docker-engine docker.io containerd runc
```

## Étape 2 : Mise en place du dépôt Docker
Pour configurer le dépôt officiel Docker :

1. Installer les dépendances nécessaires :
   ```bash
   sudo apt install ca-certificates curl gnupg lsb-release
   ```

2. Créer le répertoire pour les clés :
   ```bash
   sudo mkdir -m 0755 -p /etc/apt/keyrings
   ```

3. Télécharger et ajouter la clé GPG officielle de Docker :
   ```bash
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
   ```

4. Ajouter le dépôt Docker aux sources APT :
   ```bash
   echo \
     "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
     $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   ```

## Étape 3 : Installation de Docker
Une fois le dépôt configuré, installez Docker avec les commandes suivantes :

1. Mettre à jour les paquets disponibles :
   ```bash
   sudo apt update
   ```

2. Installer Docker et ses plugins :
   ```bash
   sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
   ```

## Étape 4 : Premier pas avec Docker

1. Vérifier les conteneurs en cours d’exécution :
   ```bash
   docker ps
   ```

2. Exécuter un conteneur Nginx :
   ```bash
   docker run nginx:latest
   ```

3. Vérifier tous les conteneurs (actifs ou arrêtés) :
   ```bash
   docker ps -a
   ```

4. Lancer un conteneur Nginx en arrière-plan :
   ```bash
   docker run -d nginx:latest
   ```

---

## Support

En cas de problème, veuillez contacter un administrateur sur le Discord officiel du serveur :
[Discord](https://discord.gg/6ffyCYq3Ea).

---

