# Guide : Créer un Serveur Minecraft Conteneurisé

Ce guide vous explique comment créer un serveur Minecraft conteneurisé en utilisant Docker et `docker-compose`.

## Prérequis

Avant de commencer, assurez-vous d'avoir installé les outils suivants :
- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Étape 1 : Préparer le fichier `docker-compose`

Créez un fichier `docker-compose.yml` dans un répertoire de votre choix et collez-y la configuration suivante :

```yaml
version: "3"

services:
  mc:
    container_name: minecraft-cobblemon
    image: itzg/minecraft-server:java21
    ports:
      - 30010:25565
    stdin_open: true
    restart: unless-stopped
    logging:
      driver: "json-file"
      options:
        max-size: "50m"
        max-file: "5"

    environment:
      # Server options
      MEMORY: 10G
      TYPE: AUTO_CURSEFORGE
      CF_API_KEY: '$$2a$$10$$z/76rVbmGrf8RNP4/eNw6./ycmYWLWR4eBcUFzm.8crO6WXchiawa'
      CF_SLUG: cobblemon-fabric
      CF_FILE_ID: "6035005"
      EULA: "TRUE"
      SERVER_PORT: '25565'
      VERSION: 1.21.1
      # Pack options
      SKIP_GENERIC_PACK_UPDATE_CHECK: 'true'
      USE_MODPACK_START_SCRIPT: "false"
      ENABLE_WHITELIST: 'false'
    volumes:
      - cobblemon:/data

volumes:
  cobblemon:
    name: cobblemon
```

## Étape 2 : Lancer le serveur

1. **Accédez au répertoire contenant le fichier `docker-compose.yml` :**
   ```bash
   cd /chemin/vers/votre/repertoire
   ```

2. **Démarrez le conteneur :**
   ```bash
   docker-compose up -d
   ```

   L'option `-d` lance le conteneur en arrière-plan.

## Étape 3 : Vérifiez le statut du serveur

Pour vous assurer que le serveur fonctionne correctement, utilisez la commande suivante :
```bash
docker logs minecraft-cobblemon
```

Cette commande affiche les journaux du serveur.

## Étape 4 : Gérer le serveur

### Arrêter le serveur
Pour arrêter le serveur, exécutez :
```bash
docker-compose down
```

### Mettre à jour l'image Docker
Pour mettre à jour l'image Docker, exécutez :
```bash
docker-compose pull
docker-compose up -d
```

## Options Personnalisées

Vous pouvez ajuster les paramètres suivants dans le fichier `docker-compose.yml` :
- **Mémoire** : Changez la valeur de `MEMORY` pour allouer plus ou moins de RAM au serveur.
- **Port** : Modifiez le port exposé en ajustant `30010:25565`.
- **Pack CurseForge** : Remplacez les valeurs de `CF_SLUG` et `CF_FILE_ID` pour utiliser un autre modpack.

## Étape 5 : Sauvegarder les données

Le volume `cobblemon` contient les données du serveur. Vous pouvez les sauvegarder en copiant ce volume :
```bash
docker run --rm -v cobblemon:/data -v $(pwd):/backup alpine tar czf /backup/cobblemon_backup.tar.gz /data
```

## Étape 6 : Restaurer une sauvegarde

Pour restaurer une sauvegarde, utilisez la commande suivante :
```bash
docker run --rm -v cobblemon:/data -v $(pwd):/backup alpine tar xzf /backup/cobblemon_backup.tar.gz -C /
```

## Support

En cas de problème, consultez les journaux du serveur avec :
```bash
docker logs minecraft-cobblemon
```

Ou visitez la [documentation officielle de l'image Docker itzg/minecraft-server](https://hub.docker.com/r/itzg/minecraft-server).

