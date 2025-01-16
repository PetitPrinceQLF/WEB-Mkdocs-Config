# Guide d'installation et d'utilisation de Git

## Installation de Git

### Étape 1 : Installation de Git

1. Téléchargez Git depuis [git-scm.com](https://git-scm.com/).
2. Installez-le en sélectionnant l'option pour ajouter Git à `PATH`.
3. Une fois installé, ouvrez Git Bash pour accéder aux commandes Git.

### Étape 2 : Configuration de Git

1. Configurez votre nom d'utilisateur :
   ```bash
   git config --global user.name "Rudy David"
   ```

2. Configurez votre email :
   ```bash
   git config --global user.email "tonemail@example.com"
   ```

3. Vérifiez la configuration :
   ```bash
   git config --list
   ```

---

## Utilisation de Git

### Étape 3 : Utilisation de SSH (facultatif)

1. Générez une clé SSH :
   ```bash
   ssh-keygen -t rsa -b 4096 -C "tonemail@example.com"
   ```

2. Ajoutez la clé à l'agent SSH :
   ```bash
   eval $(ssh-agent -s) 
   ssh-add ~/.ssh/id_rsa
   ```

3. Copiez la clé publique :
   ```bash
   cat ~/.ssh/id_rsa.pub
   ```

4. Ajoutez la clé dans GitHub (Settings > SSH and GPG keys).

### Étape 4 : Cloner un dépôt GitHub

1. Clonez un dépôt avec HTTPS :
   ```bash
   git clone https://github.com/username/repo.git
   ```

2. Ou clonez avec SSH :
   ```bash
   git clone git@github.com:username/repo.git
   ```

### Étape 5 : Travailler avec Git

1. Ajoutez les fichiers au suivi :
   ```bash
   git add .
   ```

2. Créez un commit avec un message :
   ```bash
   git commit -m "Message du commit"
   ```

3. Poussez les changements vers GitHub :
   ```bash
   git push origin main
   ```

4. Récupérez les mises à jour du dépôt distant :
   ```bash
   git pull origin main
   ```

### Étape 6 : Créer et basculer sur une branche

1. Créez une nouvelle branche :
   ```bash
   git branch nom-de-la-branche
   ```

2. Basculez sur une branche :
   ```bash
   git checkout nom-de-la-branche
   ```

3. Créez et basculez sur une branche en une seule étape :
   ```bash
   git checkout -b nom-de-la-branche
   ```

4. Vérifiez la branche active :
   ```bash
   git branch
   ```

### Étape 7 : Initialiser un dépôt Git

1. Initialisez Git dans un répertoire :
   ```bash
   git init
   ```

2. Vérifiez l'état du dépôt :
   ```bash
   git status
   ```

---

## Support

En cas de problème, veuillez contacter un administrateur sur le Discord officiel du serveur :
[Discord](https://discord.gg/6ffyCYq3Ea).

---

