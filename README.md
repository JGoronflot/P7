
# Bilemo

Projet 7 - Créez un web service exposant une API
[![Codacy Badge](https://app.codacy.com/project/badge/Grade/2fe5027328564975b9858d747308acdd)](https://www.codacy.com/gh/JGoronflot/P7/dashboard?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=JGoronflot/P7&amp;utm_campaign=Badge_Grade)

## Description

Vous êtes en charge du développement de la vitrine de téléphones mobiles de l’entreprise BileMo
Vous devez ainsi implémenter les fonctionnalités suivantes : 
```
* Consulter la liste des produits BileMo.
* consulter les détails d’un produit BileMo.
* Consulter la liste des utilisateurs inscrits liés à un client sur le site web.
* Consulter le détail d’un utilisateur inscrit lié à un client.
* Ajouter un nouvel utilisateur lié à un client.
* Supprimer un utilisateur ajouté par un client.
```
Contraintes :
```
* Seuls les clients référencés peuvent accéder aux API. 
* Les clients de l’API doivent être authentifiés via OAuth ou JWT.
```

## Prérequis

Choisissez votre serveur en fonction de votre système d'exploitation:

    - Composer : (https://getcomposer.org/)
    - Git : (https://git-scm.com/downloads)
    - Windows : WAMP (http://www.wampserver.com/)
    - MAC : MAMP (https://www.mamp.info/en/mamp/)
    - Linux : LAMP (https://doc.ubuntu-fr.org/lamp)
    - XAMP (https://www.apachefriends.org/fr/index.html)

## Installation
1. Clonez ou téléchargez le repository GitHub dans le dossier voulu :
```
    git clone https://github.com/JGoronflot/P7
```
2. Générer les clés SSH pour JWT:
```
    mkdir -p config/jwt
    openssl genpkey -out config/jwt/private.pem -aes256 -algorithm rsa -pkeyopt rsa_keygen_bits:4096
    openssl pkey -in config/jwt/private.pem -out config/jwt/public.pem -pubout
```
3. Configurez vos variables d'environnement tel que la connexion à la base de données/chemin vers les clés JWT `.env.local`:
```
    DATABASE_URL="mysql://DB_USER:DB_PASSWORD@127.0.0.1:3306/bilemo"
    APP_ENV=dev
    
    ###> lexik/jwt-authentication-bundle ###
    JWT_SECRET_KEY=%kernel.project_dir%/config/jwt/private.pem
    JWT_PUBLIC_KEY=%kernel.project_dir%/config/jwt/public.pem
    JWT_PASSPHRASE=yourpassphrase
    ###< lexik/jwt-authentication-bundle ###
```
4. Téléchargez et installez les dépendances back-end du projet avec [Composer](https://getcomposer.org/download/) :
```
    composer install

```
5. Créez la base de données si elle n'existe pas déjà, taper la commande ci-dessous en vous plaçant dans le répertoire du projet :
```
    php bin/console doctrine:database:create
```
6. Créez les tables de la base de données :
```
    php bin/console doctrine:schema:update --force
```
   
7. (Optionnel) Installer les fixtures pour avoir une démo de données fictives :
```
    php bin/console doctrine:fixtures:load
```
8. Lancement du serveur :
```
    symfony server:start -d
```
9. Le projet est maintenant installé, vous pouvez tester l'application sur cette URL:
```
    http://127.0.0.1:8000/api/doc
```

Documentation :
```
    - Bilemo : http://88.151.197.130:8000/api/doc
```

## Auteur

**Goronflot Jimmy**
